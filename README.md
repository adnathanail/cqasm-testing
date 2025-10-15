# cqasm-testing

## Quantum Inspire CLI Usage instructions

### First setup

Install [pipx](https://pipx.pypa.io/stable/installation)

Install the QI tool
```bash
pipx install quantuminspire
```

Login to the Quantum Inspire platform
```bash
qi login
```

### Running a circuit

[Docs](https://pypi.org/project/quantuminspire/)

Get the ID of the backend you want to run on
```bash
qi backends list

#┏━━━━┳━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━┓
#┃ id ┃ name        ┃ status  ┃ is_hardware ┃ supports_raw_data ┃ number_of_qubits ┃ max_number_of_shots ┃
#┡━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━┩
#│ 1  │ QX emulator │ IDLE    │ False       │ True              │ 10               │ 2048                │
#│ 3  │ Starmon-7   │ IDLE    │ True        │ True              │ 7                │ 19192               │
#│ 4  │ Tuna-5      │ OFFLINE │ True        │ True              │ 5                │ 19192               │
#│ 5  │ Ry emulator │ IDLE    │ True        │ True              │ 9                │ 1024                │
#└────┴─────────────┴─────────┴─────────────┴───────────────────┴──────────────────┴─────────────────────┘
```

Upload a `.cq` file for running
```bash
qi files upload algorithms/deutsch-algorithm/deutsch-algorithm.cq 1 --num-shots 16

#Upload file with name: algorithms/deutsch-algorithm/deutsch-algorithm.cq
#job_id 200380
```

Get the results of a job
```bash
qi results get 200380

#Raw results:
#{
#    'items': [
#        {
#            'id': 193487,
#            'created_on': datetime.datetime(2025, 10, 15, 14, 6, 50, 392399, tzinfo=TzInfo(0)),
#            'job_id': 200380,
#            'execution_time_in_seconds': 0.008474,
#            'shots_requested': 1024,
#            'shots_done': 1024,
#            'results': {'0110': 1024},
#            'raw_data': None
#        }
#    ],
#    'total': 1,
#    'page': 1,
#    'size': 50,
#    'pages': 1
#}
```

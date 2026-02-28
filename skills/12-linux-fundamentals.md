# Linux Fundamentals

**Source:** The Linux Command Line (William Shotts) + How Linux Works, 3rd Edition (Brian Ward)
**Category:** Supplementary (E) — ถ้าพื้นฐาน Linux ยังไม่แน่น (สำคัญมากตอน deploy จริง)
**Intention:** พื้นฐาน command line, shell, internals, networking, virtualization, containers

---

## Key Skills

### 1. Command Line Essentials
- **Navigation** — `cd`, `ls`, `pwd`, `find`, `locate`
- **File operations** — `cp`, `mv`, `rm`, `mkdir`, `chmod`, `chown`
- **Text processing** — `cat`, `grep`, `sed`, `awk`, `sort`, `uniq`, `wc`, `cut`
- **Piping & redirection** — `|`, `>`, `>>`, `<`, `2>&1`
- **File viewing** — `head`, `tail`, `less`, `tail -f` (follow logs)
- **Archive & compression** — `tar`, `gzip`, `zip`, `unzip`

### 2. Shell Scripting
- Bash scripting basics: variables, conditionals, loops
- Script structure: shebang (`#!/bin/bash`), arguments (`$1`, `$@`, `$#`)
- Exit codes and error handling (`set -euo pipefail`)
- Common patterns: setup scripts, deployment scripts, health checks
- Use shellcheck for linting shell scripts

### 3. Process Management
- Process lifecycle: `fork`, `exec`, `wait`
- View processes: `ps`, `top`, `htop`
- Signal handling: `SIGTERM`, `SIGKILL`, `SIGHUP`
- Background processes: `&`, `nohup`, `screen`, `tmux`
- System services: `systemd`, `systemctl`, `journalctl`

### 4. User & Permission Management
- Users and groups: `useradd`, `usermod`, `groups`
- File permissions: `rwx`, octal notation (755, 644)
- Ownership: `chown user:group file`
- Sudo and privilege escalation
- SSH key management: `ssh-keygen`, `authorized_keys`, `ssh-agent`

### 5. Networking
- Network configuration: `ip`, `ifconfig`, `netstat`/`ss`
- DNS resolution: `dig`, `nslookup`, `/etc/hosts`, `/etc/resolv.conf`
- Connectivity testing: `ping`, `traceroute`, `curl`, `wget`
- Ports and firewalls: `iptables`, `ufw`, `firewalld`
- `netstat -tlnp` / `ss -tlnp` — see what's listening on which ports

### 6. Package Management
- Debian/Ubuntu: `apt update`, `apt install`, `dpkg`
- RHEL/CentOS: `yum`, `dnf`, `rpm`
- Keep systems updated for security patches
- Understand package dependencies

### 7. Filesystem & Storage
- Linux filesystem hierarchy: `/etc`, `/var`, `/home`, `/tmp`, `/opt`
- Disk usage: `df -h`, `du -sh`
- Mount points and `/etc/fstab`
- Log files in `/var/log/` — `syslog`, `auth.log`, application logs

### 8. Containers & Virtualization
- **Docker basics** — `build`, `run`, `stop`, `exec`, `logs`, `ps`
- Dockerfile: `FROM`, `COPY`, `RUN`, `CMD`, `EXPOSE`
- Docker Compose for multi-container setups
- Container networking and volumes
- Understanding how containers use Linux namespaces, cgroups, and overlay filesystems

### 9. Environment & Configuration
- Environment variables: `export`, `.bashrc`, `.profile`, `.env`
- Configuration files: `/etc/` conventions
- `cron` for scheduled tasks
- `systemd` service files for daemon management

---

## Practical Application for Web Apps

| Skill | When to Apply |
|-------|---------------|
| Command line | Daily development, debugging, log analysis |
| Shell scripting | Build scripts, CI/CD automation, deployment |
| Process management | Managing app processes, debugging hangs/crashes |
| Networking | Debugging connectivity issues, firewall config |
| SSH | Accessing production servers securely |
| Docker | Containerizing your app, dev environment parity |
| Logs | Diagnosing production issues via `tail -f`, `grep`, `journalctl` |

---

## Checklist for Deploy Readiness

- [ ] Comfortable navigating filesystem and managing files via CLI
- [ ] Can write basic shell scripts for automation
- [ ] Understand file permissions and SSH key authentication
- [ ] Can debug network connectivity issues (ports, DNS, firewalls)
- [ ] Know how to check running processes and system resources
- [ ] Can read and search application logs efficiently
- [ ] Can build and run Docker containers
- [ ] Understand basic firewall and security hardening

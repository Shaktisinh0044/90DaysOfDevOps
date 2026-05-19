### 1. Kernel
- Core brain of Linux
- Manages CPU, RAM, disk, network
- Only part that talks directly to hardware
- You never touch it directly

### 2. User Space
- Where your apps and processes live
- Chrome, Docker, Nginx, VS Code all run here
- Apps request resources from kernel via system calls

### 3. systemd (init system)
- First process that starts when Linux boots (PID 1)
- Starts all other services and processes
- Manages service lifecycle (start, stop, restart)

---

## What is a Process?

- Every running program = a process
- Each process has a unique **PID** (Process ID)
- Processes are created by the kernel when you run a command or start a service
- Example: When you open Chrome → kernel creates Process #1234

---

## Process States

Every process can be in one of these states:

| State     | Meaning                                    |
|-----------|--------------------------------------------|
| **Running**   | Actively using CPU right now           |
| **Sleeping**  | Waiting for I/O or an event            |
| **Stopped**   | Paused manually (Ctrl+Z)               |
| **Zombie**    | Finished execution but not cleaned up yet |

### Why Zombie Matters
- Process is done but parent hasn't collected exit status yet
- Takes up space in process table
- If you see many zombies → parent process has a bug

---

## What is systemd?

systemd is the **service manager** for Linux.

### What it does:
- Starts services on boot (Nginx, Docker, SSH)
- Restarts crashed services automatically
- Manages logs for all services
- Controls what runs when system starts

### Why it matters for DevOps:
- Service crashed? → systemd can auto-restart it
- Want to see logs? → journalctl reads from systemd
- Need to start/stop a service? → systemctl is the command

### Key Concept
systemd is **PID 1** — the very first process Linux runs. Everything else is started by systemd or its children.

---

## 5 Commands I'll Use Daily

| Command                  | What It Does                          |
|--------------------------|---------------------------------------|
| `ps aux`                 | List all running processes            |
| `top`                    | Live view of CPU/RAM usage            |
| `systemctl status nginx` | Check if nginx service is running     |
| `journalctl -u nginx`    | View logs for nginx service           |
| `pstree`                 | See process tree (who started what)   |

---

## Why This Matters for DevOps

- Every server runs Linux
- Crashed service? → Check with `systemctl status` and `journalctl`
- High CPU usage? → Find the culprit with `top` and `ps`
- Container issues? → Docker containers are just Linux processes
- Debugging production? → systemd logs tell you what happened


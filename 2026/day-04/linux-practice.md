# Day 04 Linux Practice

## Process Checks

### Command 1
```bash
ps aux
```

Output:
```bash
root       1  0.0  systemd
```

Learned:
Shows all running processes.

---

### Command 2
```bash
top
```

Learned:
Shows live CPU and memory usage.

---

## Service Checks

### Command 3
```bash
systemctl status ssh
```

Learned:
SSH service is active and running.

---

### Command 4
```bash
systemctl list-units --type=service
```

Learned:
Lists all active services.

---

## Log Checks

### Command 5
```bash
journalctl -u ssh
```

Learned:
Shows logs related to SSH service.

---

### Command 6
```bash
tail -n 20 /var/log/syslog
```

Learned:
Shows recent system logs.

---

## Mini Troubleshooting

1. Checked SSH service status
2. Viewed SSH logs
3. Restarted SSH service
4. Verified service became active

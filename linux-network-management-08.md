# NETWORK MANAGEMENT

Network management in Linux involves **monitoring and managing network connections, ports, and network services**.

---

## Common Ports

| Service |   Port |
| ------- | -----: |
| SSH     |   `22` |
| HTTP    |   `80` |
| HTTPS   |  `443` |
| MySQL   | `3306` |
| SMTP    |   `25` |
| Jenkins | `8080` |
| DNS     |   `53` |

### Simple Example

```text
SSH     → 22
HTTP    → 80
HTTPS   → 443
MySQL   → 3306
Jenkins → 8080
DNS     → 53
```

---

# Check Listening Ports

To check which ports are currently listening on the server:

```bash
netstat -lntp
```

### Options

```text
-l → Show listening ports
-n → Show port numbers instead of resolving names
-t → Show TCP connections
-p → Show process/PID using the port
```

### Remember

```text
netstat
   ↓
-l → Listening
-n → Numeric
-t → TCP
-p → Process / PID
```

### Example Output

```text
Proto  Local Address    PID/Program name
tcp    0.0.0.0:22       1234/sshd
tcp    0.0.0.0:80       2345/nginx
tcp    0.0.0.0:8080     3456/java
```

This helps identify **which service is listening on which port**.

---

## Quick Commands

```bash
# Check listening TCP ports
netstat -lntp

# Search for a specific port
netstat -lntp | grep 8080

# Search for a specific service
netstat -lntp | grep nginx
```

> **Note:** On many modern Linux systems, `ss` is preferred over `netstat` because `netstat` may not be installed by default.

```bash
ss -lntp
```

### Easy Memory

```text
-l → Listening
-n → Numeric
-t → TCP
-p → Process/PID
```

**Network Management → Ports → Listening Ports → Process/PID**

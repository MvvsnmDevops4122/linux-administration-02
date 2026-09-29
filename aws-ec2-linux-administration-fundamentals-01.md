# AWS EC2 & Linux Administration Fundamentals

## AWS Region

> **AWS Region:** An AWS Region is a geographical location where AWS has multiple data centers.

### Examples

```text
us-east-1   → N. Virginia
ap-south-1  → Mumbai
````

> **Remember:** Region = Geographical location

---

## Availability Zone (AZ)

> **Availability Zone (AZ):** An Availability Zone (AZ) is an isolated location within an AWS Region, consisting of one or more data centers.

```text
             Region
                │
    ┌────────┼────────┐
    ↓           ↓           ↓
  AZ-1        AZ-2         AZ-3

ap-south-1a  ap-south-1b   ap-south-1c
```

> **Data Center = AZ**

---

# Traditional Data Center

Before cloud computing, organizations commonly maintained their own physical data centers.

### A Data Center Contains

* Servers
* Storage
* Networking equipment
* Power systems
* Cooling systems
* Physical security
* Operating systems
* Backup systems

> **The organization is responsible for maintaining the physical infrastructure.**

---

# Migration to Cloud

Organizations can migrate applications and infrastructure from traditional data centers to cloud platforms such as AWS.

---

# Latency

> **Latency:** Delay in communication between systems.

```text
Nearby Region → Usually lower latency
Far Region    → Usually higher latency
```

---

# What is a Computer?

> **A computer is an IP-enabled device that can connect to a network and process data.**

### A Typical Computer Consists Of

```text
Computer
   │
   ├── CPU       → Processing
   ├── RAM       → Temporary memory
   ├── Storage   → Long-term/Persistent storage
   └── OS        → Manages hardware and provides services to applications
```

---

# Computers Are Named Based on Their Purpose

```text
Server   : run/hosts app (website, DB, apps)
PC       : personal tasks (browsing, watching, banking)
Mobile   : Communication
```

---

# Hardware and Software

A computer system consists of **hardware and software**.

### Hardware

```text
CPU, RAM, Storage
```

### Software

```text
OS
```

> **OS is software that manages hardware resources and provides an environment for applications to run.**

### Examples

* Linux
* Windows
* Chrome
* VS Code

---

# Linux

> **Linux is a kernel.**

> **Linux is an Open-source Unix-like operating system.**

> **Linus Torvalds created the Linux kernel and Git (1991).**

> **The Linux Kernel was developed mainly using the C programming language.**

---

# Kernel

> **The kernel is the core part of an operating system. It helps software communicate with hardware.**

---

# Unix

> **Unix is an operating system family.**

> **Linux follows many Unix concepts/principles, so Linux is called a Unix-like operating system.**

> **Linux is not Unix. Linux is Unix-like.**

---

# Linux Distribution / OS

> **A Linux Distribution is a complete operating system built around the Linux Kernel, along with system tools, libraries, and package management tools.**

### Examples

* RHEL / Red Hat
* Ubuntu
* Debian
* Oracle Linux
* Fedora
* Amazon Linux

---

# Linux Architecture

> **Linux architecture explains how a user interacts with the computer hardware through the Linux operating system.**

```text
User → Application → Utilities → Shell → Kernel → Hardware
```

### 1. User

> **A user is a person who interacts with the Linux system to perform tasks.**

**Example:** You want to create a file.

---

### 2. Application

> **Applications are programs that allow users to perform specific tasks.**

**Examples:**

* Git
* Jenkins
* VS Code
* Web Browser

---

### 3. Utilities

> **Utilities are Linux tools/commands used to perform common system tasks.**

**Examples:**

```text
ls
cp
mv
mkdir
grep
```

**Action:** Utilities perform tasks such as listing, copying, moving, and searching files.

---

### 4. Shell

> **A shell is a command-line interface that allows users to interact with the operating system by executing commands.**

**Examples:**

* Bash
* Zsh

---

### 5. Kernel

> **The kernel is the core of Linux. It acts as a bridge between software and hardware.**

---

### 6. Hardware

> **Hardware is the physical part of the computer.**

### Examples

* CPU
* RAM
* HDD/SSD
* Network Card
* Keyboard

> **Hardware provides the actual resources needed to run applications.**

---

# AWS SECURITY GROUP / FIREWALL

## Firewall

> **A firewall controls network traffic based on rules.**

## AWS Security Group

> **A Security Group is a virtual firewall for AWS resources such as EC2 instances.**

---

## Inbound / Ingress Traffic

> **Inbound/Ingress traffic → traffic coming into EC2**

### Examples

```text
SSH    → TCP 22
HTTP   → TCP 80
HTTPS  → TCP 443
```

### Example Source

```text
0.0.0.0/0        → Any IPv4 address
```

> **Allows traffic from any IPv4 address on the internet.**

```text
122.183.36.3/32  → Only IP 122.183.36.3
```

> **Allows traffic only from the single IP address 122.183.36.3.**

---

## Outbound / Egress Traffic

> **Outbound/Egress traffic → traffic going out of EC2**

---

# Authentication

> **Authentication means verifying who you are.**

## Authentication Mechanisms

```text
What you know → Username, Password, PIN
What you have → OTP, Security Key, Token
What you are  → Fingerprint, Retina, Face, Palm
```

---

# SSH Key

> **An SSH key is used to securely authenticate and connect to a remote server.**

### Generate SSH Key

```bash
ssh-keygen -f <file-name>
```

This generates a key pair:

```text
Private Key → Keep Secret
Public Key  → Can be shared
```

---

# Protocol

> **A protocol is a set of rules that defines how devices communicate with each other over a network.**

### Example

```text
https://www.facebook.com/ → HTTPS
```

> **HTTPS → Used for secure web communication.**

---

# SSH

> **SSH = Secure Shell**

> **SSH is a protocol used to securely connect to a remote system.**

### Example

```bash
ssh -i <private-key> ec2-user@<IP-address>
```

> **Default SSH Port: SSH → TCP 22**

---

# NETWORK PORTS

TCP and UDP port numbers range from:

```text
0 – 65535
```

> **Total: 65,536 ports**

---

# Common Network Protocols

```text
HTTP, HTTPS, SSH, FTP, SMTP, DNS, TCP, UDP, DHCP
```

### Important

```text
TCP and UDP
→ Transport-layer protocols

HTTP, HTTPS, SSH, FTP, SMTP, DNS, DHCP
→ Application-layer protocols
```

---

# Protocol + IP Address + Port

```text
https://example.com:443
```

```text
Protocol → HTTPS
Port     → 443
```

> **The hostname `example.com` is resolved to an IP address through DNS.**

---

# ACCESSING AN EC2 SERVER

Suppose:

```text
Public IP  → <public-ip>
SSH Port   → 22
User       → ec2-user
Key        → mykey.pem
```

### Command

```bash
ssh -i mykey.pem ec2-user@<public-ip>
```

---

# Client–Server Architecture

> **Client–Server architecture is a distributed architecture where the client sends a request to the server, and the server processes the request and sends a response back to the client.**

### Process

```text
Client → Request → Server → Database
Client ← Response ← Server
```

### Simple Flow

```text
Client  ─────────→  Server
          Request

Client  ←─────────  Server
          Response
```

---

## Example: Opening `https://google.com`

```text
Browser → Client
```

1. You enter `https://google.com`
2. Browser sends a request to Google's server.
3. Google server receives and processes the request.
4. Google server sends a response back.
5. Browser displays the Google webpage.

---

# WINDOWS vs LINUX PATH FORMAT

### Windows

```text
C:\devops\daws-90s
```

### Linux

```text
/c/devops/daws-90s
```

> **Note:** `/c/...` is commonly seen in Git Bash on Windows. A native Linux path would normally look like `/home/user/...`.

---

# LINUX DIRECTORY PATHS

## Absolute Path

> **An absolute path starts from the root directory `/`.**

### Example

```text
/c/devops/daws-90s
```

---

## Relative Path

> **A relative path starts from the current directory.**

### Example

```text
daws-90s/daws-90s
```

### Remember

```text
Absolute → Starts from /
Relative → Starts from current location
```

---

# LINUX USERS

Linux has different users and privilege levels.

## Normal User

> **A normal user has limited permissions to perform system-level operations.**

Prompt commonly ends with:

```text
$
```

### Example

```text
[ec2-user@server ~]$
```

---

## Root User

> **A root user has full administrative privileges on the Linux system.**

Prompt commonly ends with:

```text
#
```

### Example

```text
[root@server ~]#
```

---

# SUDO

> **`sudo` allows an authorized user to execute a command with elevated privileges.**

### Example

```bash
sudo yum install nginx
```

> **Elevated privileges = higher permissions to perform administrative tasks.**

```
```

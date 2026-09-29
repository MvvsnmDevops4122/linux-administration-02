# PROCESS MANAGEMENT

A **process** is a running instance of a program.

When a program is executed, the Linux operating system creates a process to run that program.

### Example

```bash
cat devops.txt
```

When this command runs, Linux creates a process for `cat`.

```text
Program
   ↓
Execute
   ↓
Process
   ↓
Running
   ↓
Complete
```

> **Simple meaning:** A program is a set of instructions, while a process is that program while it is running.

---

## Process ID (PID)

Every process in Linux has a unique **PID (Process ID)**.

```text
PID → Identifies a running process
```

Example:

```text
Process → nginx
PID     → 1234
```

### PPID

**PPID (Parent Process ID)** identifies the process that created the current process.

```text
Parent Process
      ↓
   Child Process
```

A process can create another process.

---

# Process Commands

## 1. Show Current User's Processes

```bash
ps
```

Displays processes associated with the current terminal/session.

---

## 2. Show All Processes

```bash
ps -ef
```

Displays processes running on the system.

Commonly used for process investigation.

---

## 3. Search for a Process

```bash
ps -ef | grep <process-name>
```

### Example

```bash
ps -ef | grep nginx
```

This searches the process list for `nginx`.

---

## 4. Show Process for a Specific User

```bash
ps -u <username>
```

### Example

```bash
ps -u satya
```

---

# Background and Foreground Processes

## Background Process

A process that runs in the **background**, allowing the terminal to be used for other commands.

### Example

```bash
ping google.com &
```

The `&` runs the command in the background.

```text
Command
   ↓
Process
   ↓
Background
```

---

## Foreground Process

A process that runs directly in the terminal and occupies the terminal until it finishes or is moved to the background.

### Example

```bash
ping google.com
```

```text
Command
   ↓
Process
   ↓
Foreground Terminal
```

### Difference

| Foreground                 | Background                              |
| -------------------------- | --------------------------------------- |
| Runs directly in terminal  | Runs in background                      |
| Occupies the terminal      | Terminal can be used for other commands |
| Example: `ping google.com` | Example: `ping google.com &`            |

---

# Move a Process to Background

Press:

```text
Ctrl + Z
```

This **suspends** the foreground process.

Then use:

```bash
bg
```

to continue it in the background.

To bring it back to the foreground:

```bash
fg
```

---

# Killing a Process

## Normal Termination

```bash
kill <PID>
```

### Example

```bash
kill 1234
```

This sends the default **SIGTERM (15)** signal, requesting the process to terminate gracefully.

---

## Force Kill

```bash
kill -9 <PID>
```

### Example

```bash
kill -9 1234
```

`-9` sends **SIGKILL**, which forcefully terminates the process.

> Use `kill -9` only when a process does not terminate normally.

---

# Terminate Process by Name

```bash
pkill <process-name>
```

### Example

```bash
pkill nginx
```

---

## Force Kill Process by Name

```bash
pkill -9 <process-name>
```

### Example

```bash
pkill -9 nginx
```

---

# Important Process Commands

| Purpose                    | Command                 |
| -------------------------- | ----------------------- |
| Current user's processes   | `ps`                    |
| All processes              | `ps -ef`                |
| Search process             | `ps -ef  | grep <name>` |
| User's processes           | `ps -u <username>`      |
| Run in background          | `<command> &`           |
| Suspend foreground process | `Ctrl + Z`              |
| Terminate by PID           | `kill <PID>`            |
| Force terminate by PID     | `kill -9 <PID>`         |
| Terminate by name          | `pkill <name>`          |
| Force terminate by name    | `pkill -9 <name>`       |

---

# Process Management Flow

```text
Program
   ↓
Execute
   ↓
Process Created
   ↓
PID Assigned
   ↓
Process Runs
   ↓
Monitor / Manage
   ↓
Process Completes
```

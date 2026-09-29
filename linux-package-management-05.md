# PACKAGE MANAGEMENT

**Package Management** is the process of **installing, removing, updating, searching, and managing software packages** on a Linux system.

A **package manager** helps administrators install software and manage its dependencies.

---

## 1. What is a Package?

A **package** is a bundle of software files required to install and run an application on a Linux system.

### Examples

```text
nginx
git
vim
httpd
mysql
```

A package can contain:

* Application binaries
* Configuration files
* Libraries
* Documentation
* Metadata
* Dependency information

---

## 2. What is a Package Manager?

A **package manager** is a tool used to manage software packages.

It can perform operations such as:

```text
Search
   ↓
Install
   ↓
Update
   ↓
Remove
   ↓
Query / Verify
```

### Common Package Managers

| Linux Distribution | Package Manager |
| ------------------ | --------------- |
| RHEL               | `dnf`           |
| Rocky Linux        | `dnf`           |
| AlmaLinux          | `dnf`           |
| CentOS Stream      | `dnf`           |
| Amazon Linux       | `dnf`           |
| Fedora             | `dnf`           |
| Ubuntu             | `apt`           |
| Debian             | `apt`           |

---

# 3. DNF

**DNF** stands for **Dandified YUM**.

It is the modern package-management utility used by many RPM-based Linux distributions.

### Syntax

```bash
dnf install <package-name>
```

### Example

```bash
dnf install nginx
```

---

# 4. YUM vs DNF

## YUM

YUM was widely used on older RHEL-based systems.

```bash
yum install nginx
```

## DNF

DNF is the modern replacement for YUM on current RHEL-based systems.

```bash
dnf install nginx
```

### Simple Way to Remember

```text
YUM → Older package-management tool
DNF → Modern package-management tool
```

---

# 5. Package Repository

A **package repository** is a location that stores software packages and package metadata.

The package manager connects to configured repositories to:

* Search for packages
* Download packages
* Install packages
* Download required dependencies
* Get package updates

---

# 6. Repository Configuration

On RHEL-based systems, repository configuration files are commonly stored under:

```bash
/etc/yum.repos.d/
```

List repository configuration files:

```bash
ls -l /etc/yum.repos.d/
```

---

# 7. Linux Package Management Flow

```text
YUM / DNF
    ↓
/etc/yum.repos.d/
    ↓
Repository Configuration (.repo files)
    ↓
Repository URL & Information
    ↓
Connect to Package Repository
    ↓
Find Required Package
    ↓
Download Package
    ↓
Resolve Dependencies
    ↓
Install Package
```

---

# 8. Search for a Package

### Syntax

```bash
dnf search <package-name>
```

### Example

```bash
dnf search nginx
```

---

# 9. Check Package Information

### Syntax

```bash
dnf info <package-name>
```

### Example

```bash
dnf info nginx
```

This displays information such as:

* Package name
* Version
* Architecture
* Repository
* Package size
* Description

---

# 10. Install a Package

### Syntax

```bash
dnf install <package-name>
```

### Example

```bash
dnf install nginx
```

To automatically answer **yes** to confirmation prompts:

```bash
dnf install nginx -y
```

### `-y`

```text
-y → Automatically answers yes to confirmation prompts
```

---

# 11. Check Installed Packages

To list all installed packages:

```bash
dnf list installed
```

To check a specific package:

```bash
dnf list installed | grep nginx
```

Another useful command:

```bash
rpm -q nginx
```

---

# 12. Remove a Package

### Syntax

```bash
dnf remove <package-name>
```

### Example

```bash
dnf remove nginx
```

---

# 13. Update a Specific Package

### Syntax

```bash
dnf update <package-name>
```

### Example

```bash
dnf update nginx
```

---

# 14. Update All Packages

```bash
dnf update
```

This checks for available updates and updates installed packages.

---

# 15. List Available Packages

```bash
dnf list available
```

This displays packages available from configured repositories that are not currently installed.

---

# 16. List Installed Packages

```bash
dnf list installed
```

To check a particular package:

```bash
dnf list installed | grep nginx
```

---

# 17. Check Configured Repositories

```bash
dnf repolist
```

This shows the currently enabled repositories.

To display all repositories:

```bash
dnf repolist all
```

---

# 18. Package Management Commands

| Operation               | Command                      |
| ----------------------- | ---------------------------- |
| Search package          | `dnf search <package-name>`  |
| Package information     | `dnf info <package-name>`    |
| Install package         | `dnf install <package-name>` |
| Remove package          | `dnf remove <package-name>`  |
| Update package          | `dnf update <package-name>`  |
| Update all packages     | `dnf update`                 |
| List available packages | `dnf list available`         |
| List installed packages | `dnf list installed`         |
| Check repositories      | `dnf repolist`               |
| List all repositories   | `dnf repolist all`           |

---

# 19. RPM

**RPM** is a low-level package management tool used for RPM packages and the RPM package database.

### Syntax

```bash
rpm -q <package-name>
```

### Example

```bash
rpm -q nginx
```

---

# 20. DNF vs RPM

```text
RPM
 ↓
Low-level package management
 ↓
Works with RPM packages and package database
```

```text
DNF
 ↓
High-level package management
 ↓
Repository management
 ↓
Package installation
 ↓
Dependency resolution
```

### Simple Difference

```text
RPM → Low-level package management

DNF → Repository + Package management
       + Dependency resolution
```

---

# 21. Package Management Flow — Quick Revision

```text
User
 ↓
dnf install <package>
 ↓
Repository Configuration
 ↓
Repository Information
 ↓
Find Package
 ↓
Resolve Dependencies
 ↓
Download Package
 ↓
Install Package
```

---

# 22. Important Commands to Remember

```bash
# Search package
dnf search nginx

# Check package information
dnf info nginx

# Install package
dnf install nginx

# Install without confirmation
dnf install nginx -y

# Remove package
dnf remove nginx

# Update specific package
dnf update nginx

# Update all packages
dnf update

# List available packages
dnf list available

# List installed packages
dnf list installed

# Check repositories
dnf repolist

# Query installed RPM package
rpm -q nginx
```

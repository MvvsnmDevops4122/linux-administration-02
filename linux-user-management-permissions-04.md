# Linux User Management and permissions

## 1. Linux User Management

Linux User Management is the process of **creating, modifying, deleting, and managing users and groups**, as well as **controlling their access and permissions** on a Linux system.

### User Management Structure

```text
User → Group → Role → Permission
```

These concepts are commonly used across technologies such as:

* Linux
* Kubernetes
* AWS IAM
* Azure IAM

---

# 2. Types of Users in Linux

Linux commonly has two broad categories of users:

## 2.1 Normal User

A normal user has limited permissions and can perform only the operations allowed to that user.

* Shell prompt: `$`
* Home directory: `/home/<username>`

Example:

```text
/home/satya
```

## 2.2 Root User

The root user is the Linux administrator and has unrestricted access to system resources and operations.

* Shell prompt: `#`
* Home directory: `/root`

---

# 3. User, Group, Role & Permission

## User

A **user** is an individual account that can access a system.

## Group

A **group** is a collection of one or more users.

Groups are used to manage permissions efficiently instead of assigning permissions individually to every user.

## Role

A **role** defines what actions a user or group is allowed to perform by assigning specific permissions.

## Permission

**Permissions** control who can access a file or directory and what actions they can perform.

```text
User → Group → Role → Permission
```

---

# 4. Authentication vs Authorization

## Authentication

Authentication is the process of **verifying a user's identity**.

**Simple question:**

```text
Who are you?
```

Example:

```text
Entering your TCS employee ID to identify yourself.
```

## Authorization

Authorization is the process of **determining what actions and resources an authenticated user is allowed to access**.

**Simple question:**

```text
What are you allowed to do?
```

Example:

```text
After entering the office, you can access only the projects
for which you have been granted permission.
```

### Easy Difference

```text
Authentication → Who are you?
Authorization  → What are you allowed to access/do?
```

---

# 5. Roles and Permissions

A role defines the type of access required by a user.

| Role    | Example Permissions                   |
| ------- | ------------------------------------- |
| Trainee | Read-only access                      |
| Junior  | Read + specific write operations      |
| Senior  | Read + write access                   |
| Lead    | Read + write + update + delete access |

### Remember

```text
Action   → What can you perform?
           Read, Write, Delete, Create

Resource → What can you access?
           File, Server, Database, Project
```

A user has a role, and the role has permissions.

---

# 6. Linux Users and Groups

In Linux, role-like access can be implemented using **users, groups, and permissions**.

Example groups:

```text
devops-trainee
devops-junior
devops-senior
devops-lead
```

---

# 7. Create a User

### Syntax

```bash
useradd <username>
```

### Example

```bash
useradd ramesh
```

When a user is created, Linux can also create a group with the same name as the user, depending on the system configuration.

---

# 8. User ID and Group ID

Every Linux user has a **UID (User ID)**.

Every Linux group has a **GID (Group ID)**.

### Root UID

```text
UID 0 → root
```

### Verify User Information

```bash
id <username>
```

Example:

```bash
id satya
```

Typical output:

```text
uid=1001(satya) gid=1001(satya) groups=1001(satya)
```

Meaning:

```text
uid    → User ID
gid    → Primary Group ID
groups → Groups the user belongs to
```

---

# 9. Important User Management Files

| File              | Purpose                             |
| ----------------- | ----------------------------------- |
| `/etc/passwd`     | User account information            |
| `/etc/group`      | Group information                   |
| `/etc/sudoers`    | Main sudo configuration             |
| `/etc/sudoers.d/` | Additional sudo configuration files |

### View User Information

```bash
cat /etc/passwd
```

or:

```bash
getent passwd <username>
```

### View Group Information

```bash
cat /etc/group
```

or:

```bash
getent group <groupname>
```

---

# 10. Create a Group

### Syntax

```bash
groupadd <group-name>
```

### Example

```bash
groupadd devops
```

---

# 11. Check Groups

### Show groups of the current user

```bash
groups
```

### Show groups of a specific user

```bash
groups <username>
```

### Detailed user and group information

```bash
id <username>
```

Example:

```bash
id satya
```

---

# 12. Primary and Secondary Groups

A Linux user has:

* One primary group
* Zero or more secondary groups

## Change Primary Group

```bash
usermod -g <group-name> <username>
```

Example:

```bash
usermod -g devops satya
```

Verify:

```bash
id satya
```

## Add a User to a Secondary Group

Use `-aG` so that existing secondary-group memberships are preserved.

```bash
usermod -aG <group-name> <username>
```

Example:

```bash
usermod -aG development satya
```

> **Important:** `-G` replaces the user's supplementary group list. Use `-aG` when you want to add another secondary group without removing existing memberships.

---

# 13. Linux File Permissions

Permissions control who can access files and directories and what actions they can perform.

There are three basic permissions:

| Permission | Symbol | Numeric Value |
| ---------- | ------ | ------------: |
| Read       | `r`    |             4 |
| Write      | `w`    |             2 |
| Execute    | `x`    |             1 |

### Meaning for Files

* `r` → Read the file
* `w` → Modify the file
* `x` → Execute the file

### Meaning for Directories

* `r` → List directory contents
* `w` → Create/delete/rename entries
* `x` → Enter/access the directory

---

# 14. File Type and Permissions

Example:

```text
-rwxr-x---
```

The first character identifies the file type.

```text
- → Regular file
d → Directory
```

The remaining nine characters represent permissions:

```text
Owner | Group | Others
rwx   | r-x   | ---
```

---

# 15. Permission Categories

Permissions are divided into three categories:

```text
Owner | Group | Others
```

Example:

```text
rwx | r-- | r--
```

Numeric values:

```text
Owner  → 4 + 2 + 1 = 7
Group  → 4 + 0 + 0 = 4
Others → 4 + 0 + 0 = 4
```

Therefore:

```text
744
```

---

# 16. Create a File and Check Permissions

Create a file:

```bash
touch devops.txt
```

Check permissions:

```bash
ls -l devops.txt
```

Example:

```text
-rw-r--r--  satya devops  devops.txt
```

The output contains:

```text
Permissions | Owner | Group | File
```

---

# 17. chmod — Change File Permissions

`chmod` is used to change the permissions of files and directories.

### Syntax

```bash
chmod <permissions> <file>
```

### Give Execute Permission to Owner

```bash
chmod u+x devops.txt
```

### Give Execute Permission to Group

```bash
chmod g+x devops.txt
```

### Give Full Permission to Owner, Group, and Others

```bash
chmod 777 devops.txt
```

### Remove All Permissions from Others

```bash
chmod o-rwx devops.txt
```

### Remove Write and Execute from Group

```bash
chmod g-wx devops.txt
```

---

# 18. Numeric chmod

Permission values:

```text
Read    = 4
Write   = 2
Execute = 1
```

Examples:

```text
7 = rwx = 4 + 2 + 1
6 = rw- = 4 + 2
5 = r-x = 4 + 1
4 = r-- = 4
0 = --- = 0
```

### Example

```bash
chmod 755 devops.txt
```

Means:

```text
Owner  → rwx
Group  → r-x
Others → r-x
```

---

# 19. chmod on Directories Recursively

### Change directory permissions

```bash
chmod 777 foldername
```

### Change permissions for a directory and everything inside it

```bash
chmod -R 777 foldername
```

> Use recursive permission changes carefully, especially with `777`, because they can grant broad access.

---

# 20. File Ownership

Ownership determines which user and group own a file or directory.

Example:

```text
-rw-r--r--  satya  devops  devops.txt
```

Here:

```text
Owner → satya
Group → devops
```

---

# 21. chown — Change Ownership

`chown` is used to change the owner and/or group ownership of files and directories.

### Change Owner

```bash
chown <username> <file>
```

Example:

```bash
chown suresh devops.txt
```

### Change Owner and Group

```bash
chown <username>:<group> <file>
```

Example:

```bash
chown suresh:developers devops.txt
```

### Change Ownership Recursively

```bash
chown -R suresh:developers folder/
```

---

# 22. chgrp — Change Group Ownership

`chgrp` is used to change the group ownership of a file or directory.

### Syntax

```bash
chgrp <group> <file>
```

Example:

```bash
chgrp developers devops.txt
```

---

# 23. sudo

`sudo` allows an authorized user to execute commands with elevated privileges.

### Run a command with sudo

```bash
sudo <command>
```

Example:

```bash
sudo systemctl restart sshd
```

The user may be prompted for their password depending on the sudo configuration.

---

# 24. sudoers Configuration

The main sudo configuration file is:

```text
/etc/sudoers
```

Additional configuration can be placed under:

```text
/etc/sudoers.d/
```

### Edit sudoers safely

```bash
visudo
```

or:

```bash
visudo -f /etc/sudoers.d/<filename>
```

---

# 25. Give sudo Access to a User

One approach is to add the user to the appropriate administrative group, depending on the Linux distribution.

Another approach is to create a sudoers rule.

Example:

```text
satya ALL=(ALL) ALL
```

This allows `satya` to run commands through `sudo` according to the rule.

### Passwordless sudo

```text
satya ALL=(ALL) NOPASSWD: ALL
```

This allows the user to run sudo commands without entering a password.

> Passwordless sudo should be used carefully because it grants powerful administrative access.

---

# 26. Give sudo Access Only to Specific Commands

Instead of giving full sudo access, a user can be allowed to run only specific commands.

Example:

```text
satya ALL=(ALL) /usr/bin/systemctl restart nginx
```

This follows the **principle of least privilege**.

---

# 27. SSH Authentication

SSH can authenticate users using:

1. Password-based authentication
2. Key-based authentication

---

# 28. Password-Based SSH Authentication

Set a password:

```bash
passwd <username>
```

Example:

```bash
passwd satya
```

Connect to a server:

```bash
ssh <username>@<server-ip>
```

Example:

```bash
ssh satya@192.168.1.10
```

---

# 29. Enable Password Authentication for SSH

SSH server configuration is commonly located at:

```text
/etc/ssh/sshd_config
```

Check:

```text
PasswordAuthentication yes
```

Validate the configuration:

```bash
sshd -t
```

Then restart/reload the SSH service:

```bash
systemctl restart sshd
```

> Keep an existing administrative session available when changing SSH authentication so that you do not accidentally lock yourself out.

---

# 30. SSH Key-Based Authentication

SSH key-based authentication uses a key pair:

```text
Public Key  → Stored on the server
Private Key → Kept securely on the client
```

### Generate a Key Pair

```bash
ssh-keygen
```

This commonly creates:

```text
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

### Important

**Never share the private key.**

Only the public key should be copied to the server.

---

# 31. authorized_keys

The public key for a user is normally stored in:

```text
~/.ssh/authorized_keys
```

Example:

```text
/home/satya/.ssh/authorized_keys
```

The server checks this file to determine whether the presented public key is authorized for that account.

---

# 32. SSH Key-Based Authentication Setup

### Step 1: Create `.ssh` directory

```bash
sudo mkdir -p /home/satya/.ssh
```

### Step 2: Create `authorized_keys`

```bash
sudo touch /home/satya/.ssh/authorized_keys
```

### Step 3: Generate keys on the client

```bash
ssh-keygen
```

### Step 4: Copy the public key

```bash
cat ~/.ssh/id_rsa.pub
```

Copy the public key into:

```text
/home/satya/.ssh/authorized_keys
```

### Step 5: Set ownership

```bash
sudo chown -R satya:satya /home/satya/.ssh
```

### Step 6: Set permissions

```bash
sudo chmod 700 /home/satya/.ssh
sudo chmod 600 /home/satya/.ssh/authorized_keys
```

### Step 7: Connect using the private key

```bash
ssh -i ~/.ssh/id_rsa satya@<server-ip>
```

---

# 33. SSH Key Authentication Flow

```text
Client Machine
     |
     | Private Key
     ↓
Linux Server
     |
     ↓
/home/satya/.ssh/authorized_keys
     |
     ↓
Matching Public Key
     |
     ↓
Authentication Successful
     |
     ↓
Login as satya
```

---

# 34. Remove User from a Group

To remove a user from a supplementary group:

```bash
gpasswd -d satya devops
```

This removes `satya` from the `devops` group.

---

# 35. Lock a User Account

Lock the user's password:

```bash
sudo usermod -L satya
```

Equivalent:

```bash
sudo passwd -l satya
```

Verify:

```bash
passwd -S satya
```

> Locking a password does not necessarily terminate an existing session or disable every authentication method. SSH keys and active sessions may need to be handled separately.

---

# 36. Terminate an Existing User Session

Check the user's processes:

```bash
ps -u satya
```

Terminate the user's processes:

```bash
sudo pkill -u satya
```

Use this carefully because it terminates the user's running processes.

---

# 37. Backup a User's Home Directory

Create a backup directory:

```bash
mkdir -p /backup
```

Create a compressed archive:

```bash
tar -czvf /backup/satya-backup.tar.gz /home/satya
```

Verify:

```bash
ls -lh /backup/
```

---

# 38. Find Command

`find` is used to search for files and directories based on conditions.

### Syntax

```bash
find <where-to-search> <options> <what-to-search>
```

### Search from the root directory

```bash
find /
```

### Find a file by name

```bash
find / -name "*.log"
```

### Case-insensitive name search

```bash
find / -iname "*.log"
```

### Find a specific file

```bash
find / -type f -name "devops.txt"
```

### Find a specific directory

```bash
find / -type d -name "devops"
```

### Find files by permissions

```bash
find / -perm 777
```

### Find files owned by a specific user

```bash
find / -user ramesh
```

> Searching from `/` can take time and may produce permission-denied messages. `sudo` may be required for complete results.

---

# 39. Delete a User Account

After completing the required backup:

### Delete only the user account

```bash
sudo userdel satya
```

### Delete the user and home directory

```bash
sudo userdel -r satya
```

The `-r` option removes the user's home directory and mail spool where applicable.

> Before deleting a user, verify their files, processes, scheduled jobs, SSH access, and ownership of important resources.

---



# 40. Important Commands Cheat Sheet

| Task                     | Command                  |
| ------------------------ | ------------------------ |
| Create user              | `useradd username`       |
| Set password             | `passwd username`        |
| Create group             | `groupadd groupname`     |
| Show user ID/groups      | `id username`            |
| Show user's groups       | `groups username`        |
| Change primary group     | `usermod -g group user`  |
| Add secondary group      | `usermod -aG group user` |
| Lock password            | `usermod -L user`        |
| Unlock password          | `usermod -U user`        |
| Delete user              | `userdel user`           |
| Delete user + home       | `userdel -r user`        |
| Change permissions       | `chmod`                  |
| Change owner             | `chown`                  |
| Change group owner       | `chgrp`                  |
| Run privileged command   | `sudo`                   |
| Edit sudoers safely      | `visudo`                 |
| Generate SSH keys        | `ssh-keygen`             |
| Check SSH configuration  | `sshd -t`                |
| Find files               | `find`                   |
| Create archive           | `tar -czvf`              |
| Check processes          | `ps`                     |
| Terminate user processes | `pkill -u username`      |

---

# 41. Key Takeaways

* **User** → Identifies who can access the system.
* **Group** → Helps manage permissions for multiple users.
* **Role** → Represents a defined set of permissions.
* **Authentication** → Verifies identity.
* **Authorization** → Determines allowed access and actions.
* **chmod** → Changes file permissions.
* **chown** → Changes file ownership.
* **chgrp** → Changes group ownership.
* **sudo** → Provides controlled elevated privileges.
* **SSH keys** → Provide key-based authentication.
* **`/etc/passwd`** → Stores user account information.
* **`/etc/group`** → Stores group information.
* **`/etc/sudoers`** → Controls sudo access.
* **`find`** → Searches for files and directories.
* **`tar`** → Creates archives/backups.
* **`userdel`** → Deletes user accounts.
* **`dnf`** → Manages software packages.
* Always follow the **principle of least privilege**: give users only the access they actually need.

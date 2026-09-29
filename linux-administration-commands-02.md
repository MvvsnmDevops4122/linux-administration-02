

# 📘 Linux Commands & Administration

> Practical Linux reference for DevOps, Cloud, CI/CD, troubleshooting, and system administration.

---

## 1. Linux Command Syntax

### General Syntax

```bash
command <options> <inputs>
```

* `command` → Action to perform
* `options` → Modify command behavior
* `inputs/arguments` → Target on which the command operates

### Example

```bash
ls -l /home
```

```text
ls      → command
-l      → option
/home   → input
```

---

## 2. `uname` — System Information

Displays information about the Linux system.

```bash
uname
```

### Display all available information

```bash
uname -a
```

`-a` → Display all available system information.

---

## 3. Absolute Path vs Relative Path

### Absolute Path

A complete path that starts from the root.

```text
/home/ec2-user
/opt/application/logs
```

### Relative Path

A path based on the current working directory.

```text
repos/
../logs/
```

### Remember

```text
Absolute Path → starts from root
Relative Path → starts from current directory
```

---

## 4. CRUD

```text
C → Create
R → Read
U → Update
D → Delete
```

CRUD represents the four basic operations commonly performed on data, files, and resources.

---

# 📂 Linux Filesystem

## 5. Linux Root Directory

```text
/
```

`/` → Root directory and top-level directory of the Linux filesystem.

---

## 6. Important Linux Directories

| Directory | Purpose                                     |
| --------- | ------------------------------------------- |
| `/`       | Root directory                              |
| `/home`   | Home directories of users                   |
| `/etc`    | Configuration files                         |
| `/tmp`    | Temporary files                             |
| `/bin`    | Traditional location for essential commands |

Examples:

```text
/home/satya
/home/ec2-user
```

> On modern Linux distributions, `/bin` may be linked to `/usr/bin`.

---

# 📁 File & Directory Management

## 7. `pwd`

Displays the current working directory.

```bash
pwd
```

Example:

```text
/home/ec2-user
```

---

## 8. `ls`

Lists files and directories.

```bash
ls
```

### Long listing

```bash
ls -l
```

Displays:

* Permissions
* Owner
* Group
* Size
* Modification time
* File/directory name

### Useful options

```bash
ls -a
ls -lh
ls -lt
ls -lr
ls -ltr
ls -i
```

```text
-a → all files, including hidden
-l → long format
-h → human-readable sizes
-t → sort by modification time
-r → reverse order
-i → inode number
```

---

## 9. Hidden Files

Linux hidden files/directories normally start with:

```text
.
```

Examples:

```text
.bashrc
.ssh
```

Display hidden files:

```bash
ls -la
```

---

## 10. `cd`

Change directory.

```bash
cd /path
```

Go to home directory:

```bash
cd
```

Previous directory:

```bash
cd -
```

One directory back:

```bash
cd ..
```

Two directories back:

```bash
cd ../..
```

---

## 11. `tree`

Displays files and directories in tree format.

```bash
tree
```

---

## 12. `touch`

Creates an empty file if it does not exist.

```bash
touch devops.txt
```

Create multiple files:

```bash
touch one.txt two.txt three.txt
```

> If the file already exists, `touch` updates its timestamps.

---

## 13. `mkdir`

Creates a directory.

```bash
mkdir devops
```

Create multiple directories:

```bash
mkdir linux aws devops
```

### `-p`

Creates parent directories when required.

```bash
mkdir -p parent/child1/child2
```

### `-v`

Displays what was created.

```bash
mkdir -v devops
```

---

## 14. `rmdir`

Removes an **empty directory**.

```bash
rmdir devops
```

> `rmdir` cannot remove a directory containing files.

---

## 15. `rm`

Remove a file:

```bash
rm file.txt
```

Remove multiple files:

```bash
rm file1.txt file2.txt
```

Remove directory recursively:

```bash
rm -r devops
```

Force recursive removal:

```bash
rm -rf devops
```

```text
-r → recursive
-f → force
```

⚠️ Always verify the path before using `rm -rf`.

---

# 📋 Copy, Move & Rename

## 16. `cp`

### Syntax

```bash
cp <source> <destination>
```

Copy file to directory:

```bash
cp devops.txt DevOps/
```

Copy file:

```bash
cp file1.txt file2.txt
```

Copy directory:

```bash
cp -r Python DevOps/
```

Copy all Java files:

```bash
cp *.java destination_dir/
```

---

## 17. `mv`

### Move

```bash
mv file.txt /tmp/
```

### Rename

```bash
mv old.txt new.txt
```

### Move directory

```bash
mv DevOps/ Python/
```

> `mv` is used for both **moving and renaming**.

---

# 📄 File Content & Redirection

## 18. `cat`

Display file content:

```bash
cat devops.txt
```

Display multiple files:

```bash
cat file1.txt file2.txt
```

Display line numbers:

```bash
cat -n file.txt
```

### Create a file using `cat`

```bash
cat > devops.txt
```

Enter content and press:

```text
Ctrl + D
```

`>` → Overwrites existing content.

### Append content

```bash
cat >> devops.txt
```

`>>` → Appends content.

### Merge files

```bash
cat file1 file2 > merge.txt
```

```text
file1 + file2
      ↓
  merge.txt
```

### Reverse content

```bash
tac file.txt
```

---

## 19. Output Redirection

### Overwrite

```bash
command > file.txt
```

### Append

```bash
command >> file.txt
```

### Clear a file without deleting it

```bash
> file.txt
```

```text
>  → overwrite
>> → append
```

---

# 📖 File Viewing

## 20. `head`

Displays the first 10 lines by default.

```bash
head file.txt
```

First 3 lines:

```bash
head -n 3 file.txt
```

Alternative:

```bash
head -3 file.txt
```

### Display lines 35–50

```bash
head -50 file.txt | tail -15
```

---

## 21. `tail`

Displays the last 10 lines by default.

```bash
tail file.txt
```

Last 3 lines:

```bash
tail -n 3 file.txt
```

### Follow live logs

```bash
tail -f app.log
```

This is especially useful for monitoring application logs.

---

## 22. `more`

Displays file content page by page.

```bash
more file.txt
```

---

## 23. `diff`

Compare files line by line:

```bash
diff file1 file2
```

Side-by-side comparison:

```bash
diff -y file1 file2
```

---

# 🔍 Search & Text Processing

## 24. `grep`

Searches for text or patterns.

```bash
grep "linux" file.txt
```

Linux is case-sensitive by default:

```text
linux
Linux
LINUX
```

### Important options

```bash
grep -i "linux" file.txt
```

`-i` → Case-insensitive

```bash
grep -n "linux" file.txt
```

`-n` → Show line numbers

```bash
grep -c "linux" file.txt
```

`-c` → Count matching lines

```bash
grep -v "linux" file.txt
```

`-v` → Show non-matching lines

```bash
grep -l "linux" *
```

`-l` → Show filenames containing the match

```bash
grep -w "linux" file.txt
```

`-w` → Match whole words

```bash
grep -o "linux" file.txt
```

`-o` → Show only matching text

### Context search

```bash
grep -B5 "error" demo.txt
```

5 lines before.

```bash
grep -A5 "error" demo.txt
```

5 lines after.

```bash
grep -C5 "error" demo.txt
```

5 lines before and after.

### Multiple patterns

```bash
grep -iE "error|error1" demo.txt
```

### Quick reference

```text
-i → ignore case
-n → line number
-c → count
-v → inverse match
-l → matching filenames
-w → whole word
-o → matching text only
-A → after
-B → before
-C → before + after
```

---

## 25. `wc`

Counts lines, words, and bytes.

```bash
wc file.txt
```

Count lines:

```bash
wc -l file.txt
```

Count words:

```bash
wc -w file.txt
```

Count bytes:

```bash
wc -c file.txt
```

---

## 26. `sort`

Alphabetical sort:

```bash
sort file.txt
```

Reverse sort:

```bash
sort -r file.txt
```

Sort by second field:

```bash
sort -k 2 data.txt
```

Remove duplicates:

```bash
sort -u file.txt
```

---

## 27. `cut`

Extracts specific fields from text.

### Syntax

```bash
cut -d "<delimiter>" -f <field-number> file
```

```text
-d → delimiter
-f → field
```

Example:

```text
name:password:1001:user
```

Extract first field:

```bash
cut -d ":" -f1 file
```

Multiple fields:

```bash
cut -d ":" -f1,3 /etc/passwd
```

---

# 👤 Users & Groups

## 28. `/etc/passwd`

Contains information about Linux user accounts.

```bash
cat /etc/passwd
```

Example:

```text
root:x:0:0:root:/root:/bin/bash
```

### Extract usernames

```bash
cut -d ":" -f1 /etc/passwd
```

### Extract UIDs

```bash
cut -d ":" -f3 /etc/passwd
```

### Extract username + UID

```bash
cut -d ":" -f1,3 /etc/passwd
```

---

## 29. `id`

Displays user information such as:

* UID
* GID
* Groups

```bash
id
```

```bash
id username
```

---

## 30. `groups`

Displays the groups a user belongs to.

```bash
groups
```

```bash
groups username
```

---

# ⚙️ Advanced Text Processing

## 31. `awk`

`awk` is used for text processing, field extraction, and conditional filtering.

### Extract username

```bash
awk -F ":" '{print $1}' /etc/passwd
```

```text
-F ":" → field separator
$1     → first field
```

### Find users with UID greater than 999

```bash
awk -F ":" '$3 > 999 {print $1}' /etc/passwd
```

```text
$3     → UID field
> 999  → condition
$1     → username
```

---

## 32. `tr`

Translates or replaces characters.

### Lowercase → Uppercase

```bash
cat demo.txt | sort | tr 'a-z' 'A-Z'
```

### Uppercase → Lowercase

```bash
cat demo.txt | sort | tr 'A-Z' 'a-z'
```

---

## 33. Pipe `|`

A pipe sends the output of one command as the input of another command.

```bash
command1 | command2
```

Example:

```bash
curl -s <URL> | grep "linux"
```

Flow:

```text
curl
 ↓
Output
 ↓
grep
 ↓
Matching lines
```

> Pipe allows multiple commands to work together.

---

# 🌐 Network Utilities

## 34. `wget`

Downloads files from a URL.

```bash
wget <URL>
```

Example:

```bash
wget https://example.com/file.txt
```

---

## 35. `curl`

Transfers data to or from a URL.

```bash
curl <URL>
```

Common DevOps uses:

* API testing
* Endpoint testing
* Data transfer
* Shell scripting
* Downloading resources

Example:

```bash
curl https://example.com
```

Silent mode:

```bash
curl -s https://example.com
```

---

# 🔎 File Search

## 36. `find`

Searches for files and directories based on conditions such as name, type, permissions, and modification time.

### Search by name

Case-sensitive:

```bash
find . -name "filename"
```

Case-insensitive:

```bash
find . -iname "filename"
```

### Find files

```bash
find . -type f
```

### Find directories

```bash
find . -type d
```

### Find empty files

```bash
find . -type f -empty
```

### Find non-empty files

```bash
find . -type f ! -empty
```

### Find empty directories

```bash
find . -type d -empty
```

### Search by permission

```bash
find . -perm 777
```

### Search by modification time

```bash
find . -mtime -1
```

Modified within approximately the last 24 hours.

```bash
find . -mtime +1
```

Modified more than approximately 24 hours ago.

### Delete empty files

```bash
find . -type f -empty -delete
```

⚠️ Always verify the search condition before using `-delete`.

### Modify file timestamp for testing

```bash
touch -d "2 days ago" filename
```

---

# ✏️ Stream Editing

## 37. `sed`

`sed` is a stream editor used to replace, delete, and print selected text.

### Replace first occurrence on each line

```bash
sed 's/unix/linux/' abc.txt
```

### Replace second occurrence

```bash
sed 's/unix/linux/2' abc.txt
```

### Replace all occurrences

```bash
sed 's/unix/linux/g' abc.txt
```

### Replace on line 3

```bash
sed '3 s/unix/linux/' abc.txt
```

### Replace within line range

```bash
sed '1,3 s/unix/linux/' abc.txt
```

### Delete line 5

```bash
sed '5d' filename.txt
```

### Delete lines 3–6

```bash
sed '3,6d' filename.txt
```

### Display lines 60–80

```bash
sed -n '60,80p' filename.txt
```

```text
-n → suppress automatic output
p  → print selected lines
```

### Replace and print only line 2

```bash
sed -n '2 s/am/was/p' sample.txt
```

### Replace all occurrences on line 1 and print

```bash
sed -n '1 s/unix/linux/gp' sample.txt
```


---

## 39. Nano

`nano` is a beginner-friendly command-line text editor.

```bash
nano demo.txt
```

Install on RPM-based systems when required:

```bash
sudo yum install nano -y
```

Common shortcuts:

```text
Ctrl + O → Save
Ctrl + X → Exit
```

---

# 40. TAR Command

## What is TAR?

`tar` is used to **create and extract archive files**.

An archive is a single file that contains multiple files and/or directories.

### Common Formats

| Format | Description |
|---|---|
| `.tar` | TAR archive |
| `.tar.gz` | TAR archive compressed using gzip |
| `.tgz` | Same as `.tar.gz` |
| `.zip` | ZIP archive with compression |

> `.tar.gz` is commonly used in Linux environments.

---

## Create a `.tar.gz` Archive

### Syntax

```bash
tar -czvf <file-name>.tar.gz <files/folders>
````

### Example

```bash
tar -czvf aws.tar.gz devops aws
```

This creates:

```text
aws.tar.gz
```

containing:

```text
devops/
aws/
```

---

## Meaning of `tar -czvf`

```text
tar
 │
 ├── c → Create
 ├── z → gzip compression
 ├── v → Verbose output
 └── f → Archive file name
```

### `c` → Create

Creates a new TAR archive.

```bash
tar -c ...
```

### `z` → gzip

Compresses the TAR archive using gzip.

```bash
tar -cz ...
```

### `v` → Verbose

Displays the files/directories being processed.

```bash
tar -czv ...
```

### `f` → File

Specifies the archive file name.

```bash
-f backup.tar.gz
```

### Complete Meaning

```bash
tar -czvf backup.tar.gz devops aws
```

> Create a TAR archive, compress it using gzip, display the files being processed, and save the archive as `backup.tar.gz`.

---

## Extract a `.tar.gz` Archive

### Syntax

```bash
tar -xzvf <file-name>.tar.gz
```

### Example

```bash
tar -xzvf aws.tar.gz
```

### Options

```text
x → Extract
z → gzip
v → Verbose
f → File
```

---

## List Archive Contents

To view the contents without extracting:

```bash
tar -tzvf backup.tar.gz
```

```text
t → List contents
z → gzip
v → Verbose
f → File
```

---

## TAR Quick Revision

### Create

```bash
tar -czvf backup.tar.gz directory/
```

### Extract

```bash
tar -xzvf backup.tar.gz
```

### List

```bash
tar -tzvf backup.tar.gz
```

### Easy Memory

```text
C → Create
X → Extract
T → List

Z → gzip
V → Verbose
F → File
```

---

# ZIP and UNZIP

ZIP is commonly used to archive and compress files/directories.

## Create ZIP

```bash
zip -r ansible.zip Ansible/
```

`-r` means recursively include the directory and its contents.

## Extract ZIP

```bash
unzip ansible.zip
```

---

# Working with Compressed Files

## Search inside a `.gz` file

```bash
zgrep "<pattern>" file.gz
```

Example:

```bash
zgrep "ERROR" application.log.gz
```

## Display a compressed file

```bash
zcat file.gz
```

This displays the contents without manually extracting the file.

---

# 41. FIND Command

## What is `find`?

`find` is used to **search for files and directories based on conditions**.

### Syntax

```bash
find <where-to-search> <conditions>
```

---

## Find `.log` Files

```bash
find / -iname "*.log"
```

### Meaning

```text
/          → Search from root
-iname     → Case-insensitive name search
"*.log"    → Files ending with .log
```

---

## Find a Directory by Name

```bash
find / -type d -name "devops"
```

```text
-type d → Search for directories
-name   → Match the name
```

---

## Find Files Owned by a User

```bash
find / -user ramesh
```

This searches for files/directories owned by `ramesh`.

---

## Exclude a User's Home Directory

```bash
find / -user ramesh -not -path "/home/ramesh/*"
```

This excludes:

```text
/home/ramesh/
```

---

## Search by Name

### Case-sensitive

```bash
find . -name "filename"
```

### Case-insensitive

```bash
find . -iname "filename"
```

---

## Find Files

```bash
find . -type f
```

## Find Directories

```bash
find . -type d
```

---

## Find Empty Files

```bash
find . -type f -empty
```

## Find Non-Empty Files

```bash
find . -type f ! -empty
```

## Find Empty Directories

```bash
find . -type d -empty
```

---

## Search by Permission

```bash
find . -perm 777
```

This finds files/directories with the specified permission mode.

---

## Search by Modification Time

### Modified within approximately the last 24 hours

```bash
find . -mtime -1
```

### Modified more than approximately 24 hours ago

```bash
find . -mtime +1
```

---

## Delete Empty Files

```bash
find . -type f -empty -delete
```

> Always verify the search condition before using `-delete`.

---

## Modify File Timestamp for Testing

```bash
touch -d "2 days ago" filename
```

---

## FIND Quick Revision

```bash
find . -type f
find . -type d
find . -name "filename"
find . -iname "*.log"
find . -user ramesh
find . -empty
find . -mtime -1
find . -mtime +1
```

---

## Real-World Example

> **For example, in an online shopping application, the frontend displays products and accepts user actions, the backend processes login, product availability, cart, orders and payments, and the database stores users, products, orders and payment-related data.**

---

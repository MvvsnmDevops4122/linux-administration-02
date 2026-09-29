# Vim Editor in Linux

## What is Vim?

Vim (Vi Improved) is a powerful command-line text editor available on Linux systems.

It allows users to create, edit, search, and modify files directly from the terminal.

### Open a File

```bash
vim <file-name>
```

- If the file exists, Vim opens it.
- If the file does not exist, Vim creates and opens a new file.

## Vim Modes

Vim has three important modes:

1. Normal Mode
2. Insert Mode
3. Command-Line Mode

### 1. Normal Mode

Normal Mode is the default mode in Vim. It is used for navigating through files and performing text operations such as copying, deleting, pasting, and undoing changes.

**Essential Commands**

| Command | Description |
|---|---|
| `u` | Undo changes |
| `Ctrl + r` | Redo changes |
| `gg` | Go to the beginning of the file |
| `G` | Go to the end of the file |
| `yy` | Copy the current line |
| `p` | Paste below the current line |
| `dd` | Delete the current line |
| `M` | Move cursor to the middle of the visible screen |
| `P` | Paste above the current line |

### 2. Insert Mode

Insert Mode is used for typing and editing text inside a file.

**Essential Commands**

| Command | Description |
|---|---|
| `i` | Insert text before the cursor |
| `I` | Insert text at the beginning of the line |
| `a` | Insert text after the cursor |
| `A` | Insert text at the end of the line |
| `o` | Open a new line below the current line and enter Insert Mode |
| `O` | Open a new line above the current line and enter Insert Mode |
| `Esc` | Return to Normal Mode |

### 3. Command-Line Mode

Command-Line Mode is used in Vim for executing commands such as saving, quitting, searching, and performing file operations.

## Essential Commands in Command-Line Mode

### 1. Save and Exit Commands

| Command | Description |
|---|---|
| `:w` | Save the file |
| `:q` | Quit Vim |
| `:wq` | Save and quit |
| `:q!` | Force quit without saving |

### 2. Display and Navigation

| Command | Description |
|---|---|
| `:set nu` | Display line numbers |
| `:set nonu` | Hide line numbers |
| `:<line-number>` | Move cursor to a specific line |

**Example:**

```vim
:20
```

Moves the cursor to line 20.

### 3. Search Commands

| Command | Description |
|---|---|
| `/<word-to-search>` | Search forward for a specified word |
| `?<word-to-search>` | Search backward for a specified word |
| `n` | Move to the next search result |
| `N` | Move to the previous search result |

**Example:**

```vim
/Linux
```

Searches forward for `Linux`.

### 4. Delete Commands

| Command | Description |
|---|---|
| `:<line-number>d` | Delete a specific line |
| `:2,5d` | Delete lines 2 to 5 |
| `:%d` | Delete all lines in the file |

**Example:**

```vim
:2d
```

Deletes line 2.

### 5. Find and Replace Commands

#### Clear Search Highlights

```vim
:noh
```

Clears search highlights.

#### Replace the First Occurrence on a Specific Line

```vim
:2s/<word-to-find>/<word-to-replace>/
```

Replaces the first occurrence of the word on line 2.

**Example:**

```vim
:2s/Linux/Unix/
```

#### Replace All Occurrences on a Specific Line

```vim
:2s/<word-to-find>/<word-to-replace>/g
```

Replaces all occurrences of the word on line 2.

**Example:**

```vim
:2s/Linux/Unix/g
```

#### Replace the First Occurrence in All Lines

```vim
:%s/<word-to-find>/<word-to-replace>/
```

Replaces the first occurrence in each line of the file.

#### Replace All Occurrences in All Lines

```vim
:%s/<word-to-find>/<word-to-replace>/g
```

Replaces all occurrences of the word throughout the file.

**Example:**

```vim
:%s/Linux/Unix/g
```

## Vim Workflow

```text
                +----------------+
                |   Vim Editor   |
                +----------------+
                         |
                         v
                +----------------+
                |   Normal Mode  |
                | Navigation and |
                |  text commands |
                +----------------+
                   |           |
             i / a / o       : / /
                   |           |
                   v           v
          +---------------+  +-------------------+
          |  Insert Mode  |  | Command-Line Mode |
          | Type and edit |  | Save, search,     |
          |     text      |  | quit, execute     |
          +---------------+  |    commands       |
                   |          +-------------------+
                   | Esc              |
                   v                  |
          +---------------+          |
          |  Normal Mode  |<---------+
          +---------------+
```


---
date: '2025-10-03T15:57:01Z'
draft: false 
title: 'Linux File Permissions'
tags:
  - linux
  - security
  - permissions
image: /blogs/permission-denied.jpg
---

## Permissions : Read, Write, Execute
###  `r` (Read) Permission: 
with `r` permission user can:
- View the content of a file
- List the contents of a directory 
### `w` (Write) Permission:
with `w` permission user can:
- Modify a file 
- Create, rename, delete file or dir within a directory 
### `x` (Execute) permission: 
with `x` permission user can :
- Execute a file as script 
- Can enter in a directory 

## Permission Category : User, Group, Others
### `u` for User 

The files owner 
### `g` for Group

The group associated with the file or 

### `o` for Others 

Everyone Else on the planet.

## Interpreting Permission String
When you list files with `ls -l`, you’ll see something like this:

`-rwxr-xr-- 1 alice developers 4096 Apr 4 14:00 script.sh`

Let’s dissect it:

- `-` – Regular file (other values include `d` for directory, `l` for symbolic link, etc.)
- `rwx` – Owner (`alice`) has read, write, and execute permissions
- `r-x` – Group (`developers`) has read and execute permissions
- `r--` – Others can only read the file
- `1` – Number of hard links
- `alice` – Owner
- `developers` – Group
- `4096` – File size in bytes
- `Apr 4 14:00` – Last modification date
- `script.sh` – File name

## File Ownership : User & Group
Files in linux associated with a 
- an owner of the file
- a group
_By default: 
- Who (user) create  a file is the owner of the file 
- The file is assigned to the primary group of the user (who created the file)

## Changing Permissions
Linux has a command for changing permissions & it is `chmod`.
### Symbolic Mode
Uses Symbols (letter & symbols) as permissions & permission Category

#### Permissions
- `r` : read
- `w` : write
- `x` :  Execute 
#### Permission Category
- `u` : user
- `g` : group
- `o` : Others 
- `a` : All 
#### Permission Operator
- `+` : Add Permission 
- `-` : Remove Permission 
- `=` : Assign Exact Permission
### Numeric Mode 
This mode uses **octal values** to represent permission bits:

| Permission | Octal | Binary | Description           |
| ---------- | ----- | ------ | --------------------- |
| `---`      | 0     | 000    | No Permissions        |
| `--x`      | 1     | 001    | Execute Only          |
| `--w`      | 2     | 010    | Write Only            |
| `-wx`      | 3     | 011    | Write & Execute       |
| `r--`      | 4     | 100    | Read Only             |
| `r-x`      | 5     | 101    | Read & Execute        |
| `rw-`      | 6     | 110    | Read & Write          |
| `rwx`      | 7     | 111    | Read, Write & Execute |

You sum these for each category:

- `7` = `rwx`
- `6` = `rw-`
- `5` = `r-x`
- `4` = `r--`

### Commands
```bash
chmod ugo+rwx filename
chmod 777 filename
```

## Changing Ownership & Group
Using `chown` & `chgrp` 

### Ownership 
Changing ownership 
```shell
chown newuser filename
```

### Group 
Changing Group 
```shell
chgrp newgroup filename 
```

### Ownership & Group 
Changing both ownership & group 
```shell
chown newuser:newgroup filename 
```


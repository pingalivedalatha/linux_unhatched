# Linux Unhatched
“My progress through Cisco’s Linux Unhatched labs"

This repository documents my journey through Cisco’s Linux Unhatched labs, including commands, insights, and screenshots.

## Progress Tracker
| Lab    | Status        | Screenshot                     |
|--------|---------------|--------------------------------|
| Lab 1  | ✅ Completed   | ![Lab 1](images/lab1.png)       |
| Lab 2  | ✅ Completed   | ![Lab 2](images/lab2.png)       |
| Lab 3  | ✅ Completed   | ![Lab 3](images/lab3_1.png)     |
| Lab 4  | ✅ Completed   | ![Lab 4](images/lab4_1.png)     |
| Lab 5  | ✅ Completed   | ![Lab 5](images/lab5.png)       |

## Labs Completed

### Lab 1
- **Commands:** `ls`, `ls -l`, `ls -r`, `ls -lr`

**What They Do:**
- `ls`: Lists directory contents
- `ls -l`: Lists contents in long format, showing permissions, ownership, and timestamps
- `ls -r`: Lists contents in reverse order
- `ls -lr`: Combines both options—lists contents in long format and reverse order

**Insights:**
- Got "Permission denied" when running `ls` in some directories → learned about file permissions
- Typing `ls-r` gave an error → spacing matters (`ls -r` is correct)

**Screenshot:**  
![Lab 1 Screenshot](images/lab1.png)

---

### Lab 2
- **Commands:** `clear`, `pwd`, `cd`, `cd ..`, `cd .`, `cd ~`

**What They Do:**
- `clear`: Clears the terminal screen (tidies up the workspace).
- `pwd`: Prints the working directory (shows your current location in the filesystem).
- `cd [path]`: Changes directory to the specified path.
- `cd /`: Moves to the root directory (the top of the filesystem tree).
- `cd ..`: Moves up one level to the parent directory.
- `cd .`: Refers to the current directory (not very useful with `cd`, but important later).
- `cd ~`: Returns to the home directory of the current user (`/home/sysadmin`).

**Concepts Learned:**
- Directories in Linux are like folders in Windows/Mac.
- A **path** is a list of directories separated by `/`.
- **Absolute paths** always start with `/` (e.g., `/home/sysadmin`).
- **Relative paths** use shortcuts:
  - `..` → parent directory
  - `.` → current directory
  - `~` → home directory of the logged-in user

**Insights:**
- Learned that Linux always starts you in your home directory (`/home/sysadmin`) when you log in as `sysadmin`.
- Understood the difference between absolute and relative paths.
- Practiced navigating between directories using `cd` and shortcuts.

**Screenshot:**  
![Lab 2 Screenshot](images/lab2.png)

---
### Lab 3
- **Commands:** `ls`, `ls -l`, `ls -lt`, `ls -lS`, `ls -lr`, `ls -lSr`

**What They Do:**
- `ls`: Lists files in the current directory (alphabetical by default).
- `ls -l`: Long listing with details (file type, permissions, hard link count, owner, group, size, timestamp, filename).
- `ls -lt`: Sorts by timestamp (newest first).
- `ls -lS`: Sorts by file size (largest first).
- `ls -lr`: Reverses the order (alphabetical Z→A).
- `ls -lSr`: Sorts by size, smallest first.

**Concepts Learned:**
- **File types:**  
  - `-` regular file, `d` directory, `b` block device, `c` character device,  
  - `s` socket, `p` pipe, `l` symbolic link.
  ![Lab 3 Screenshot](images/file_type.png)
- **Permissions:** Control read (`r`), write (`w`), and execute (`x`) access for owner, group, and others.
- **Ownership:** Split into **user** (creator/owner) and **group**.
- **Hard link count:** Number of directory entries pointing to a file (directories always have at least 2).
- **File size:** Shown in bytes; directories often show multiples of the filesystem block size (commonly 4096 bytes).
- **Timestamps:** Show last modification time.
- **Symbolic links:** Display with `->` pointing to the target file.

**Insights:**
- `/var/log` is a great practice directory because it contains many file types, different owners/groups, and varied sizes/timestamps.
- Sorting options (`-t`, `-S`, `-r`) make it easier to analyze files by time, size, or order.
- Learned that a directory’s size reflects the space used to store its entries, not the total size of files inside.

**Why /var/log is used:**
- Contains a wide variety of files (regular files, directories, links).
- `ls -l /var/log` will list every file and directory entry, even if they have different owners, groups, or permissions.
- You can always *see* the files and their details (permissions, ownership, size, timestamps), but you may not be able to open or read all of them without the right privileges (e.g., some require root).
- Safe to explore with `ls` because you’re only listing, not modifying.
- Logs reflect real system activity, so sorting and listing options show meaningful differences.
- Other directories (like `/home`) may not have enough variety to demonstrate permissions, ownership, and sorting.

📦 **Block Size Visualization**  
Even a tiny file (like 1 byte) still consumes a full filesystem block (commonly 4096 bytes). 
This is why directories often show sizes like 4096 or 8192 — it reflects the space used for their entries, not the total size of files inside.

**Screenshot:**
![Lab 3 Screenshot](images/lab3_1.png)
![Lab 3 Screenshot](images/lab3_2.png)
![Lab 3 Screenshot](images/lab3_3.png)

---

### Lab 4
- **Commands:** `su`, `su -`, `su -l`, `su --login`, `exit`, `sudo`, `sudo -u`

**What They Do:**
- `su`: Switches to another user account (default is root) by opening a new shell.
- `su -`, `su -l`, `su --login`: Starts a login shell with the new user’s environment fully configured.
- `exit`: Logs out of the current shell and returns to the previous user.
- `sudo`: Executes a single command with administrative privileges (without switching users).
- `sudo -u [user] [command]`: Executes a command as a specified user.

**Concepts Learned:**
- **Administrative access** is required for sensitive commands (e.g., system-level operations).
- **`su` vs `sudo`:**
  - `su` opens a new shell as another user (usually root).
  - `sudo` runs a single command as another user (default is root), without switching shells.
- **Login shell options** (`su -`, `su --login`) ensure the new shell uses the target user’s environment.
- **Password security:** Passwords (like `netlab123`) are required but not shown when typed.
- **Prompt change:** When using `su`, the shell prompt changes to reflect the new user (e.g., `root@localhost`).
- **Steam Locomotive (`sl`) command** was used to demonstrate permission control:
  - Fails when run as `sysadmin`.
  - Succeeds when run as `root` via `su` or `sudo`.

**Insights:**
- Switching users with `su` gives full root access, which can be risky if not handled carefully.
- Using `sudo` is safer for one-off commands—it limits the scope of elevated access.
- Learned how to verify which user is active based on the shell prompt.
- Practiced using `exit` to safely return to the original user.

**Screenshot:**  
![Lab 4 Screenshot 1](images/lab4_1.png)  
![Lab 4 Screenshot 2](images/lab4_2.png)

---

### Lab 5
- **Commands:** `cd`, `ls -l`

**What They Do:**
- `cd ~/Documents`: Navigates to the Documents folder in the home directory.
- `ls -l hello.sh`: Displays file details including type, permissions, owner, group, size, and timestamp.

**Concepts Learned:**
- File types: `-` for regular files, `d` for directories.
- Permissions are grouped into **Owner**, **Group**, and **Others**—each with `r` (read), `w` (write), `x` (execute).
- Only one permission set applies based on your relationship to the file.
- Ownership fields show who owns the file and which group it belongs to.

**Insights:**
- Permissions affect how users interact with files and directories.
- Example: `-r--rw-rwx` means the owner has read-only access, while others have more.
- Owner permissions take precedence—even if the owner is in the group.

**Screenshot:**  
![Lab 5 Screenshot](images/lab5.png)

---

### Lab 6
- **Commands:** `chmod`, `ls -l`, `./hello.sh`

**What They Do:**
- `chmod u+x hello.sh`: Adds execute permission for the user owner of the file.
- `ls -l hello.sh`: Verifies permission changes.
- `./hello.sh`: Executes the script from the current directory.

**Concepts Learned:**
- **chmod** stands for “change mode” (not “change permission”) because permissions were historically called modes of access.
- **Symbolic method** of `chmod` uses:
  - `u`, `g`, `o`, `a` to target user, group, others, or all.
  - `+`, `-`, `=` to add, remove, or set exact permissions.
  - `r`, `w`, `x` for read, write, and execute.
- Only the **file owner or root** can change permissions.
- Without execute permission, a script like `hello.sh` cannot be run—even if readable.
- Adding `x` for the user owner enables script execution.

**Insights:**
- Using `chmod u+x` is a safe way to grant execution rights without affecting group or others.
- `./hello.sh` runs the script from the current directory—this avoids relying on the system’s PATH.
- After permission is granted, the script runs successfully and prints “Hello World!”

**Screenshot:**  
![Lab 6 Screenshot](images/lab6.png)

---

## Bonus: Easter Egg Discovery
- **Command Used:** `aptitude moo`
- **What It Does:** Displays a humorous message—“There are no Easter Eggs in this program.”
- **Insight:** This is a hidden joke built into the `aptitude` package manager. If you keep adding `-v` flags (like `aptitude -v moo`, `aptitude -vv moo`), you’ll uncover more playful responses.

![Aptitude Moo Easter Egg](images/Easter_egg.png)

---

## Notes
Each lab includes:
- A brief summary of what was learned
- Key commands used
- Screenshots for visual reference

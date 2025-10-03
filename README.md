# linux_unhatched
“My progress through Cisco’s Linux Unhatched labs"

This repository documents my journey through Cisco’s Linux Unhatched labs, including commands, insights, and screenshots.

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
- **Commands:**  
- **Summary:**  
- **Screenshot:** [Add image or link here]

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

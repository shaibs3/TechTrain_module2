
# Overlay Filesystem Lab

In this lab, you will explore the basic concepts of overlay filesystems, specifically focusing on the lower, upper, and merged directories. You will learn how files are layered, modified, and merged.

## Setup
Start by creating a directory structure for the exercises:
```bash
mkdir -p /tmp/{lower,upper,merged,work}
```

---

## Exercise 1: Exploring Basic Overlay Structure

**Objective:** Set up an overlay filesystem with `lower`, `upper`, and `merged` directories to understand how they interact.

1. **Add Files to the Lower Directory:**
   ```bash
   echo "File in lower directory" > /tmp/lower/file1.txt
   echo "Another file in lower directory" > /tmp/lower/file2.txt
   ```

2. **Mount the Overlay Filesystem:**
   ```bash
   sudo mount -t overlay overlay -o lowerdir=/tmp/lower,upperdir=/tmp/upper,workdir=/tmp/work /tmp/merged
   ```

3. **Explore the Merged Directory:**
   ```bash
   ls /tmp/merged
   ```
   You should see `file1.txt` and `file2.txt`, demonstrating that files in the lower directory appear in the merged view.

---

## Exercise 2: Modifying Files and Observing Changes

**Objective:** Modify files in the merged directory and observe how changes appear in the upper directory.

1. **Modify an Existing File in the Merged Directory:**
   ```bash
   echo "Modified content in merged directory" >> /tmp/merged/file1.txt
   ```

2. **Verify that file1.txt was created in the Upper Directory:**
   ```bash
   ls /tmp/upper
   ```
   
3. Compare the contents of **file1.txt** in the upper directory to **file1.txt** in the lower directory. Which file will be reflected in /tmp/merged ? 

4. **Create a New File in the Merged Directory:**
   ```bash
   echo "New file in merged directory" > /tmp/merged/file3.txt
   ```
5. On which directory, will this new file be created? **/tmp/lower** or **/tmp/upper** and why?


---

## Exercise 3: Deleting Files and Understanding Overlay Behavior

**Objective:** Delete a file from the merged directory and see how the overlay filesystem handles deletions.

1. **Delete a File from the Merged Directory:**
   ```bash
   rm /tmp/merged/file2.txt
   ```

2. **Check the Upper Directory for Deletion Markers:**
   ```bash
   ls -a /tmp/upper
   ```
   A "whiteout" marker should appear, hiding `file2.txt` from the lower layer without deleting it.

3. **Verify the Lower Directory Remains Unchanged:**
   ```bash
   ls /tmp/lower
   ```
   The original `file2.txt` should still be in the lower directory.

4. **List the Merged Directory Contents:**
   ```bash
   ls /tmp/merged
   ```
   **Question** Do you see file2.txt in the merged directory?

5. **Cleanup:**
   ```bash
   sudo umount -l /tmp/merged
   ```

---

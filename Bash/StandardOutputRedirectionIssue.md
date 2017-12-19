# How to Read and Write the Same File In-place

### Problem:
`cat foo.txt > foo.txt` would produce an empty file of foo.txt.

### Cause:
When you use `>`, the file is opened in truncation mode so its contents are removed before the command attempts to read it.

### Solution:

Use an intermediary file and overwrite the original one when done and only if no error occurred while running the utility (this is the safest and more common way).
 
`cat foo.txt > foo.txt.temp && mv foo.txt.temp foo.txt`

---
Reference:
- [StackOverflow - Why does redirecting the output of a file to itself produce a blank file?](https://superuser.com/a/597257)

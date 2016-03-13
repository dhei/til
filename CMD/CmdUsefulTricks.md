# Useful Tricks of batch scripting

Inspired by a StackOverflow question [Hidden features of Windows batch files](http://stackoverflow.com/questions/245395/hidden-features-of-windows-batch-files)

---
Comments are more readable by `::` instead of `REM`, but please make sure there's [no `%` chars or redirection operators](http://ss64.com/nt/rem.html) in your command.
```bat
:: double-colun looks nicer than REM as comments
:: but be careful because it doesn't work for all cases
```

---
Command separators:

`&&` the second command will only run if the first command succeeded

`||` the second command will only run if the first command failed 

```bat
cls & dir
copy a b && echo Success
copy a b || echo Failure
```

---
Write a blank line:

```bat
echo.
```
---

Reference:
- Stackoverflow [Hidden features of Windows batch files](http://stackoverflow.com/questions/245395/hidden-features-of-windows-batch-files)
- Rob van der Woude [Batch HowTos](http://www.robvanderwoude.com/batchhowto.php)
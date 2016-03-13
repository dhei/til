# Useful Paths in batch scripting

Useful paths when executing batch script `test.bat` in directory `c:\Temp\long dir name with spaces\`

| Example    | Definition                  | Output                             |
|------------|-----------------------------|------------------------------------|
| `%~d0`     | d: returns the drive letter | c:                                 |
| `%~dp0`    | p: returns the path         | c:\Temp\long dir name with spaces\ |
| `%~x0`     | x: returns the file extension  | .bat                            |

Reference:
- Stackoverflow [What does %~dp0 mean, and how does it work?](http://stackoverflow.com/questions/5034076/what-does-dp0-mean-and-how-does-it-work)
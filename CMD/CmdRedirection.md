# Batch Redirection

Redirection examples:

| Example              | Explaination                                                       |
|----------------------|--------------------------------------------------------------------|
| `command > file.txt`   | Write standard output of command to file                           |
| `command >> file.txt`  | Append standard output of command to file                          |
| `commandA | commandB`  | Redirect standard output of commandA to standard input of commandB |
| `command < file.txt`   | command gets standard input from file                              |
| `command 2> file.txt`  | Write standard error of command to file                            |
| `command 2>> file.txt` | Append standard error of command to file                           |

It's ok to use spaces in redirection commands. Note however, that a space between an `ECHO` command and a `>` will be redirected too. `DIR>filename.txt` and `DIR > filename.txt` are identical, `ECHO Hello world>filename.txt` and `ECHO Hello world > filename.txt` are not, even though they are both valid.


Reference:
- Rob van der Woude [Redirection](http://www.robvanderwoude.com/redirection.php)
- Rob van der Woude [Display & Redirect Output](http://www.robvanderwoude.com/battech_redirection.php)
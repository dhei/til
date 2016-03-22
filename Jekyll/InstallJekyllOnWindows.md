# How to Install Jekyll on Windows

Windows package management tool [Chocolatey](https://chocolatey.org/) is the best tool available to install and manage Jekyll on Windows.

### Prerequisite: Chocolatey & Ruby
You will need chocolatey and ruby to install Jekyll

### Instructions:

(1) Install chocolatey (on Windows) if you don't already have it
```PowerShell
iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```
(2) Install ruby via chocolatey (on Windows) if you don't already have it
```
choco install ruby -y
```
(3) Close and re-open a new command prompt with **Administrator** privilege

(4) Install Jekyll
```
gem install jekyll
```

(5) run this command from your website's directory to serve your website locally and browse it on `http://localhost:4000/`
```
jekyll serve
```

---
Reference:
- David Burela: [Easily install Jekyll on Windows with 2 command prompt entries and Chocolatey](https://davidburela.wordpress.com/2015/11/28/easily-install-jekyll-on-windows-with-3-command-prompt-entries-and-chocolatey/)
- [README](https://github.com/dhei/dhei.github.io/blob/master/README.md) of [My Blog](http://diheiblog.com) 

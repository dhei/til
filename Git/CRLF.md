# CRLF Line Ending and .gitattributes

Every time you press return on your keyboard you're actually inserting an invisible character called a line ending. Historically, different operating systems have handled line endings differently. Windows uses CRLF while OS X uses LF for line ending. So it's a headache to deal with difference line endings cross-platform.

### What is `text=auto` in .gitattributes?
>This ensures that all files that git considers to be text will have normalized (LF) line endings in the repository. The core.eol configuration variable controls which line endings git will use for normalized files in your working directory; the default is to use the native line ending for your platform, or CRLF if core.autocrlf is set.

### What is `core.autocrlf` in git config?
>Git will process all text files and make sure **CRLF** is replaced by **LF** when `core.autocrlf=true`

### Solution for Cross-platform projects

1. git config --global core.autocrlf true
2. Add a .gitattributes file with `* text=auto` to the repository
3. Perform a [once-and-for-all line ending normalization](https://help.github.com/articles/dealing-with-line-endings/#refreshing-a-repository-after-changing-line-endings)

### A Much Simpler Solution for Windows-only projects

1. Remove .gitattributes (if present) from the repository
2. git config --global core-autocrlf false

Reference:
- Git Documentation: [gitattributes](https://git-scm.com/docs/gitattributes)
- GitHub Documentation: [Dealing with line endings](https://help.github.com/articles/dealing-with-line-endings/)
- StackOverflow: [What's the best CRLF (carriage return, line feed) handling strategy with Git?](http://stackoverflow.com/questions/170961/whats-the-best-crlf-carriage-return-line-feed-handling-strategy-with-git)
- A good article on background and history of end of line from Tim Clem: [Mind the End of Your Line](http://adaptivepatchwork.com/2012/03/01/mind-the-end-of-your-line/)
- A good article on how to deal with this issue from Scott Hanselman: [You're just another carriage return line feed in the wall](http://www.hanselman.com/blog/YoureJustAnotherCarriageReturnLineFeedInTheWall.aspx)
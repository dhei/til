# Merge two Git repositories

### Scenario #1
>Merge one repository as a subdirectory of another repository

### Solution: Subtree Merge

Example: Move repo-a/src as a subdirectory dir-a of repo-b/dest

1. Clone repo-b and navigate to repo-b
2. In repo-b, add repo-a as remote and fetch it
3. In repo-b, prepare merge with merge strategy 'ours'
4. In repo-b, read content from repo-a and store it under subdirectory dir-a
5. In repo-b, commit


    git clone repo-b https://github.com/repo-b-url
    cd repo-b

    git remote add -f repo-a https://github.com/repo-a-url

    git merge -s ours --no-commit repo-a/src

    git read-tree --prefix=dir-a/ -u repo-a/src

    git commit -m "Merge project a into project b"

**Cautions: This solution will lose history of repo-a**

Reference:

- [Subtree merging and you](http://nuclearsquid.com/writings/subtree-merging-and-you/)
- Git Documentaion [Subtree Merging](https://git-scm.com/book/en/v1/Git-Tools-Subtree-Merging)

---
### Scenario #2
>Move two repositories as two different subdirectories of a new repository while preserving history

### Solution: Merge Twice

Example: Move repo-a/src as dir-a and repo-b/dest as dir-b of repo-new

1. Create a new empty repository repo-new
2. Make a initial dummy commit in repo-new
3. Add repo-a as remote and fetch
4. Merge repo-a/src into repo-new/master
5. mkdir dir-a
6. Move all files into dir-a
7. Commit the move of dir-a
8. Add repo-b as remote and fetch
9. Merge repo-b/dest into repo-new/master
10. mkdir dir-b
11. Move all files coming from repo-b into dir-b
12. Commit the move of dir-b

Reference:

- [Merging Two Git Repositories Into One Repository Without Losing File History](http://saintgimp.org/2013/01/22/merging-two-git-repositories-into-one-repository-without-losing-file-history/)
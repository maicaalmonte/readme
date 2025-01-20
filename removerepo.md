steps to remove a repository (saving this shit bc im forgetful)

1. clone repository
```bash
    git clone https://github.com/maicaalmonte/maicaalmonte.git
    cd maicaalmonte
```
2. view commit history
```bash
    git log
```
3. reset or rebase
<br> reset your current branch to a specific commit
```bash
    git reset --hard 27884ee50b6abfb209b33feef3edd89d1e14c0d2^
```
b. interactive rebase to modify commits in your history:
```bash
    git rebase -i 27884ee50b6abfb209b33feef3edd89d1e14c0d2^
```
4. to remove the commit you want to remove in the list of commits
<br>a. look for the line corresponding to the commit
```bash
    pick 27884ee <commit message>
```
b. change the word pick to drop
```bash
     drop 27884ee <commit message>
```
5. save the file and exit
```bash
    press "ESC", type "wq", and press "ENTER"
```
6. force push to github
```bash
    git push origin main --force
```
##Instruction
### Download

    $ git --git-dir=/dev/null clone --depth=1 git@gitlab.cloud.isobar.ru:vziks/git-remote-big-files.git

### Checkout all remote brach to local

    $ git-remote-big-files/git-checkout-all-branch.sh
    
### Run script to remote file 

    $ git-remote-big-files/remote-file.sh <destination to file>
    
#### Example
    $ git-remote-big-files/remote-file.sh database/production/1.sql

### Add file to gitignore if need

    $ echo "database/production/1.sql" >> .gitignore
    $ git add .gitignore
    $ git commit -m "Add big data file to .gitignore"

### Check file and remote garbage

    $ git for-each-ref --format='delete %(refname)' refs/original | git update-ref --stdin
    $ git reflog expire --expire=now --all
    $ git gc --prune=now
    
### Force-push your local changes to overwrite your remote repository
    $ git push origin --force --all
    $ git push origin --force --tags
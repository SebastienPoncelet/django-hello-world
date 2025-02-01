# Project set up

## From scratch

### Create a repo:
```bash
gh auth login
gh repo create <repo_name> --public
```

### Add the remote URL to the local repository
```bash
git remote add origin https://github.com/<username>/<repo_name>.git
```

### Push the first commit
```bash
git push -u origin master
```




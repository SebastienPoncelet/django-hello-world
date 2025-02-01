# Project set up

## From scratch

### Create a repo:
```bash
gh auth login
gh repo create <repo_name> --public
```

### Initialize a Git repository
```bash
git init
```

### Add the remote URL to the local repository
```bash
git remote add origin https://github.com/<username>/<repo_name>.git
```

### Push the first commit
```bash
git push -u origin master
```

## Set up the pre-commit hook

### Installation
```bash
pipenv pre-commit install
```

### Create a `.pre-commit-config.yaml` file
This file contains basic hooks to be run, such as:
```yaml
# https://ljvmiranda921.github.io/notebook/2018/06/21/precommits-using-black-and-flake8/
#
# To skip certain hooks on commit:
# SKIP=flake8 git commit -m "foo"

exclude: >
  (?x)(
    /migrations/|
    /docs/
  )

default_language_version:
  python: python3.9

repos:
  # code formatter
  - repo: https://github.com/psf/black
    rev: 25.1.0
    hooks:
      - id: black

  - repo: https://github.com/asottile/add-trailing-comma
    rev: v3.1.0
    hooks:
      - id: add-trailing-comma

  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer

  - repo: https://github.com/pre-commit/mirrors-prettier
    rev: v3.1.0
    hooks:
      - id: prettier
        files: '^.*?\.html$'

  # code style checker
  - repo: https://github.com/pycqa/flake8
    rev: 7.1.1
    hooks:
      - id: flake8
        additional_dependencies: [flake8-bugbear]
        exclude: /(data_migrations|.jupyter)/
```







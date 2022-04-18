# Step deploy

## In server

We create on the server a repository **--Bare** for production :

**Create everything with the user so that everything created has this user and group.Access the server as a user not like root. But when climbing from local you can mistake and we will have to change the user:group con chown**

`git init --bare domino.git`

Into hook directory create file **post-receive**
`cd dominio.git/hooks`
`nano post-receive`

In this file we put the Hook that makes when doing Push, the information is saved in a defined directory:

```bash
#!/bin/sh
GIT_WORK_TREE=/home/<user-name>/<domain.com>/public-folder git checkout -f
```

*Other option*

```bash
#!/bin/sh
git --work-tree=/home/<domain>/public_html/main --git-dir=/home/<domain>/<git>.git checkout -f master
```

Save and changes permissions:

`chmod +x post-receive`

## In local

Before starting repository we create a gitignore with the files and directories that we want to ignore.
[Make gitignore](https://www.gitignore.io/)

Start repo

```bash
git init
git add .
git commit -m "Start Proyect"
```

Add remote repository

```bash
git remote add <remote-branch> ssh://<user-name>@<domain>/home/<domain>/<git>.git
```

Push:

`git push <remote-brach> <branch>`

---

[<-- main](/README.md)

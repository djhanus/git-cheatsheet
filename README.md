# Git Cheat Sheet
short-hand notes for common git commands

## remote push deployment

1. Login to remote server:

```shell
$ mkdir /home/user/repo.git
$ cd /home/user/repo.git
$ git init --bare
```

2. Create trigger script in `/home/user/repo.git/hooks/post-receive`:

```bash
#!/bin/sh
git --work-tree=/home/user/path/to/repo --git-dir=/home/user/repo.git checkout -f
```

Make sure the file is executable:
`$ chmod +x ~/user/repo.git/hooks/post-receive`

3. Clone the bare repo to the working directory:

```shell
$ git clone ~/user/repo.git ~/user/path/to/repo`
```

4. Prepare the local client side:

```shell
$ git remote add staging ssh://user@hostname/home/user/repo.git
```

List and check local remotes:

```shell
$  git remote -v
```

5. Done. Push changes to specific remote with:

```shell
$  git push staging master
```
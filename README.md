
# Linux guide: 🚀
### sync-git-repo

**Server:** Linux


## Installation

Use key-generator for rsa-public and private

**Important:** export private key using ssh format, for the public key copy key generated.

```bash
  cd /root/.ssh
  mv local/rs-public.pub .
  mv local/rs-private .
  touch config
  nano config
```
insert into config:
```bash
Host repo-name.github.com
 HostName github.com
 IdentityFile ~/.ssh/rs-private

Host *
IdentityFile ~/.ssh/id_rsa
```
## Config key into git repo

**Settings:** open deploy keys and add a key named and add private key.

**Important:** deploy key name must be the same used for configure private key into server.


## Cmd

#### set permission to private key

```bash
  chmod 600 rs-private
```
- [chmod calculator](https://chmod-calculator.com/)

| cmd | param     | Description                |
| :-------- | :------- | :------------------------- |
| `chmod` | `600` | **Required**. rs-private |





## Init repo

```bash
cd git-repo/
 git init
 git remote add origin git@repo-name.github.com:repo-source/repo-name.git
 git pull
 git branch --set-upstream-to=origin/master master  
 git status
cd ..
chown -R www-data:www-data git-repo
```



## SSH
ssh-keygen을 통한 key 복사

### 1. Create New Key
```zsh
cd ~/.ssh
ssh-keygen -t rsa -f id_rsa
ls
>>> id_rsa id_rsa.pub
```

### 2. Send id_rsa
Send **public** key to remote server
```zsh
scp -P 22 id_rsa.pub (user)@(IP):(ABS_PATH)
```

### 3. At Server
```zsh
ssh (user)@(IP) -p 22
mkdir ~/.ssh # ~/.ssh 디렉토리가 없는 경우
chmod 700 ~/.ssh

cat id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

### 4. Upload new IP on Config
```config
Host (HOSTNAME)
  HostName (IP)
  User (USERNAME)
  Port (PORT-NUMBER)
  IdentityFile ~/.ssh/id_rsa
```

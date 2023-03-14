# Ubuntu-setup

## GitHub (`gh`)

### 1. Install `gh`
```zsh
type -p curl >/dev/null || sudo apt install curl -y
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

### 2. GitHub Login through CLI
Then login through `gh`
```zsh
gh auth login
```

### 3. Upgrading GH
Upgrade GH
```zsh
sudo apt update
sudo apt install gh
```

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

## `watch`
For gpu monitoring
```zsh
watch -d -n 0.5 nvidia-smi
```
- `-d`: Show **d**ifference
- `-n`: Time interval
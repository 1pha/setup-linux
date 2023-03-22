# Linux Basic setups

## 1. Default setup for zsh

### Install ZSH
```bash
sudo apt-get update
sudo apt install zsh
```

### ZSH as default shell
```zsh
chsh -s $(which zsh)
```

### Pretty ZSH

```zsh
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/sindresorhus/pure.git ~/.zsh/pure
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```

- Add the followings to `~/.zshrc` file.
- `source activate` may not work
```zsh
path+=/opt/conda/bin
TZ=Asia/Seoul
LANG=C.UTF-8
LC_ALL=C.UTF-8
PYTHONDONTWRITEBYTECODE=1
PYTHONUNBUFFERED=1
PYTHONIOENCODING=UTF-8
PYTHONHTTPSVERIFY=0
source activate
fpath+=("$HOME/.zsh/pure")\nautoload -U promptinit; promptinit\nprompt pure
source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=111'
```

## 2. `tmux`
```bash
sudo apt-get install zsh
ctrl b, d to exti
```
### Basic usage
- New session: `tmux new -s work`
- Exit session: **CTRL B, D**
- Resume to session: `tmux attach -t work`
- Divide session into pane:
    - Horizontal spilt: **CTRL B, "**
    - Vertical split: **CTRL B, %**
- Entering Command mode: **CTRL B, :**
    - Removing panes: `kill-pane -t (index)`, where index counts from 0


## 3. `rsync`

Reference
- [Rsync basics](https://www.lesstif.com/system-admin/rsync-data-backup-12943658.html)
- [Changing ports](https://gkstamin.tistory.com/entry/Linux-rsync%EC%8B%9C-ssh-%ED%8F%AC%ED%8A%B8-%EB%B3%80%EA%B2%BD-%EB%B0%8F-%EC%82%AC%EC%9A%A9)
```bash
rsync -e 'ssh -p 20000' LOCALDIR REMOTEDIR
```
Flags
- `-v`: verbosity
- `-r`: recursive
- `-a`: archive mode
- `-z`: Data compress
- `-h`: Human-readable
- `-e`: Extra ssh flags to feed

## 4. Checking storage for certain directory

```bash
ls | xargs du -sh
```

## 5. Mounting External disk

```bash
sudo fdisk -l
sudo mkfs.ext4 /dev/sda
sudo mount /dev/sda /mnt
```
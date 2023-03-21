# ZSH

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

## 1. Pretty ZSH

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
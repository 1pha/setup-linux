# Simple Nifty Commands

## `watch`: To monitor something
For gpu monitoring
```bash
watch -d -n 0.5 nvidia-smi
```

* `-d`: Show **d**ifference
* `-n`: Time interval

## `tmux`: Running in background, but accessible
```bash title="Installing tmux"
sudo apt-get install tmux
```

### Basic usage
* `tmux` consists of session - pane hierarchy.
`work` is the name of session.
* New session: `tmux new -s work`
* Exit session: **CTRL B, D**
* Resume to session: `tmux attach -t work`
* Divide session into pane:
    - Horizontal spilt: **CTRL B, "**
    - Vertical split: **CTRL B, %**
* Entering Command mode: **CTRL B, :**
    - Removing panes: `kill-pane -t (index)`, where index counts from 0

## `rsync`: Send files to remote server
``` bash title="Basic rsync usage"
rsync -e 'ssh -p 20000' LOCALDIR REMOTEDIR
```
Flags

* `-v`: verbosity
* `-r`: recursive
* `-a`: archive mode
* `-z`: Data compress
* `-h`: Human-readable
* `-e`: Extra ssh flags to feed

Sometimes permission issue may be raised.


Reference

* [Rsync basics](https://www.lesstif.com/system-admin/rsync-data-backup-12943658.html)
* [Changing ports](https://gkstamin.tistory.com/entry/Linux-rsync%EC%8B%9C-ssh-%ED%8F%AC%ED%8A%B8-%EB%B3%80%EA%B2%BD-%EB%B0%8F-%EC%82%AC%EC%9A%A9)

## Checking storage for certain directory

``` bash
ls | xargs du -sh
```
!!! question "What is `xargs`?"
    Sometimes you want outputs from a certain command such as list, and feed them to other commands. This is available through `xargs`. Above command allows `ls` stdout to be stdin of `du -sh` command.


## Mounting External disk
``` bash title="Mounting external disk"
sudo fdisk -l
sudo mkfs.ext4 /dev/sda # (1)
sudo mount /dev/sda /mnt
```

1. Please check your disk name: `dev/sda`

## Mounting External disk
``` bash title="Mounting external disk"
sudo fdisk -l
sudo mkfs.ext4 /dev/sda # (1)
sudo mount /dev/sda /mnt
```

1. Please check your disk name: `dev/sda`
# NVIDIA-SMI
- Follow official [instructions](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#) from nvidia.
    - 2. Pre-install
    - 3.10 Ubuntu Package Manager Installation
    - 4. Driver installation
- This worked for me (Mar 22, 2023)
```bash
sudo apt-get install cuda-drivers-525
sudo apt install cuda-drivers-525
lspci | grep -i nvidia
uname -m && cat /etc/*release
sudo apt-get install linux-headers-$(uname -r)
sudo apt autoremove
sudo apt-get install linux-headers-$(uname -r)
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb
sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda
sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-key del 7fa2af80
sudo apt-get update
sudo apt-get install cuda
sudo apt-get install nvidia-gds
reboot
sudo reboot
sudo apt-get install cuda-drivers-525
sudo reboot
nvidia-smi
```
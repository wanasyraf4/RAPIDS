![image](https://github.com/wanasyraf4/RAPIDS/assets/107595740/d2325586-e982-4950-96f4-b5c06c59cd69)


# Prerequisite RAPIDS setup

- On WSL2
- On ubuntu server

![image](https://github.com/wanasyraf4/RAPIDS/assets/107595740/a9b5daaf-47b9-408c-af9f-c74310ffedf8)

## Install on WSL2

======== Notes =======

A. make sure WSL2 with:
> wsl --list --verbose

B. Make sure GPU compute capability 6+, check here:
> https://developer.nvidia.com/cuda-gpus

======================


1. **update env**
> sudo apt update and sudo apt upgrade -

2. **Install cuda compiler** (this is cuda compiler 11.8 since rapids use 11.4 till 11.8, 12.1 and 12.2 not yet supported)
> wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin

> sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600

> wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb

> sudo dpkg -i cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb

> sudo cp /var/cuda-repo-wsl-ubuntu-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/

> sudo apt-get update

> sudo apt-get -y install cuda

3. **edit .bashrc**
> nano .bashrc

add on bottom depending on cuda compiler installed

> export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}

> export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64:$LD_LIBRARY_PATH

4. **Update gcc**
> sudo apt upgrade gcc

5. **install and Update pip**
> pip install --upgrade pip

6. **restart WSL**
On CMD not ubuntu terminal:
> wsl --shutdown


![image](https://github.com/wanasyraf4/RAPIDS/assets/107595740/711f1546-7ca1-49d6-a203-3148092823b9)

## Install on ubuntu server (AWS EC2, AWS AMI Google Cloud, proxmox, etc etc)
1. **update env**
> sudo apt update and sudo apt upgrade -y

2. **getting cuda compiler** (note that the cuda compiler is 11.8)
> wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-keyring_1.0-1_all.deb

> sudo dpkg -i cuda-keyring_1.0-1_all.deb

> sudo apt-get update

> sudo apt-get -y --no-install-recommends install cuda-toolkit-11-8

> sudo apt install nvidia-headless-525-server nvidia-utils-525-server libnvidia-encode-525-serve

3. **edit .bashrc**
> nano .bashrc

add on bottom depending on cuda compiler installed

> export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}

> export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64:$LD_LIBRARY_PATH

after save, run bash
> source ~/.bashrc

check path
> echo $PATH

4. **update and restart server**
> sudo apt update 

> sudo reboot


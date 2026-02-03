### Install History

- ubuntu22.04
- ip : static : inet 172.30.1.207/24 brd 172.30.1.255 scope global noprefixroute enp34s0
- user: mulder, path: /home/mulder, pwd : 6448
- access: ssh mulder@g3090

```
# nvidia drive cuda cudnn
  sudo apt update && upgrade -y
  sudo apt install build-essential gcc ubuntu-drivers-common dkms vim nvidia-modprobe
  sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
  sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
  cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
  blacklist nouveau
  sudo update-initramfs -u
  lsmod |grep nouveau
  ubuntu-drivers devices
  sudo apt install nvidia-driver-525
  sudo reboot
  nvidia-smi
  sudo apt install -y nvidia-utils-525
  sudo apt install -y nvidia-cuda-toolkit
  ldconfig -p | grep cudnn
  sudo apt install git
  nvcc -V

  cd Downloads/
  sudo dpkg -i cudnn-local-repo-ubuntu2204-8.9.7.29_1.0-1_amd64.deb
  nvidia-smi

# uv for python
  curl -LsSf https://astral.sh/uv/install.sh | sh

  cd ~/Project/mulder
  uv venv -p 3.13
  source .venv/bin/activate
  deactivate

# nvidia-docker
  sudo apt install -y ca-certificates curl gnupg lsb-release
  distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
  curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
  curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
  sudo apt update
  sudo apt install -y nvidia-docker2
  sudo systemctl restart docker
  sudo usermod -aG docker $USER
  sudo reboot

  docker ps -a
  docker run --rm --gpus all nvidia/cuda:11.6.2-base-ubuntu20.04 nvidia-smi

# ssh
  sudo apt update
  sudo apt install openssh-server

```

# rp4b-llama
LLaMA on Raspberry Pi 4B

## Device

- Raspberry Pi 4B (8GB)
- 32GB MicroSD

## Setup

1. Setup Miniforge

- Target Path: ~/miniforge3

```
cd ~/Downloads/
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-aarch64.sh
bash Miniforge3-Linux-aarch64.sh
```

- Add $PATH and execute conda.sh

```
nano ~/.bashrc
export PATH="~/miniconda3/bin:$PATH"
source ~/miniforge3/etc/profile.d/conda.sh
```

- Reboot

```
sudo reboot
```

- Create new conda environment
```
conda create -n sky
conda activate sky
```

# rp4b-llama
LLaMA on Raspberry Pi 4B

## Device

- Raspberry Pi 4B (8GB)
- 32GB MicroSD

## Setup

### 1. Setup Miniforge

- Install miniforge3 aarch64 (arm64)

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

- Create new conda environment (I named it, sky)
```
conda create -n sky
conda activate sky
```

### 2. Setup PyLLaMA

- Install PyLLaMA and dependencies
```
pip install pyllama -U
pip install transformers
```

- If you get the error "ImportError: cannot import name 'ParamSpec' from 'typing_extensions'"
```
pip uninstall typing_extensions
pip uninstall fastapi
pip install --no-cache fastapi
```

- Clone a pyllama git repository (e.g., ~/Desktop/Playground/)
```
git clone https://github.com/juncongmoo/pyllama.git
```

- Download LLaMA 7B model (models: 7B/13B/30B/65B)
```
cd pyllama
python -m llama.download --model_size 7B
```

- (optional) To run on a Raspberry Pi 4GB model, you must follow [quantization process](https://github.com/juncongmoo/pyllama#-quantize-llama-to-run-in-a-4gb-gpu)

### 3. Inference

- Run inference.py

```
python inference.py --ckpt_dir ./pyllama_data/7B --tokenizer_path ./pyllama_data/tokenizer.model
```

## Reference

- [Miniforge](https://github.com/conda-forge/miniforge/)
- [PyLLaMA](https://github.com/juncongmoo/pyllama)

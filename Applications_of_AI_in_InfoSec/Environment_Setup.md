# Environment Setup

```
# Create virtual environment
python3 -m venv ai-env
source ai-env/bin/activate

# Install core packages
pip install jupyterlab numpy pandas scikit-learn matplotlib seaborn tensorflow keras

jupyter notebook

or

python3 -m notebook
```

### Launches in browser
<img width="1892" height="557" alt="image" src="https://github.com/user-attachments/assets/b5ff91ca-189a-4db6-b763-a23d845df37e" />
<img width="1383" height="354" alt="image" src="https://github.com/user-attachments/assets/162db1f9-7aed-4e4a-9472-fb460fc2caee" />

### Using Miniconda in linux: 

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh -b -u
```

```
┌──(kali㉿kali)-[~]
└─$ eval "$(/home/$USER/miniconda3/bin/conda shell.$(ps -p $$ -o comm=) hook)"

                                                                                                                                                                                                                                         
(base) ┌──(kali㉿kali)-[~]
└─$ 
```

```
conda create -n ai python=3.11
conda activate ai
```

```
# Core AI/Data Science packages
conda install -y numpy scipy pandas scikit-learn matplotlib seaborn transformers datasets tokenizers accelerate evaluate optimum huggingface_hub nltk category_encoders

# PyTorch + GPU support (optional if you don't have NVIDIA GPU)
conda install -y pytorch torchvision torchaudio pytorch-cuda=12.4 -c pytorch -c nvidia

# Additional Python tools via pip
pip install requests requests_toolbelt

```

Activating it moving forward:
```
conda activate ai
```

















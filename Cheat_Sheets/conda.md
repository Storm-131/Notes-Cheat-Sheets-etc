# Conda - Cheats 🐍

---

### Basics

```bash
conda info
conda --version

conda activate RL
conda activate base

conda deactivate
```

---

### Create Environments

```python
conda list			
conda env list

conda create --name torch python=3.10.9

conda activate compgen
conda deactivate

conda update -n base conda
conda update --all --yes
```

---

### Setting up channels

```python
conda config --add channels defaults
e.g. bioconda conda-forge anaconda
```

---

### Export / Save environment

```python
conda env export --name vscode > vscode.yaml  # Create YAML-File

conda config --set restore_free_channel true
conda env create -f file.yaml  # Load from YAML-File

conda list --explicit > spec-file.txt    # Safe environment
conda create --name myenv python=3.9.12 --file spec-file.txt    # Create identical environment

# -- WARNING: If channels are outdated, you may use this:
CONDA_RESTORE_FREE_CHANNEL=1 conda env create -f virtual_platform_mac.yml
```

---

### Cleaning / Removing

```python
conda clean -a -d   # Dry Run
conda clean -a      # Clean the whole system:

conda remove numpy 				     # Remove package
conda env remove --name ENV_NAME	 # Remove environment

# Full Remove (of anaconda installation)
conda install anaconda-clean
anaconda-clean --yes    # Remove all anaconda-related files, no confirmation
```

---

### Autocomplete

Tip: Close Terminal completely to update

```bash
# 1) Install this
conda install argcomplete

# 2) Add to zsh profile
open -a sublime ~/.zshrc

# Add this Anaconda-Path to ~/.zshrc
autoload -Uz compinit
fpath+=/Users/miniconda3/conda-zsh-completion-master
compinit # -i

# Give right to folder
compaudit
sudo chmod -R 755 /Users/...
```

---

### Switch between osx-64 and ARM

```python
# Into new version (ARM M1)
CONDA_SUBDIR=osx-arm64 conda env create -n tf -f tf-metal-arm64.yaml
conda activate tf
conda config --env --set subdir osx-arm64 ## permanently set the subdir
conda install tensorflow

# Into old version (osx-64)
CONDA_SUBDIR=osx-64 conda create -n torch python=3.9
conda activate torch
conda config --env --set subdir osx-64
```

---

### Flush Base

```python
conda install --rev 1
pip uninstall -y -r <(pip freeze)
conda update conda
```

---

### Add conda to zsh

Add a config file. Find the Anaconda-Installation via the Alias.

```bash
touch ~/.zshrc        # Create config-file
open ~/.zshrc         # Open config-file

# Add Anaconda-Path to ~/.zshrc (Might be altered!)
export PATH="/opt/anaconda3/bin:$PATH"

source ~/.zshrc       # Restart Terminal with new configuration
```

---

# Project Commands Reference

This file contains the commands used for managing the conda environment and Docker for this project.

## Conda Commands

### Create the environment
```powershell
conda create -n env_rl_project python=3.10 -y
```

### Activate the environment
```powershell
conda activate env_rl_project
```

### Install dependencies
```powershell
pip install -r requirements.txt
```

### Export the environment
To YAML (portable version without absolute paths):
```powershell
conda env export -n env_rl_project --no-builds | Select-Object -SkipLast 1 > environment.yml
```

### Run the project using conda
```powershell
conda run -n env_rl_project python Gan.py
```

---

## Docker Commands

### Build the Docker image
```powershell
docker build -t gan-project .
```

### Run the Docker container
```powershell
docker run --name gan-container gan-project
```

### Stop and remove the container
```powershell
docker stop gan-container
docker rm gan-container
```

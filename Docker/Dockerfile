# Utilisation de l'image de base PyTorch avec ROCm
FROM docker.io/rocm/pytorch:rocm6.3.1_ubuntu22.04_py3.10_pytorch as BUILD

# Installation des dépendances système
RUN apt-get update && apt-get install -y \
    git \
    python3-pip \
    python3-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Configuration de variables d'environnement pour ROCm
ENV HSA_OVERRIDE_GFX_VERSION=11.0.0
ENV PYTORCH_ROCM_ARCH=gfx1100

# Création du répertoire de travail
WORKDIR /app

# Clone de ComfyUI
RUN git clone https://github.com/comfyanonymous/ComfyUI.git .

# Installation des dépendances Python
RUN pip3 install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.2 --force-reinstall
RUN pip3 install -r requirements.txt

FROM BUILD as RUN

# Port d'exposition
EXPOSE 8188

# Répertoire pour les modèles
VOLUME /app/models/configs

# Commande de démarrage
CMD ["python3", "main.py", "--listen", "0.0.0.0"]


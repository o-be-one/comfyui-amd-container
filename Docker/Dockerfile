# Use the PyTorch base image with ROCm
FROM docker.io/rocm/pytorch:rocm6.3.1_ubuntu22.04_py3.10_pytorch AS BUILD

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    python3-pip \
    python3-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Set environment variables for ROCm
ENV TAG_COMFYUI=v0.3.13
ENV HSA_OVERRIDE_GFX_VERSION=11.0.0
ENV PYTORCH_ROCM_ARCH=gfx1100

# Create the working directory
WORKDIR /app

# Clone ComfyUI
RUN git clone --branch ${TAG_COMFYUI} https://github.com/comfyanonymous/ComfyUI.git .

# Install Python dependencies
RUN pip3 install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.2 --force-reinstall
RUN pip3 install -r requirements.txt

FROM BUILD AS RUN

VOLUME ["/app/models/configs"]

# Port for exposing
EXPOSE 8188

# Startup command
CMD ["python3", "main.py", "--listen", "0.0.0.0"]
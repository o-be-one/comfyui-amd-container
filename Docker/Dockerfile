FROM docker.io/rocm/pytorch:rocm6.3.1_ubuntu22.04_py3.10_pytorch

RUN apt-get update && apt-get install -y \
    git \
    python3-pip \
    python3-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

ENV HSA_OVERRIDE_GFX_VERSION=11.0.0
ENV PYTORCH_ROCM_ARCH=gfx1100

WORKDIR /app

RUN git clone https://github.com/comfyanonymous/ComfyUI.git . \
    && pip3 install -r requirements.txt \
    && pip3 install --no-cache-dir \
    torch \
    torchvision \
    torchaudio \
    --index-url https://download.pytorch.org/whl/rocm6.2 \
    --force-reinstall \
    && pip3 install numpy scipy --force-reinstall

EXPOSE 8188

VOLUME /app/models/configs

CMD ["python3", "main.py", "--listen", "0.0.0.0"]

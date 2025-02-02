# comfyui-amd-container

Run **ComfyUI** in a container (Podman/Docker) with AMD graphics card.  
✅ Tested with Podman (requires `root`)  
🚀 Tested on [MaximumSettings](MAXIMUMSETTINGS.md)

**Reference Configuration**:
- CPU: AMD 7800X3D
- GPU: AMD 7900XTX (24GB VRAM)
- RAM: 32 GB DDR5
- OS: Linux Mint 22

## Prerequisites

### Hardware
- AMD graphics card compatible with ROCm (excluding integrated GPUs)
- 16 GB+ system RAM

### Software
- Podman + podman-compose **OR** Docker + docker-compose
- DKMS (`sudo apt install dkms`)
- Linux headers (`linux-headers-generic`)
- Build tools (gcc/g++)

## Installation

1. **Prepare the AMD kernel modules**:
```bash
# Download the AMD installation package
wget https://repo.radeon.com/amdgpu-install/<VERSION>/ubuntu/focal/amdgpu-install_<VERSION>.deb

# Install DKMS dependencies
sudo apt install ./amdgpu-install_<VERSION>.deb
sudo amdgpu-install --usecase=dkms
```

2. **Check the installation**:
```bash
dkms status | grep amdgpu  # Should return 'amdgpu' with status 'installed'
lsmod | grep amdgpu  # Check if the module is loaded
```

3. **Start ComfyUI**:
```bash
# With Podman
sudo podman compose -f docker-compose.yaml up

# With Docker
docker compose -f docker-compose.yaml up
```

## Key Features
- 🛠️ Docker image maintained via GitHub Actions
- 📦 Specific version of ComfyUI (no manual build)
- 🔒 Isolation via containers (without modifying the host)
- 📄 Unified documentation ([MaximumSettings](MAXIMUMSETTINGS.md))

## Roadmap
| Status | Feature                             |
|--------|-------------------------------------|
| ✅     | Complete documentation               |
| ✅     | Versioning of ComfyUI               |
| ✅     | CI/CD with GitHub Container Registry |
| ⏳     | Verified Docker compatibility        |
| ⏳     | Dependabot integration               |
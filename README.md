# comfyui-amd-docker (WIP)
**Work in Progress**
Run ComfyUI in container (including Podman) using your AMD GPU graphic card.
*Built to work with Podman for now.*

## Requirements

### Host machine

- podman
- podman-compose
- amdgpu-dkms (required to properly run AMD GPU in containers)

## Status

At this time it works in cpu mode but not in gpu, on my side as Linux machine I'm using is a bare metal in cloud with some settings required by the provider. I'm trying to figure out how to properly install amdgpu-dkms without breaking requirements.
Spec:
- CPU: AMD 7800X3D
- GPU: AMD 7900XTX
- RAM: 32go DDR5 (upgrade to 96gb soon)

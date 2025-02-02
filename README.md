# comfyui-amd-container

Exécutez **ComfyUI** dans un conteneur (Podman/Docker) avec carte graphique AMD.  
✅ Testé avec Podman (nécessite `root`)  
🚀 Fonctionne aussi avec [MaximumSettings](MAXIMUMSETTINGS.md)

**Configuration de référence** :
- CPU : AMD 7800X3D
- GPU : AMD 7900XTX (24GB VRAM)
- RAM : 32 Go DDR5
- OS : Linux Mint 22

## Prérequis

### Matériel
- Carte graphique AMD compatible ROCm (hors GPU intégrés)
- 16 Go+ RAM système

### Logiciel
- Podman + podman-compose **OU** Docker + docker-compose
- DKMS (`sudo apt install dkms`)
- Headers Linux (`linux-headers-generic`)
- Outils de compilation (gcc/g++)

## Installation

1. **Préparer les modules kernel AMD** :
```bash
# Télécharger le package d'installation AMD
wget https://repo.radeon.com/amdgpu-install/<VERSION>/ubuntu/focal/amdgpu-install_<VERSION>.deb

# Installer les dépendances DKMS
sudo apt install ./amdgpu-install_<VERSION>.deb
sudo amdgpu-install --usecase=dkms
```

2. **Vérifier l'installation** :
```bash
dkms status | grep amdgpu  # Doit retourner 'amdgpu' avec status 'installed'
lsmod | grep amdgpu  # Vérifier le chargement du module
```

3. **Démarrer ComfyUI** :
```bash
# Avec Podman
sudo podman-compose -f docker-compose.yaml up

# Avec Docker
docker-compose -f docker-compose.yaml up
```

## Fonctionnalités clés
- 🛠️ Image Docker maintenue via GitHub Actions
- 📦 Version spécifique de ComfyUI (pas de build manuel)
- 🔒 Isolation via containers (sans modifier l'hôte)
- 📄 Documentation unifiée ([MaximumSettings](MAXIMUMSETTINGS.md))

## Roadmap
| Statut | Fonctionnalité                     |
|--------|------------------------------------|
| ✅     | Documentation complète             |
| ✅     | Versionnage de ComfyUI             |
| ✅     | CI/CD avec GitHub Container Registry |
| ⏳     | Compatibilité Docker vérifiée      |
| ⏳     | Intégration Dependabot             |
# MaximumSettings User Guide (AMD GPU Setup)

**Prérequis** : Ce guide complète le [README.md](README.md) principal et nécessite une instance **MaximumSettings** "Bare Metal" (tiers 4).

## Configuration requise pour l'hôte

Les instances MaximumSettings utilisent des pilotes AMD Mesa génériques. Pour les workloads d'IA avancées :  

1. **Mise à jour des outils de compilation** :
```bash
sudo apt install gcc-14 g++-14
```

2. **Installation des headers de kernel spécifiques** :  
[Télécharger les headers pour le noyau 6.10.10](https://mirrors.portworx.com/mirrors/https/kernel.ubuntu.com/mainline/v6.10.10/amd64/linux-headers-6.10.10-061010-generic_6.10.10-061010.202409121037_amd64.deb)  
```bash
sudo apt install ./linux-headers-6.10.10-generic_6.10.10-061010.202409121037_amd64.deb
```

3. **Vérification de l'installation** :  
```bash
dpkg -l | grep linux-headers-6.10.10-061010-generic
```

4. **Redémarrage du système** :  
```bash
sudo reboot
```

**Note** : Si votre noyau est différent du 6.10.10, adaptez les numéros de version dans les commandes.

## Prochaines étapes

Poursuivez avec le [README.md](README.md) principal pour :  
1. Installer ```amdgpu-dkms```
2. Démarrer le conteneur ComfyUI
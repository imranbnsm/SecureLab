# Machines virtuelles déployées

## Pare-feu
- pfSense Community Edition
- Rôle : routage, filtrage, NAT, DHCP

## Poste client LAN
- Ubuntu Linux
- Rôle : poste utilisateur interne
- Adresse IP : attribuée dynamiquement via DHCP

Ce poste est utilisé pour valider l’accès au pare-feu et à Internet.

![Séléction du réseau LAN pour le client Ubuntu](../docs/images/ubuntu_network.png)

> Nous choisissons le réseau LAN pour le client Ubuntu

![IP du clien Ubuntu attribuée par pfSense](../docs/images/ubuntu_ip.png)
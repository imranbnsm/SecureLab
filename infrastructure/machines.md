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

## Serveur Active Directory
- Windows Server 2022
- Rôle : contrôleur de domaine, DNS, Active Directory
- Domaine : `technova.local`
- Adresse IP statique LAN : 192.168.10.10
- Mot de passe administrateur robuste (8+ caractères, alphanumérique et spécial)
- OU (Unités d'Organisation) créées : `Users`, `Servers`, `IT`, `RH`, `Sales`
- Groupes de sécurité créés : `GRP-IT`, `GRP-RH`, `GRP-SALES`
- Attribution des utilisateurs aux groupes correspondants

![VM AD réseau VMware](../docs/images/ad-serv_vmware_network.png)
>On place la VM sur le réseau LAN

![ipv4 Serveur](../docs/images/srv-ad_ipv4.png)
>On attribue manuellement les caractéristiques ipv4 du serveur

![Rôles installés sur le serveur AD](../docs/images/srv-ad_roles.png)

![Domain controllers & OU](../docs/images/srv-ad_domain.png)

![Attribution utilisateurs → groupes](../docs/images/srv-ad_group_attribution.png)
>On crée utilisateurs et groupes pour les futures restrictions comportementales

![Connexion domaine réussie](../docs/images/srv-ad_login.png)
>On se connecte via le compte administrateur au domaine local
# Architecture réseau du projet SecureLab

## Vue d’ensemble

L’architecture réseau du projet SecureLab repose sur une segmentation en trois zones distinctes, protégées par un pare-feu central. Cette organisation permet de limiter la surface d’attaque, de contrôler les flux réseau et de respecter les principes fondamentaux de sécurité.

Les trois zones sont :
- le réseau externe (WAN),
- le réseau interne (LAN),
- la zone démilitarisée (DMZ).

Un pare-feu pfSense assure le routage, le filtrage des flux et la traduction d’adresses (NAT).

---
Le diagramme ci-dessous illustre la segmentation réseau, les machines virtuelles déployées ainsi que les flux autorisés et interdits entre les différentes zones.

![Diagramme Réseau SecureLab](./images/Diagramme_Réseau_SecureLab.png)

---

## Description des zones réseau

### Réseau WAN – Réseau externe

Le réseau WAN représente l’accès à Internet. Il est connecté au pare-feu pfSense via une interface configurée en DHCP/NAT à l’aide de l’hyperviseur.

Cette zone inclut également une machine Kali Linux utilisée pour simuler un attaquant externe. Elle permet de réaliser des tests d’intrusion contrôlés sur les services exposés.

> **Note de virtualisation :**  
> Dans cet environnement virtualisé, le réseau WAN du pare-feu pfSense représente l’Internet ainsi que les réseaux externes.  
> L’hyperviseur joue le rôle de fournisseur d’accès, ce qui permet de simuler un accès Internet réel sans déployer de routeur physique intermédiaire.


---

### Réseau LAN – Réseau interne

Le réseau LAN (`192.168.10.0/24`) correspond au réseau interne de l’entreprise. Il héberge :
- les postes de travail des employés (Windows et Linux),
- un serveur Windows assurant les rôles d’Active Directory, de DNS et de serveur de fichiers.

Les postes clients obtiennent leurs adresses IP via DHCP et utilisent le serveur Active Directory pour l’authentification centralisée. L’accès à Internet depuis le LAN est autorisé mais filtré par le pare-feu.

---

### Réseau DMZ – Services exposés

La DMZ (`192.168.20.0/24`) héberge les services destinés à être accessibles depuis Internet. Dans le cadre du projet, elle contient un serveur web exécutant un service HTTP/HTTPS.

Cette zone est isolée du réseau interne afin de limiter l’impact d’une compromission d’un service exposé. Les communications initiées depuis la DMZ vers le LAN sont bloquées par défaut.

---

## Rôle du pare-feu pfSense

Le pare-feu pfSense joue un rôle central dans l’architecture. Il assure :
- le routage entre les différentes zones réseau,
- la mise en œuvre des règles de filtrage,
- la traduction d’adresses (NAT),
- le contrôle des flux entrants et sortants.

Le pare-feu est de type *stateful*, ce qui signifie que les réponses à des connexions initiées depuis une zone autorisée sont automatiquement acceptées, sans nécessiter de règles entrantes générales.

---


## Politique de filtrage réseau

Les principes de filtrage appliqués sont les suivants :
- le trafic LAN vers Internet est autorisé (HTTP, HTTPS, DNS),
- le trafic LAN vers la DMZ est autorisé (HTTP, HTTPS),
- le trafic WAN vers la DMZ est autorisé uniquement pour les services web,
- le trafic WAN vers le LAN est strictement interdit,
- le trafic initié depuis la DMZ vers le LAN est bloqué.

Cette politique permet de respecter les principes de segmentation du réseau, d’exposition contrôlée des services et de moindre privilège.



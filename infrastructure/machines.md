# Machines Virtuelles Déployées

## 1. Pare-feu

Voir la page [firewall.md](../security/firewall.md) pour plus d'informations.

- **Nom** : pfSense Community Edition  
- **Rôle** : Routage, filtrage, NAT, DHCP  


## 2. Poste Client LAN
- **Système d'exploitation** : Ubuntu Linux  
- **Rôle** : Poste utilisateur interne test  
- **Adresse IP** : Attribuée dynamiquement via DHCP  

Ce poste est utilisé pour valider l’accès au pare-feu et à Internet.

![Sélection du réseau LAN pour le client Ubuntu](../docs/images/ubuntu_network.png)

> Nous choisissons le réseau LAN pour le client Ubuntu

![IP du client Ubuntu attribuée par pfSense](../docs/images/ubuntu_ip.png)

---

## 3. Serveur Active Directory
- **Nom** : Windows Server 2022  
- **Rôle** : Contrôleur de domaine, DNS, Active Directory  
- **Domaine** : `technova.local`  
- **Adresse IP statique LAN** : 192.168.10.10  
- **Mot de passe administrateur** : Robuste (8+ caractères, alphanumérique et spécial)  
- **OU (Unités d'Organisation) créées** : `Users`, `Servers`, `IT`, `RH`, `Sales`  
- **Groupes de sécurité créés** : `GRP-IT`, `GRP-RH`, `GRP-SALES`  
- **Attribution des utilisateurs aux groupes correspondants**  

![VM AD réseau VMware](../docs/images/ad-serv_vmware_network.png)
> On place la VM sur le réseau LAN

![ipv4 Serveur](../docs/images/srv-ad_ipv4.png)
> On attribue manuellement les caractéristiques ipv4 du serveur

![Rôles installés sur le serveur AD](../docs/images/srv-ad_roles.png)

![Domain controllers & OU](../docs/images/srv-ad_domain.png)

![Attribution utilisateurs → groupes](../docs/images/srv-ad_group_attribution.png)
> On crée utilisateurs et groupes pour les futures restrictions comportementales

![Connexion domaine réussie](../docs/images/srv-ad_login.png)
> On se connecte via le compte administrateur au domaine local

---

## 4. Machine Utilisateur Locale Windows 11
- **Nom** : Windows 11 Professionnal Edition  
- **Rôle** : Poste utilisateur IT de l'entreprise Technova 
- **Adresse IP** : Attribuée dynamiquement via DHCP  

Nous installons tout d'abord la VM sur le sous-réseau LAN :

![Sous réseau LAN](../docs/images/windows11_network.png)

Nous vérifions que la machine reçoit une IP dynamiquement, qu'elle peut ping le serveur AD et que la résolution de noms de domaines fonctionne : 

![IP Windows 11](../docs/images/windows11_ip.png)

![Ping SRV-AD](../docs/images/windows11_ping_ad-srv.png)

![Test DNS](../docs/images/windows11_dns.png)

Nous configurons ensuite la machine pour qu'elle fasse partie du domaine Technova défini sur AD : 

![Domain Join](../docs/images/windows11_domain_join.png)

Nous pouvons ensuite nous connecter en tant qu'utilisateur créé au préalable sur AD, en changeant le mot de passe après la première connexion : 

![Première connexion Windows 11](../docs/images/windows_11_login_it_new_password.png)

## 5. Machine Utilisateur Locale Windows 11
- **Nom** : Windows 11 Professionnal Edition  
- **Rôle** : Poste utilisateur RH de l'entreprise Technova 
- **Adresse IP** : Attribuée dynamiquement via DHCP  

Après avoir suivi les mêmes étapes d'installation que la VM précdente, nous nous connectons au domaine TECHNOVA via le compte utilisateur appartenant au groupe RH crée sur AD : 

![Première connexion Windows 11](../docs/images/windows_11_login_rh.png)

![Avertissement mot de passe](../docs/images/login_windows_11_rh_new_password.png)
>La GPO mot de passe est appliquée sur les hôtes non administrateurs / SI

![Message affiché connexion](../docs/images/windows_11_login_rh_message.png)
>On se connecte ensuite en créant un mot de passe adéquat puis nous sommes avertis par un message.


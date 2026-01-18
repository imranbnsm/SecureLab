# Validation de l’installation pfSense

## Accès à l’interface d’administration

L’interface Web du pare-feu pfSense est accessible depuis le réseau LAN via HTTPS.  
Un certificat auto-signé est utilisé, ce qui entraîne un avertissement de sécurité côté navigateur, comportement attendu dans un environnement de test.

![Avertissement de sécurité](../docs/images/ubuntu_unsecure_connection.png)

![Interface web pfsense](../docs/images/ubuntu_login_web_pfsense.png)
> Nous utilisons les identifiants par défaut {admin ; pfsense} pour la première connexion, ils seront changés par la suite.

---

## Tests de connectivité réseau

### LAN → Pare-feu
Un test de connectivité ICMP a été effectué depuis un poste client LAN vers la passerelle pfSense.

Résultat : succès.

![Test connectivité LAN -> pfSense](../docs/images/test_ping_lan_to_pfsense.png)

---

### LAN → Internet (IP)
Un ping vers une adresse publique (8.8.8.8) confirme le bon fonctionnement du routage et du NAT.

Résultat : succès.

![Test connectivité LAN -> Internet](../docs/images/test_ping_lan_to_internet.png)

---

### LAN → Internet (DNS)
La résolution DNS a été validée via un ping vers un nom de domaine public.

Résultat : succès.

![Test connectivité LAN -> Internet](../docs/images/test_ping_lan_dns.png)

# FAIRE TEST VERS 8.8.8.8

---

### Pare-feu → LAN
Un test ICMP depuis pfSense vers le poste client LAN confirme la connectivité bidirectionnelle contrôlée.

![Test connectivité pfSense -> LAN](../docs/images/test_ping_pfsense_to_lan.png)

---

## Conclusion

Ces tests valident :
- le bon fonctionnement du DHCP,
- le rôle de passerelle du pare-feu,
- l’accès Internet depuis le LAN,
- la cohérence de la segmentation réseau.

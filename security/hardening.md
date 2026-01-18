# Principes de durcissement

## Politique de mots de passe

Les systèmes déployés utilisent des mots de passe robustes comprenant :
- au minimum 8 caractères,
- des caractères alphanumériques,
- des caractères spéciaux.

Cette politique permet de réduire les risques liés aux attaques par force brute.

![Mot de passe robuste client Ubuntu](../docs/images/ubuntu_password.png)

## Sécurisation des accès administrateur

Le compte administrateur du pare-feu pfSense a été sécurisé par la modification du mot de passe par défaut.  
Un mot de passe robuste d’au moins 8 caractères, combinant lettres, chiffres et caractères spéciaux, a été mis en place.

![Mot de passe robuste compte administrateur pfSense](../docs/images/pfsense_admin_password.png)

Cette mesure permet de réduire significativement les risques liés aux attaques par force brute ou à l’utilisation d’identifiants connus.

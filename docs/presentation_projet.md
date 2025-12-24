# Projet SecureLab : Modernisation de l'Infrastructure TechNova Solutions

## 1. Présentation de l'Entreprise
**TechNova Solutions** est une PME de services informatiques (support, développement, conseil) comptant une vingtaine d'employés. Dans le cadre de sa croissance, l'entreprise doit moderniser son système d'information pour répondre à des besoins accrus de sécurité et de centralisation.

---

## 2. Objectifs du Projet
Le projet vise à transformer l'infrastructure existante selon quatre axes majeurs :
* **Centralisation :** Authentification unique des utilisateurs.
* **Sécurisation :** Contrôle strict des accès au réseau interne.
* **Hébergement :** Gestion des services internes et des services exposés.
* **Résilience :** Protection contre les attaques réseau conventionnelles.

---

## 3. Architecture Réseau Cible
L'infrastructure repose sur un environnement virtualisé avec une segmentation par pare-feu (Firewall) permettant de séparer les flux :

| Zone | Description & Usage |
| :--- | :--- |
| **LAN Employés** | Réseau interne pour les postes de travail des collaborateurs. |
| **Zone Serveurs** | Serveurs de fichiers, contrôleurs de domaine (AD/LDAP). |
| **DMZ** | Services exposés sur Internet (Portails clients, Web, etc.). |



---

## 4. Méthodologie SecureLab
Le projet adopte une double approche pour garantir une sécurité maximale :

### 🛡️ Volet Défensif (Blue Team)
* **Déploiement de l'infrastructure :** Configuration des VLANs et du routage.
* **Services d'Annuaire :** Centralisation des identités pour l'authentification.
* **Filtrage :** Mise en place de règles de pare-feu et de systèmes de détection d'intrusion.

### ⚔️ Volet Offensif (Red Team)
* **Audit de sécurité :** Tests d'intrusion sur les services exposés.
* **Contrôle de conformité :** Vérification de la robustesse des politiques de mots de passe et des droits d'accès.
* **Simulation d'attaques :** Évaluation de la résistance face aux menaces réseau basiques.

---

> **Note technique :** L'intégralité de ce laboratoire est réalisée en environnement virtualisé, permettant une isolation totale avant le déploiement en production.

# Projet SecureLab : Modernisation de l'Infrastructure TechNova Solutions

## Contexte général

SecureLab est un projet académique réalisé dans le cadre d’une formation en informatique en école d'ingénieur, avec pour objectif de consolider et démontrer des compétences en réseaux et cybersécurité en vue d’une poursuite d’études en Master Réseaux & Sécurité.

Le projet repose sur la conception et le déploiement d’une infrastructure réseau d’entreprise fictive, entièrement virtualisée, intégrant des mécanismes de sécurité réalistes ainsi qu’une démarche d’audit.

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

L’infrastructure repose sur un environnement virtualisé segmenté par un pare-feu central. Cette segmentation permet de contrôler les flux réseau, de limiter la surface d’attaque et de séparer les ressources internes des services exposés.

| Zone | Description & Usage |
| :--- | :--- |
| **LAN – Réseau interne** | Réseau interne de l’entreprise destiné aux postes de travail des employés et aux serveurs internes (Active Directory, DNS, serveur de fichiers). |
| **DMZ – Zone démilitarisée** | Zone intermédiaire hébergeant les services exposés vers Internet, notamment le serveur web accessible en HTTP/HTTPS. |
| **WAN – Réseau externe** | Réseau externe représentant Internet. Il permet l’accès aux services exposés de la DMZ et sert de point d’entrée pour les communications externes. |



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

## Périmètre et limites

Le projet se concentre volontairement sur des aspects fondamentaux des réseaux et de la cybersécurité. Certaines fonctionnalités avancées (haute disponibilité, cloud, SIEM, messagerie électronique) ne sont pas implémentées afin de conserver un périmètre réaliste et maîtrisé, en adéquation avec un projet académique de niveau licence/master.

> **Note technique :** L'intégralité de ce laboratoire est réalisée en environnement virtualisé, permettant une isolation totale avant le déploiement en production.


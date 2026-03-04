# ⚙️ Automatisation d'infrastructure avec Ansible & Proxmox (Cas d'usage : serveurs Minecraft)

## 📌 Objectif du projet

Ce projet a pour but de **démontrer et mettre en œuvre l'automatisation complète d'une infrastructure serveur** à l'aide de **Proxmox** et **Ansible**.

Le cas concret utilisé ici est **le déploiement automatique de serveurs Minecraft** mais **l'objectif principal n'est pas Minecraft en lui-même**.  
Minecraft sert uniquement de **support pédagogique** pour illustrer une problématique réelle d'administration système :

> 👉 *Comment déployer rapidement proprement et de manière reproductible plusieurs serveurs à partir d'une infrastructure virtualisée ?*

---

## 🎯 Problématique

Dans un contexte classique créer plusieurs serveurs implique :
- Création manuelle des machines ou conteneurs
- Configuration réseau répétitive
- Installation des dépendances
- Risque d'erreurs humaines
- Perte de temps importante

L'objectif de ce projet est donc de **supprimer les tâches manuelles répétitives** grâce à l'automatisation.

---

## 🧠 Principe de la solution

La solution repose sur deux briques principales :

### 🖥️ Proxmox VE
- Héberge l'infrastructure
- Fournit les conteneurs LXC
- Permet une gestion centralisée des ressources

### 🤖 Ansible
- Outil d'automatisation sans agent
- Permet :
  - La création automatique des conteneurs LXC
  - Leur démarrage
  - Leur préparation système
  - L'installation et la configuration des services



---

## 🟩 Pourquoi Minecraft ?

Minecraft est utilisé car :
- Il nécessite un environnement serveur réel (Java utilisateurs scripts)
- Il est facilement testable
- Il permet de visualiser immédiatement le résultat

⚠️ **Mais le même playbook peut être adapté pour :**
- Serveurs web (Apache / Nginx)
- Serveurs applicatifs
- Bases de données
- Outils de supervision (Zabbix Grafana…)
- Environnements de tests ou de formation

👉 **Minecraft n'est qu'un exemple d'application déployée automatiquement.**

---

## 🧩 Fonctionnalités automatisées

Ce projet permet de :
- Créer automatiquement plusieurs conteneurs LXC
- Les démarrer et vérifier leur état
- Installer les paquets nécessaires
- Installer Java 21 (Temurin)
- Créer un utilisateur dédié
- Déployer un serveur applicatif (Minecraft)
- Accepter automatiquement l'EULA
- Créer un script de démarrage du service
- Rejouer le playbook sans casser l'existant (idempotence)

---

## 🚀 Mise en œuvre et Utilisation

### 1. Prérequis
Pour exécuter ce projet vous devez disposer de :
- Un serveur **Proxmox VE** opérationnel (ici `10.2.0.253`)
- Un template de conteneur Debian 12 téléchargé sur le stockage local Proxmox
- Une machine de contrôle sous Linux (Debian/Ubuntu) avec **Ansible** installé
- Une paire de clés SSH configurée entre la machine de contrôle et le serveur Proxmox

### 2. Configuration de l'inventaire
Avant de lancer le déploiement adaptez le fichier `inventory.ini` à votre réseau.
Vous pouvez modifier la variable `ct_ids` pour choisir le nombre de serveurs à créer ou changer la RAM allouée via `ct_memory`.

### 3. Lancement du déploiement
Depuis la machine de contrôle naviguez dans le dossier du projet et exécutez la commande suivante :

```bash
ansible-playbook -i inventory.ini deploy_minecraft_lxc.yml
<img width="846" height="924" alt="Capture d’écran 2026-03-04 à 15 26 57" src="https://github.com/user-attachments/assets/c1827d59-7fae-4813-b9c2-43d00946c213" />


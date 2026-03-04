# 🛠️ Fichier de Commandes et Dépannage (Cheat Sheet)

## 🗄️ 1. Gestion des Conteneurs (Proxmox)
* **Lister les conteneurs** : `pct list`
* **Statut d'un conteneur** : `pct status 402`
* **Entrer dans un conteneur** : `pct enter 402`
* **Arrêter un conteneur** : `pct stop 402`
* **Démarrer un conteneur** : `pct start 402`
* **Supprimer un conteneur** : `pct destroy 402`
> 💡 **Note importante** : Si un conteneur est supprimé par erreur Ansible le recréera automatiquement lors de sa prochaine exécution.

## ⚙️ 2. Dépannage Ansible et YAML
* **Tester la connexion avec toutes les machines cibles** : `ansible all -m ping -i inventory.ini`
* **Vérifier la syntaxe du Playbook sans l'exécuter** : `ansible-playbook --syntax-check deploy_minecraft_lxc.yml`
* **Lancer le Playbook en mode débogage** : `ansible-playbook -i inventory.ini deploy_minecraft_lxc.yml -vvv`
* **Lancer une commande rapide sur le groupe Minecraft** : `ansible minecraft -a "uptime" -i inventory.ini`

## 🔐 3. Dépannage SSH et Sécurité
* **Générer une nouvelle paire de clés SSH** : `ssh-keygen -t rsa -b 4096`
* **Envoyer la clé publique vers l'hôte Proxmox** : `ssh-copy-id root@10.2.0.253`
* **Tester la connexion SSH sans mot de passe** : `ssh root@10.2.0.253`
* **Réparer une erreur de clé corrompue** : `ssh-keygen -R 10.2.0.253`
* **Redémarrer le service SSH en cas de blocage réseau** : `systemctl restart ssh`

## 🌐 4. Dépannage Système et Réseau
* **Afficher les adresses IP de la machine** : `ip a`
* **Vérifier la consommation de la mémoire RAM** : `free -m` ou `htop`
* **Vérifier l'espace disque restant** : `df -h`
* **Tester la résolution DNS** : `ping api.adoptium.net`

## 🎮 5. Gestion du Serveur Minecraft
* **Démarrer le serveur manuellement** : `sudo -u minecraft /opt/minecraft/server/start.sh`
* **Arrêter le serveur proprement via le processus système** : `pkill -f server.jar`
* **Voir si le serveur tourne en arrière-plan** : `ps aux | grep java`
* **Vérifier que le port Minecraft écoute bien les connexions entrantes** : `ss -lntp | grep 25565`

## 🖥️ 6. Console et Logs Minecraft
* **Se connecter à la console du jeu** : `screen -r minecraft`
* **Quitter la console sans arrêter le serveur** : `CTRL + A` puis `D`
* **Voir les logs en direct pour détecter les erreurs** : `tail -f /opt/minecraft/server/logs/latest.log`

### 👑 Commandes administrateur en jeu (Console)
* **Donner les droits admin** : `/op joueur`
* **Retirer les droits admin** : `/deop joueur`
* **Passer en mode créatif** : `/gamemode creative joueur`
* **Ajouter un joueur à la liste blanche** : `/whitelist add joueur`
* **Sauvegarder la carte immédiatement** : `/save-all`
* **Éteindre le serveur en douceur** : `/stop`

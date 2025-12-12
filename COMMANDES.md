# Commandes utiles – Minecraft / Proxmox

## Proxmox – conteneurs

Lister les conteneurs :
pct list

Statut d’un conteneur :
pct status 152

Entrer dans un conteneur :
pct enter 152

Arrêter un conteneur :
pct stop 152

Démarrer un conteneur :
pct start 152

Supprimer un conteneur :
pct destroy 152

➡️ Si supprimé : Ansible le recréera automatiquement

---

## Minecraft – serveur

Démarrer le serveur :
sudo -u minecraft /opt/minecraft/server/start.sh

Arrêter le serveur proprement :
pkill -f server.jar

Voir si le serveur tourne :
ps aux | grep java

Voir le port Minecraft :
ss -lntp | grep 25565

---

## Console Minecraft

Se connecter à la console :
screen -r minecraft

Quitter sans arrêter :
CTRL + A puis D

Commandes admin :
/op joueur
/deop joueur
/gamemode creative joueur
/whitelist add joueur
/save-all
/stop

---

## Logs

Voir les logs en direct :
tail -f /opt/minecraft/server/logs/latest.log

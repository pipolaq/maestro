# maestro

# INTRODUCTION ET REMERCIEMENTS
Ce programme permet de commander un poêle à granule, basé sur la technologie Maestro, en s'interfaçant directement avec les serveurs MCZ.

Il est très grandement basé sur le travail de Anthony et EtienneME sur le forum suivant: https://community.jeedom.com/t/mcz-maestro-et-jeedom/6159/183
Git original: https://github.com/Anthony-55/maestro
J'ai créé ce git pour aider certaines personnes qui le demandaient, je ne souhaite en aucun cas m'approprier le code qui n'est pas le mien, et sans lequel ce programme n'existerait pas.

Ce programme, bien que fonctionnel, est tout sauf optimisé (code approximatif, code restant non utilisé du travail sur lequel il est basé.) N'hésitez pas à l'améliorer et à contribuer ;)

## INSTALLATION
Ce programme nécéssite :
..* Python3
..* paho-mqtt
..* websocket (code à supprimer pour s'en passer)
..* Socket.io python client: https://python-socketio.readthedocs.io/en/latest/client.html

Pour l'installer (même procédure que celle présentée par Anthony sur son git)
```sh
git clone https://github.com/pipolaq/maestro.git
cd maestro
```

Ensuite, modifiez le fichier "maestro.py" en remplaçant "votreserial" et "votremac" par votre numéro de série et votre adresse mac. Gardez bien les double quote
Modifiez aussi le fichier config.

Ensuite :

```
sudo bash install_daemon
```



Pour démarrer le daemon : :
```sh
sudo systemctl start maestro.service
```

Pour activer le lancement automatique au démarrage du RPI :
```sh
sudo systemctl enable maestro.service 
```

Pour finir, il arrive que le programme plante (communication avec les serveurs MCZ ou bug du broker MQTT). J'ai donc un scenario qui check toutes les 10 minutes la date de la dernière remontée d'information, et si celle-ci est supérieure à 4 minutes, le scenario déclenche un 
```
systemctl restart maestro.service
```

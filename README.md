# Interface wifi **HomeAssitant** pour **Diverter**
Vous trouverez ici une configuration yaml esphome pour le module **wifi** de votre choix. Elle vous permettra, en plus des fonctions natives du **diverter**, d'ajouter son contrôle à distance directement depuis homeAssitant.

- [Introduction](#Introduction)
- [Fonctionnalités](#Fonctionnalités)
- [Prérequis](#Prérequis)
- [Instructions d'installation](#Instructions-installation)
- [Pour aller plus loin](#Pour-aller-plus-loin)

---

## Introduction
S'integre à **home assitant** par défaut

Le module wifi met à disposition un "appareil" accessible depuis homeAssitant. cf copie d'écran ci-dessous. Cette solution  composant **ESPHome**, permet l'ajout automatique et sans effort du composant dans home assistant automatique.

Pour plus d'informations sur le **diverter**, veuillez suivre ce lien : [http://wikinid.free.fr/wiki/Main/DiverterModule](http://wikinid.free.fr/wiki/Main/DiverterModule)

---

## Fonctionnalités
**Remontée** d'infos et prise de **controle**.

Vous pouvez contrôler votre **diverter** depuis l'interface **HA**. Elle permet de rendre visible des grandeurs invisibles, tel que l'affichage des informations de puissances produite, consommée ou injectée. En plus de sa fonction de "diverter", cette solution permet de prendre le **contrôle** de la marche forcée.

## Aperçu de l'interface web accessible en autonome

<p align="center">
<img src="https://raw.githubusercontent.com/lcailler/diverter2esphome/refs/heads/main/screenshot00.png" width="600">
</p>

---

## Prérequis
**Shelly** ou tout autre module wifi compatible **ESPHome**

La configuration disponible ici est adaptée à un [Shelly](https://devices.esphome.io/devices/Shelly-1).
Avec quelques adaptations **mineures**, vous pourrez adapter cette configuration à d'autres modules wifi. Vous trouverez la liste exhautive de plus de 200 modules wifi supportés en suivant ce lien : https://devices.esphome.io/standards/global.

<p align="center">
<img src="https://www.msxfaq.de/sonst/bastelbude/esp8266/esp8266-boards-shelly.gif" width="500">
</p>

---

## Instructions installation

### installation esphome

Plusieurs façons pour installer esphome sur votre carte esp8266 ou autre. Cela peut être via home assistant mais aussi directement depuis votre pc, mais encore depuis votre navigateur web.

Concrètement, sous home assistant, ajouter le composant "ESPHome Device Builder", puis ouvrir "l'interface utilisateur web". Voici un guide : https://www.hacf.fr/esphome-introduction/

Sur votre pc, vous trouverez un guide complet en suivant ce lien : https://peyanski.com/complete-esphome-installation-guide/

Depuis votre navigateur web, vous trouverez un guide complet en suivant ce lien : https://web.esphome.io


### flash du firmware

Avec ESPHome flasher le firmware basé sur les fichiers yaml suivants : shelly-diverter.yaml & secrets.yaml

### câblage croisé

Il vous faudra câbler ici les signaux tx, rx, gnd du module wifi vers le diverter. Il vous faudra relier les signaux gnd entre eux, le signal tx sur le rx et inversement. Le tx du module wifi au rx du diverter, le rx du module wifi sur le tx du diverter. On parle dans ce cas de câblage croisé.

Attention a ne pas utiliser le signal 3.3v pour alimenter un module wifi. La quantité de courant sur ce signal ne permet pas d'alimenter un module wifi trop gourmand en courant. Si jamais vous connectez l'alimention d'un module sur le signal 3.3v, vous vous exposez à mettre le diverter dans un état de reset continue, sans fin. Le diverter ne sera alors plus fonctionnel.

Autre détail technique, les signaux tx/rx du diverter sont compatibles signaux ttl 3.3v.

<img src="http://lionel.wiki.free.fr/download/projets/diverterV1_7_20190705/connect_diverter_03.png" width="400">

### première mise sous tension :

Pas d'obligation de renseigner vos paramètres Wi-Fi dans la configuration yaml.
Une fois flashée, si votre configuration Wi-Fi n'est pas faite, un hotspot Wi-Fi est activé. Connectez-vous sur ce hotspot et configurez votre Wi-Fi local, ssid et password.


## Pour aller plus loin

Voici quelques raisons pour lesquels vous pourriez faire évoluer le yaml partagé ici :
+ si vous voulez ajouter un automatisme, esphome rend trés accessible ce type de chose.
+ supporter d'autres cartes compatibles ESPHome.
+ prendre le contrôle du relais présent sur le module wifi sonfoff basic.
+ automatiser la mise à on/off du relais sur des seuils de production solaire, ou sur des plages horaires etc ....
+ ....

https://esphome.io

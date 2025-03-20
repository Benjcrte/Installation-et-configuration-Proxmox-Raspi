# Installation et configuration de Proxmox sur un Raspberry Pi

À l’aide de Raspberry Pi Imager, installez Pi OS Lite

![image](https://github.com/user-attachments/assets/9086fec3-2ba6-4dc4-ab7e-ab3d5380c319)


Modifier les réglages :
Mettre les identifiants de la connexion internet ,définir un nom d’utilisateur et son mot de passe, puis activer les SSH


![image](https://github.com/user-attachments/assets/f5c0b5af-b925-451d-a997-0dc2e77e3020)

  
![image](https://github.com/user-attachments/assets/992d5138-9b79-46d0-b332-fd9dd30ddfb3)
![image](https://github.com/user-attachments/assets/12ebb649-18a2-495c-b9d2-f21a7ccdd5e4)

Appuie sur OUI

![image](https://github.com/user-attachments/assets/7a30a3a1-0a18-46be-aee1-b0e3276d6558)


Définir un mot de passe pour root
Proxmox utilisera le compte root en arrière-plan, mais aussi pour se connecter à l’interface web, donc vous devez définir un mot de passe pour celui-ci (non effectué par défaut sur la plupart des distributions) :
 
Ajouter le dépôt Proxmox aux sources APT
Ensuite, nous devons ajouter le dépôt de portage de Proxmox à notre sources.list pour APT (et ainsi obtenir l’accès à plus de paquets via les commandes APT).
Voici les étapes :
•	Ajouter l’URL du serveur à une nouvelle configuration dans /etc/apt:

  *echo 'deb [arch=arm64] https://mirrors.apqa.cn/proxmox/debian/pve bookworm port' | sudo tee /etc/apt/sources.list.d/pveport.list*
 
•	Ajouter la clé du serveur à vos sources de confiance:

 *curl -L https://mirrors.apqa.cn/proxmox/debian/pveport.gpg | sudo tee /etc/apt/trusted.gpg.d/pveport.gpg >/dev/null*
 
•	Exécuter une mise à jour pour ajouter cette source aux prochaines installations:

*sudo apt update*
 
Installer les paquets Proxmox avec APT
Nous pouvons maintenant enfin installer les paquets pour Proxmox, en utilisant cette commande simple:

 *sudo apt install proxmox-ve postfix open-iscsi ifupdown2*


Lors de l’installation des paquets, vous serez invité à configurer un serveur de messagerie. Si vous ne savez pas comment faire, sélectionnez simplement “Local only” dans la liste et laissez les paramètres par défaut (appuyez sur Entrée).


![image](https://github.com/user-attachments/assets/930a7917-6bd9-4f59-8b99-f17b1188d8b4)

 

Après quelques minutes, tout est installé et Proxmox est prêt à être utilisé.
Interface web Proxmox
Si tout s’est bien passé jusqu’à présent, l’interface web Proxmox devrait être disponible à l’adresse https://IP:8006.
Ensuite, vous obtiendrez un formulaire de connexion. Les identifiants par défaut pour Proxmox sont :
•	Identifiant : root
•	Mot de passe : le même que pour votre système Linux (vous l’avez défini au début de ce tutoriel).


![image](https://github.com/user-attachments/assets/e99a4dfb-6602-44f5-8dfe-462c141c8f1b)



Enfin, vous pouvez accéder à l’interface habituelle de Proxmox. 


![image](https://github.com/user-attachments/assets/14eb588f-cec0-43df-ab06-690eb2175483)

 
Télécharger des images ISO sur Proxmox
Avant d’installer quoi que ce soit, vous aurez besoin d’images ISO pour le système que vous souhaitez essayer dans votre première machine virtuelle et aussi télécharger des templetes pour le conteneur

Créer un pont réseau
Si vous voulez avoir un accès réseau dans vos machines virtuelles, vous devez d’abord créer un pont réseau. Voici comment faire :
•	Cliquez sur votre nœud dans le menu de gauche (nom du serveur sous “Datacenter”).
•	Allez à System > Network.
•	Cliquez sur “Create” puis “Linux bridge”.
•	Remplissez le formulaire avec les valeurs que vous souhaitez utiliser, par exemple :


![image](https://github.com/user-attachments/assets/fbd13794-3c16-440b-931c-2502c0c020a0)


On va créer un conteneur :

![image](https://github.com/user-attachments/assets/dba2127b-45d5-445d-9ae0-fef187705abe)

Bien jouer le conteneur fonctionne AMUSE TOi BIEN


![Capture d'écran 2025-03-06 193643](https://github.com/user-attachments/assets/7888d9fa-02e4-4985-a51d-78d157be8dcd)




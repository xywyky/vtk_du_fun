Si vous utilisez Virtualbox vous pouvez  installer les extensions   qui permettent d'ajuster la taille de l'écran est de monter un répertoire partagé entre l'hôte(Mac OS ou Windows ou Linux) ———————
Marche à suivre:


installez  ubuntu sous virtualbox

ouvrez un xterm 


sudo apt install build-essential dkms

dans VB: menu Devices/Insert Guest Additions CD image

Executez l’installateur en tant que root: 
cd /media/
sudo  VBoxLinuxAdditions.run 


puis dans le xterm: 

sudo adduser $USERNAME vboxsf


shutdown de  Ubuntu 

dans VB creer un dossier partagé permanent


relancer la machine virtuelle ubuntu

Si vous avez activé l’acceleration matérielle il faut ne pas l’utiliser:
export LIBGL_ALWAYS_SOFTWARE=true


dans VB sur l'hôte créer un dossier partagé permanent pointant sur /mnt/etu

Vous y placerez vos exercices et les données utilsées par vtk


relancer la machine virtuelle ubuntu


en principe vous pouvez redimensionner la fenêtre et accéder à vos fichiers.

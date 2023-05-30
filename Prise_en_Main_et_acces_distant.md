Prise en main et acces distant 

 

Client 

pour verifier que lon ait a la racine 

Pwd  >> devrait etre /home/user 

Generer une cle 

Ssh-keygen –t ed22519 –N ‘ ‘ -C email@example.com 

Appuyez sur ENTER sans rien ecrire 

Essayer la connection:  

ssh username@ip_serveur –p port ("$ip a” sur le serveur pour voir l’ip) 

Verifier quon ait bien sur le serveur avec la commande  

$uname 

Créer le fichier de config 

$touch ~/.ssh/config 

Editer le fichier de config ($name) 

Host website 

 Hostname [ip] 

User [username] 

port [port] 

Tester la nouvelle connection 

Ssh website 

		 

Serveur: 

Securiser l’acces ssh du serveur 

Copier la config du serveur au cas ou 

Sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig 

Sudo cp /etc/ssh/sshd_config.origin /etc/ssh/sshd_config 

Editer la config 

Sudo nano /etc/ssh/sshd_config  

Mettre 

 PermitEmptyPassords no 

 Changer le Port a celui voulu 

 Redemarrez le demon ssh avec: 

Sudo systemctl restart sshd.service 

 Mettre 

PermitRootLogin no 

 Mettre  

ClientAliveInterval 300 

 Mettre 

ClientAliveCountMax 2 

 Donne l’acces a certain ou un group 

AllowUsers User1 User2 

Ou 

AllowGroup ssh_group 

  10. Si le dossier .ssh existe pas le créer avec: 

$touch .ssh 

$Cd .ssh 

$touch authorized_keys 

 11. Editez le fichier /etc/ssh/sshd_config et mettre: 

PasswordAuthentication no 

 12. Mettre 

PubkeyAuthentication yes 

13. Ensuite decomenter la ligne: 

AuthorizedKeysFile .ssh/authorized_keys 

14. Ensuite 

X11forwarding no 

Finalement: Désactiver le protocole ssh 1 

 

 

 

 

 

 

 

 

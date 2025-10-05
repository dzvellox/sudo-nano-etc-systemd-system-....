# sudo-nano-etc-systemd-system-....

Crée les fichiers :

sudo nano /etc/systemd/system/client_to_render.service
# coller le contenu, sauvegarder

sudo nano /etc/systemd/system/api_user.service
# coller le contenu, sauvegarder


Recharge systemd :

sudo systemctl daemon-reload


Active les services au démarrage :

sudo systemctl enable client_to_render.service
sudo systemctl enable api_user.service


Démarre-les maintenant :

sudo systemctl start client_to_render.service
sudo systemctl start api_user.service


Vérifie qu’ils tournent :

sudo systemctl status client_to_render.service
sudo systemctl status api_user.service

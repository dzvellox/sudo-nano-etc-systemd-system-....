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


pour installer venv

sudo apt install python3-venv -y
3️⃣ Créer un environnement virtuel
Va dans le dossier de ton projet, par exemple /home/pi/api-pi :

bash
Copier le code
cd /home/pi/api-pi
python3 -m venv relay-venv
Cela crée un dossier relay-venv contenant Python et pip isolés.

4️⃣ Activer l’environnement virtuel
bash
Copier le code
source relay-venv/bin/activate
Tu verras ton prompt changer, par exemple : (relay-venv) pi@raspberrypi:~$

Maintenant, tout ce que tu installes avec pip ira dans cet environnement, pas globalement.

5️⃣ Installer les dépendances
Par exemple, pour FastAPI et psycopg2 :

bash
Copier le code
pip install fastapi uvicorn psycopg2-binary pydantic
6️⃣ Désactiver l’environnement
Quand tu as fini :

bash
Copier le code
deactivate
💡 Astuce : ton fichier systemd doit pointer vers le Python de ce venv, par exemple :

ini
Copier le code
ExecStart=/home/pi/api-pi/relay-venv/bin/python3 /home/pi/api-pi/client_to_render.py

Vérifie qu’ils tournent :

sudo systemctl status client_to_render.service
sudo systemctl status api_user.service

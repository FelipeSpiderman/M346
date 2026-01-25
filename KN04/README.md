# KN04

## Korrektur

Fehler:
B) fehlt: Ein Screenshot der Details der Instanz. Scrollen Sie so weit runter, dass das Feld "Key pair assigned at launch", sichtbar ist.

B) Fehlermeldung bei ssh ist wegen ungeschütztem Key, nicht wegen server antwort.

C) wieso ist php-mysql am richtigen Ort?

C) für was ist die pipe in cloud-init |

C) wichtig: DB instanz löschen und neu erstellen ohne manuelle installation.

Fehlersuche: http://44.212.94.28/db.php (achtung öffentlich IP von Web server kann ändern). Mögliche Fehler:

falsche IP oder Credentials in db.php
Firewallprobleme (bei DB server)
DB server läuft nicht korrekt

Lösung:

![alt text](images/3.png)
![alt text](images/2.png)
![alt text](images/1.png)

Instanzerstellung mit init.yaml
![alt text](images/image4.png)

login mit key 2
![alt text](images/image.png)

login mit key 1
![alt text](images/image2.png)

Inhalt von /var/log/cloud-init-output.log
![alt text](images/image3.png)

grep:
![alt text](images/image8.png)

index.html von web:
![alt text](images/image5.png)

db.php von der db:
![alt text](images/image6.png)

info.php auf der web:
![alt text](images/image7.png)

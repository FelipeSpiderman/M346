# KN 03

## Korrektur

Fehler:
2 screenshots fehlen (URLs)

Lösung:

![alt text](images/1.png)
![alt text](images/image-2.png)
![alt text](images/3.png)
![alt text](images/image-3.png)

```bash
sudo apt update
sudo apt install apache2
sudo apt install php
sudo apt install libapache2-mod-php -y
sudo apt install mariadb-server -y
sudo apt install php-mysql -y
sudo mysql -sfu root -e "GRANT ALL ON _._ TO 'admin'@'%' IDENTIFIED BY 'Ubuntu' WITH GRANT OPTION;"
sudo systemctl restart mariadb.service
sudo systemctl restart apache2
cd ~
git clone https://gitlab.com/ch-tbz-it/Stud/m346/m346scripts.git
sudo nano ~/m346scripts/KN03/db.php
ls
cd m346scripts/
ls
cat README.md
sudo cp ~/m346scripts/KN03/\*.php /var/www/html/
cd KN03
ls
cat db.php
mysql -u admin -p
```

Dann mit dem command **SELECT Host, User FROM mysql.user;** habe ich folgendes ausgeben lassen:
![alt text](images/image2.png)
Meine SQL-SELECT-Abfrage liest die Daten aus der Tabelle `TABELLENNAME` aus und zeigt die gespeicherten Datensätze an. Damit überprüfe ich, dass die Datenbank funktioniert und korrekt verbunden ist.

website mit public ip:

![alt text](images/image3.png)

instanz details
![alt text](images/image.png)

inbound, outbound rules
![alt text](images/image4.png)

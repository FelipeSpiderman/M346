# KN02: IaaS - Virtuelle Server

## Korrektur

Fehler:
C) Abgabe fehlt: Screenshot mit dem ssh-Befehl und des Resultats unter Verwendung des zweiten Schlüssels

--> Ihre Datei hat zu viele Rechte, darum der Fehler

Lösung:
![alt text](images/12.png)

## A) Umgang mit AWS Kurs (20%)

Zu Beginn in AWS habe ich auf **Launch AWS Academy Learner Lab** geklickt. Dort kann ich mein Lab starten, sehe wie viel Zeit ich noch zur verfügung habe, kann meine Lab starten und stoppen und ich kann auch auf dem **AWS** mit dem grünen Punkt klicken, welches mich zu einer neuen Page führt

![Details der Instanzerstellung](./images/image7.png)

## B) Instanz erstellen (40%)

Bei der Instanzerstellung, habe ich meine Instanz KN02 gennant, es auf Ubuntu gestellt und setzte den Instanztyp als t3.micro

![Details der Instanzerstellung](./images/image1.png)

Danach muss ich noch ein Keypair erstellen und herunterladen, damit ich mich dann zur Instanz verbinden kann.

![Details der Instanzerstellung](./images/image2.png)

Dann wäre das das nötige und ich erstellte somit meine Instanz

![Details der Instanzerstellung](./images/image3.png)
![Details der Instanzerstellung](./images/image4.png)

## C) Zugriff mit SSH-Key (40%)

Damit ich Zugriff auf meine Erstellte Instanz erstellen kann, muss man den generierten Schlüssel, den man heruntergeladen
hat(in meinem Fall felipe1.pem), zur verfügung haben und am besten im gleichen Pfad wie den Schlüssel die commands auszuführen.

Danach habe ich folgende commands in der Reihenfolge ausgeführt:

1. chmod 400 "felipe1.pem"
2. ssh -i "felipe1.pem" ubuntu@ec2-54-204-227-155.compute-1.amazonaws.com

![Details der Instanzerstellung](./images/image6.png)

Diese commands habe ich in der AWS SSH-Connection gefunden und nachbefolgt.

![Details der Instanzerstellung](./images/image5.png)

### Zweiter schlüssel anwenden für ssh verbindung:

![Details der Instanzerstellung](./images/image8.png)

### Statistiken der Instanz

![alt text](./images/image9.png)

![alt text](./images/image10.png)

![alt text](./images/image11.png)

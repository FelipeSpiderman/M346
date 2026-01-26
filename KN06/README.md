# KN06

## Korrektur

Fehler:
.NET App läuft nicht, weil im cloud-init die Werte noch falsch ersetzt werden.

Sicherstellen, dass alle teile laufen (Load Balancer, Target Groups, Auto Scaler)

Lösung:

![alt text](correctedimages/1.png)
![alt text](correctedimages/2.png)
![alt text](correctedimages/3.png)
![alt text](correctedimages/4.png)
![alt text](correctedimages/5.png)
![alt text](correctedimages/6.png)
![alt text](correctedimages/7.png)
![alt text](correctedimages/8.png)
![alt text](correctedimages/9.png)
![alt text](correctedimages/10.png)
![alt text](correctedimages/11.png)
Frage: "Wie müssten Sie den DNS konfigurieren, damit app.tbz-m346.ch funktioniert?"
Antwort:

Erstelle einen CNAME-Eintrag bei deinem DNS-Provider:

app.tbz-m346.ch -> CNAME -> lb-webapi-123456.us-east-1.elb.amazonaws.com

![alt text](correctedimages/12.png)
![alt text](correctedimages/13.png)
![alt text](correctedimages/14.png)
auto scaling hat automatisch gerade 2 instanzen erstellt ohne dass ich etwas machen musste

mongodb.com details:
mongosh "mongodb+srv://connection:e2WM3aeuUwEuVths@cluster0.y0wxtsm.mongodb.net/?retryWrites=true&w=majority" --apiVersion 1
connection
e2WM3aeuUwEuVths

![alt text](images/1.png)
![alt text](images/2.png)
![alt text](images/3.png)
![alt text](images/4.png)
![alt text](images/5.png)
![alt text](images/6.png)

um volumen zu vergrösern, auf die instanz klicken / wählen, zu volumen tab wechseln, auf die volumen id klicken, rechts klick auf das volumen und dann volumen grösse anpassen.
![alt text](images/7.png)
![alt text](images/8.png)

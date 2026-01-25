# KN05

## Korrektur

Fehler:

private IPs definieren und dann auch setzen in den instanzen

security groups überarbeiten

outgoing ports (all open)
3306 muss eingeschränkt sein - gemäss auftrag!

static ips wurden nicht zugewiesen

Lösung:

Webserver: 172.31.32.10
Datenbank: 172.31.32.20

![alt text](images/1.png)
![alt text](images/2.png)
![alt text](images/3.png)
![alt text](images/4.png)
![alt text](images/5.png)
![alt text](images/7.png)
![alt text](images/6.png)
![alt text](images/8.png)
![alt text](images/9.png)
![alt text](images/10.png)
![alt text](images/11.png)
![alt text](images/12.png)

VPC: Ein eigenes, isoliertes Netzwerk in AWS, in dem deine Server laufen.
Subnet: Ein Teilbereich der VPC. Es teilt das Netzwerk in kleinere Zonen.
Private IP: Nur intern in AWS erreichbar. Nicht über das Internet sichtbar.
Public IP: Eine IP, über die man den Server aus dem Internet erreichen kann.
Static IP (Elastic IP): Eine öffentliche IP, die immer gleich bleibt – auch nach einem Neustart.

Alle Subnets:
![alt text](images/image4.png)

Subnet of KN04
![file path](images/image.png)
![file path](images/image2.png)

Irgendein Subnet zu KN05 nennen:
![alt text](images/image5.png)

Private IP:
Webserver: 10.0.2.10
Datenbank: 10.0.2.20

(Regeln: im Bereich des Subnet-KN05 und letzte Zahl durch 10 teilbar)

Seurity regeln:
![alt text](images/image3.png)

Elastic IP allocaten und umbenennen:
![alt text](images/image6.png)
![alt text](images/image7.png)

für die instanz diese yaml files benutzen:
![alt text](KN05-db.yaml)
![alt text](KN05-web.yaml)

instanz security groups:
![alt text](images/image8.png)
![alt text](images/image9.png)

inbound rules:
![alt text](images/image10.png)
![alt text](images/image11.png)

stopping the instances info:
![alt text](images/image12.png)
![alt text](images/image13.png)

isntance after restart:
![alt text](images/image14.png)
![alt text](images/image15.png)

checking if the server works:
![alt text](images/image16.png)
![alt text](images/image17.png)
![alt text](images/image18.png)

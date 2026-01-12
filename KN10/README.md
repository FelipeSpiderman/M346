# KN10: Kostenberechnung - Cloud Migration CRM System

**Student:** Felipe Pereira  
**Klasse:** AP24b  
**Datum:** 06.01.2026

---

## Inhaltsverzeichnis

1. [Ausgangslage](#ausgangslage)
2. [Teil A: IaaS - Rehosting](#teil-a-iaas---rehosting)
3. [Teil B: PaaS - Replattforming](#teil-b-paas---replattforming)
4. [Teil C: SaaS - Repurchasing](#teil-c-saas---repurchasing)
5. [Teil D: Interpretation & TCO-Analyse](#teil-d-interpretation--tco-analyse)

---

## Ausgangslage

Aktuelle On-Premise CRM-Infrastruktur:

**Web Server:** 1 CPU Core, 2 GB RAM, 20 GB Storage (Ubuntu)  
**Datenbank Server:** 2 CPU Cores, 4 GB RAM, 100 GB Storage (Ubuntu)  
**Backup-Strategie:** Täglich (7d) + Wöchentlich (4w) + Monatlich (3m) = **1400 GB total**  
**Benutzer:** 30 aktive Nutzer

Ziel: Evaluation verschiedener Cloud-Migrationsoptionen zur Kostenreduktion und erhöhten Flexibilität.

---

## Teil A: IaaS - Rehosting

### AWS Kostenrechnung

![AWS Calculator Overview](images/1.png)
*AWS Pricing Calculator - Komponenten-Übersicht*

#### Gewählte Konfiguration

**Web Server - EC2 t3.micro**
- 1 vCPU, 1 GB RAM, 20 GB gp3 SSD
- **Kosten:** ~$7-8/Monat

**Datenbank Server - EC2 t3.small**
- 2 vCPUs, 2 GB RAM, 100 GB gp3 SSD
- **Kosten:** ~$15-17/Monat

**Backup Storage - S3 Standard**
- 1400 GB Kapazität
- **Kosten:** ~$30-32/Monat

![AWS Cost Summary](images/5.png)
*AWS Gesamtkostenübersicht*

**AWS Gesamtkosten:** ca. **$57/Monat** (~$684/Jahr)

#### Komponentenbegründung

**t3.micro (Web):** Burstable Performance ideal für Web-Workloads mit 30 Usern. RAM-Reduktion vertretbar durch Cloud-Effizienz, bei Bedarf sofort auf t3.small upgrade möglich.

**t3.small (DB):** RAM auf 2 GB reduziert (statt 4 GB) zur Kostenoptimierung. Cloud-Datenbanken sind effizienter als On-Premise. Schnelles Upgrade auf t3.medium möglich falls benötigt.

**gp3 SSD:** Besseres Preis-Leistungs-Verhältnis als gp2, deutlich schneller als On-Premise HDDs.

**S3 Backups:** Automatische Multi-AZ Replikation, hohe Verfügbarkeit. Kostenoptimierung möglich durch Lifecycle Policies (ältere Backups → S3 Glacier = 50-70% Ersparnis).

---

### Azure Kostenrechnung

![Azure Calculator Overview](images/13.png)
*Azure Pricing Calculator - Komponenten-Übersicht*

#### Gewählte Konfiguration

**Web Server - VM B1s**
- 1 vCPU, 1 GB RAM, 20 GB Standard HDD
- **Kosten:** ~$9-10/Monat

**Datenbank Server - VM B2s**
- 2 vCPUs, 4 GB RAM, 100 GB Standard HDD
- **Kosten:** ~$38-40/Monat

**Backup Storage - Blob Storage (Hot Tier, LRS)**
- 1400 GB Kapazität
- **Kosten:** ~$28-30/Monat

![Azure Cost Summary](images/16.png)
*Azure Gesamtkostenübersicht*

**Azure Gesamtkosten:** ca. **$80/Monat** (~$960/Jahr)

#### Komponentenbegründung

**B1s/B2s VMs:** Burstable-Serie für variable Workloads. Bei DB volle 4 GB RAM beibehalten für Performance-Sicherheit.

**Standard HDD:** Kostenoptimierung - für 30 User ausreichend, Upgrade auf Premium SSD jederzeit möglich.

**Blob Storage Hot Tier:** Für regelmäßigen Backup-Zugriff optimiert. LRS bietet 3x Replikation innerhalb eines Rechenzentrums.

**AWS vs. Azure:** Azure ~40% teurer ($80 vs. $57), aber mehr Performance-Reserven durch 4 GB DB-RAM.

---

## Teil B: PaaS - Replattforming

### Heroku Kostenrechnung

![Heroku Pricing](images/18.png)
*Heroku Pricing-Übersicht*

#### Gewählte Konfiguration

**Web Dyno - Standard 1X**
- 512 MB RAM, Auto-Scaling, SSL inkl.
- **Kosten:** $25/Monat

**Heroku Postgres - Standard-0**
- 64 GB Storage, 4 GB RAM Cache, 120 Connections
- Automatische Backups, 4-Tage Rollback, High Availability
- **Kosten:** $50/Monat

**Heroku Gesamtkosten:** **$75/Monat** ($900/Jahr)

#### Komponentenbegründung

**Standard 1X Dyno:** 512 MB RAM klingen wenig, aber Heroku Dynos sind hochoptimiert und Container-basiert. Horizontal Scaling bei Bedarf (mehrere Dynos). Für 30 User ausreichend.

**Standard-0 Postgres:** Fully Managed Service - keine Wartung, Updates, Monitoring nötig. Continuous Protection ermöglicht Point-in-Time Recovery (4 Tage). Backup-Automatisierung komplett inkludiert.

**Hauptvorteile:**
- Kein DevOps-Team für Infrastruktur nötig
- Deployment via Git-Push in Minuten
- Automatisches Scaling
- Entwickler fokussieren auf Code statt Server-Verwaltung

---

## Teil C: SaaS - Repurchasing

### Zoho CRM

![Zoho CRM Pricing](images/20.png)
*Zoho CRM Editions-Vergleich*

#### Empfohlene Konfiguration

**Plan:** Professional Edition  
**Preis:** €20/User/Monat  
**User:** 30  
**Kosten:** **€600/Monat** (~€7,200/Jahr bzw. ~$7,800/Jahr)

**Begründung:** Professional bietet optimales Preis-Leistungs-Verhältnis mit Workflow-Automatisierung, Custom Modules und Inventory Management. Standard fehlen wichtige Features, Enterprise/Ultimate zu teuer für 30 User.

---

### Salesforce Sales Cloud

![Salesforce Pricing](images/22.png)
*Salesforce Sales Cloud Editions*

#### Empfohlene Konfiguration

**Plan:** Professional Edition  
**Preis:** $80/User/Monat  
**User:** 30  
**Kosten:** **$2,400/Monat** ($28,800/Jahr)

**Begründung:** Essentials limitiert auf 10 User (nicht nutzbar). Professional bietet komplettes CRM mit API-Zugriff und erweiterten Reports. Enterprise ($165/User) und Unlimited ($330/User) überdimensioniert für unsere Anforderungen.

**Hinweis:** Salesforce ist Marktführer, aber 4x teurer als Zoho Professional.

---

## Teil D: Interpretation & TCO-Analyse

### Kostenvergleich - Reine Cloud-Kosten

| Variante     | Monatlich | Jährlich | Ranking |
|--------------|-----------|----------|---------|
| AWS IaaS     | $57       | $684     | 1️⃣      |
| Heroku PaaS  | $75       | $900     | 2️⃣      |
| Azure IaaS   | $80       | $960     | 3️⃣      |
| Zoho SaaS    | ~$650     | ~$7,800  | 4️⃣      |
| Salesforce   | $2,400    | $28,800  | 5️⃣      |

**Warum diese Unterschiede?**

Die Preisunterschiede (Faktor 42 zwischen AWS und Salesforce!) erklären sich durch verschiedene Service-Levels:

- **IaaS:** Nur VMs + Storage, alles andere selbst managen
- **PaaS:** Plattform inklusive, Infrastruktur automatisiert
- **SaaS:** Fertige Software, pro User, keine Entwicklung nötig

---

### Total Cost of Ownership (TCO) - Realistische Gesamtkosten

Bei reinen Cloud-Kosten fehlen **versteckte Kosten**: Personal, Zeit, Zusatzservices.

#### Hidden Costs pro Variante

**IaaS (AWS/Azure):**
- DevOps/SysAdmin: 0.5-1 FTE → ~$2,000-3,000/Monat
- Monitoring, Load Balancer, SSL, Traffic → ~$100-150/Monat
- **Zusatzkosten:** ~$2,100-3,150/Monat

**PaaS (Heroku):**
- Developer: 0.2-0.3 FTE → ~$800-1,200/Monat
- Monitoring Add-ons → ~$35-70/Monat
- **Zusatzkosten:** ~$835-1,270/Monat

**SaaS (Zoho/Salesforce):**
- CRM Admin: 0.1 FTE → ~$400-600/Monat
- Add-ons, Consultants → ~$50-200/Monat
- **Zusatzkosten:** ~$450-800/Monat

#### TCO-Vergleich über 3 Jahre

| Variante     | Monatlich (real) | 3 Jahre Total  | TCO Ranking        |
|--------------|------------------|----------------|--------------------|
| Heroku PaaS  | $910-1,345       | $32,760-48,420 | 1️⃣ **Best Value**  |
| Zoho SaaS    | $1,050-1,450     | $37,800-52,200 | 2️⃣                 |
| AWS IaaS     | $2,157-3,207     | $77,652-115,452| 3️⃣                 |
| Azure IaaS   | $2,180-3,230     | $78,480-116,280| 4️⃣                 |
| Salesforce   | $2,800-3,200     | $100,800-115,200| 5️⃣                |

**Überraschende Erkenntnis:** AWS/Azure erscheinen günstig, werden aber mit Personal-Kosten zu den teuersten Optionen! Heroku bietet bestes Preis-Leistungs-Verhältnis.

---

### Aufwandsvergleich

#### IaaS - Migrations- & Betriebsaufwand

**Migration:** 3-4 Wochen
- Infrastruktur-Setup, Netzwerk, Security
- Installation Web/DB-Server
- Testing, Daten-Migration, Go-Live

**Laufender Aufwand:** 0.5-1 FTE (20-40h/Woche)
- Monitoring, Updates, Security Patches
- Backup-Tests, Performance-Optimierung
- Incident Response, Disaster Recovery Tests

**Benötigte Skills:** Cloud-Architektur, Linux Administration, Networking, Security

**Risiken:** Single Point of Failure, Fehler bei Updates, verzögerte Security-Patches

---

#### PaaS - Migrations- & Betriebsaufwand

**Migration:** 2-3 Wochen
- Code-Anpassungen (12-Factor-App)
- Heroku Setup, CI/CD, Add-ons
- Testing, Daten-Migration, Go-Live

**Laufender Aufwand:** 0.2-0.3 FTE (8-12h/Woche)
- Deployments, Monitoring, App-Wartung
- Keine Server-Administration!

**Benötigte Skills:** Applikations-Entwicklung, Git, Environment Variables

**Vorteile:** Minimaler Infrastruktur-Aufwand, schnelle Deployments, automatisches Scaling

---

#### SaaS - Migrations- & Betriebsaufwand

**Migration:** 4-6 Wochen
- Daten-Migration ($2,000-5,000 einmalig)
- Customization, User Training
- Go-Live

**Laufender Aufwand:** 0.1 FTE (4-8h/Woche)
- User-Verwaltung, Reports, Anpassungen
- Keine technischen Skills nötig

**Vorteile:** Minimaler IT-Aufwand, sofort einsatzbereit, kontinuierliche Updates

---

### Empfehlung

**Für unsere Firma (30 User, CRM-System):**

**#1 Heroku (PaaS)** - Bestes Preis-Leistungs-Verhältnis
- Niedrigste TCO über 3 Jahre
- Minimaler Personal-Aufwand
- Flexibilität durch eigene Software
- Schnelle Time-to-Market

**#2 Zoho CRM (SaaS)** - Falls keine Eigenentwicklung gewünscht
- Sofort einsatzbereit
- Sehr geringer IT-Aufwand
- Gut für kleine Teams

**Nicht empfohlen:** IaaS (AWS/Azure) - Nur bei großen, spezialisierten IT-Teams sinnvoll, da Personal-Kosten den Vorteil günstiger Cloud-Ressourcen zunichtemachen.
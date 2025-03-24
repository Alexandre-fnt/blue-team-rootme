# SQL Injection - Bypass Login

## 📌 Description du challenge
Ce challenge consiste à contourner un formulaire de connexion via une injection SQL.

## 🚀 Méthode d'attaque
- Injection `' OR 1=1 --` dans le champ identifiant.

![Injection en action](images/sql_bypass.png)

## 🔍 Analyse Blue Team
### 🔹 Détection :
- Logs montrant des requêtes suspectes (`' OR 1=1 --`).
- Alertes sur plusieurs tentatives de connexion échouées.

![Log d'attaque détecté](images/sql_alert_log.png)

### 🔹 Prévention :
- Utilisation de requêtes préparées.
- Activation d’un **WAF** pour bloquer les patterns d’injection.

### 🔹 Réaction :
- Blocage automatique après X tentatives.
- Investigation des logs pour voir s’il y a d’autres signes d’intrusion.

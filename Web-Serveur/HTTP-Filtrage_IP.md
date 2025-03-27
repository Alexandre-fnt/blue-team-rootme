## 📌 Description du challenge  
Ce challenge consiste à contourner un filtrage d’IP sur un intranet restreint. L’accès est refusé aux utilisateurs extérieurs au réseau local, sauf authentification.  

## 🚀 Méthode d'attaque  
Nous avons remarqué que l'application web se base uniquement sur l'adresse IP de l'utilisateur pour restreindre l'accès. En modifiant une requête HTTP et en y ajoutant une adresse IP interne dans un champ spécifique, nous avons pu contourner la restriction et obtenir la validation.  


### 📜 Pseudo-code de l'attaque 
``` 
1. Ouvrir une connexion HTTP vers l’URL cible.  
2. Ajouter un en-tête HTTP spécifique contenant une adresse IP interne (ex. `10.0.0.1`).  
3. Envoyer la requête au serveur et récupérer la réponse.  
4. Vérifier si la réponse contient un message de validation.  
```
(Le mot de passe a été flouté pour éviter la divulgation de la réponse.)
![Challenge HTTP User-Agent](../Images/http-user-agent-blurred.png)

## 🔍 Analyse Blue Team  

### 🔹 Détection :  
- Surveiller les requêtes HTTP avec un en-tête modifiant l’adresse IP.  
- Analyser les logs pour détecter des accès inhabituels depuis des adresses internes simulées.  

### 🔹 Prévention :  
- Ne pas se fier aux en-têtes HTTP injectés par l’utilisateur (`Client-IP`, `X-Forwarded-For`, etc.).  
- Utiliser l’adresse source réelle de la requête et non un en-tête potentiellement manipulé.  

### 🔹 Réaction :  
- Mettre en place un WAF pour bloquer les requêtes contenant des en-têtes suspects.  
- Appliquer des règles de filtrage réseau basées sur des listes blanches d’IP autorisées au lieu de s’appuyer sur des en-têtes HTTP.  
- Auditer régulièrement les mécanismes d’authentification et de filtrage d’IP.  
# HTML - Code source

## 📌 Description du challenge
Ce challenge consiste à analyser le code source HTML d’une page web pour y trouver un mot de passe caché. 

## 🚀 Méthode d'attaque
1. **Accéder à la page web** et ouvrir l'outil d'inspection (`Ctrl + U` ou `F12 > Inspecter l'élément`).  
2. **Chercher les champs sensibles** : analyser les balises `<input>`, `<script>`, `<meta>`, etc.  
3. **Trouver le mot de passe** dans un commentaire, un script JavaScript ou une variable en clair.  

## 🔍 Analyse Blue Team
### 🔹 Détection :
- Effectuer des scans automatiques du code source avec des outils comme Burp Suite ou ZAP.
- Surveiller les logs d'accès pour détecter des comportements suspects (ex : ouverture répétée du code source).

### 🔹 Prévention :
- Ne jamais stocker d'informations sensibles en clair dans le HTML.
- Supprimer les commentaires contenant des mots de passe avant la mise en production.

### 🔹 Réaction :
- Retirer immédiatement le mot de passe exposé et forcer une mise à jour.
- Notifier les administrateurs système et imposer un changement de mot de passe.
- Effectuer un audit de sécurité pour éviter que ce type d’erreur ne se reproduise.

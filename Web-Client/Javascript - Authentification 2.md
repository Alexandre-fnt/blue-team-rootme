## 📌 Description du challenge  

Ce challenge propose une page web affichant une fenêtre pop-up demandant un identifiant et un mot de passe.

## 🚀 Méthode d'attaque  
1. **Lancement du challenge :** la page web demande un identifiant et un mot de passe via des `prompt()`.
2. **Inspection du code source :**  
   - On remarque une balise `<script>` qui appelle une fonction `connexion()`.
   - En cliquant sur cette fonction dans les outils développeur, on voit le code JavaScript.
3. **Analyse du JavaScript :**  
   - Une liste `TheLists` contient une chaîne
   - Cette chaîne est ensuite découpée avec `.split(':')` pour extraire le login et le mot de passe
   - Une alerte (`alert()`) indique que si les identifiants sont bons, alors le challenge est validé.

## 🔍 Analyse Blue Team  
### 🔹 Détection :  
- Surveiller les accès répétés à cette page.
- Suivre l’exécution des scripts côté client ou l'interaction excessive avec les prompts.
- Détection possible via analyse des logs de navigateur avec une extension de sécurité (ex : CSP violations).

### 🔹 Prévention :  
- **Ne jamais stocker ni traiter des identifiants côté client**.
- Utiliser une authentification côté serveur, avec une base de données sécurisée.
- Mettre en œuvre des pratiques de codage sécurisé : suppression du code sensible dans les pages web, obfuscation, etc.

### 🔹 Réaction :  
- Corriger la logique d’authentification pour qu’elle soit traitée côté serveur.
- Mettre en place des revues de sécurité du code avant publication.
- Sensibiliser les développeurs aux failles de logique côté client.
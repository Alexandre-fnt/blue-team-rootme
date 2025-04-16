## 📌 Description du challenge

Ce challenge propose une page web contenant un champ de mot de passe via une fenêtre pop-up JavaScript, avec une vérification du mot de passe dans le code source.

## 🚀 Méthode d'attaque
1. **Lancement du challenge :** une fenêtre pop-up s'affiche pour entrer un mot de passe.  
2. **Comportement :** si on entre un mot de passe incorrect, la page semble vide.  
3. **Inspection de la page :**  
   - En inspectant le code source (clic droit > "Afficher le code source de la page" ou via les outils dev),  
   - On remarque que la fonction `login()` est définie directement dans le JavaScript.  
   - Le mot de passe attendu est codé en clair dans la condition `if (password == "motdepasse")`.  
4. **Solution :** récupérer ce mot de passe dans le code, relancer la page, et le rentrer dans la pop-up.

## 🔍 Analyse Blue Team
### 🔹 Détection :
- Inspecter les journaux d'accès HTTP pour repérer des accès récurrents à la page en question sans authentification correcte.
- Requêtes JavaScript ou appels aux fonctions côté client peuvent être suivis par un WAF ou un reverse proxy.

### 🔹 Prévention :
- **Ne jamais stocker de mot de passe en clair dans le code client (JavaScript).**
- Utiliser une authentification côté serveur (via une API ou des sessions).
- Obfusquer le code JavaScript (même si ce n'est pas une vraie protection, ça retarde les attaques).

### 🔹 Réaction :
- Dépublier la page ou modifier le challenge si elle est exposée publiquement.
- Informer les développeurs des risques de logique côté client non sécurisée.
- Mettre en place des processus de revue de code pour vérifier ce type de faille avant mise en production.

---

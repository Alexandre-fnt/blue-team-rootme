## 📌 Description du challenge


Ce challenge propose une page web qui affiche une pop-up demandant un mot de passe.
---

## 🚀 Méthode d'attaque

1. **Lancement du challenge** : une fenêtre `prompt()` apparaît pour entrer le mot de passe.
2. **Affichage du code source** : clic droit > "Afficher le code source de la page".
3. **Observation** : dans la balise `<script>`, on repère une variable `pass` contenant une chaîne commençant par des caractères comme `%63%37...`.
4. **Analyse** :
   - On comprend qu’il s’agit d’une chaîne de caractères encodée en hexadécimal (URL encoding).
   - Le mot de passe est ensuite comparé via `if(h == unescape(pass))`.
5. **Décodage** :
   - On utilise **CyberChef** ou un outil en ligne de décodage URL pour convertir la chaîne.
   - Le résultat donne le mot de passe en clair à utiliser dans la pop-up.

---

## 🔍 Analyse blue team

### 🔹 Détection :
- Surveiller les accès à des fichiers JavaScript contenant des données encodées ou obfusquées.
- Analyser les logs d’accès avec des outils de SIEM pour repérer les tentatives d’automatisation ou les utilisateurs inspectant trop souvent le code source.

### 🔹 Prévention :
- Ne jamais inclure de secrets (même encodés) dans du JavaScript côté client.
- Implémenter l’authentification via une API sécurisée côté serveur.
- Limiter l’accès aux ressources critiques à l’aide d’un système de session et de token.

### 🔹 Réaction :
- Revoir les développements contenant du JavaScript sensible.
- Avertir les développeurs et renforcer les revues de code sur la logique d’authentification.
- Obfusquer le code JavaScript uniquement pour retarder l’analyse, mais ne jamais y stocker d’information critique.

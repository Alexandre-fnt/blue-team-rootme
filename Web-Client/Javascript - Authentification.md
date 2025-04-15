## 📌 Description du challenge

Ce challenge présente une page d'authentification classique avec un formulaire HTML. L'objectif est de retrouver le login et le mot de passe permettant de s'authentifier, mais aucune information n'est directement visible.  
L'analyse du comportement du bouton "login" révèle une fonction JavaScript appelée `Login()` contenant les identifiants en clair.

---

## 🚀 Méthode d'attaque

1. **Inspection du code HTML** via l'outil développeur du navigateur (F12).
2. Observation que le bouton d'authentification appelle une fonction JavaScript nommée `Login()`.
3. Ouverture de l’onglet **Console** et exécution de la commande suivante :
   ```js
   alert(Login)

## 🔍 Analyse Blue Team
### 🔹 Détection :

- Sur un site réel, cette attaque ne laisserait que très peu de traces côté serveur.

- Une solution de monitoring front-end ou un WAF avancé pourrait détecter des comportements suspects liés à la console du navigateur.

- Des outils comme Content Security Policy (CSP) reporting peuvent détecter des tentatives d’exécution JavaScript non autorisées.

### 🔹 Prévention :

- Ne jamais hardcoder de secrets dans le code JavaScript côté client.

- Utiliser une vraie logique d’authentification côté serveur.

- Minimiser et ofusquer le code JavaScript pour compliquer l’analyse (ce n’est pas une solution complète mais peut ralentir l'attaquant).

- Ajouter une Content Security Policy (CSP) stricte pour limiter l’exécution de code malicieux.

- Désactiver l'accès à la console JS pour les utilisateurs non autorisés via des scripts de contrôle.

### 🔹 Réaction :

- Si une fuite de credentials est suspectée, changer immédiatement les identifiants.

- Implémenter une authentification sécurisée côté serveur.

- Auditer le code source pour s'assurer qu'aucune autre fonction ou variable ne contient des données sensibles côté client.

- Communiquer avec les développeurs pour former à la sécurité des scripts frontend.
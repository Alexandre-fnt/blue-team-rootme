## 📌 Description du challenge

Ce challenge repose sur la mauvaise configuration d’un serveur HTTP laissant visible l’arborescence de ses répertoires. L’objectif est de trouver un fichier contenant le flag en explorant l’index public des fichiers.

---

## 🚀 Méthode d'attaque

1. **Page principale vide :** aucun champ ou contenu utile visible.
2. **Inspection du code source :**
   - On découvre un `include("admin/pass.html")`, ce qui laisse penser à un chemin relatif vers une ressource.
3. **Accès direct à l'URL complète :**
   - En accédant à `/admin/pass.html`, on tombe sur une fausse piste (page troll).
4. **Remontée d’un niveau dans l’arborescence :**
   - En allant simplement sur `/admin/`, on accède à une **vue d’index de répertoire**.
   - Cette page affiche les fichiers avec leurs noms, tailles et dates.
5. **Exploration manuelle :**
   - On y retrouve le `pass.html` et un sous-dossier nommé `backup/`.
   - En accédant à `/admin/backup/`, on découvre un fichier `admin.txt` contenant le flag.

---

## 🔍 Analyse Blue Team
### 🔹 Détection :
- Surveillance des requêtes HTTP vers des chemins non documentés comme `/admin/` ou `/backup/`.
- Alertes sur les accès à des ressources sensibles ou peu communes.

### 🔹 Prévention :
- **Désactiver l’indexation de répertoire** dans la configuration du serveur web (Apache, Nginx...).
- Placer un fichier `index.html` vide dans les répertoires pour éviter l'affichage de leur contenu.
- Restreindre l'accès aux répertoires sensibles par authentification ou filtrage IP.

### 🔹 Réaction :
- Auditer les fichiers exposés publiquement pour détecter d’éventuelles fuites.
- Supprimer les fichiers inutiles en production (ex : anciens fichiers de dev, sauvegardes).
- Mettre à jour la configuration du serveur pour bloquer l’accès aux chemins sensibles.

---

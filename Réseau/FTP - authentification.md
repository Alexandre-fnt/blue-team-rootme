## 📌 Description du challenge
**Nom :** FTP - Authentification  
**Catégorie :** Réseau  
**Difficulté estimée :** Facile

Ce challenge repose sur l’analyse d’un échange FTP non chiffré capturé dans un fichier réseau. L’objectif est de retrouver le mot de passe utilisé par l’utilisateur.

---

## 🚀 Méthode d'attaque

1. **Ouverture de la capture Wireshark** : le fichier contient une communication entre un client et un serveur FTP.
2. **Protocole TCP** : l’échange se fait en clair (pas de chiffrement comme dans FTPS).
3. **Suivi du flux TCP** :
   - Clic droit sur un paquet > *Suivre* > *Flux TCP*.
   - Le flux montre la commande `USER` suivie de la commande `PASS`.
4. **Extraction du mot de passe**

--- 

## 🔍 Analyse Blue Team
### 🔹 Détection :
- Analyse des logs réseau ou des captures pour détecter l'utilisation de FTP en clair.
- Détection d’envois non chiffrés de credentials via IDS (Snort, Suricata).

### 🔹 Prévention :
- **Éviter FTP** : préférer FTPS ou SFTP pour chiffrer les identifiants et les transferts.
- Bloquer les ports FTP (21) si non utilisés.
- Mise en place de politiques de sécurité pour interdire les protocoles non sécurisés.

### 🔹 Réaction :
- Informer les utilisateurs et administrateurs sur les risques liés à FTP.
- Supprimer ou restreindre les accès FTP en faveur de protocoles sécurisés.
- Rechercher d’éventuelles fuites d’identifiants et forcer leur changement.

---


## Description du challenge

Ce challenge repose sur l’analyse d’un échange Telnet non chiffré capturé dans un fichier réseau. L’objectif est de retrouver le mot de passe utilisé par l’utilisateur.

---

## Méthode d'attaque

1. **Ouverture de la capture Wireshark** : le fichier contient une communication entre un client et un serveur Telnet.
2. **Protocole TCP** : comme Telnet ne chiffre rien, les identifiants passent en clair.
3. **Suivi du flux TCP** :
   - Clic droit sur un paquet > *Suivre* > *Flux TCP*.
   - Le flux montre directement ce que tape l’utilisateur.
4. **Extraction du mot de passe** :
   - On repère l’identifiant et le mot de passe saisis manuellement, affichés en clair dans le flux.
   - Il suffit de les copier pour valider le challenge.

---

## Analyse Blue Team
### 🔹 Détection :
- Analyse des flux réseau montrant une connexion en Telnet.
- Détection de credentials transmis en clair via IDS (Snort, Suricata).

### 🔹 Prévention :
- **Éviter Telnet** : utiliser SSH à la place, qui chiffre l’ensemble des communications.
- Désactiver le service Telnet sur les machines.
- Bloquer le port 23 (par défaut pour Telnet) au niveau du pare-feu.

### 🔹 Réaction :
- Identifier les hôtes utilisant Telnet et les migrer vers SSH.
- Changer immédiatement les identifiants transmis si compromission possible.
- Mettre en place une politique de sécurité interdisant l’usage de Telnet en environnement de production.

---

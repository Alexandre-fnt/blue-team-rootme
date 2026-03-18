## Description du challenge

Ce challenge consiste à analyser une capture réseau d’un échange HTTP chiffré via SSL/TLS. L’objectif est de récupérer les informations échangées en clair en déchiffrant le trafic à l’aide d’une clé privée fournie.

---

## Méthode d'attaque

1. **Ouverture de la capture Wireshark** : on observe du trafic SSL/TLS (port 443).
2. **Trafic chiffré** : les échanges HTTP sont invisibles par défaut.
3. **Indice dans l’énoncé** : il mène à un site externe où la clé privée utilisée lors de l’échange est fournie.
4. **Import de la clé dans Wireshark** :
   - Aller dans *Édition > Préférences > Protocoles > TLS*.
   - Ajouter une clé privée RSA correspondant au port utilisé (ex: `443,http,/chemin/vers/clé.pem`).
5. **Lecture du flux déchiffré** :
   - Les échanges TLS sont maintenant lisibles.
   - On peut suivre le flux et retrouver les données HTTP échangées, dont les identifiants ou autres éléments utiles pour valider le challenge.

---

## Analyse Blue Team
### 🔹 Détection :
- Analyse réseau montrant un trafic TLS pouvant indiquer une compromission si la clé privée fuite.
- Surveillance des téléchargements ou accès à des fichiers contenant des clés privées.

### 🔹 Prévention :
- **Ne jamais exposer une clé privée** sur un site ou un dépôt public.
- Utiliser des certificats éphémères ou avec PFS (Perfect Forward Secrecy) pour éviter le déchiffrement même en cas de fuite de la clé.
- Restreindre l’accès aux certificats/clefs sur les serveurs via des permissions strictes.

### 🔹 Réaction :
- Révoquer et régénérer les certificats compromis immédiatement.
- Rechercher les fuites de données liées à la compromission du canal SSL.
- Mettre en place une surveillance continue des fichiers sensibles et des accès aux certificats.

---

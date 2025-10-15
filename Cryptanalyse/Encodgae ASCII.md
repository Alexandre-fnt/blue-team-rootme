## 📌 Description du challenge

**Nom :** Encodage ASCII
**Catégorie :** Cryptanalyse
**Difficulté estimée :** Facile

Ce challenge consiste à décoder un message chiffré en ASCII hexadécimal afin d'obtenir le flag.

---

## 🚀 Méthode d'attaque

1. **Analyse de l’énoncé :** il indique que le message est encodé en ASCII hexadécimal.
2. **Utilisation d’un outil en ligne :**

   * Rendez-vous sur le site [https://www.dcode.fr/code-ascii](https://www.dcode.fr/code-ascii).
   * Collez la chaîne de caractères fournie.
   * Sélectionnez le décodage *ASCII Hexadecimal → Texte*.

---

## 🔍 Analyse Blue Team

### 🔹 Détection :

* Surveiller les transferts de fichiers ou de messages contenant des chaînes hexadécimales suspectes.
* Détecter les tentatives d’obfuscation de données via des formats encodés (hex, base64, ASCII...).

### 🔹 Prévention :

* Mettre en place des contrôles de contenu pour identifier les encodages anormaux dans les flux réseau ou les e-mails.
* Utiliser des outils DLP (Data Loss Prevention) capables de reconnaître et bloquer des encodages de données sensibles.

### 🔹 Réaction :

* Déterminer l’origine du message encodé et vérifier s’il contient des données sensibles.
* Former les analystes SOC à reconnaître les schémas d’encodage classiques (Base64, ASCII, Hex...).

---

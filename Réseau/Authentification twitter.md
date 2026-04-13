##  Challenge : Authentification Twitter (HTTP Basic)

### Description du challenge  
Ce challenge repose sur l’analyse d’une capture réseau contenant une session d’authentification à un service simulant Twitter.  
L’objectif est de retrouver le mot de passe de l’utilisateur à partir des informations présentes dans la requête HTTP.

---

## ⚔️ Méthode d’attaque  

### Analyse de la capture  
La capture réseau est ouverte avec Wireshark.  
On constate qu’une seule trame est présente, ce qui simplifie l’analyse.

### Inspection du protocole HTTP  
En examinant la trame, on accède à la section **Hypertext Transfer Protocol (HTTP)**.  
Dans les en-têtes HTTP, on observe un champ :

```http
Authorization: Basic <valeur_base64>
```

### Exploitation de l’authentification Basic  
Le mécanisme **HTTP Basic Auth** encode simplement les identifiants en Base64 (et non en chiffrement).

Le format est le suivant :
```
username:password → encodé en Base64
```

### Extraction du mot de passe  
Il suffit donc de :

1. Copier la valeur Base64 du champ `Authorization`
2. La décoder (via un outil ou script)
3. Obtenir directement :


➡️ Le mot de passe est ainsi récupéré en clair.

---

##  Analyse Blue Team  

### 🔹 Détection  
- Analyse des logs HTTP pour identifier la présence d’en-têtes `Authorization: Basic`  
- Détection de trafic HTTP non chiffré contenant des credentials  
- Utilisation d’IDS/IPS (ex : Snort, Suricata) pour repérer les authentifications en clair  

---

### 🔹 Prévention  
- ❌ Ne jamais utiliser HTTP Basic sans chiffrement  
- ✅ Utiliser HTTPS pour chiffrer les échanges (TLS)  
- Implémenter des méthodes d’authentification sécurisées (tokens, OAuth, sessions sécurisées)  
- Désactiver les mécanismes d’authentification obsolètes  

---

### 🔹 Réaction  
- Identifier les comptes compromis et forcer la réinitialisation des mots de passe  
- Informer les utilisateurs du risque de fuite d’identifiants  
- Mettre en place une supervision accrue du trafic réseau  
- Corriger rapidement la configuration pour imposer HTTPS  
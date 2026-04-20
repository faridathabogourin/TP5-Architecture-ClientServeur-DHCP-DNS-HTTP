# 🌐 TP5 — Architecture Client/Serveur : DHCP, DNS & HTTP/HTTPS

> **Cours :** Base de Réseaux — ECE Paris | 2025/2026  
> **Auteur :** Faridath ABOGOURIN  
> **Outil principal :** Cisco Packet Tracer  

---

## 📋 Contexte

Dans le cadre du cours de Base de Réseaux à l'ECE Paris, ce TP avait pour objectif de simuler l'infrastructure réseau d'une petite entreprise en configurant une architecture **LAN / DMZ** avec plusieurs services réseaux essentiels.

Le rôle adopté était celui d'**administrateur réseau**, chargé de déployer et valider l'ensemble des services.

---

## 🎯 Objectifs du TP

- Comprendre le principe d'une architecture **client/serveur**
- Installer et configurer les services réseaux : **DHCP**, **DNS** et **HTTP/HTTPS**
- Distinguer les protocoles de la **couche application**
- Mettre en place une **zone démilitarisée (DMZ)** pour isoler les serveurs exposés

---

## 🏗️ Architecture réseau

```
        [ LAN ]                      [ DMZ ]
   PC1 ─┐                      ┌─ Web Server (www.ece.fr)
   PC2 ─┤── Switch1 ── Router ─┤
         │                     └─ Internal DNS Server
         └── DHCP Server
```

**Équipements utilisés :**
- 2 PC clients (PC1, PC2)
- 1 Routeur 2911
- 2 Switches 2960-24TT
- 1 Serveur Web (HTTP/HTTPS)
- 1 Serveur DNS interne
- 1 Serveur DHCP

---

## ⚙️ Étapes réalisées

### 1. Vérification de la connectivité
- Test des liaisons entre tous les périphériques via `ping`
- Validation PC1 → Web Server, PC1 → DNS Server, PC1 → Routeur LAN/DMZ

### 2. Configuration du serveur Web (HTTP/HTTPS)
- Activation des services HTTP et HTTPS
- Modification de la page HTML par défaut (`index.html`)
- Accès depuis le LAN via `http://192.168.2.2`

### 3. Configuration du serveur DNS
- Création d'un enregistrement de type **A Record** : `www.ece.fr → 192.168.2.2`
- Activation du service DNS sur `Internal_DNS_Server`
- Accès à la page web via URL `http://www.ece.fr` depuis le LAN

### 4. Déploiement du service DHCP
- Ajout d'un serveur DHCP configuré en **statique**
- Paramétrage du pool d'adresses :
  - Plage : `192.168.1.10 → 192.168.1.59` (50 hôtes max)
  - Passerelle par défaut : `192.168.1.1`
  - DNS Server : `192.168.2.2`
  - Masque : `255.255.255.0`
- Passage des PCs en configuration **dynamique (DHCP)**
- Validation : `DHCP request successful` sur PC1 et PC2

---

## ✅ Résultats & Validation

| Test | Résultat |
|------|----------|
| PC1 → Web Server (ping) | ✅ 0% perte |
| PC1 → DNS Server (ping) | ✅ 0% perte |
| PC1 → Routeur LAN | ✅ 0% perte |
| Accès `http://192.168.2.2` | ✅ Page HTML affichée |
| Accès `http://www.ece.fr` | ✅ Résolution DNS fonctionnelle |
| Attribution DHCP automatique | ✅ IP attribuée dynamiquement |
| Test DNS (ping www.ece.fr) | ✅ Résolution vers 192.168.2.2 |

---

## 🛠️ Outils & Technologies

| Outil | Usage |
|-------|-------|
| Cisco Packet Tracer | Simulation réseau complète |
| HTTP / HTTPS | Services web |
| DNS | Résolution de noms de domaine |
| DHCP | Attribution dynamique d'adresses IP |
| HTML | Personnalisation de la page web serveur |

---

## 📁 Contenu du dépôt

```
TP5-Architecture-ClientServeur-DHCP-DNS-HTTP/
│
├── README.md             ← Ce fichier
└── TP5_rapport.pdf       ← Rapport complet avec captures d'écran
```

---

## 💡 Compétences démontrées

- Conception et lecture d'une **topologie réseau**
- Configuration d'une architecture **LAN / DMZ**
- Déploiement de services réseaux (**DHCP, DNS, HTTP/HTTPS**)
- Résolution de problèmes réseau (diagnostic, ping, validation)
- Administration de **serveurs** sous Cisco Packet Tracer

---

> *TP réalisé dans le cadre du cours Base de Réseaux — ECE Paris, année 2025/2026.*

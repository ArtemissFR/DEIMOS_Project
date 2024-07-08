<p align="center">
  <img src="Documentation/DEIMOS.png" alt="Deimos Icon" width="700"/>
</p>

# Indication
- ## ✔️ = Fait
- ## ❌ = A faire
- ## ⚠️ = A confirmer
- ## 🔜 = Solution trouver
- ## 💭 = Voir plus tard | Pas important

---

# 4 - Configuration matérielle
## 4.1 - Support matériel
  - [R1] Choisir et configurer son matériel : status = ❌
## 4.2 - BIOS/UEFI
  - [R2] Configurer le BIOS/UEFI : status = ❌
## 4.3 - Démarrage sécurisé UEFI
### 4.3.1 - Clés préchargées
  - [R3] Activer le démarrage sécurisé UEFI : status = ❌
### 4.3.2 - Nouvelles clés
  - [R4] Remplacer les clés préchargées : status = ❌

---

# 5 - Configuration du noyau Linux

---

# 6 - Configuration système

---

# 7 - Configuration des services
  - [R62] Désactiver les services non nécessaires : status = ✔️
  - [R63] Désactiver les fonctionnalités des services non essentielles : status = ✔️
  - [R64] Configurer les privilèges des services : status = 💭
## 7.1 - Cloisonnement
  - [R65] Cloisonner les services : status = ❌ | 🔜 (Docker)
  - [R66] Durcir les composants de cloisonnement : status = ❌ | 🔜 (Docker)
## 7.2 - Services système
### 7.2.1 - Pluggable Authentication Module ou module d'authentification enfichable
  - [R67] Sécuriser les authentifications distante par PAM : status = 💭
  - [R68] Protéger les mots de passe stockés  : status = ⚠️
### 7.2.2 - Name Service Switch ou service de gestion de noms
  - [R69] Sécuriser les accès aux bases utilisateur distantes : status = ❌
  - [R70] Séparer les comptes système et d'administrateur de l'annuaire : status = ❌
### 7.2.3 - Journalisation
  - [R71] Mettre en place un système de journalisation : status = ❌ | 🔜 (Surveillance : Prometheus/ELK Stack/Kibana)
  - [R72] Mettre en place des journaux d'activité de service dédiés : status = ❌ | 🔜 (Surveillance : Prometheus/ELK Stack/Kibana)
  - [R73] Journaliser l'activité système avec auditd : status = ❌
### 7.2.4 - Messagerie
  - [R74] Durcir le service de messagerie locale : status = 💭
  - [R75] Configurer un alias de messagerie des comptes de service : status = 💭
### 7.2.5 - Surveillance du système de fichiers
  - [R76] Sceller et vérifier l'intégrité des fichiers : status = 💭
  - [R77] Protéger la base de données des scellés : status = 💭
## 7.3 Services réseau
  - [R78] Cloisonner les services réseau : status = ❌ | 🔜 (Docker)
  - [R79] Durcir et surveiller les services exposés : status = ❌ | 🔜 (Configuration + MAJ auto | Surveillance : Prometheus/ELK Stack/Kibana)
  - [R80] Réduire la surface d'attaque des services réseau : status = ❌ | 🔜 (Pare-feu : ufw | Protection :  fail2ban)

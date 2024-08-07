<p align="center">
  <img src="Documentation/DEIMOS.png" alt="Deimos Icon" width="700"/>
</p>

# Indication
- ## ✔️ = Fait | A tester
- ## ❌ = A faire
- ## ⚠️ = A confirmer
- ## 🔜 = Solution trouver
- ## 💭 = Voir plus tard | Pas important

---

# 4 - Configuration matérielle
## 4.1 - Support matériel
  - [R1] Choisir et configurer son matériel : status = ✔️
## 4.2 - BIOS/UEFI
  - [R2] Configurer le BIOS/UEFI : status = ✔️
## 4.3 - Démarrage sécurisé UEFI
### 4.3.1 - Clés préchargées
  - [R3] Activer le démarrage sécurisé UEFI : status = ✔️
### 4.3.2 - Nouvelles clés
  - [R4] Remplacer les clés préchargées : status = ⚠️

---

# 5 - Configuration du noyau Linux
## 5.1 - Chargeur de démarrage
  - [R5] Configurer un mot de passe pour le chargeur de démarrage : status = ❌
## 5.2 - Configuration dynamique
  - [R6] Protéger les paramètres de ligne de commande du noyau et l'initramfs : status = ✔️
### 5.2.1 - Configuration de la mémoire
  - [R7] Activer l'IOMMU : status = ✔️
  - [R8] Paramétrer les options de configuration de la mémoire : status = ⚠️
### 5.2.2 - Configuration du noyau
  - [R9] Paramétrer les options de configuration du noyau : status = ⚠️
  - [R10] Désactiver le chargement des modules noyau : status = ✔️
### 5.2.3 - Configuration des processus
  - [R11] Activer et configurer le LSM Yama : status = ✔️
### 5.2.4 - Configuration du réseau
  - [R12] Paramétrer les options de configuration du réseau IPv4 : status = ✔️
  - [R13] Désactiver le plan IPv6 : status = ✔️
### 5.2.5 - Configuration des systèmes de fichiers
  - [R14] Paramétrer les options de configuration des systèmes de fichiers : status = ❌
## 5.3 - Configuration statique
### 5.3.1 - Configuration indépendante de la cible matérielle
  - [R15] Paramétrer les options de compilation pour la gestion de la mémoire : status = 💭
  - [R16] Paramétrer les options de compilation pour les structures de données du noyau : status = 💭
  - [R17] Paramétrer les options de compilation pour l'allocateur mémoire : status = 💭
  - [R18] Paramétrer les options de compilation pour la gestion des modules noyau : status = 💭
  - [R19] Paramétrer les options de compilation pour les évènements anormaux : status = 💭
  - [R20] Paramétrer les options de compilation pour les primitives de sécurité du noyau : status = 💭
  - [R21] Paramétrer les options de compilation pour les plugins du compilateur : status = 💭
  - [R22] Paramétrer les options de compilation pour la pile réseau : status = 💭
  - [R23] Paramétrer les options de compilation pour divers comportements du noyau : status = 💭
### 5.3.2 - Configuration spécifique aux architectures matérielles
  - [R24] Paramétrer les options de compilation spécifiques aux architectures 32 bits : status = 💭
  - [R25] Paramétrer les options de compilation spécifiques aux architectures x86_64 bits : status = 💭
  - [R26] Paramétrer les options de compilation spécifiques aux architectures ARM : status = 💭
  - [R27] Paramétrer les options de compilation spécifiques aux architectures ARM 64 bits : status = 💭

---

# 6 - Configuration système
## 6.1 - Partitionnement
  - [R28] Partitionnement type : status = ❌
  - [R29] Restreindre les accès au dossier /boot : status = ❌
## 6.2 - Comptes d'accès
### 6.2.1 - Comptes utilisateur
  - [R30] Désactiver les comptes utilisateur inutilisés : status = ⚠️
  - [R31] Utiliser des mots de passe robustes : status = ⚠️
  - [R32] Éxpirer les sessions utilisateur locales : status = ❌
### 6.2.2 - Comptes administrateur
  - [R33] Assurer l'imputabilité des actions d'administration : status = ❌
### 6.2.3 - Comptes de service
  - [R34] Désactiver les comptes de service : status = ❌
  - [R35] Utiliser des comptes de service uniques et exclusifs : status = ❌
## 6.3 - Contrôle d'accès
### 6.3.1 - Modèle traditionnel Unix
  - [R36] Modifier la valeur par défaut de UMASK : status = ❌
  - [R37] Utiliser des fonctionnalités de contrôle d'accès obligatoire MAC : status = ❌
  - [R38] Créer un groupe dédié à l'usage de sudo : status = ❌
  - [R39] Modifier les directives de configuration sudo : status = ❌
  - [R40] Utiliser des utilisateurs cibles non-privilégiés pour les commandes sudo : status = ❌
  - [R41] Limiter l'utilisation de commandes nécessitant la directive EXEC : status = ❌
  - [R42] Bannir les négations dans les spécifications sudo : status = ❌
  - [R43] Préciser les arguments dans les spécifications sudo : status = ❌
  - [R44] Éditer les fichiers de manière sécurisée avec sudo : status = ❌
### 6.3.2 - AppArmor
  - [R45] Activer les profils de sécurité AppArmor : status = ❌
### 6.3.3 - SELinux
  - [R46] Activer SELinux avec la politique targeted : status = ❌
  - [R47] Confiner les utilisateurs interactifs non privilégiés : status = ❌
  - [R48] Paramétrer les variables SELinux : status = ❌
  - [R49] Désinstaller les outils de débogage de politique SELinux : status = ❌
## 6.4 - Fichiers et répertoires
### 6.4.1 - Fichiers et répertoires sensibles
  - [R50] Restreindre les droits d'accès aux fichiers et aux répertoires sensibles : status = ❌
  - [R51] Changer les secrets et droits d'accès dès l'installation : status = ❌
### 6.4.2 - Fichiers IPC nommés, sockets ou pipes
  - [R52] Restreindre les accès aux sockets et aux pipes nommées : status = ❌
### 6.4.3 - Droits d'accès
  - [R53] Éviter les fichiers ou répertoires sans utilisateur ou sans groupe connu : status = ❌
  - [R54] Activer le sticky bit sur les répertoires inscriptibles : status = ❌
  - [R55] Séparer les répertoires temporaires des utilisateurs : status = ❌
  - [R56] Éviter l'usage d'exécutables avec les droits spéciaux setuid et setgid : status = ❌
  - [R57] Éviter l'usage d'exécutables avec les droits spéciaux setuid root et setgid root : status = ❌
## 6.5 - Gestion des paquets
  - [R58] N'installer que les paquets strictement nécessaires : status = ✔️
  - [R59] Utiliser des dépôts de paquets de confiance : status = ✔️
  - [R60] Utiliser des dépôts de paquets durcis : status = ✔️
## 6.6 - Veille et maintenance
  - [R61] Effectuer des mises à jour régulières : status = ✔️

---

# 7 - Configuration des services
  - [R62] Désactiver les services non nécessaires : status = ✔️
  - [R63] Désactiver les fonctionnalités des services non essentielles : status = ✔️
  - [R64] Configurer les privilèges des services : status = 💭
## 7.1 - Cloisonnement
  - [R65] Cloisonner les services : status = ✔️ | 🔜 (Docker)
  - [R66] Durcir les composants de cloisonnement : status = ✔️ | 🔜 (Docker)
## 7.2 - Services système
### 7.2.1 - Pluggable Authentication Module ou module d'authentification enfichable
  - [R67] Sécuriser les authentifications distante par PAM : status = 💭
  - [R68] Protéger les mots de passe stockés  : status = ⚠️
### 7.2.2 - Name Service Switch ou service de gestion de noms
  - [R69] Sécuriser les accès aux bases utilisateur distantes : status = ✔️ | 🔜 (Config OpenSSH)
  - [R70] Séparer les comptes système et d'administrateur de l'annuaire : status = ❌
### 7.2.3 - Journalisation
  - [R71] Mettre en place un système de journalisation : status = ❌ | 🔜 (Surveillance : Prometheus/ELK Stack/Kibana)
  - [R72] Mettre en place des journaux d'activité de service dédiés : status = ❌ | 🔜 (Surveillance : Prometheus/ELK Stack/Kibana)
  - [R73] Journaliser l'activité système avec auditd : status = ✔️
### 7.2.4 - Messagerie
  - [R74] Durcir le service de messagerie locale : status = 💭
  - [R75] Configurer un alias de messagerie des comptes de service : status = 💭
### 7.2.5 - Surveillance du système de fichiers
  - [R76] Sceller et vérifier l'intégrité des fichiers : status = 💭
  - [R77] Protéger la base de données des scellés : status = 💭
## 7.3 Services réseau
  - [R78] Cloisonner les services réseau : status = ✔️ | 🔜 (Docker)
  - [R79] Durcir et surveiller les services exposés : status = ❌ | 🔜 (Configuration + MAJ auto | Surveillance : Prometheus/ELK Stack/Kibana)
  - [R80] Réduire la surface d'attaque des services réseau : status = ❌ | 🔜 (Pare-feu : ufw | Protection :  fail2ban)

---

# Cahier de Recette - Déploiement des Mesures de Sécurité sur AlmaLinux

## Définition du Cahier de Recette

Un **cahier de recette** est un document détaillé qui décrit les procédures et les critères pour tester et valider une solution informatique avant sa mise en production. Il sert à vérifier que la solution respecte les exigences spécifiées et fonctionne correctement dans l'environnement cible. Dans le contexte de ce projet, le cahier de recette fournit une méthodologie pour déployer et vérifier les mesures de sécurité sur une machine AlmaLinux en utilisant un script Ansible. Il inclut des étapes spécifiques, des critères de validation, et des procédures pour garantir que les configurations matérielles, BIOS/UEFI, démarrage sécurisé UEFI, et les paramètres du noyau Linux sont correctement mises en place.

## 4 - Configuration Matérielle

### 4.1 - Support Matériel

**Objectif :** S'assurer que le matériel est correctement choisi et configuré pour les besoins de sécurité.

- **[R1] Choisir et configurer son matériel :** ✔️

**Description :**
- **Étapes préalables :** Vérifiez que le matériel est compatible avec AlmaLinux.
- **Vérification :** Confirmez que le matériel est éligible aux dernières mises à jour de sécurité et configurations recommandées.
- **Vérification via Ansible :** Créez un playbook Ansible pour collecter des informations sur le matériel (CPU, RAM, stockage) et vérifier leur conformité aux spécifications requises.
- **Validation :** Les informations sur le matériel doivent correspondre aux spécifications définies dans la documentation technique.

**Script Ansible exemple :**
```yaml
---
- name: Vérifier la configuration matérielle
  hosts: all
  tasks:
    - name: Collecter les informations matérielles
      command: "dmidecode -t system"
      register: hardware_info

    - name: Afficher les informations matérielles
      debug:
        msg: "{{ hardware_info.stdout }}"
```

### 4.2 - BIOS/UEFI

**Objectif :** Configurer le BIOS/UEFI pour garantir les meilleures pratiques de sécurité.

- **[R2] Configurer le BIOS/UEFI :** ✔️

**Description :**
- **Étapes préalables :** Accéder à l’interface BIOS/UEFI pour configurer les paramètres de sécurité.
- **Vérification :** Assurez-vous que les paramètres de sécurité, tels que le mot de passe administrateur, la gestion des périphériques, et les options de démarrage sécurisé sont correctement configurés.
- **Validation :** Vérifiez que les paramètres définis sont en conformité avec les politiques de sécurité de l’organisation.

**Notes :** La configuration BIOS/UEFI est souvent manuelle et peut nécessiter des outils spécifiques du fabricant pour une automatisation complète.

### 4.3 - Démarrage Sécurisé UEFI

**Objectif :** Assurer que le démarrage sécurisé UEFI est correctement configuré pour protéger le système contre les attaques de bootkit.

#### 4.3.1 - Clés Préchargées

- **[R3] Activer le démarrage sécurisé UEFI :** ✔️

**Description :**
- **Étapes préalables :** Accédez à l’interface UEFI pour activer le démarrage sécurisé.
- **Vérification :** Confirmez que le démarrage sécurisé est activé dans les paramètres UEFI.
- **Validation :** Utilisez `efibootmgr` pour vérifier l'état du démarrage sécurisé.

**Commandes exemple :**
```bash
efibootmgr -v
```

#### 4.3.2 - Nouvelles Clés

- **[R4] Remplacer les clés préchargées :** ✔️

**Description :**
- **Étapes préalables :** Importer ou remplacer les clés de démarrage sécurisé si nécessaire pour répondre aux exigences de sécurité.
- **Vérification :** Assurez-vous que les nouvelles clés sont correctement importées et que le système utilise les clés de démarrage sécurisé mises à jour.
- **Validation :** Vérifiez que les nouvelles clés sont bien présentes et utilisées par le système.

**Commandes exemple :**
```bash
# Pour importer une clé
mokutil --import /path/to/your_key.der

# Pour gérer les clés UEFI
efibootmgr -v
```

## 5 - Configuration du Noyau Linux

### 5.1 - Chargeur de Démarrage

**Objectif :** Protéger l'accès au chargeur de démarrage pour éviter toute modification non autorisée.

- **[R5] Configurer un mot de passe pour le chargeur de démarrage :** ❌

**Description :**
- **Étapes préalables :** Accéder à la configuration du chargeur de démarrage (comme GRUB) pour ajouter un mot de passe.
- **Vérification :** Assurez-vous que le mot de passe est correctement configuré et protégé.
- **Validation :** Le mot de passe doit être requis pour accéder aux options de démarrage ou modifier les paramètres du chargeur de démarrage.

**Notes :** Cette étape nécessite une intervention manuelle ou l'utilisation d'outils spécifiques pour configurer le mot de passe du chargeur de démarrage.

### 5.2 - Configuration Dynamique

**Objectif :** Assurer que les paramètres de configuration du noyau et les options de démarrage sont sécurisés et que les configurations sont protégées.

#### 5.2.1 - Configuration de la Mémoire

- **[R7] Activer l'IOMMU :** ✔️

**Description :**
- **Étapes préalables :** Configurer le noyau pour activer l'IOMMU (Input-Output Memory Management Unit).
- **Vérification :** Assurez-vous que l'IOMMU est activé en vérifiant les paramètres du noyau.
- **Validation :** L'IOMMU doit être activé pour améliorer la sécurité de la gestion de la mémoire des périphériques.

**Commandes exemple :**
```bash
dmesg | grep -i iommu
```

- **[R8] Paramétrer les options de configuration de la mémoire :** ⚠️

**Description :**
- **Étapes préalables :** Configurer les options de gestion de la mémoire dans le noyau (par exemple, `memmap`, `highmem`).
- **Vérification :** Confirmez que les paramètres de mémoire sont correctement appliqués.
- **Validation :** Les options doivent être en accord avec les meilleures pratiques de sécurité et les recommandations.

**Commandes exemple :**
```bash
cat /proc/cmdline
```

#### 5.2.2 - Configuration du Noyau

- **[R9] Paramétrer les options de configuration du noyau :** ⚠️

**Description :**
- **Étapes préalables :** Modifier les options de configuration du noyau (par exemple, `kernel.parameters`).
- **Vérification :** Vérifiez que les options sont correctement appliquées.
- **Validation :** Les paramètres doivent renforcer la sécurité du noyau sans compromettre la fonctionnalité.

**Commandes exemple :**
```bash
cat /proc/cmdline
```

- **[R10] Désactiver le chargement des modules noyau :** ✔️

**Description :**
- **Étapes préalables :** Configurer le noyau pour interdire le chargement dynamique des modules.
- **Vérification :** Assurez-vous que le chargement des modules est désactivé.
- **Validation :** Le système ne doit pas permettre le chargement de nouveaux modules pour éviter les modifications non autorisées.

**Commandes exemple :**
```bash
echo "install_modules = 0" >> /etc/modprobe.d/blacklist.conf
```

#### 5.2.3 - Configuration des Processus

- **[R11] Activer et configurer le LSM Yama :** ✔️

**Description :**
- **Étapes préalables :** Activer le module de sécurité Linux (LSM) Yama pour renforcer les contrôles de sécurité des processus.
- **Vérification :** Assurez-vous que Yama est activé et configuré correctement.
- **Validation :** Yama doit être actif et ses politiques doivent être appliquées pour renforcer la sécurité des processus.

**Commandes exemple :**
```bash
cat /proc/sys/kernel/yama/ptrace_scope
```

#### 5.2.4 - Configuration du Réseau

- **[R12] Paramétrer les options de configuration du réseau IPv4 :** ✔️

**Description :**
- **Étapes préalables :** Configurer les options de sécurité pour IPv4 dans le noyau.
- **Vérification :** Assurez-vous que les paramètres IPv4 sont configurés correctement.
- **Validation :** Les options IPv4 doivent renforcer la sécurité du réseau sans affecter les performances.

**Commandes exemple :**
```bash
sysctl net.ipv4.conf.all.*
```

- **[R13] Désactiver le plan IPv6 :** ✔️

**Description :**
- **Étapes préalables :** Désactiver le plan IPv6 pour réduire la surface d'attaque.
- **Vérification :** Confirmez que le plan IPv6 est désactivé.
- **Validation :** Le système ne doit pas accepter les connexions IPv6.

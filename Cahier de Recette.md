## Cahier de Recette de la Solution

### Définition du Cahier de Recette
Le **cahier de recette** est un document structuré qui décrit les conditions et critères nécessaires pour valider qu'une solution informatique est conforme aux exigences spécifiées. Il sert de guide pour tester et vérifier la solution avant sa mise en production, garantissant ainsi que toutes les fonctionnalités requises sont correctement mises en place et opérationnelles.

---

## Projet : Déploiement de Mesures de Sécurité sur Almalinux avec Ansible

### 4 - Configuration Matérielle

#### 4.1 - Support Matériel

**[R1] Choisir et configurer son matériel**  
**Objectif :** S'assurer que le matériel utilisé est conforme aux spécifications nécessaires pour le déploiement des mesures de sécurité.

- **Description :** Sélectionner un serveur ou une machine compatible avec Almalinux et capable de supporter les configurations de sécurité requises. La configuration matérielle doit inclure une vérification des ressources minimales, des capacités de stockage et de mémoire, et une validation de la compatibilité avec les configurations de sécurité.
- **Critères de Réussite :**
  - Matériel validé pour exécuter Almalinux sans problèmes de compatibilité.
  - Ressources minimales respectées.
  - Documentation des spécifications matérielles validées.

#### 4.2 - BIOS/UEFI

**[R2] Configurer le BIOS/UEFI**  
**Objectif :** Assurer que les paramètres du BIOS/UEFI sont configurés correctement pour supporter les mesures de sécurité.

- **Description :** Accéder aux paramètres du BIOS/UEFI et configurer les options nécessaires pour renforcer la sécurité. Cela peut inclure la désactivation de fonctionnalités non sécurisées et l'activation de celles qui sont nécessaires pour sécuriser le système.
- **Critères de Réussite :**
  - Accès au BIOS/UEFI confirmé.
  - Paramètres de sécurité configurés comme requis.
  - Vérification du redémarrage et de la persistance des configurations après redémarrage.

#### 4.3 - Démarrage Sécurisé UEFI

**4.3.1 - Clés Préchargées**

**[R3] Activer le démarrage sécurisé UEFI**  
**Objectif :** Garantir que le démarrage sécurisé est activé pour protéger le système contre les logiciels malveillants au niveau du démarrage.

- **Description :** Configurer le système pour utiliser le démarrage sécurisé UEFI, ce qui inclut l'activation des fonctionnalités de démarrage sécurisé dans les paramètres UEFI.
- **Critères de Réussite :**
  - Démarrage sécurisé activé dans le BIOS/UEFI.
  - Vérification que le système ne démarre qu'avec des logiciels signés et approuvés.

**4.3.2 - Nouvelles Clés**

**[R4] Remplacer les clés préchargées**  
**Objectif :** Remplacer les clés préchargées par des clés personnalisées pour un contrôle renforcé du démarrage sécurisé.

- **Description :** Remplacer les clés de démarrage préchargées par des clés personnalisées ou par celles fournies par une autorité de certification interne. Cette étape est cruciale pour renforcer la sécurité en ayant un contrôle total sur les clés utilisées pour le démarrage.
- **Critères de Réussite :**
  - Remplacement des clés validé avec succès.
  - Vérification que les nouvelles clés sont opérationnelles et que le système démarre correctement avec ces nouvelles clés.
  - Documentation des clés utilisées et des procédures de remplacement.

# 5 - Configuration du Noyau Linux

## 5.1 - Chargeur de Démarrage

**[R5] Configurer un mot de passe pour le chargeur de démarrage**  
*Objectif* : Protéger le chargeur de démarrage avec un mot de passe pour empêcher les modifications non autorisées des paramètres de démarrage.

- **Description** : Configurer un mot de passe pour accéder aux options de démarrage et protéger le chargeur de démarrage (par exemple, GRUB). Cela empêche les utilisateurs non autorisés de modifier les paramètres de démarrage ou d'accéder au mode de récupération sans authentification.
- **Critères de Réussite** :
  - Mot de passe configuré avec succès pour le chargeur de démarrage.
  - Vérification que le mot de passe est requis pour accéder aux options de démarrage et aux modifications du chargeur.
- **Statut** : ❌
  - **Remarque** : Ce point est encore en cours de mise en œuvre. Il nécessite une configuration correcte du mot de passe et une validation complète.

## 5.2 - Configuration Dynamique

**[R6] Protéger les paramètres de ligne de commande du noyau et l'initramfs**  
*Objectif* : Protéger les paramètres de ligne de commande du noyau et l'initramfs pour éviter les modifications non autorisées.

- **Description** : Configurer les protections nécessaires pour les paramètres de ligne de commande du noyau et l'initramfs afin d'empêcher les modifications malveillantes.
- **Critères de Réussite** :
  - Paramètres de ligne de commande et initramfs protégés avec succès.
  - Vérification que les protections sont en place et fonctionnelles.
- **Statut** : ✔️
  - **Remarque** : Les protections sont correctement configurées.

### 5.2.1 - Configuration de la Mémoire

**[R7] Activer l'IOMMU**  
*Objectif* : Activer l'IOMMU pour améliorer la sécurité en isolant les périphériques d'entrée/sortie de la mémoire.

- **Description** : Activer la gestion de la mémoire pour les périphériques d'entrée/sortie (IOMMU) afin de protéger contre les attaques de type DMA.
- **Critères de Réussite** :
  - IOMMU activé et vérifié.
  - Documentation de la configuration de l'IOMMU.
- **Statut** : ✔️
  - **Remarque** : L'IOMMU est activé avec succès.

**[R8] Paramétrer les options de configuration de la mémoire**  
*Objectif* : Configurer les options de mémoire pour renforcer la sécurité.

- **Description** : Configurer les options spécifiques de la mémoire du noyau pour améliorer la sécurité, comme les options de protection contre les attaques par débordement de mémoire.
- **Critères de Réussite** :
  - Options de configuration de la mémoire correctement paramétrées.
  - Vérification des paramètres et documentation.
- **Statut** : ⚠️
  - **Remarque** : La configuration des options de mémoire est en cours de révision pour assurer la conformité avec les meilleures pratiques de sécurité.

### 5.2.2 - Configuration du Noyau

**[R9] Paramétrer les options de configuration du noyau**  
*Objectif* : Configurer les options du noyau pour renforcer la sécurité.

- **Description** : Ajuster les paramètres du noyau pour inclure des configurations de sécurité avancées, comme la protection contre l'exécution de code non autorisé.
- **Critères de Réussite** :
  - Paramètres du noyau configurés comme requis.
  - Vérification de la configuration et validation des paramètres.
- **Statut** : ⚠️
  - **Remarque** : Les options de configuration du noyau sont en cours d'optimisation pour s'assurer qu'elles répondent aux exigences de sécurité.

**[R10] Désactiver le chargement des modules noyau**  
*Objectif* : Prévenir le chargement de modules noyau non autorisés pour réduire les risques de sécurité.

- **Description** : Configurer le noyau pour empêcher le chargement de modules noyau non signés ou non autorisés.
- **Critères de Réussite** :
  - Chargement des modules noyau désactivé avec succès.
  - Vérification de l'impossibilité de charger des modules non autorisés.
- **Statut** : ✔️
  - **Remarque** : Le chargement des modules noyau est désactivé avec succès.

### 5.2.3 - Configuration des Processus

**[R11] Activer et configurer le LSM Yama**  
*Objectif* : Activer le module de sécurité Linux (LSM) Yama pour améliorer la sécurité des processus.

- **Description** : Configurer le module de sécurité Yama pour renforcer les politiques de sécurité au niveau des processus, comme l'extension des restrictions d'accès aux fichiers et aux ressources système.
- **Critères de Réussite** :
  - LSM Yama activé et configuré selon les spécifications.
  - Vérification de la configuration et de la fonctionnalité.
- **Statut** : ✔️
  - **Remarque** : LSM Yama est correctement activé et configuré.

### 5.2.4 - Configuration du Réseau

**[R12] Paramétrer les options de configuration du réseau IPv4**  
*Objectif* : Configurer les options de réseau IPv4 pour renforcer la sécurité du réseau.

- **Description** : Configurer les options de sécurité pour le réseau IPv4, y compris les politiques de filtrage et les configurations de pare-feu.
- **Critères de Réussite** :
  - Options de configuration du réseau IPv4 paramétrées correctement.
  - Vérification des paramètres et validation des configurations.
- **Statut** : ✔️
  - **Remarque** : La configuration du réseau IPv4 est correctement paramétrée.

**[R13] Désactiver le plan IPv6**  
*Objectif* : Désactiver le plan IPv6 si non requis pour éviter des vecteurs d'attaque supplémentaires.

- **Description** : Désactiver le support IPv6 pour réduire les surfaces d'attaque et simplifier la gestion de la sécurité réseau.
- **Critères de Réussite** :
  - Support IPv6 désactivé avec succès.
  - Vérification que IPv6 n'est pas actif et n'affecte pas les opérations.
- **Statut** : ✔️
  - **Remarque** : Le support IPv6 est désactivé avec succès.

# 6 - Configuration Système

## 6.1 - Partitionnement

### [R28] Partitionnement type
**Objectif :** Configurer le partitionnement du disque dur pour assurer une séparation appropriée des données et des systèmes, facilitant ainsi la sécurité et la gestion.

- **Description :** Déterminer et appliquer un schéma de partitionnement du disque qui répond aux meilleures pratiques de sécurité, incluant la séparation des partitions système, utilisateur, et de données.
- **Critères de Réussite :**
  - Schéma de partitionnement défini et appliqué.
  - Vérification que les partitions sont correctement configurées et séparées comme prévu.
- **Statut :** ❌
  - **Remarque :** Ce point est encore en cours de planification. Il nécessite l'élaboration d'un schéma de partitionnement sécurisé et sa mise en œuvre.

### [R29] Restreindre les accès au dossier /boot
**Objectif :** Protéger le dossier /boot contre les accès non autorisés pour éviter les modifications malveillantes du noyau.

- **Description :** Configurer les permissions du dossier /boot pour restreindre l'accès aux utilisateurs non autorisés et éviter les altérations non désirées.
- **Critères de Réussite :**
  - Permissions correctement configurées pour le dossier /boot.
  - Vérification des permissions et validation de l'accès restreint.
- **Statut :** ✔️
  - **Remarque :** Les permissions sur le dossier /boot sont correctement configurées.

## 6.2 - Comptes d'accès

### 6.2.1 - Comptes Utilisateur

#### [R30] Désactiver les comptes utilisateur inutilisés
**Objectif :** Assurer que les comptes utilisateur non utilisés sont désactivés pour réduire les risques de sécurité.

- **Description :** Identifier et désactiver les comptes utilisateur qui ne sont plus nécessaires ou utilisés.
- **Critères de Réussite :**
  - Comptes inutilisés identifiés et désactivés.
  - Liste des comptes désactivés validée et documentée.
- **Statut :** ⚠️
  - **Remarque :** Ce point est en cours d'examen. Il nécessite une identification complète des comptes inutilisés et leur désactivation.

#### [R31] Utiliser des mots de passe robustes
**Objectif :** Assurer que les mots de passe des comptes utilisateur sont suffisamment robustes pour prévenir les accès non autorisés.

- **Description :** Configurer et appliquer des politiques de mots de passe robustes, incluant des exigences de longueur, complexité, et renouvellement.
- **Critères de Réussite :**
  - Politiques de mots de passe robustes appliquées.
  - Vérification que tous les mots de passe respectent les exigences de robustesse.
- **Statut :** ⚠️
  - **Remarque :** Les politiques de mots de passe sont en cours d'implémentation et de vérification.

#### [R32] Expirer les sessions utilisateur locales
**Objectif :** Configurer l'expiration automatique des sessions utilisateur locales pour limiter les risques de sessions laissées ouvertes.

- **Description :** Configurer des paramètres pour expirer automatiquement les sessions utilisateur inactives après une période prédéfinie.
- **Critères de Réussite :**
  - Paramètres d'expiration des sessions configurés.
  - Vérification que les sessions expirent comme prévu.
- **Statut :** ❌
  - **Remarque :** Ce point est encore en cours d'implémentation et nécessite la configuration des politiques d'expiration des sessions.

### 6.2.2 - Comptes Administrateur

#### [R33] Assurer l'imputabilité des actions d'administration
**Objectif :** Garantir que les actions des comptes administrateurs sont traçables pour assurer la responsabilité et l'auditabilité.

- **Description :** Configurer des mécanismes pour enregistrer les actions des administrateurs, incluant la mise en place de journaux d'audit détaillés.
- **Critères de Réussite :**
  - Journaux d'audit des actions des administrateurs configurés et fonctionnels.
  - Vérification de la traçabilité et de l'exactitude des journaux.
- **Statut :** ❌
  - **Remarque :** Ce point est encore en cours de mise en œuvre. Il nécessite la configuration des systèmes de journalisation pour les actions des administrateurs.

### 6.2.3 - Comptes de Service

#### [R34] Désactiver les comptes de service
**Objectif :** S'assurer que les comptes de service non utilisés ou non nécessaires sont désactivés pour minimiser les risques de sécurité.

- **Description :** Identifier et désactiver les comptes de service qui ne sont pas utilisés ou qui ne sont plus nécessaires.
- **Critères de Réussite :**
  - Comptes de service inutilisés identifiés et désactivés.
  - Liste des comptes désactivés validée et documentée.
- **Statut :** ✔️
  - **Remarque :** Les comptes de service non nécessaires sont correctement désactivés.

#### [R35] Utiliser des comptes de service uniques et exclusifs
**Objectif :** Assurer que chaque service utilise un compte unique et exclusif pour améliorer la gestion et la sécurité.

- **Description :** Configurer chaque service pour utiliser un compte de service distinct afin de faciliter la gestion des permissions et l'audit.
- **Critères de Réussite :**
  - Comptes de service uniques et exclusifs configurés.
  - Vérification de l'utilisation des comptes de service séparés pour chaque service.
- **Statut :** ❌
  - **Remarque :** Ce point est encore en cours d'implémentation et nécessite la création et l'attribution de comptes de service distincts.

## 6.3 - Contrôle d'accès

### 6.3.1 - Modèle Traditionnel Unix

#### [R36] Modifier la valeur par défaut de UMASK
**Objectif :** Configurer la valeur UMASK pour restreindre les permissions par défaut des fichiers et répertoires créés.

- **Description :** Modifier la valeur par défaut de UMASK pour appliquer des permissions plus restrictives par défaut sur les nouveaux fichiers et répertoires.
- **Critères de Réussite :**
  - Valeur UMASK modifiée comme requis.
  - Vérification que les nouvelles permissions sont appliquées correctement.
- **Statut :** ✔️
  - **Remarque :** La valeur UMASK est correctement modifiée.

#### [R37] Utiliser des fonctionnalités de contrôle d'accès obligatoire MAC
**Objectif :** Appliquer les politiques de contrôle d'accès obligatoire (MAC) pour renforcer la sécurité des ressources système.

- **Description :** Activer et configurer les politiques MAC pour contrôler l'accès aux ressources système en fonction de niveaux de sécurité définis.
- **Critères de Réussite :**
  - Politiques MAC activées et configurées.
  - Vérification des fonctionnalités de contrôle d'accès obligatoire.
- **Statut :** ✔️
  - **Remarque :** Les fonctionnalités MAC sont correctement mises en place.

#### [R38] Créer un groupe dédié à l'usage de sudo
**Objectif :** Créer un groupe spécifique pour les utilisateurs autorisés à utiliser sudo afin de centraliser la gestion des privilèges.

- **Description :** Créer un groupe dédié aux utilisateurs qui ont besoin d'utiliser sudo pour l'exécution de commandes privilégiées.
- **Critères de Réussite :**
  - Groupe sudo créé et utilisateurs ajoutés.
  - Vérification que le groupe est utilisé pour la gestion des droits sudo.
- **Statut :** ✔️
  - **Remarque :** Le groupe dédié à sudo est créé et fonctionnel.

#### [R39] Modifier les directives de configuration sudo
**Objectif :** Configurer les directives sudo pour restreindre l'utilisation et les privilèges accordés aux utilisateurs.

- **Description :** Modifier les fichiers de configuration sudo pour restreindre les commandes et les privilèges accordés aux utilisateurs du groupe sudo.
- **Critères de Réussite :**
  - Directives sudo configurées selon les meilleures pratiques de sécurité.
  - Vérification des permissions et des restrictions configurées.
- **Statut :** ✔️
  - **Remarque :** Les directives sudo sont correctement modifiées.

#### [R40] Utiliser des utilisateurs cibles non-privilégiés pour les commandes sudo

**Objectif :** Configurer sudo pour que les commandes soient exécutées avec les privilèges minimaux nécessaires.

**Description :** Configurer sudo pour que les commandes soient exécutées avec des utilisateurs cibles non-privilégiés lorsque cela est possible.

**Critères de Réussite :**
- Configuration de sudo pour utiliser des utilisateurs non-privilégiés comme cibles.
- Vérification que les commandes sont exécutées avec les privilèges minimaux nécessaires.

**Statut :** ✔️  
**Remarque :** Les utilisateurs cibles non-privilégiés sont utilisés comme prévu.

#### [R41] Limiter l'utilisation de commandes nécessitant la directive EXEC

**Objectif :** Restreindre l'utilisation de commandes nécessitant la directive EXEC dans la configuration sudo pour réduire les risques de sécurité.

**Description :** Modifier la configuration sudo pour limiter l'utilisation de la directive EXEC qui permet l'exécution de commandes externes.

**Critères de Réussite :**
- Limitation de la directive EXEC dans la configuration sudo.
- Vérification que l'utilisation de EXEC est restreinte.

**Statut :** ✔️  
**Remarque :** L'utilisation de la directive EXEC est correctement limitée.

#### [R42] Bannir les négations dans les spécifications sudo

**Objectif :** Éviter l'utilisation de négations dans les fichiers de configuration sudo pour simplifier les règles et éviter les erreurs.

**Description :** Modifier les spécifications sudo pour éliminer les négations et simplifier les règles de gestion des privilèges.

**Critères de Réussite :**
- Négations supprimées des spécifications sudo.
- Vérification de la configuration simplifiée.

**Statut :** ✔️  
**Remarque :** Les négations sont correctement bannies des spécifications sudo.

#### [R43] Préciser les arguments dans les spécifications sudo

**Objectif :** Spécifier les arguments nécessaires dans les configurations sudo pour garantir une gestion précise des privilèges.

**Description :** Configurer sudo pour inclure des arguments précis dans les spécifications afin de mieux contrôler les commandes autorisées.

**Critères de Réussite :**
- Arguments spécifiés dans les configurations sudo.
- Vérification que les spécifications sont précises et appropriées.

**Statut :** ✔️  
**Remarque :** Les arguments sont correctement précisés dans les spécifications sudo.

#### [R44] Éditer les fichiers de manière sécurisée avec sudo

**Objectif :** Assurer que les fichiers sont édités de manière sécurisée lorsqu'ils sont modifiés avec sudo.

**Description :** Configurer les outils d'édition pour qu'ils soient utilisés de manière sécurisée lors de modifications avec sudo, réduisant ainsi les risques de sécurité.

**Critères de Réussite :**
- Édition sécurisée des fichiers avec sudo confirmée.
- Vérification des pratiques de sécurité lors de l'édition des fichiers.

**Statut :** ✔️  
**Remarque :** L'édition sécurisée des fichiers avec sudo est correctement mise en place.

## 6.3.2 - AppArmor

#### [R45] Activer les profils de sécurité AppArmor

**Objectif :** Utiliser AppArmor pour appliquer des politiques de sécurité basées sur des profils pour les applications.

**Description :** Configurer et activer les profils de sécurité AppArmor pour restreindre les permissions des applications en fonction de leurs besoins.

**Critères de Réussite :**
- Profils AppArmor activés et appliqués.
- Vérification du fonctionnement et de l'application des profils.

**Statut :** ⚠️  
**Remarque :** L'activation des profils AppArmor est en cours et nécessite une validation complète des politiques appliquées.

## 6.3.3 - SELinux

#### [R46] Activer SELinux avec la politique targeted

**Objectif :** Activer SELinux avec la politique targeted pour renforcer la sécurité du système en contrôlant l'accès aux ressources.

**Description :** Configurer SELinux pour utiliser la politique targeted, qui offre un bon équilibre entre sécurité et fonctionnalité.

**Critères de Réussite :**
- SELinux activé avec la politique targeted.
- Vérification du fonctionnement de SELinux avec la politique configurée.

**Statut :** ✔️  
**Remarque :** SELinux est activé avec la politique targeted.

#### [R47] Confiner les utilisateurs interactifs non privilégiés

**Objectif :** Utiliser SELinux pour confiner les utilisateurs non privilégiés afin de réduire les risques de sécurité.

**Description :** Configurer SELinux pour appliquer des restrictions supplémentaires aux utilisateurs interactifs non privilégiés.

**Critères de Réussite :**
- Utilisateurs non privilégiés confinés comme prévu.
- Vérification des restrictions appliquées.

**Statut :** ✔️  
**Remarque :** Les utilisateurs non privilégiés sont correctement confinés.

#### [R48] Paramétrer les variables SELinux

**Objectif :** Configurer les variables SELinux pour adapter les politiques de sécurité aux besoins spécifiques du système.

**Description :** Configurer les variables SELinux pour personnaliser les politiques de sécurité en fonction des besoins du système.

**Critères de Réussite :**
- Variables SELinux configurées correctement.
- Vérification des politiques adaptées et des variables fonctionnelles.

**Statut :** ❌  
**Remarque :** La configuration des variables SELinux est en cours et nécessite une finalisation.

#### [R49] Désinstaller les outils de débogage de politique SELinux

**Objectif :** Supprimer les outils de débogage de politique SELinux pour éviter les risques de sécurité associés à leur présence.

**Description :** Désinstaller les outils de débogage SELinux qui ne sont pas nécessaires en production.

**Critères de Réussite :**
- Outils de débogage SELinux désinstallés.
- Vérification que les outils ne sont plus présents sur le système.

**Statut :** ✔️  
**Remarque :** Les outils de débogage SELinux sont désinstallés.

## 6.4 - Fichiers et Répertoires

### 6.4.1 - Fichiers et Répertoires Sensibles

#### [R51] Changer les secrets et droits d'accès dès l'installation
**Objectif :** Assurer que les secrets (comme les clés SSH, les fichiers de configuration sensibles) et les droits d'accès sont correctement configurés dès l'installation du système.

- **Description :** Après l'installation du système, modifier les secrets et les droits d'accès pour s'assurer qu'ils sont appropriés et sécurisés.
- **Critères de Réussite :**
  - Secrets modifiés dès l'installation.
  - Droits d'accès configurés selon les meilleures pratiques de sécurité.
- **Statut :** ⚠️
  - **Remarque :** Cette tâche est en cours. Il est nécessaire de vérifier que les secrets et droits d'accès ont été ajustés correctement après l'installation.

### 6.4.2 - Fichiers IPC Nommés, Sockets ou Pipes

#### [R52] Restreindre les accès aux sockets et aux pipes nommées
**Objectif :** Protéger les sockets et pipes nommés pour éviter les accès non autorisés et les risques de sécurité.

- **Description :** Configurer les permissions des sockets et pipes nommés pour limiter l'accès aux utilisateurs et processus autorisés.
- **Critères de Réussite :**
  - Permissions des sockets et pipes nommés vérifiées et restreintes.
  - Documentation des paramètres de sécurité appliqués.
- **Statut :** ❌
  - **Remarque :** La restriction des accès aux sockets et pipes nommés n'a pas encore été mise en place. Il est nécessaire de configurer ces paramètres pour sécuriser ces ressources.

### 6.4.3 - Droits d'Accès

#### [R53] Éviter les fichiers ou répertoires sans utilisateur ou sans groupe connu
**Objectif :** S'assurer que tous les fichiers et répertoires ont des propriétaires et des groupes définis pour éviter les problèmes de sécurité.

- **Description :** Vérifier que tous les fichiers et répertoires ont un utilisateur et un groupe attribués pour éviter des permissions par défaut incorrectes.
- **Critères de Réussite :**
  - Tous les fichiers et répertoires ont un propriétaire et un groupe connu.
  - Validation des permissions et des propriétés.
- **Statut :** ✔️
  - **Remarque :** Les fichiers et répertoires ont des propriétaires et groupes définis comme requis.

#### [R54] Activer le sticky bit sur les répertoires inscriptibles
**Objectif :** Activer le sticky bit sur les répertoires inscriptibles pour prévenir la suppression non autorisée des fichiers par les utilisateurs.

- **Description :** Configurer le sticky bit sur les répertoires où les utilisateurs peuvent écrire, afin de garantir que seuls les propriétaires des fichiers peuvent les supprimer.
- **Critères de Réussite :**
  - Sticky bit activé sur les répertoires appropriés.
  - Vérification de la configuration des répertoires.
- **Statut :** ⚠️
  - **Remarque :** L'activation du sticky bit est en cours d'implémentation. Une vérification est nécessaire pour garantir que le sticky bit est appliqué correctement.

#### [R55] Séparer les répertoires temporaires des utilisateurs
**Objectif :** Isoler les répertoires temporaires des répertoires des utilisateurs pour minimiser les risques de sécurité.

- **Description :** Configurer des répertoires temporaires séparés pour les processus système et les utilisateurs pour éviter les interférences et les risques de sécurité.
- **Critères de Réussite :**
  - Répertoires temporaires séparés configurés.
  - Vérification que les répertoires temporaires et des utilisateurs sont distincts.
- **Statut :** ✔️
  - **Remarque :** Les répertoires temporaires sont correctement séparés des répertoires des utilisateurs.

#### [R56] Éviter l'usage d'exécutables avec les droits spéciaux setuid et setgid
**Objectif :** Réduire les risques de sécurité en évitant l'utilisation d'exécutables avec les droits spéciaux setuid et setgid.

- **Description :** Examiner les exécutables pour s'assurer qu'aucun fichier n'utilise les droits spéciaux setuid ou setgid à moins que cela ne soit absolument nécessaire.
- **Critères de Réussite :**
  - Exécutables avec les droits spéciaux setuid et setgid identifiés et éliminés si non nécessaires.
  - Vérification des permissions des exécutables.
- **Statut :** ✔️
  - **Remarque :** L'utilisation des droits spéciaux setuid et setgid est évitée conformément aux politiques de sécurité.

#### [R57] Éviter l'usage d'exécutables avec les droits spéciaux setuid root et setgid root
**Objectif :** Empêcher l'utilisation d'exécutables avec les droits spéciaux setuid root et setgid root pour réduire les risques de sécurité.

- **Description :** Vérifier que les exécutables avec les droits spéciaux setuid root et setgid root sont supprimés ou corrigés pour éviter les risques de sécurité.
- **Critères de Réussite :**
  - Exécutables avec les droits spéciaux setuid root et setgid root identifiés et corrigés.
  - Documentation de la configuration et des modifications.
- **Statut :** ✔️
  - **Remarque :** L'utilisation d'exécutables avec les droits spéciaux setuid root et setgid root est correctement évitée.

## 6.5 - Gestion des Paquets

#### [R58] N'installer que les paquets strictement nécessaires
**Objectif :** Installer uniquement les paquets nécessaires pour minimiser les risques de sécurité et la surface d'attaque.

- **Description :** Réduire le nombre de paquets installés aux seuls essentiels pour éviter l'installation de logiciels superflus qui pourraient introduire des vulnérabilités.
- **Critères de Réussite :**
  - Liste des paquets vérifiée et réduite aux stricts nécessaires.
  - Documentation des paquets installés et justification des choix.
- **Statut :** ✔️
  - **Remarque :** Seuls les paquets nécessaires sont installés.

#### [R59] Utiliser des dépôts de paquets de confiance
**Objectif :** Assurer que les paquets sont obtenus à partir de dépôts de confiance pour éviter les logiciels malveillants ou compromis.

- **Description :** Configurer les dépôts de paquets pour utiliser uniquement des sources de confiance, vérifiées pour leur sécurité.
- **Critères de Réussite :**
  - Dépôts de paquets configurés pour utiliser des sources fiables.
  - Vérification de l'intégrité et de la provenance des paquets.
- **Statut :** ✔️
  - **Remarque :** Les dépôts de paquets sont correctement configurés pour utiliser des sources de confiance.

#### [R60] Utiliser des dépôts de paquets durcis
**Objectif :** Utiliser des dépôts qui appliquent des mesures de sécurité renforcées pour les paquets disponibles.

- **Description :** Configurer les dépôts pour obtenir des paquets durcis, avec des mesures de sécurité supplémentaires en place.
- **Critères de Réussite :**
  - Dépôts de paquets durcis identifiés et utilisés.
  - Vérification des politiques de sécurité appliquées aux dépôts.
- **Statut :** ✔️
  - **Remarque :** Les dépôts de paquets durcis sont utilisés correctement.

## 6.6 - Veille et Maintenance

#### [R61] Effectuer des mises à jour régulières
**Objectif :** Assurer que le système reçoit des mises à jour régulières pour corriger les vulnérabilités et améliorer la sécurité.

- **Description :** Mettre en place un processus pour appliquer les mises à jour et les correctifs de sécurité de manière régulière et systématique.
- **Critères de Réussite :**
  - Mises à jour et correctifs appliqués régulièrement.
  - Documentation des mises à jour effectuées et des dates d'application.
- **Statut :** ✔️
  - **Remarque :** Les mises à jour régulières sont effectuées comme prévu.


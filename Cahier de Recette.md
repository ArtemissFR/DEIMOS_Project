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

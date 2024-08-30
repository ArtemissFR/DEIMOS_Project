
---
# DEIMOS PROJECT

<p align="center">
  <img src="Documentation/DEIMOS.png" alt="Deimos Icon" width="700"/>
</p>

## Projet de Configuration Ansible pour Linux selon les Recommandations de l'ANSSI

ReadMe : [Francais](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/README_FR.md) | [English](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/README_ENG.md)

### Introduction

Bienvenue dans ce projet de configuration Ansible visant à sécuriser une machine AlmaLinux 9 en suivant les recommandations de l'Agence nationale de la sécurité des systèmes d'information (ANSSI). La sécurité informatique est devenue une priorité incontournable, et il est crucial de s'assurer que nos systèmes sont protégés contre les diverses menaces actuelles.

Ce projet a pour objectif de fournir un guide et un ensemble de scripts Ansible permettant d'automatiser la mise en place de configurations sécurisées sur des machines tournant sous AlmaLinux 9. En adoptant les conseils de l'ANSSI, nous visons à renforcer la sécurité de nos infrastructures tout en facilitant la gestion et la maintenance de nos systèmes.

### Comment réaliser les prérequis SSH ?

1. [Alma Linux] Donner un mot de passe au compte Root :
   
   ```bash
   passwd root
   ```
2. [Alma Linux] Générer une paire de clés SSH :
   
   ```bash
   ssh-keygen
   ```

3. [Alma Linux] Autoriser la connexion via Root :
   
   ```bash
   nano /etc/ssh/sshd_config
   ```
   ```bash
   Modifier : "PermitRootLogin Yes"
   ```
   
4. [Ansible] Configurer SSH :
   
   ```bash
   ssh-keygen
   ```
   ```bash
   ssh-copy-id root@{ip de la machine alma linux}
   ```

### Comment utiliser le Playbook ?

1. Télécharger le dépots :
   
   ```bash
   git clone https://github.com/ArtemissFR/DEIMOS_Project
   cd DEIMOS_Project
   ```

2. Configurer l'hôte distant :
   
   ```bash
   nano hosts.ini
   ```

3. Lancer le playbook :
   
   ```bash
   ansible-playbook Launch_Playbook.yml
   ```

4. Lancer le playbook (localement) :
   
   ```bash
   ansible-playbook Launch_Playbook_Locally.yml
   ```

---

## Partie détaillée :

### Rôles

| Nom du Rôle | Description |
|-------------|-------------|
| **Language_Selection**  | Un rôle permettant de choisir la langue utilisée pour la suite du playbook. |
| **Notify** | Un rôle à simple but d'information pour l'utilisateur. |
| **Gather_Facts**  | Un rôle pour récupérer et afficher des informations sur le matériel de la machine distante. |
| **ANSSI_Configuration**  | Un rôle pour configurer des paramètres afin de correspondre aux recommandations de l'ANSSI. |


### Détails des Rôles
#### Rôle "Language_Selection" :
| Tâches | 
|--------|
| - Proposition d'un choix de la langue |

#### Rôle "Notify" :
| Tâches | 
|--------|
| - Affichage du noms des membres créateurs du Playbook |
| - Affichage du lien vers le Projet |

#### Rôle "Gather_Facts" :
| Tâches | 
|--------|
| - Récupération et affichage des informations sur le système d'exploitation |
| - Récupération et affichage des informations sur l'espace disque |
| - Récupération et affichage des informations sur la mémoire |
| - Récupération et affichage des informations sur le processeur |
| - Récupération et affichage des informations sur les processus en cours |
| - Récupération et affichage des informations sur le réseau |

#### Rôle "ANSSI_Configuration" :
| Sous-Catégories | Tâches | 
|-----------------|--------|
| *Hardware Configuration* | - Activation du Boot sécurisé UEFI |
| ~ | - Remplacement des clés préchargées |
| *Linux Kernel Configuration* | - Protection du système de commande Kernel |
| ~ | - Activation IOMMU |
| ~ | - Désactivation des modules de chargement Kernel |
| ~ | - Configuration du Kernel Yama |
| ~ | - Configuration du Kernel |
| *Syteme Configuration* | - Installation des packages de base |
| ~ | - Installation des packages de Réseaux |
| ~ | - Installation des packages de Bureautique |
| ~ | - Ajout des dépots de confiance |
| ~ | - Mise a jour de tout les paquets |
| ~ | - Suppression des paquets inutiles |
| ~ | - Activation de l'automatisation des mises a jour |
| *Services Configuration* | - Désactivation des services inutiles |
| ~ | - Mise en place de la conteneurisation (not working) |
| ~ | - Configuration des paramètre SSH |
| ~ | - Configuration Auditd |

#### Rôle "ANSSI_Configuration" :
| Catégories | Script | Tâches | 
|------------|--------|--------|
| **Hardware Configuration** | *["R3_UEFI_Secure_Boot.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/4-hardware_configuration/R3_UEFI_Secure_Boot.yml)* | Ce script Yaml installe d'abord le paquet mokutil sur un système. Ensuite, il vérifie si le démarrage sécurisé UEFI est activé. Si ce n'est pas le cas, il tente d'activer la validation pour le démarrage sécurisé UEFI. |
| **Hardware Configuration** | *["R4_replace_preloaded_keys.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/4-hardware_configuration/R4_replace_preloaded_keys.yml)* | Ce script Yaml sert à gérer les entrées de démarrage EFI sur un système Linux. Il commence par s'assurer que l'outil efibootmgr est installé. Ensuite, il crée une nouvelle entrée de démarrage EFI avec une commande personnalisée, et supprime une ancienne entrée de démarrage si elle existe. Il vérifie ensuite que la nouvelle entrée a bien été créée et affiche la sortie de la commande efibootmgr pour validation. |
| **Linux Kernel Configuration** | *["R6_Protect_kernel_command_line.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/5-linux_kernel_configuration/R6_Protect_kernel_command_line.yml)* | Ce script Yaml assure la sécurité et la configuration de certains fichiers essentiels au démarrage du système. Il commence par s'assurer que le paquet dracut est installé, ce qui est crucial pour la gestion des images d'initramfs. Ensuite, il ajuste les permissions des fichiers de configuration GRUB (/boot/grub2/grub.cfg et /boot/efi/EFI/almalinux/grub.cfg) pour qu'ils ne soient lisibles que par l'utilisateur root, renforçant ainsi la sécurité en limitant l'accès à ces fichiers sensibles. Enfin, il force la mise à jour de l'image d'initramfs avec la commande dracut -f, garantissant que les modifications apportées à la configuration du système soient prises en compte au prochain démarrage. |
| **Linux Kernel Configuration** | *["R7_Enable_IOMMU.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/5-linux_kernel_configuration/R7_Enable_IOMMU.yml)* | Ce script Yaml sert à activer l'IOMMU (Input-Output Memory Management Unit) sur un serveur. Il modifie le fichier de configuration de GRUB pour ajouter l'option iommu=force, met à jour la configuration de GRUB pour que les changements prennent effet, et redémarre ensuite le serveur pour appliquer ces modifications. |
| **Linux Kernel Configuration** | *["R10_Disable_loading_kernel_modules.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/5-linux_kernel_configuration/R10_Disable_loading_kernel_modules.yml)* | Ce script Yaml sert à désactiver le chargement des modules du noyau sur un système Linux en modifiant le fichier de configuration /etc/sysctl.conf. Il ajoute ou modifie une ligne pour définir kernel.modules_disabled à 1, ce qui empêche le chargement de nouveaux modules du noyau. Ensuite, il applique immédiatement cette modification en rechargeant la configuration des paramètres système avec la commande sysctl -p. |
| **Linux Kernel Configuration** | *["R11_Kernel_yama_configuration.yml"](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/roles/ANSSI_Configuration/tasks/5-linux_kernel_configuration/R11_Kernel_yama_configuration.yml)* | Ce script Yaml sert à configurer et appliquer un paramètre de sécurité pour le noyau Linux en utilisant Yama, un module de sécurité. Il crée un fichier de configuration (/etc/sysctl.d/99-yama.conf) pour activer la protection ptrace (en la définissant à 1), applique les paramètres de sysctl, puis vérifie que la configuration de Yama est bien en place et appliquée correctement. Cela renforce la sécurité du système en limitant la capacité des processus à tracer d'autres processus, réduisant ainsi les risques de certaines attaques. |
| **Linux Kernel Configuration** | *"R11_Kernel_yama_configuration.yml"* | Ce script Yaml sert à configurer et appliquer un paramètre de sécurité pour le noyau Linux en utilisant Yama, un module de sécurité. Il crée un fichier de configuration (/etc/sysctl.d/99-yama.conf) pour activer la protection ptrace (en la définissant à 1), applique les paramètres de sysctl, puis vérifie que la configuration de Yama est bien en place et appliquée correctement. Cela renforce la sécurité du système en limitant la capacité des processus à tracer d'autres processus, réduisant ainsi les risques de certaines attaques. |

---
[Document des recommandations de l'ANSSI](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/ANSSI/fr_np_linux_configuration-v2.0.pdf)

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/fr/thumb/3/31/Anssi.png/800px-Anssi.png" alt="Deimos Icon" width="300"/>
</p>

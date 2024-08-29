
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
| **Notify**  | Un rôle à simple but d'information pour l'utilisateur. |
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

---
[Document des recommandations de l'ANSSI](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/ANSSI/fr_np_linux_configuration-v2.0.pdf)

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/fr/thumb/3/31/Anssi.png/800px-Anssi.png" alt="Deimos Icon" width="300"/>
</p>

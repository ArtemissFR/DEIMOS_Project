
---
# DEIMOS PROJECT

<p align="center">
  <img src="DEIMOS.png" alt="Deimos Icon" width="600"/>
</p>

## Projet de Configuration Ansible pour Linux selon les Recommandations de l'ANSSI

ReadMe file : [Francais](https://github.com/ArtemissFR/DEIMOS_Project/Documentation/README_FR.md) | [English](https://github.com/ArtemissFR/DEIMOS_Project/Documentation/README_ENG.md)

### Introduction

Bienvenue dans ce projet de configuration Ansible visant à sécuriser une machine AlmaLinux 9 en suivant les recommandations de l'Agence nationale de la sécurité des systèmes d'information (ANSSI). La sécurité informatique est devenue une priorité incontournable, et il est crucial de s'assurer que nos systèmes sont protégés contre les diverses menaces actuelles.

Ce projet a pour objectif de fournir un guide et un ensemble de scripts Ansible permettant d'automatiser la mise en place de configurations sécurisées sur des machines tournant sous AlmaLinux 9. En adoptant les conseils de l'ANSSI, nous visons à renforcer la sécurité de nos infrastructures tout en facilitant la gestion et la maintenance de nos systèmes.

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

### Rôles

| Nom du Rôle | Description |
|-------------|-------------|
| **Language_Selection**  | Un rôle permettant de choisir la langue utilisée pour la suite du playbook. |
| **Gather_Facts**  | Un rôle pour récupérer et afficher des informations sur le matériel de la machine distante. |
| **Packages_Installation**  | Un rôle pour installer des packages recommandés sur la machine distante. |
| **Security_Configuration**  | Un rôle pour configurer des paramètres afin de correspondre aux recommandations de l'ANSSI. |


### Détails des Rôles
#### Rôle "Language_Selection" :
| Tâches | 
|--------|
| - Proposition d'un choix de la langue |

#### Rôle "Gather_Facts" :
| Tâches | 
|--------|
| - Récupération et affichage des informations sur le système d'exploitation |
| - Récupération et affichage des informations sur l'espace disque |
| - Récupération et affichage des informations sur la mémoire |
| - Récupération et affichage des informations sur le processeur |
| - Récupération et affichage des informations sur les processus en cours |
| - Récupération et affichage des informations sur le réseau |

#### Rôle "Packages_Installation" :
| Tâches | 
|--------|
| - Mise à jour des paquets présents sur le système |
| - Installation de paquets de base nécessaires |
| - Installation de paquets de bureautique |
| - Suppression des paquets inutiles pour optimiser l'espace et les performances du système |

---

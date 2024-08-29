
---
# DEIMOS PROJECT

<p align="center">
  <img src="DEIMOS.png" alt="Deimos Icon" width="700"/>
</p>

## Ansible Configuration Project for Linux According to ANSSI Recommendations

ReadMe : [Francais](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/README_FR.md) | [English](https://github.com/ArtemissFR/DEIMOS_Project/blob/main/Documentation/README_ENG.md)

### Introduction

Welcome to this Ansible configuration project aimed at securing an AlmaLinux 9 machine by following the recommendations of the French National Cybersecurity Agency (ANSSI). Cybersecurity has become an essential priority, and it is crucial to ensure that our systems are protected against various current threats.

The objective of this project is to provide a guide and a set of Ansible scripts to automate the implementation of secure configurations on machines running AlmaLinux 9. By adopting ANSSI's recommendations, we aim to strengthen the security of our infrastructures while facilitating the management and maintenance of our systems.

---

### How to Set Up SSH Prerequisites

1. **[Alma Linux] Set a Password for the Root Account:**
   
   ```bash
   passwd root
   ```

2. **[Alma Linux] Generate an SSH Key Pair:**
   
   ```bash
   ssh-keygen
   ```

3. **[Alma Linux] Allow Root Login via SSH:**
   
   ```bash
   nano /etc/ssh/sshd_config
   ```
   ```bash
   Modify: "PermitRootLogin Yes"
   ```

4. **[Ansible] Configure SSH:**
   
   ```bash
   ssh-keygen
   ```
   ```bash
   ssh-copy-id root@{Alma Linux machine IP}
   ```

### How to Use the Playbook?

1. **Download the Repository:**
   
   ```bash
   git clone https://github.com/ArtemissFR/DEIMOS_Project
   cd DEIMOS_Project
   ```

2. **Configure the Remote Host:**
   
   ```bash
   nano hosts.ini
   ```

3. **Run the Playbook:**
   
   ```bash
   ansible-playbook Launch_Playbook.yml
   ```

4. **Run the Playbook (Locally):**
   
   ```bash
   ansible-playbook Launch_Playbook_Locally.yml
   ```

---

## Detailed Section:

### Roles

| Role Name              | Description |
|------------------------|-------------|
| **Language_Selection** | A role allowing the selection of the language used for the rest of the playbook. |
| **Notify**             | A role solely for informing the user. |
| **Gather_Facts**       | A role to gather and display information about the hardware of the remote machine. |
| **ANSSI_Configuration**| A role to configure settings according to ANSSI recommendations. |


### Role Details
#### "Language_Selection" Role:
| Tasks | 
|-------|
| - Propose a language selection |

#### "Notify" Role:
| Tasks | 
|-------|
| - Display the names of the playbook creators |
| - Display the link to the Project |

#### "Gather_Facts" Role:
| Tasks | 
|-------|
| - Gather and display operating system information |
| - Gather and display disk space information |
| - Gather and display memory information |
| - Gather and display processor information |
| - Gather and display running processes information |
| - Gather and display network information |

#### "ANSSI_Configuration" Role:
| Sub-Categories           | Tasks | 
|--------------------------|-------|
| *Hardware Configuration* | - Enable UEFI Secure Boot |
| ~                        | - Replace preloaded keys |
| *Linux Kernel Configuration* | - Protect Kernel command system |
| ~                        | - Enable IOMMU |
| ~                        | - Disable Kernel module loading |
| ~                        | - Configure Kernel Yama |
| ~                        | - Configure the Kernel |
| *System Configuration*   | - Install basic packages |
| ~                        | - Install network packages |
| ~                        | - Install office packages |
| ~                        | - Add trusted repositories |
| ~                        | - Update all packages |
| ~                        | - Remove unnecessary packages |
| ~                        | - Enable automatic updates |
| *Services Configuration* | - Disable unnecessary services |
| ~                        | - Implement containerization (not working) |
| ~                        | - Configure SSH parameters |
| ~                        | - Configure Auditd |

---

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/fr/thumb/3/31/Anssi.png/800px-Anssi.png" alt="Deimos Icon" width="300"/>
</p>

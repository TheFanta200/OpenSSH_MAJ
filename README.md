# Prérequis

Pour exécuter cette procédure, le compte utilisé doit être `root` ou avoir des privilèges `sudo`.

# Systèmes d'exploitation validés

- **Debian** : Toutes les versions
- **Ubuntu** : Toutes les versions sauf 24.04
- **RedHat** : Version 9

# Étapes de configuration

1. Copier l'intégralité du fichier Ansible dans le répertoire `/etc/ansible`.

2. Crée un fichier ".ansible_vault_password" avec un mdp dans le dossier `/root/`.

3. Créer un fichier vault pour sécuriser tous les comptes utilisés :

   ```sh
   ansible-vault create global_vars/Linux.yml
   ```

4. Saisie et modification des informations suivantes dans le fichier vault :

    ```yaml
    ### Credential Linux ####
    ansible_ssh_user: "XXXXX"
    ansible_ssh_pass: "XXXXX"
    ansible_become_pass: "XXXXX"

    ### Version SSH ###
    ### Valeur en float : 1.1 #
    min_ssh_version: 8.5
    max_ssh_version: 9.7

    ### Valeur SSH Install ###
    openssh_version: "9.8p1"
    openssh_url: "https://cdn.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-{{ openssh_version }}.tar.gz"
    openssh_tar: "/tmp/openssh-{{ openssh_version }}.tar.gz"
    openssh_src_dir: "/tmp/openssh-{{ openssh_version }}"
    ```

5. Configuration des hôtes dans le fichier `hosts`.

6. Lancement du playbook :

    ```bash
    ansible-playbook playbook.yml 
    ```

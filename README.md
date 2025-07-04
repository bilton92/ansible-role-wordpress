# Rôle Ansible : wordpress

Ce rôle Ansible permet d’installer et configurer un site **WordPress** avec une base de données **MariaDB** sur des systèmes **Ubuntu/Debian** ou **Rocky Linux/RedHat**. Il prend en charge les différences de gestion de paquets, de services, et de répertoires entre distributions.

---

## 🧰 Prérequis

- Ansible ≥ 2.10
- Accès root (ou sudo) sur les hôtes cibles
- Une connexion SSH fonctionnelle

---

## ⚙️ Variables configurables

| Variable               | Description                                             | Valeur par défaut        |
|------------------------|---------------------------------------------------------|---------------------------|
| `db_name`              | Nom de la base de données MariaDB                       | `wordpress_db`            |
| `db_user`              | Utilisateur MariaDB                                     | `wp_user`                 |
| `db_password`          | Mot de passe de l’utilisateur MariaDB                   | `wp_pass`                 |
| `wp_url`               | URL de téléchargement de WordPress                      | Voir `defaults/main.yml`  |
| `wp_install_dir`       | Répertoire d’installation de WordPress                  | `/var/www/html/wordpress` |
| `wp_config_template`   | Chemin vers le template `wordpress.conf.j2`             | `templates/wordpress.conf.j2` |
| `web_user`             | Utilisateur du serveur web (`www-data` ou `apache`)     | Dépend de l’OS            |
| `httpd_service`        | Nom du service web (`apache2` ou `httpd`)               | Détecté automatiquement   |

---

## 📁 Structure du rôle

wordpress_role_bilal
|
|-- README.md
|-- defaults
|   `-- main.yml
|-- files
|-- handlers
|   `-- main.yml
|-- meta
|   `-- main.yml
|-- tasks
|   `-- main.yml
|-- templates
|   |-- wordpress.conf.j2
|   `-- wp-config.php.j2
|-- tests
|   |-- inventory
|   `-- test.yml
`-- vars
    `-- main.yml

## 🚀 Utilisation

### 1. Depuis un playbook

```yaml
- name: Déploiement WordPress
  hosts: all
  become: true
  roles:
    - wordpress_role_bilal
```
### 2. Depuis Ansible Galaxy

ansible-galaxy install bilton92.wordpress

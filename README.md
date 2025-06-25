
# SAE 4.01 – Développement d'une application complexe

## 🎯 Objectif du projet

Ce projet vise à moderniser la **gestion de la ludothèque de l’Université Sorbonne Paris Nord**, qui regroupe plus de **17 000 jeux de société**, certains datant du XIXe siècle. L’objectif est de remplacer l'ancien système de gestion sous Excel par une **application web robuste et évolutive**, accompagnée d’une **base de données relationnelle** et de **scripts de traitement automatisés**.

---

## 🧱 Structure du projet

```plaintext
SAE-S4-main/
├── Content/              # Contient CSS et images
│   ├── CSS/
│   └── img/
├── Controllers/          # Logique PHP et PHPMailer
│   └── PHPMailer-master/
├── Models/               # Modèles de données
├── Views/                # Vues HTML / PHP
├── database_jeux.sql     # Script SQL de création de la BDD
├── README.md             # Documentation
```

---

## ⚙️ Fonctionnalités principales

- 🔍 **Recherche avancée** dans la ludothèque
- 📦 **Gestion des jeux et des exemplaires physiques**
- 📊 **Suivi des prêts et des emprunteurs**
- 👤 **Gestion des utilisateurs et rôles (lecteur, gestionnaire, admin)**
- 🧹 **Scripts Python** de nettoyage et préparation des données
- 🖼️ **Intégration prévue d’illustrations de jeux**

---

## 🛠️ Technologies utilisées

- **Backend** : PHP
- **Base de données** : MySQL
- **Frontend** : HTML, CSS, JavaScript
- **Scripts** : Python (pandas)
- **Modélisation** : Modèle Entité-Association amélioré, respect des 3FN & BCNF

---

## 🧠 Modélisation de la base de données

Le modèle relationnel permet :
- La gestion des **jeux de société** (multi-auteurs, éditeurs, catégories, mécanismes)
- Le suivi des **exemplaires physiques** via la table `boite`
- La gestion des **prêts**, **emprunteurs** et **utilisateurs** avec **droits différenciés**

### Schéma relationnel simplifié :

```sql
JEUX(jeu_id, titre, ...), BOITE(boite_id, jeu_id, ...),
AUTEUR, EDITEUR, CATEGORIE, MECANISME, ...
PRET, EMPRUNTEUR, PERSONNE, ROLE, PERSONNEROLE
```

> 📌 Le schéma respecte les formes normales jusqu’à la **BCNF**.

---

## 🚀 Installation locale avec WAMP

### Prérequis :
- [WAMP Server](https://www.wampserver.com/)
- [Python 3.x](https://www.python.org/) + `pip`
- Navigateur web moderne
- MySQL intégré avec WAMP (v8.0 recommandé)

---

### Étapes :

#### 1. Cloner le projet
```bash
git clone git clone https://github.com/votre_projet/SAE-S4-main.git

```

#### 2. Placer les fichiers
Copier le dossier `SAE-S4-main/` dans le répertoire suivant :
```
C:/wamp64/www/app/
```

#### 3. Créer et configurer la base de données

1. Lancer **WAMP Server** (icône verte)
2. Accéder à [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
3. Créer une base de données, ex. `ludotheque`
4. Importer :
   - `sql/creation_tables.sql`
   - `sql/script_insertion.sql`

##### ⚠️ Si vous utilisez `LOAD DATA INFILE` :
- Déplacer `inventaire.csv` dans :
  ```
  C:/wamp64/tmp/inventaire.csv
  ```
- Modifier le chemin dans `creation_tables.sql` :
  ```sql
  LOAD DATA INFILE 'C:/wamp64/tmp/inventaire.csv' INTO TABLE ...
  ```
- Ajouter dans `my.ini` (section `[mysqld]`) :
  ```ini
  secure-file-priv=""
  ```
- Redémarrer MySQL depuis WAMP

#### 4. Configurer les identifiants MySQL
Dans `app/identifiants/identifiant.php` :
```php
<?php
$dsn = 'mysql:host=localhost;dbname=ludotheque';
$username = 'root';
$password = ''; // vide par défaut sous WAMP
?>
```

#### 5. Lancer le serveur
Accéder au site :
```
http://localhost/SAE-S4/
```

## 👨‍💻 Équipe

Groupe Dyotech (BUT2 Informatique 2024/2025) :
- **ABDOUL Sajith**
- **MAHDJOUB Ciffedinne**
- **GNANAPRAGASAM Royston**
- **KESSAVANNE Dhanoush**

---

## 📄 Rapport & Ressources


- [Version Drive s301(si lien expiré)](https://drive.google.com/drive/folders/1o0HUy2CeCfMBVKCZ8CLMnOgTMujFHPqs?usp=drive_link)

---

## ✅ À venir / évolutions possibles

- 🔍 Recherche filtrée multi-critères
- 🗑️ Suppression de jeux
- 🖼️ Ajout d’images pour chaque jeu
- 📑 Suivi des logs et connexions

---

## 📢 Remarque

Ce projet a été développé dans le cadre de la SAE 4.01 de BUT2 Informatique. Il vise à illustrer la conception, le développement et la mise en production d’une application complète à partir d’un existant.

# 🏠 Omnes Immobilier

Application web d'agence immobilière développée en PHP et MySQL, réalisée en équipe de quatre lors du projet « piscine » de l'ECE Paris (mai-juin 2024).

Le site met en relation des **clients** à la recherche d'un bien avec les **agents immobiliers** de l'agence, sous la supervision d'un **administrateur**. Il couvre tout le parcours : consultation des biens, recherche multicritère, prise de rendez-vous, messagerie et paiement.


## ✨ Fonctionnalités

### Pour les visiteurs et clients
- **Catalogue de biens** : parcourir l'ensemble des propriétés, chacune avec sa page détaillée (photos, adresse, prix, agent référent)
- **Recherche multicritère** : filtrer par type de bien, ville, description et fourchette de prix, ou rechercher un agent par son nom
- **Inscription et connexion**, avec un espace personnel « Mon compte »
- **Prise de rendez-vous** avec un agent, via une grille de créneaux horaires disponibles, et annulation possible
- **Messagerie** : discussion directe avec un agent et historique des conversations
- **Paiement des honoraires** : saisie des informations de carte et étape d'authentification (paiement simulé)

### Pour les agents
- Tableau de bord personnel avec leurs rendez-vous
- Gestion de leurs disponibilités
- Réponse aux messages des clients
- Profil public avec photo et CV

### Pour l'administrateur
- Ajout, modification et suppression des agents
- Ajout et gestion des biens immobiliers
- Création d'autres comptes administrateurs

## 🛠️ Technologies

| Couche | Technologies |
|---|---|
| Back-end | PHP (mysqli, requêtes préparées, sessions) |
| Base de données | MySQL (11 tables) |
| Front-end | HTML, CSS, JavaScript (requêtes asynchrones avec `fetch`) |
| Environnement | WAMP / XAMPP, phpMyAdmin |
| Collaboration | Git et GitHub (plus de 260 commits à quatre) |

### Modèle de données

La base `pj_piscine` s'articule autour des tables suivantes : `client`, `agent`, `admin`, `biens`, `rdv`, `dispo_agents`, `dispo_agents_heure_par_heure`, `communication` (messagerie), `consultations`, `infos_financieres` et `test_paiement`.

## 🚀 Installation

1. Installez un serveur local : [XAMPP](https://www.apachefriends.org/) ou [WAMP](https://www.wampserver.com/).
2. Clonez le dépôt dans le dossier web du serveur (`htdocs` pour XAMPP, `www` pour WAMP) :
   ```bash
   git clone https://github.com/bnvala/WD_Alice_Edouard_Chloe_Victor.git
   ```
3. Démarrez Apache et MySQL, ouvrez phpMyAdmin et importez le fichier `pj_piscine.sql`, qui crée la base et ses données.
4. Si besoin, adaptez les identifiants de connexion dans `db.php` (par défaut : utilisateur `root`, sans mot de passe).
5. Ouvrez [http://localhost/WD_Alice_Edouard_Chloe_Victor/accueil.php](http://localhost/WD_Alice_Edouard_Chloe_Victor/accueil.php).

## 📁 Organisation du code

```
├── accueil.php, toutparcourir.php, recherche.php   # Pages publiques
├── form.php, traitement_co.php, inscription_client.php   # Authentification
├── mon_compte_*.php                                 # Espaces client, agent, admin
├── creneaux.php, formrdv.php, traitement_rdv.php    # Prise de rendez-vous
├── chat.php, mes_messages.php, historique_message.php   # Messagerie
├── paiement.php, verif_paiement.php                 # Paiement
├── gerer_agents.php, gerer_biens.php, ajouter_*.php # Administration
├── wrapper.php                                      # En-tête et navigation communs
├── pages_biens/                                     # Pages de détail des biens
├── photos_biens/, photos_agents/, cv_agents/        # Médias
├── pj_piscine.sql                                   # Script de la base de données
└── db.php                                           # Connexion à la base
```

## 🔭 Pistes d'amélioration

Ce projet a été réalisé en une semaine dans un cadre pédagogique. Avec le recul, voici ce que nous améliorerions pour une mise en production :

- **Sécurité des mots de passe** : les hacher avec `password_hash()` / `password_verify()` au lieu de les stocker en clair
- **Données bancaires** : ne jamais stocker le CVV, et déléguer le paiement à un prestataire spécialisé (Stripe, par exemple)
- **Requêtes SQL** : généraliser les requêtes préparées, déjà utilisées dans la majorité du code, à la recherche multicritère
- **Architecture** : centraliser la connexion à la base dans `db.php` et les identifiants dans des variables d'environnement, et générer les pages de biens dynamiquement à partir d'un seul modèle plutôt qu'un fichier par bien
- **Qualité** : ajouter des tests et un linter, et retirer les fichiers de test

## 👥 Équipe

Projet réalisé par **Alice, Edouard, Chloé et Victor**, étudiants à l'ECE Paris.

| Membre | Contributions principales |
|---|---|
| Alice | *à compléter* |
| [Edouard](https://github.com/Edouardmnt) | Messagerie client-agent, recherche multicritère, pages des biens, en-tête et navigation, espace client |
| Chloé | *à compléter* |
| Victor | *à compléter* |

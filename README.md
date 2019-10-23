# Challenge : Découverte SQL

## Création base de données (BDD) et tables

### 1. Analyse & Réflexion :mag_right:

**Concevoir la BDD :**

- une base de données `blog`
- une table `auteurs`
- une table `articles`
- une table `categories`
- attention, on oublie pas de tout nommer en anglais :grin:

**Description des tables :**

#### `auteurs`
- Nom
- Image (photo)
- Adresse e-mail

#### `articles`
- Titre de l'article
- Résumé
- Corps du texte
- Date et heure de publication
- Nombre de visionnages
- Auteur
- Catégorie

#### `categories`
- Intitulé

### 2. Modèle Conceptuel de Données :page_facing_up:

:pencil: À partir de cette description, **modéliser les entités et leurs associations dans un MCD** (avec [Mocodo](http://mocodo.wingi.net/))

### 3. Dictionnaire de données :notebook:

|Champ|Type|Spécificités|Description|
|-|-|-|-|
|nom_du_champ|VARCHAR(255)|NULL, valeur par défaut, INDEX, etc.|Que contient ce champ, si besoin de préciser.|
|etc.|...|...|...|

Normalement, à partir des informations ci-dessus (1. et 2.) et des fiches récap, tu devrais être capable de créer le **dictionnaire de données**.  
Mais, tu as de la chance, le **dictionnaire de données** est déjà créé et partiellement renseigné dans le fichier `structure-donnees.md`. 

:pencil: Le type de chaque champs n'est pas assez précis dans le **dictionnaire de données**. A toi de définir un type précis MySQL (INT(11), VARCHAR(255), etc.).

### 4. Création :hammer:

Une fois tes tables définies, crée-les dans MySQL à l'aide de phpMyAdmin.  

:pencil:  **Créer via phpMyAdmin** la base de données et les 3 tables précédemment décrites.

:bulb: **Mega Bonus** Ajouter, si nécessaire, un champ permettant d'établir la liaison/relation/association entre 2 tables (Foreign Key liée à la Primary Key)

## Insertion de données :pencil2:
Intégrer des données via l'interface de PMA.

:pencil:  **Insérer des données d'exemple** (Le fichier `contenus.md` en contient déjà, intégre-les ils te serviront à comprendre le type des champs attendu, puis n'hésite pas à en ajouter d'autres).

## Requêtes SQL :computer:

:pencil: **Écrire les requêtes SQL** permettant d'obtenir les résultats suivants, reporter les requêtes SQL dans un fichier `requetes.md` _(à pusher)_.

> Tu devrais avoir un minimum de données dans tes tables pour que la requête soit pertinente.

- **Auteurs**
    - Lister les auteurs
- **Articles**
    - Lister tous les articles

## Bonus SQL

C'est le moment d'apprendre seul à utiliser le langage SQL.  
Tu as de la chance, il y a une doc super bien expliquée et français ! :tada: => https://sql.sh/

:pencil: **Écrire les requêtes SQL** permettant d'obtenir les résultats suivants, reporter les requêtes SQL dans un fichier `requetes.md` _(à pusher)_.


- **Auteurs**
    - Lister les auteurs par ordre alphabétique (sur le nom) ([doc](https://sql.sh/cours/order-by))
    - Lister les auteurs dont l'e-mail contient _@gmail.com_ ([doc](https://sql.sh/cours/where/like/wildcards))
    - Lister les auteurs qui n'ont pas d'image de profil ([doc](https://sql.sh/cours/where/is))
- **Articles**
    - Lister le titre et la date de publication de tous les articles ([doc](https://sql.sh/cours/select))
    - Afficher le titre d'un article en particulier (en passant l'`id` de l'article) ([doc](https://sql.sh/cours/where))
    - Trier par ordre décroissant tous les articles par la date de publication ([doc](https://sql.sh/cours/order-by))
    - Compter le nombre d'articles ([doc](https://sql.sh/fonctions/agregation/count)) et renommer la colonne en `nbArticles` ([doc](https://sql.sh/cours/alias))

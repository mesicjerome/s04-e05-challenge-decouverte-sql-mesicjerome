# Requêtes

## Auteurs

### Lister les auteurs

```sql
SELECT *
FROM `author`;
```

### Lister les auteurs par ordre alphabétique (sur le nom)

```sql
SELECT *
FROM `author`
ORDER BY `name` ASC;
```

### Lister les auteurs dont l'e-mail contient @gmail.com

```sql
SELECT *
FROM `author`
WHERE `email` LIKE '%@gmail.com%'; -- % devant et derrière car "contient" et pas "se termine par"
```

### Lister les auteurs qui n'ont pas d'image de profil

```sql
SELECT *
FROM `author`
WHERE `image` IS NULL;
```

```sql
SELECT *
FROM `author`
WHERE ISNULL(`image`);
```

## Articles

### Lister tous les articles

```sql
SELECT *
FROM `post`;
```

### Lister le titre et la date de publication de tous les articles

```sql
SELECT
    `title`,
    `publish_date`
FROM `post`
```

### Afficher le titre d'un article en particulier (en passant l'id de l'article)

```sql
SELECT `title`
FROM `post`
WHERE `id` = 1;
```

### Trier par ordre décroissant tous les articles par la date de publication

```sql
SELECT *
FROM `post`
ORDER BY `publish_date` DESC
```

## En option, démo de requêtes avec relations

### Lister tous les articles avec leur nom d'auteur et l'intitulé de la catégorie

```sql
SELECT
    `post`.*,
    `author`.`name` AS author_name,
    `category`.`name` AS category_name
FROM `post`
-- Je viens joindre ma table `author` à la requête de manière à pouvoir afficher le nom de l'auteur
-- J'ai fait en sorte de lier la table post à la table author avec une clé étrangère reprennant l'id de l'auteur (clé primaire de l'auteur)
-- Donc je spécifie dans quel cas un post est lié à un auteur dans ma jointure avec ON
-- Un post est lié à un auteur quand post.author_id (clé étrangère) est égal à author.id (clé primaire de author)
INNER JOIN `author` ON `author`.`id` = `post`.`author_id` -- `base_de_donnees`.`table`.`colonne`
INNER JOIN `category` ON `category`.`id` = `post`.`category_id`
```

### Afficher tous les articles dont la catégorie commence par M

```sql
SELECT `post`.*
FROM `post`
INNER JOIN `category`
ON
    `category`.`id` = `post`.`category_id`
    AND `category`.`name` LIKE 'M%';
```

```sql
SELECT `post`.*
FROM `post`
INNER JOIN `category` ON `category`.`id` = `post`.`category_id`
WHERE `category`.`name` LIKE 'M%';
```

### Lister tous les articles dont l'auteur est donné (via son id)

```sql
SELECT `post`.*
FROM `post`
INNER JOIN `author` ON `author`.`id` = `post`.`author_id`
WHERE `author`.`id` = 1;
```

Attention la requête suivante ne fonctionne pas :

```sql
SELECT *
FROM `post`
INNER JOIN `author` ON `author`.`id` = 1;
```

Car elle liera l'auteur qui a pour id 1 à tous nos articles

### Lister le nom de l'auteur des articles dont la catégorie est donnée (via son id)

```sql
SELECT DISTINCT `author`.* -- Si un auteur a écrit plusieurs articles dans la catégorie, DISTINCT va nous permettre de ne le retourner qu'une seule fois
FROM `author`
INNER JOIN `post` ON `post`.`author_id` = `author`.`id` -- la table post nous sert uniquement pour "joindre" un auteur à une catégorie
INNER JOIN `category` ON `category`.`id` = `post`.`category_id`
WHERE `category`.`id` = 1;
```

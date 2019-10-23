# Dictionnaire de données

## Auteurs (`author`)

|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|INT(10)|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|L'identifiant de notre auteur|
|name|VARCHAR(64)|NOT NULL|Le nom de l'auteur|
|image|VARCHAR(255)|NULL|L'avatar de l'auteur|
|email|VARCHAR(255)|NOT NULL, UNIQUE|L'e-mail de l'auteur|

## Catégories (`category`)

|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|INT(10)|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|L'identifiant de la catégorie|
|name|VARCHAR(32)|NOT NULL|Le nom de la catégorie|

## Articles (`post`)

|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|INT(10)|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|L'identifiant de l'article|
|title|VARCHAR(64)|NOT NULL|Le titre de l'article|
|summary|VARCHAR(255)|NOT NULL|Le résumé de l'article|
|content|TEXT|NOT NULL|Le contenu de l'article|
|publish_date|DATETIME|NOT NULL, DEFAULT CURRENT_TIMESTAMP|La date de publication de l'article|
|view_count|INT(10)|NOT NULL, UNSIGNED, DEFAULT 0|Le nombre de vues de l'article|

**DOCKERISER MON APPLICATION LARAVEL**
1. **Création le Dockerfile**

À la racine du projet, exécution de la commande ci-après:
```
touch Dockerfile
```
2. **Choisir l'image officielle docker qui servira de base**

Ce choix sera basé les besoins spéficifiques en termes d'environnement d'exécution du projet.
Il peut s'agir de :

- `php:7.4-fpm`
- `php:8.0-fpm`
- `php:8.1-fpm`
- ...

3. **Ajout de la ligne de l'image officielle au Dockerfile**
```
FROM php:8.1-fpm
```
4. **Ajout de la ligne d'installation des dépendances**
```
RUN apt-get update && apt-get install -y \ git \ zip \ unzip \ && docker-php-ext-install pdo pdo_mysql
```
5. **Ajout de la ligne de définition du répertoire de travail**

Le répertoire de travail est défini en fonction de vos exigences et de vos critères de customisation
```
WORDIR /var/www/html
```

6. **Ajout de la ligne de copie des fichier**
```
COPY . .
```

7. **Ajout de la ligne d'installation de composer**
```
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
```

8. **Ajout de la ligne d'exécution de composer dans le projet**
```
composer install
```

9. **Ajout de la ligne d'exposition du port pour le FPM**
```
EXPOSE 9000
```

10. **Ajout de la ligne d'exécution du serveur**
```
CMD ["php-fpm"]
```



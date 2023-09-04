* Connexion au Serveur

        ssh username@ip_address

* Entrez votre mot de passe de connexion


## Clonage du Projet

*  Changez de répertoire 

        cd www/

* Clonez le référentiel Git

        git clone https://github.com/.../...

* Si vous souhaitez renommer le répertoire du projet (Optionnel) 

        mv oldName newName 
        cd projectName (newName)

## Installation des Dépendances

* Installez les dépendances

        composer install

* Si Composer n'est pas déjà installé

        sudo apt-get install composer
        composer install

* Mettez à jour les dépendances (Optionnel)  

        composer update 

* Installer les dépendances NPM (Optionnel)

        npm install 



## Configuration des Variables d'Environnement

* Renommez le fichier .env.example en .env

        mv .env.example .env
        vi .env

    * Appuyez sur **`i`** pour entrer en mode `Insertion`.

    * Insérez la valeur de `DB_NAME` selon vos besoins.

    * Si vous avez besoin de changer le `nom d'utilisateur`, faites-le à ce stade.

    * Si vous avez besoin de changer le `mot de passe`, faites-le également.

    * Si vous avez besoin de modifier certaines `variables d'environnement`, vous pouvez le faire ici.

    * Appuyez sur la touche **`Esc`** pour quitter le mode `Insertion`.

    * Enregistrez vos modifications et quittez l'éditeur en tapant `:wq`** ou `:x` et en appuyant sur **`Entrée`**.

## Configuration de la Base de Données

---
* Connectez-vous à MySQL

        mysql -u username -p

* Entrez votre mot de passe MySQL 

    <font size=5> OU </font> 

* Connectez-vous à MySQL

        mysql -u root -p

---

* Entrez votre mot de passe MySQL (default=root)


* Créez la base de données
    
        Create database DB_NAME ;

* Quittez MySQL.
        
        exit


## Exécution des Migrations

* Exécutez les migrations Laravel pour créer la structure de base de données

    *       php artisan migrate

    *       php artisan route:list

    *       php artisan storage:link

    *       php artisan key:generate

    *       php artisan optimize



## Configuration du Virtual Host Apache

* Obtenez le chemin absolu

        pwd

* Accedez au dossier

        cd /etc/apache2/sites-available/

* Voir le contenu du dossier

        ls

* Copiez le fichier de configuration d'hôte virtuel existant pour créer un nouveau fichier

        sudo cp -r oldDomainName.conf newDomainName.conf

* Éditez le nouveau fichier de configuration

        sudo vi newDomainName.conf

    * Appuyez sur **`i`** pour entrer en mode "Insertion".

    * Modifiez la directive ServerName en remplaçant l'ancien nom de serveur par le nouveau nom de serveur avec la même `root` (radical).

    *  Modifiez la directive ServerAlias en remplaçant l'ancien nom de serveur par le nouveau nom de serveur sans `www`.

    * Modifiez la directive DocumentRoot pour qu'elle pointe vers le chemin absolu du projet, y compris le répertoire "public".

    * Laissez inchangée la première `Directory tag`

    * Modifiez le contenu de la deuxième `Directory tag` pour qu'il pointe également vers le chemin absolu du projet, y compris le répertoire `public`.

    * Modifiez la directive ErrorLog en utilisant un nom de fichier de journal d'erreurs personnalisé: `error.ServerAlias.log`

    * Modifiez la directive CustomLog en utilisant un nom de fichier de journal d'accès personnalisé: `access.ServerAlias.log `

    * Appuyez sur la touche **`Esc`** pour quitter le mode `Insertion`.

    * Pour enregistrer les modifications et quitter, tapez `:wq` ou `:x` et appuyez sur **`Entrée`**.

* Activez le nouveau virtual host

        sudo a2ensite newDomainName.conf

* Redémarrez Apache pour prendre en compte les modifications de configuration.

        sudo systemctl reload apache2



## Attribution des Permissions d'Exécution

        cd www/
        sudo chmod -R 777 projectName/
        sudo systemctl reload apache2



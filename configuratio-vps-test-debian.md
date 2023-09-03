**CONFIGURATION SERVEUR VPS AVEC OS-DEBIAN 10**

1. **Connexion au serveur via ssh**
- Entrez la commande
```
ssh username@ip_du_serveur
```
- Entrez le mot de passe

2. **Installation de `Git`**

Dans mon cas, j'exécute particulièrement des applications `PHP` donc j'installe la dernière version de `PHP`. Cette installation nécessite celle(l'installation) de `Git`.

```
sudo apt-get install git
```
3. **Installation de `PHP` depuis la source**

# cf-  https://github.com/php/php-src
- Mise à jour et  installation des dépendances
```
sudo apt-get update
sudo apt-get install build-essential libxml2-dev libssl-dev libbz2-dev libcurl4-openssl-dev libjpeg-dev libpng-dev libfreetype6-dev libmcrypt-dev libreadline-dev libzip-dev
```
- Installation des dépendances
```
sudo apt install -y pkg-config build-essential autoconf bison re2c \
                    libxml2-dev libsqlite3-dev
```

- Cloner le repo du php 
```
git clone https://github.com/php/php-src
```
- Accéder à la racine du dossier `php-src`
```
cd php-src
```

- Génération du fichier configure
```
./buildconf
```

- Exécution du fichier de configuration
```
configure --enable-debug
```

- Exécution de la commande make 
```
make -j4
```

- Exécution de la commande make test pour vérifier si les fichiers source sont bien installés
```
make test
```

- Exécution de la commande d'installation
```
sudo make install
```

- Vérification de la version de `PHP`
```
php -v
```

4. **Installation de `Composer`**
Exécution des commandes ci-après
- Mise à jour 
```
sudo apt update
sudo apt upgrade
```
- Installer `curl` si ce n'est pas encore installé
```
sudo apt install curl
```
- Installer l'extension `openssl` de PHP si ce n'est pas encore installé
- Accéder au sous-repertoire ext/openssl
```
cd php-src/ext/openssl
```
- Vérifier l'existence du fichier config.m4
```
ls
```
- Si au lieu de config.m4, vous avez config0.m4, faites 
```
mv config0.m4 config.m4
```
- Si vous avez le config.m4, faites
```
phpize
```

- Ensuite faites
```
./configure
```

- Et après
```
make 
```
- Sans oublier 
```
make test
```

- Et pour finir 
```
sudo make install
```

- Commandes d'installation
```
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

- Vérification de la version de `composer`
```
composer --version
```

4. **Installation de `Apache`**

- Mise à jour 
```
sudo apt update
```

- Installation d'apache
```
sudo apt install apache2
```

- Démarrage d'apache
```
sudo systemctl start apache2
```
- Activation d'apache pour démarrage automatique 
```
sudo systemctl enable apache2
```

- Vérification du statut
```
sudo systemctl status apache2
```

- Installation de `ufw` si ce n'est pas encore installé
```
sudo apt install ufw
```

- Autorisation de traffic sur le port 80
```
sudo ufw allow 80/tcp
```

5. **Installation de `MYSQL-SEVER`**
- Mise à jour 
```
sudo apt update
```
- Installation
```
sudo apt install mysql-server
```

- Démarrage
```
sudo systemctl start mysql
```

- Activation pour démarrage automatique
```
sudo systemctl enable mysql
```

- Vérification du statut
```
sudo systemctl status mysql
```

- Configuration initiale après installation
```
sudo mysql_secure_installation
```















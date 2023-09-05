# INSTALLEZ PHP8 SUR DEBIAN

**Ref: [https://computingforgeeks.com/how-to-install-php-on-debian-linux/](https://computingforgeeks.com/how-to-install-php-on-debian-linux/)**

1. Mettre à jour le système

    *     sudo apt update

    *     sudo apt -y upgrade
2. Rédémarrer le sytème
    
    *     reboot

3. Ajouter le repository

    *     sudo apt update

    *     sudo apt install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2

    *     echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list

4. Importer la clé du repository
    *     wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -

    *     sudo apt update

5. Installer PHP8 sur Debian

    *     sudo apt install php8.0

6. Vérifier si la version voulue a été installé

    *     php -v

7. Installer des extensions de PHP

    *     sudo apt install php8.0-<extension>
 
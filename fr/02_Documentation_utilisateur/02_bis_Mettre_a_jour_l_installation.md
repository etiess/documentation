## Installer une nouvelle version de wallabag

 Pour mettre à jour votre installation, téléchargez et décompressez l’archive dans votre installation (ici <code>/var/www/html/wallabag/</code>) :

    wget http://wllbg.org/latest
    unzip latest
    rsync -ur wallabag-version-number/* /var/www/html/wallabag/

Supprimez le répertoire <code>install</code> et videz le cache :

    cd /var/www/html/wallabag/
    rm -r cache/* install/

Pour vider le cache, il est également possible d'aller dans la page de configuration et de cliquer sur le lien pour supprimer le cache.

Vérifier dans le bas de la page de configuration que la dernière version est bien installée.

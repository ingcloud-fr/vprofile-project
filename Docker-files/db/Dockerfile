# Utilisation de l'image officielle MySQL version 8.0.33
FROM mysql:8.0.33

# Ajout de labels pour documenter le projet et l'auteur
LABEL "Project"="VProfile"
LABEL "Author"="IngCloud"

# Définir des variables d'environnement pour MySQL :
# - Le mot de passe root pour la base de données
ENV MYSQL_ROOT_PASSWORD=vprodbpass
# - Le nom de la base de données à créer automatiquement au démarrage
ENV MYSQL_DATABASE=accounts

# Ajouter un fichier de backup SQL dans le dossier spécifique pour l'initialisation de MySQL
# Les fichiers placés dans /docker-entrypoint-initdb.d/ seront exécutés lors du démarrage de MySQL
ADD db_backup.sql /docker-entrypoint-initdb.d/

# Exposer le port 3306, le port par défaut de MySQL, pour les connexions à la base de données
EXPOSE 3306

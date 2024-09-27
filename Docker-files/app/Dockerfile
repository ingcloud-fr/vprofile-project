## Étape 1 : Image pour le build
# Utilisation d'une image de base OpenJDK 11 pour compiler le projet Java
FROM openjdk:11 AS build_image

# Ajout de labels pour documenter le projet et l'auteur
LABEL "Project"="VProfile"
LABEL "Author"="IngCloud"

# Mise à jour des paquets et installation de Maven (outil de build)
RUN apt update && apt install maven -y

# Clonage du dépôt GitHub contenant le projet source
RUN git clone https://github.com/ingcloud-fr/vprofile-project.git

# Se positionner dans le dossier du projet, basculer sur la branche "docker", puis compiler le projet avec Maven
RUN cd vprofile-project && git checkout docker && mvn install

## Étape 2 : Image finale
# Utilisation d'une image Tomcat avec JDK 11 pour exécuter l'application web
FROM tomcat:9-jdk11

# Suppression des applications par défaut de Tomcat
RUN rm -rf /usr/local/tomcat/webapps/*

# Copier le fichier .war compilé à partir de l'image de build dans le dossier des applications de Tomcat
COPY --from=build_image vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Exposer le port 8080 pour que Tomcat soit accessible de l'extérieur
EXPOSE 8080

# Commande par défaut pour démarrer Tomcat
CMD ["catalina.sh", "run"]

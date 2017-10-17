# Projet Docker

# Nous devons créer un serveur tomcat et le lier à Postgres (base de données) en quelques étapes :

1) Créer 2 containers avec deux images respective crée via un dockerfile.

2) Le dossier tomcat possède le container tomcat qui utilise l'image tomcat:8-jre8 et on copie l'application dbproject.war dans le dossier /usr/local/tomcat/webapps/ pour que le serveur tomcat puisse décompresser le dossier et le lancer.

3) Le dossier postgres possède le container postgres qui utilise l'image de postgres:9.5 et on copie, également, la base de données init-db.sql pour pouvoir utiliser ces tables. Même si le container est stoppé, nous pouvons utiliser VOLUME pour enrigstrer et persister les données.

4) On va build les images sur les deux dockerfiles grâce à la commande : docker build -t tomcat:2.0

5) Une fois les deux images créees, on lance le run des deux containers grâce aux commandes suivantes :

Une fois les 2 images créees on peut run les 2 containers grace aux commandes:

+ docker run -d --name db -v /bddData:/var/lib/postgresql/data NomImagePostgres

+ docker run -d --name MyApp -p 8888:8080 --link db NomImageTomcat

Pour finir, les 2 containers sont lancés, on peut accéder a l'application web et avoir une base de données persistente derrière.








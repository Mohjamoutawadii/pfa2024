# Projet Dents

## Instructions de Configuration

1. **Récupérer l'image du backend :**  
   Exécutez la commande suivante pour télécharger l'image du backend :  
   ```bash
   docker pull mohjamoutawadii1164/pfa2024:backend
   ```

2. **Créer un réseau Docker :**  
   Créez un réseau Docker pour permettre la communication entre les conteneurs :  
   ```bash
   docker network create mohja
   ```

3. **Lancer le conteneur MySQL :**  
   Exécutez la commande suivante pour démarrer un conteneur MySQL :  
   ```bash
   docker run --name mysql-container --network mohja -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=dents -d mysql:latest
   ```

4. **Lancer phpMyAdmin :**  
   Démarrez un conteneur phpMyAdmin pour gérer votre base de données :  
   ```bash
   docker run --name phpmyadmin-container --network mohja -d --link mysql-container:db -p 8084:80 phpmyadmin
   ```

5. **Lancer l'application backend :**  
   Exécutez l'application backend avec les paramètres appropriés :  
   ```bash
   docker run --name backend-container --net mohja -p 5050:5050 --link mysql-container:mysql -e SPRING_DATASOURCE_URL=jdbc:mysql://mysql:3306/dents -e SPRING_DATASOURCE_USERNAME=root -e SPRING_DATASOURCE_PASSWORD=root mohjamoutawadii1164/pfa2024:backend
   ```

   Cela créera automatiquement un utilisateur dans votre base de données. Pour accéder à votre base de données, ouvrez votre navigateur à l'adresse suivante : [http://localhost:8084/](http://localhost:8084/)  
   Utilisez `root` comme nom d'utilisateur et mot de passe.

6. **Insérer un utilisateur dans la table admin :**  
   Allez dans la table `admin`, puis sélectionnez `insert` et choisissez l'ID de l'utilisateur créé.

7. **Accéder à l'application :**  
   Ouvrez votre navigateur à l'adresse suivante : [http://localhost:5050/login](http://localhost:5050/login)

## Identifiants de connexion

- **Nom d'utilisateur :** admin  
- **Mot de passe :** 1234

## Démonstration vidéo

Vous pouvez visionner la démonstration vidéo en suivant ce lien : [Démonstration Vidéo](https://mega.nz/file/xfcn1ahT#wj3gCkN9bkg_4W-TSgEAXOBm7iLUzSO0AZfRn5-c6Tg)


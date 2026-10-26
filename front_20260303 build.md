#### Recupération des fichiers compilés dans le conteneur docker ####


### 1 - Supprimer le dossier /dist-from-docker manuellement ou par commande ###
    - Faire une copie de ce dossier est recommandée.


### 2 - Construire le build de la nouvelle version ###
    Utiliser la commande suivante: 
    - "docker exec id_du_conteneur ng build --prod." 
        Cette commande se base sur les fichiers 
            - angular.json (surtout du paramètre: 'outputPath' car il définit le chemin de sortie des fichiers compilés)
            - DockerFile.prod (Configuration en production)


### 3 - Vérifier que le build a été bien créé vers le chemin de sortie ###
    Utiliser la commande suivante:
    - "docker exec id_du_conteneur ls /app/dist/front"
        Des fichiers hashés devrait y etre listés


### 4 - Récupérer le nouveau build ###
    Utiliser la commande suivante:
    - "docker cp id_du_conteneur:/app/dist/front ./dist-from-docker"
    Les fichiers compilés seront copiés dans le dossier dist-from-docker (ce dossier sera créé automatiquement si il n'existe pas)

Un fichier .bat a été préparé pour ne pas répéter le processus plusiseur fois mais il faut paramétrer ce fichier selon vos configurations.

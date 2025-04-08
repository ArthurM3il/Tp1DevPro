# 3 - Exécuter un serveur web dans un conteneur Docker

## a) Récupérer l'image sur le Docker Hub
- Cd : pour me placer dans le repo git
- Docker login --username "Mon username" : Afin de me connecter
- Docker pull nginx : pull l'image d'nginx depuis le hub

## b) Vérifier que l'image est bien présente en local
- Docker image ls : afin d'afficher les images présentes en local
- <img width="480" alt="Capture d’écran 2025-04-08 à 15 56 18" src="https://github.com/user-attachments/assets/31e84776-52e7-48bd-9f00-52b3802eee4f" />

## c) Créer un fichier index.html
- nano index.html : Pour créer le fichier html correspondant
- ![image](https://github.com/user-attachments/assets/1539bf60-81c8-49ec-81f5-3c2268459e24)

## d) Démarrer le conteneur
- docker run -p 8080:80 -v $(pwd):/usr/share/nginx/html --name TpUn nginx : pour lancer le conteneur sur le port 8080 et en remplaçant le fichier html de base nginx
- Accès sur localhost:8080 pour vérifier le bon fonctionnement
- <img width="296" alt="Capture d’écran 2025-04-08 à 16 18 12" src="https://github.com/user-attachments/assets/9214f463-2a93-4066-820a-339df3d584d9" />

## e) Supprimer le conteneur précédent et en créer un identique
-  docker rm -f TpUn : Pour supprimer l'ancien conteneur
-  docker run -d -p 8080:80 --name TpUnCopie nginx : Pour créer un nouveau conteneur
-  docker cp index.html TpUnCopie:/usr/share/nginx/html/index.html  : Pour copier le fichier html dans le conteneur actuel

# Build une image

## a) Créer une image à l'aide d'un Dockerfile
- nano Dockerfile : pour créer le fichier et y insérer les instructions suivante :
FROM nginx
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
- docker build -t tp-un-dockerfile . : pour construire l'image à partir du dockerfile
- docker ls image : pour vérifier si l'image a bien été crée
- <img width="506" alt="Capture d’écran 2025-04-08 à 16 57 04" src="https://github.com/user-attachments/assets/1f0c10fa-52bc-4346-861b-13c1c77703a5" />

## b) Exécuter la nouvelle image
- docker run -d -p 8080:80 --name image-container tp-un-dockerfile : Pour créer le container à partir de l'image crée précedemment<img width="1393" alt="Capture d’écran 2025-04-08 à 17 01 16" src="https://github.com/user-attachments/assets/d0214fa2-5442-442e-899f-7c6e41a2cf2f" />




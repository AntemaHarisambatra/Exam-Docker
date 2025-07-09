# Docker Cheat Sheet

Une fiche pratique pour maîtriser les commandes Docker de base et intermédiaires.

Nom             :   RAKOTONANDRIANINA
Prénom          :   Zionasoa Antema Harisambatra
Classe          :   L1B
N° matricule    :   173/LA

---

## Commandes Docker (Terminal)

```bash
docker --version                 # Vérifier la version de Docker
docker ps                        # Conteneurs en cours d'exécution
docker ps -a                     # Tous les conteneurs
docker images                    # Liste des images
docker pull <image>              # Télécharger une image depuis Docker Hub
docker run -d -p 8080:80 nginx   # Exécuter un conteneur en arrière-plan
docker stop <id|nom>             # Stopper un conteneur
docker rm <id|nom>               # Supprimer un conteneur
docker rmi <image>               # Supprimer une image

# Cycle de vie des conteneurs
docker create nginx              # Crée un conteneur sans le démarrer
docker start <id>                # Démarre un conteneur
docker restart <id>              # Redémarre un conteneur
docker stop <id>                 # Stoppe un conteneur
docker rm <id>                   # Supprime un conteneur

# Volumes
docker volume create mon_volume
docker run -v mon_volume:/data alpine sh -c "echo test > /data/fichier.txt"
docker volume ls
docker volume inspect mon_volume
docker volume rm mon_volume

# Réseaux
docker network ls
docker network create mon_reseau
docker run -d --network=mon_reseau --name nginx1 nginx
docker run -it --network=mon_reseau alpine ping nginx1

# Exécuter des commandes dans un conteneur
docker exec -it <nom> bash       # Accès au shell bash
docker logs <id>                 # Voir les logs
docker inspect <id>              # Infos détaillées (format JSON)

# Docker Compose
docker-compose up                # Démarre tous les services
docker-compose down              # Arrête et nettoie tout
```

## Exemple de Dockerfile

```dockerfile
# Image de base
FROM node:18

# Dossier de travail
WORKDIR /app

# Copier les fichiers de dépendances et installer
COPY package*.json ./
RUN npm install

# Copier le reste des fichiers
COPY . .

# Lancer l'application
CMD ["npm", "start"]
```

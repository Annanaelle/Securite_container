## Berneau Ethan & Houzelle Annaëlle
## ING4_Cybersécurité_Gr02_INTER

1.Éviter l’Exposition Involontaire de Ports 

![image](https://github.com/user-attachments/assets/91cf8899-1c4c-46c6-9dcc-5a2d471783aa)

port: 

![image](https://github.com/user-attachments/assets/6edfd505-d58d-4c8d-ab50-29a2c91e0b9d)

2.
oui nous pouvons lire le fichier

![image](https://github.com/user-attachments/assets/bcf814d0-16d6-42e6-b819-e6d59d5b0f77)

Mais nous ne pouvons pas écrire comme on peut le voir avec cette echo:

![image](https://github.com/user-attachments/assets/dfcdf371-cf10-4b53-be5f-8cf5043edf0d)
3. Auditer la configuration d’un container avec Docker Bench

Quand on audite l'host on obtient un score de :

![image](https://github.com/user-attachments/assets/3bee5764-4f53-45dd-909c-e0cea7171ade)

pour le container: 

![image](https://github.com/user-attachments/assets/8137e771-ed00-46f1-b52f-7974afcd9feb)


![image](https://github.com/user-attachments/assets/69e651f4-cb68-44cb-a9d6-2bacc6062956)
Vault

![image](https://github.com/user-attachments/assets/e1c03316-73ae-4b5b-aea6-f4fe81226b46)


5.
Context:
Télécharger l'image Docker
L'attaquant récupère l'image Docker via la commande suivante :

docker pull ety92/demo:v1

Inspecter l'historique des couches de l'image
L'attaquant utilise la commande suivante pour analyser les différentes couches de l'image et détecter où la clé API pourrait avoir été ajoutée :

docker history ety92/demo:v1

Explorer les fichiers du conteneur
En exécutant le conteneur avec la commande suivante, l'attaquant peut chercher la clé API en scannant les fichiers à l'intérieur du conteneur :

docker run -it --rm ety92/demo:v1 /bin/sh

Puis, il peut utiliser grep pour rechercher la clé API :

grep -r "API_KEY" /path/to/your/files

Analyser le Dockerfile
Si accessible, l'attaquant peut examiner le Dockerfile pour repérer des lignes où une clé API est définie en tant que variable d'environnement :

ENV API_KEY="12345"

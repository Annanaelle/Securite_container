# Securite_container
## Berneau Ethan & Houzelle Annaëlle

I. Enjeux de Sécurité des Containers

1. Lancer un Container Simple
<img width="564" alt="image" src="https://github.com/user-attachments/assets/7d1c6ec9-6b80-4994-b59c-dcf96bf7edc5" />

2. Explorer un Container en Interactif
<img width="839" alt="image" src="https://github.com/user-attachments/assets/510d443b-5ecd-47b7-b682-73e4a9976597" />

3. Analyser les ressources système d’un container
<img width="574" alt="image" src="https://github.com/user-attachments/assets/c9e12c76-e437-4616-91ad-40ce9970bd9d" />
<img width="745" alt="image" src="https://github.com/user-attachments/assets/0f3c7191-35ea-4a5a-8c4f-2391dc04c2cf" />

4. Lister les capacités d’un container
<img width="644" alt="image" src="https://github.com/user-attachments/assets/abf2ff2b-3a6e-4b1a-8887-1a1fcf23c929" />

II. Activités Pratiques
1. Tester un Container avec des Permissions Élevées
<img width="678" alt="image" src="https://github.com/user-attachments/assets/22cd044b-f856-47ee-b054-6d17b0e2d019" />

L'ajout de --privileged est dangereux puisque cela revient à donner un accès root sur son hôte au conteneur. L'isolement du conteneur n'est quasiment plus effectif.

2. Simuler une Évasion de Container
<img width="287" alt="image" src="https://github.com/user-attachments/assets/1debe4c8-d93c-463c-920b-c698d5777e64" />

Dans ce cas, le conteneur peut lire tout ce qui est lisible sur l'hôte, il n'y a donc plus aucune isolation. Ajouté à d'autres commandes comme --privileged, comme commande pourrait permettre à n'importe qui d'écrire des fichiers sur l'hôte.

3. Créer une Image Sécurisée
<img width="944" alt="image" src="https://github.com/user-attachments/assets/20ff17a3-2e09-49c3-9ac4-d195a9b99950" />
<img width="611" alt="image" src="https://github.com/user-attachments/assets/06e02594-8b28-4278-908a-8549778a4f20" />

4. Restreindre l’accès réseau d’un container
<img width="464" alt="image" src="https://github.com/user-attachments/assets/1e6345dc-bcd2-40c3-8af5-42ea19f06000" />

En exécutant entre ces 2 commandes celle-ci dessous dans un second termpinal, on obtient bien une deconnection du container.
<img width="476" alt="image" src="https://github.com/user-attachments/assets/a73b8085-c44c-4510-aa0e-7a6ba698a432" />

7. Télécharger et Scanner une Image
<img width="469" alt="image" src="https://github.com/user-attachments/assets/e973c81b-c756-4dd1-9b96-7f358e47a99b" />
<img width="853" alt="image" src="https://github.com/user-attachments/assets/771e6679-986b-4ca6-ad71-030049aafdf1" />
<img width="851" alt="image" src="https://github.com/user-attachments/assets/a1b65dad-989d-4036-ac9c-4362b00684e5" />

Les vulnérabilités de cette image sont :
- des failles OPENSSL, PHP, etc
- des failles de librairies système

8. Scanner une Image pour Détecter les Vulnérabilités
<img width="853" alt="image" src="https://github.com/user-attachments/assets/ca4247df-25a2-460f-a139-dc407e7768e7" />

Les différences entre grype et trivy sont :
- trivy analyse les vulnérabilités là où grype s'occupe plus précisement des CVE des paquets logiciels.
- trivy utilise une base de données locale, et gripe une bdd spécifique
- trivy est très rapide et concis, là ou grype est plus lent et détaillé
- trivy est multiformat là ou grivy est axé sur les images docker

  


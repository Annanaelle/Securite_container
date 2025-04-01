On installe gpg puis on peut faire la commande pour creer une clé avec ces informations.

![image](https://github.com/user-attachments/assets/2da81e96-5c10-40a4-85fd-6f95134aaac0)

on peut la voir avec:

![image](https://github.com/user-attachments/assets/b8f89832-efae-4f34-bce0-9041f2daa252)

cette technique ne marche pas a cause de l'exportation sur cosign donc il a fallu recommencer:
On régénère la clé:
![image](https://github.com/user-attachments/assets/4bf858e6-79b7-4f44-aed7-9ef0fdd84dd7)

initialisation docker:

![image](https://github.com/user-attachments/assets/f95830da-8c9a-461d-9f11-374a92484b7b)

on push et on signe avec cosign:

![image](https://github.com/user-attachments/assets/d00f11cb-7b90-49cb-bb8b-76bf60272d6e)

Les deux ont marché:

![image](https://github.com/user-attachments/assets/04115860-4b69-48cb-8e67-db7e90431e45)


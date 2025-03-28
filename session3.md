# Securite_container - session 3
## Berneau Ethan & Houzelle Annaëlle

I. Déployer un Cluster Kubernetes avec Kind
Kind est bien installé :
```bash
kind version
```
<img width="277" alt="image" src="https://github.com/user-attachments/assets/5e66a778-f23d-4829-aa64-f067c5e548a5" />

Création du cluster :

<img width="269" alt="image" src="https://github.com/user-attachments/assets/8642ad10-d16c-45f5-9fad-cd0bd76b81d7" />
```bash
kind create cluster --config kind-cluster.yaml --name cluster-1
```
<img width="863" alt="image" src="https://github.com/user-attachments/assets/9e42975b-c775-4f4c-bfb8-3924d9012eed" />

Le cluster fonctionne bien :
```bash
kubectl get nodes
```
<img width="719" alt="image" src="https://github.com/user-attachments/assets/f2b35f34-e943-4ab9-ae0e-5201fd8a6960" />

Pour afficher la liste des namespace :
``` bash
kubectl get namespaces
```
<img width="752" alt="image" src="https://github.com/user-attachments/assets/193c0429-57f7-4df5-8f5b-760ad1736e6c" />

Version de kubernetes :
```bash
 kubectl version
```
<img width="706" alt="image" src="https://github.com/user-attachments/assets/b5c0a2a8-d644-4ac7-b47d-9b7a5c53eeeb" />





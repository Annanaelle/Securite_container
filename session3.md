# Securite_container - session 3
## Berneau Ethan & Houzelle Annaëlle

1. Déployer un Cluster Kubernetes avec Kind
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

2. Expérimentation des RBAC
Création d'un namespace test-rbac
```bash
kubectl create ns test-rbac
```
<img width="799" alt="image" src="https://github.com/user-attachments/assets/3b936168-673e-44ed-9d16-9bb1b92d083a" />

Déployer ce pod dans le namespace test-rbac avec la commande 

<img width="221" alt="image" src="https://github.com/user-attachments/assets/3e2863a1-97ea-499d-bb61-a1a3d5e3a6e8" />

```bash
kubectl apply -f mon-pod.yaml
```
<img width="803" alt="image" src="https://github.com/user-attachments/assets/1aa467a6-ee7a-4be5-8749-ac893ee394fc" />

Les logs du pod :
```bash
kubectl logs nginx -n test-rbac
```
<img width="830" alt="image" src="https://github.com/user-attachments/assets/c71bbfc6-ee02-491e-8f89-fb8140f9d86a" />

Création d'un rôle et l'appliquer :

<img width="272" alt="image" src="https://github.com/user-attachments/assets/aee1490a-56a5-4c33-afe8-8ab069516fe0" />

```bash
kubectl apply -f role-pod-reader.yaml
```

<img width="851" alt="image" src="https://github.com/user-attachments/assets/ac3453af-d7a7-451c-be6c-71179a85817d" />

Afficher le rôle :
```bash
kubectl get role pod-reader -n test-rbac -o yaml
```
<img width="854" alt="image" src="https://github.com/user-attachments/assets/b2f31029-a5ed-4025-9ba9-d4040c2b369e" />











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

Créer le rôle et l'appliquer :

<img width="278" alt="image" src="https://github.com/user-attachments/assets/98726464-1537-49ab-92f7-a3e94d0c5b07" />

```bash
kubectl apply -f rolebinding-pod-reader.yaml
```
<img width="851" alt="image" src="https://github.com/user-attachments/assets/79f33099-0e60-46ae-80f2-0341f225e028" />


Création de l'utilisateur titi :
```bash
docker cp cluster-1-control-plane:/etc/kubernetes/pki/ca.crt .
docker cp cluster-1-control-plane:/etc/kubernetes/pki/ca.key .
```
<img width="851" alt="image" src="https://github.com/user-attachments/assets/5db41fc0-7346-4b10-b805-603f186acbcd" />

<img width="851" alt="image" src="https://github.com/user-attachments/assets/b0609d9b-7f3c-4096-92bf-09e23c1c635d" />

Après résolution du problème :
```bash
openssl x509 -req -in titi.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out titi.crt -days 365 -config ./openssl.conf
```
<img width="399" alt="image" src="https://github.com/user-attachments/assets/3c264753-6901-4a2e-aba6-788a2b8b2597" />

Ajout de l'utilisateur dans le kube 
```bash
kubectl config set-credentials titi --client-certificate=titi.crt --client-key=titi.key
```
<img width="953" alt="image" src="https://github.com/user-attachments/assets/8f9cf434-2428-4efd-a082-463c993c3f3e" />

Créationd 'un contexte pour titi :
```bash
kubectl config set-context titi-context --cluster=kind-kind --namespace=test-rbac --user=titi
```
<img width="943" alt="image" src="https://github.com/user-attachments/assets/cf2ed033-841b-42fe-b795-f288c60c524b" />

Basculer de contecxte :
```bash
kubectl config use-context titi-context
```
<img width="693" alt="image" src="https://github.com/user-attachments/assets/3a854d13-35ba-45d5-90ce-870c1ef441a7" />

Tentative de lister les pods :
```bash
kubectl get pods -n test-rbac
```
<img width="796" alt="image" src="https://github.com/user-attachments/assets/8452854c-dbc7-4396-9a1b-c1eec3498df0" />

On ne peut pas lister les pods puisque l'utilisateur n'a pas les droits

Pour en ajouter un, on tente la commande :
```bash
kubectl run mypod --image=nginx --namespace=test-rbac
```
<img width="772" alt="image" src="https://github.com/user-attachments/assets/07bf631f-9910-401b-847c-e60f454517fd" />

On ne peut pas non plus en ajouter

On reswitch sur le contect de base :
<img width="695" alt="image" src="https://github.com/user-attachments/assets/104b55c5-9316-4f93-9be2-9f9b4ff82d6c" />

3. Scanner un Cluster Kubernetes avec Kube-Bench











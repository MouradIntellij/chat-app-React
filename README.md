# Examen 1 TT4 - Chat Application React

# Architecture du projet

Le projet est divisé en deux parties principales :

# Examen 1 TT4 - Chat Application React

## Informations

- Nom : Elmehdi Regragui 
- Cours : TT4 - Tendances Technologiques Web
- Session : Hiver 2026

---

# Description du projet

Cette application est un chat en temps réel développé avec **React**, **Node.js**, **Express** et **Socket.io**.

L'application permet à plusieurs utilisateurs de rejoindre une **room**, d'envoyer des messages instantanément et de voir les autres participants connectés.

Les messages sont échangés en temps réel grâce à **WebSockets via Socket.io**.

---

# Architecture du projet

Le projet est divisé en deux parties principales :

- **client** : application React (frontend)
- **server** : serveur Node.js avec Socket.io (backend)

---

# Analyse du code existant

## App.js

App.js est le composant principal de l'application React.

Il gère :

- le pseudo de l'utilisateur
- la room sélectionnée
- l'état de connexion

Si l'utilisateur n'est pas connecté, l'application affiche le composant **Join.js**.  
Sinon, l'application affiche **Chat.js**.

---

## Join.js

Join.js est la page d'entrée de l'application.

Elle permet :

- d'entrer un pseudo
- de choisir une room
- de créer une nouvelle room
- de rejoindre le chat

---

## Chat.js

Chat.js est le composant principal de la salle de discussion.

Il permet :

- d'afficher la room active
- d'afficher les messages
- d'envoyer un message
- d'afficher les participants
- d'afficher la sidebar
- de quitter la room

---

## Message.js

Message.js est responsable de l'affichage des messages.

Il gère :

- les messages envoyés par l'utilisateur
- les messages envoyés par les autres utilisateurs
- les messages système
- l'heure du message
- l'indicateur **Lu ✓✓**

---

## Sidebar.js

Sidebar.js affiche :

- la liste des participants
- un avatar avec l'initiale de chaque utilisateur
- un indicateur de présence (point vert)
- l'historique des activités récentes

Les activités affichées sont :

- un utilisateur qui rejoint une room
- un utilisateur qui quitte une room

---

## SocketContext.js

SocketContext.js crée et partage la connexion Socket.io dans toute l'application React.

Grâce au **Context API**, tous les composants peuvent utiliser la même connexion socket avec :

Cela évite de recréer plusieurs connexions WebSocket.

---

## server.js

server.js est le serveur backend utilisant :

- Express
- Socket.io

Le serveur gère :

- les connexions des utilisateurs
- les rooms
- les messages envoyés
- la liste des utilisateurs
- les événements d'activité

---

# Communication frontend / backend

## Connexion Socket

Le frontend se connecte au serveur avec :

Le socket est créé dans **SocketContext.js** et partagé dans toute l'application.

---

## Rejoindre une room

Quand un utilisateur rejoint une room, le client envoie :

```javascript
socket.emit("join_room", { username, room });

lien du backend : https://chat-app-server-qgru.onrender.com

lien du frontend : https://chatapp-blue-ten.vercel.app
lancer le backend : cd server
npm install
node server.js

lancer le frontend : cd client
npm install
npm start

Accéder à l'application : http://localhost:3000 et http://localhost:5000

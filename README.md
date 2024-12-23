# 📚 **Gestion des Livres - Système de Bibliothèque** 

---

## 🌟 **Introduction**

Ce projet consiste à concevoir un système de gestion de bibliothèque en suivant les étapes classiques de conception de base de données : MCD (Modèle Conceptuel de Données), MLD (Modèle Logique de Données) et MPD (Modèle Physique de Données).

### 💡 **Concepts clés**

- **MCD** : Représentation abstraite des données et de leurs relations dans le système.
- **MLD** : Traduction du MCD en structures relationnelles (tables).
- **MPD** : Implémentation du MLD dans un SGBD en ajoutant les contraintes physiques (types de données, index, etc.).

---

## 📅 **Déroulement de l’activité**

### 1️⃣ **Introduction théorique** 

1. **MCD** : Identification des entités clés du système et de leurs relations.
2. **MLD** : Transformation du MCD en tables relationnelles, en appliquant la normalisation et en définissant les clés primaires et étrangères.
3. **MPD** : Ajout des types de données et des contraintes physiques (ex. : NOT NULL, UNIQUE, PRIMARY KEY, etc.).

### 2️⃣ **Étude de cas : Gestion d’une bibliothèque** 

#### 📖 **Contexte**
- **Utilisateur (client)** : Emprunte des livres.
- **Livre** : Catégorisé et géré par des administrateurs.
- **Emprunt** : Enregistre la date d’emprunt et la date de retour prévue.
- **Catégorie** : Classement des livres.

#### 🎯 **Objectifs**
- Identifier les entités principales : **Livre**, **Utilisateur**, **Emprunt**, **Catégorie**.
- Définir les relations entre les entités : Par exemple, un utilisateur peut emprunter plusieurs livres, un livre appartient à une seule catégorie.
- Spécifier les attributs de chaque entité : Par exemple, pour **Livre**, les attributs peuvent être le **titre**, **auteur**, **ISBN**.

---

## 🛠️ **Activité pratique**

### 1️⃣ **Étape 1 : Création du MCD** 

Les participants seront répartis en groupes pour :
- Identifier les entités et leurs attributs.
- Définir les relations entre les entités avec les cardinalités.
- Dessiner le MCD à l'aide d'un outil graphique comme **Lucidchart** ou sur **papier**.
![image](https://github.com/user-attachments/assets/d027784d-6008-4c1b-9dd0-fb3a94e8c3d7)


### 2️⃣ **Étape 2 : Transformation en MLD** 

Chaque groupe, en utilisant le MCD, devra :
- Créer les tables relationnelles correspondant aux entités.
- Définir les clés primaires et étrangères pour les relations.
- Vérifier la normalisation des tables : **1NF**, **2NF**, **3NF**.
- ![image](https://github.com/user-attachments/assets/4e5721f9-710a-4a92-8176-1c1d77ad2f1e)


### 3️⃣ **Étape 3 : Passage au MPD** 

À ce stade, chaque groupe devra :
- Ajouter les types de données pour chaque colonne des tables (par exemple, **VARCHAR**, **INT**, **DATE**).
- Appliquer les contraintes physiques sur les tables, telles que **NOT NULL**, **UNIQUE**, **PRIMARY KEY**, **FOREIGN KEY**.
![image](https://github.com/user-attachments/assets/650d0575-04ab-42d6-a3b1-c137e58554ae)
### *** Creat Base Donnée and SQL code **
create database getion_Livres;
use getion_Livres;

-- Create the User table
CREATE TABLE User (
    id_user INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL
);

-- Create the Admin table
CREATE TABLE Admin (
    id_admin INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL
);

-- Create the Category table
CREATE TABLE Category (
    id_category INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

-- Create the Livre (Book) table
CREATE TABLE Livre (
    id_livre INT AUTO_INCREMENT PRIMARY KEY,
    titre VARCHAR(200) NOT NULL,
    auteur VARCHAR(100) NOT NULL,
    id_category INT NOT NULL,
    id_admin INT NOT NULL,
    FOREIGN KEY (id_category) REFERENCES Category(id_category),
    FOREIGN KEY (id_admin) REFERENCES Admin(id_admin)
);

-- Create the Empruntent (Borrowing) table
CREATE TABLE Empruntent (
    id_empt INT AUTO_INCREMENT PRIMARY KEY,
    for_cle_id_user INT NOT NULL,
    for_cle_id_livre INT NOT NULL,
    date_emprut DATE NOT NULL,
    date_retour DATE NOT NULL,
    FOREIGN KEY (for_cle_id_user) REFERENCES User(id_user),
    FOREIGN KEY (for_cle_id_livre) REFERENCES Livre(id_livre)
);

#### **ERD**
![image](https://github.com/user-attachments/assets/5bb74fba-365e-4177-a875-f34366b35458)


---


## 🎉 **Conclusion**

Ce projet permet de comprendre les étapes essentielles de la conception d'un système de gestion de bibliothèque, depuis l'identification des entités et relations dans le MCD, jusqu'à l'implémentation physique du système dans un SGBD via le MPD. Ce processus garantit que la base de données sera bien structurée et performante, en respectant les contraintes et les bonnes pratiques de conception.

---

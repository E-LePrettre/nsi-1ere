---
author: ELP
title: 05 Fiche méthode Logicism
---

# Fiche Méthode : Utilisation de Logisim

Logisim est un logiciel de simulation de circuits logiques. Voici une fiche méthode pour vous aider à l'utiliser avec des exemples simples basés sur les portes logiques AND, OR, et NOT.

---

## 1. Installation de Logisim
- **Téléchargez Logisim** depuis le site officiel (https://sourceforge.net/projects/circuit/) ou une source de confiance.
- Une fois le fichier téléchargé, ouvrez l'application Java. Aucun processus d'installation classique n’est nécessaire.

---

## 2. Interface principale de Logisim

### Les éléments principaux :
1. **Barre d'outils** (en haut) : contient les icônes des outils pour créer et manipuler les circuits.
2. **Bibliothèque de composants** (colonne gauche) : regroupe toutes les portes logiques, entrées/sorties, et autres composants.
3. **Zone de travail** (au centre) : là où vous construisez le circuit.
4. **Console de simulation** (en bas) : permet d’observer les états logiques.

---

## 3. Création d’un circuit simple

### Exemple 1 : Porte AND
1. **Sélectionner la porte AND** :
   - Dans la bibliothèque à gauche, cliquez sur « **Gates** » (Portes logiques).
   - Cliquez sur l’icône **AND** (voir image ci-dessous).

   ![Icône porte AND](image.png)

2. **Ajouter la porte AND au circuit** :
   - Cliquez sur la zone de travail pour placer la porte AND.

   ![alt text](image-1.png)

3. **Ajouter des entrées** :
   - Dans la bibliothèque, cliquez sur « **Input/Output** ».
   - Sélectionnez l’icône **Input Pin** (entrée) et placez-en deux sur la zone de travail.

   ![alt text](image-2.png)

   ![alt text](image-3.png)

4. **Ajouter une sortie** :
   - Toujours dans « Input/Output », sélectionnez l’icône **Output Pin** (sortie).
   - Placez-la à droite de la porte AND.

   ![alt text](image-4.png)

5. **Connecter les composants** :
   - Utilisez l’outil de connexion (icône en forme de crayon).
   - Reliez chaque entrée à une des entrées de la porte AND, et reliez la sortie de la porte AND à la sortie.

    ![alt text](image-5.png)


6. **Simulation** :
   - Cliquez sur le bouton « **Simulate** » en haut de l’interface.
   - Activez/désactivez les entrées en cliquant sur les pins d’entrée pour observer le comportement de la porte AND.

![alt text](image-6.png)

![alt text](image-7.png)

Ici on voit que 1 en entrée et 0 en entrée donne 0 en sortie

### Exemple 2 : Porte OR
Répétez les étapes de l’exemple 1 en remplaçant la porte AND par une porte OR.

![alt text](image-8.png)

![alt text](image-9.png)

Ici on voit que 1 en entrée et 0 en entrée donne 1 en sortie

### Exemple 3 : Porte NOT
1. **Sélectionner la porte NOT** :
   - Dans « **Gates** », cliquez sur l’icône **NOT**.
   - Placez-la sur la zone de travail.

2. **Ajouter une entrée et une sortie** :
   - Ajoutez un **Input Pin** (entrée) à gauche de la porte NOT.
   - Ajoutez un **Output Pin** (sortie) à droite de la porte NOT.

3. **Connecter les composants** :
   - Reliez l’entrée à l’entrée de la porte NOT, et la sortie de la porte NOT à la sortie.

4. **Simulation** :
   - Cliquez sur « **Simulate** » et testez le comportement de la porte NOT.

    ![alt text](image-10.png)

    Ici on voit que 0 en entrée donne 1 en sortie
---

## 4. Fonctionnalités avancées
- **Sauvegarde** : utilisez « File > Save » pour enregistrer votre circuit.
- **Zoom** : ajustez le zoom avec les boutons + et − en haut.
- **Annotations** : ajoutez du texte explicatif à votre circuit via l’outil « **Text Tool** » dans la barre d’outils.

---




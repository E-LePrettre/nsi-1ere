---
author: ELP
title: 07c Le Javascript
--- 

**Table des matières** 

1. [Qu'est-ce que JavaScript et à quoi sert-il ? ](#_page0_x40.00_y687.92)
2. [Comment utiliser JavaScript avec HTML et CSS ?](#_page1_x40.00_y280.92)
3. [Boite de dialogue](#_page2_x40.00_y237.92)
4. [La console](#_page2_x40.00_y113.92)
5. [Les variables](#_page2_x40.00_y641.92)
6. [Les conditions](#_page4_x40.00_y693.92)
7. [Les opérateurs logiques](#_page6_x40.00_y544.92)
8. [Les boucles](#_page6_x40.00_y626.92)
9. [Les fonctions](#_page7_x40.00_y654.92)
10. [Modeler des pages web avec js ](#_page8_x40.00_y524.92)
11. [Interactions avec l’utilisateur ](#_page14_x40.00_y95.92)
12. [Exercices ](#_page18_x40.00_y36.92)

## **<H2 STYLE="COLOR:BLUE;">1. Qu'est-ce que JavaScript et à quoi sert-il ? <a name="_page0_x40.00_y687.92"></a>**</H2>
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.004.png)

JavaScript est un langage de programmation utilisé **côté client** pour ajouter des fonctionnalités interactives aux pages web.  

📌 **Caractéristiques principales :**  
✔ **Langage client-side** → Exécuté par le navigateur de l'utilisateur.  
✔ **Polyvalent** → Fonctionne sur tous les navigateurs web.  
✔ **Interactivité** → Manipulation en temps réel du contenu HTML et CSS.  

**📌 Comment fonctionne JavaScript dans une page web ?**  

1. **Le navigateur récupère le code HTML/CSS/JS** depuis un serveur web.  
2. **Le moteur JavaScript du navigateur interprète et exécute le script**.  
3. **Les modifications apportées par JavaScript sont appliquées en temps réel** (exemple : animations, formulaires interactifs, boutons dynamiques, etc.).  

➡ JavaScript **ne nécessite pas de serveur** pour fonctionner, il est directement exécuté **dans le navigateur** de l'utilisateur.

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.009.png)

## **<H2 STYLE="COLOR:BLUE;">2. Comment<a name="_page1_x40.00_y280.92"></a> utiliser JavaScript avec HTML et CSS ?**</H2>
### **<H3 STYLE="COLOR:GREEN;">2.1. Cas<a name="_page1_x40.00_y302.92"></a> général :**</H3>

Il est possible d’intégrer du JavaScript **dans le code HTML**, entre les balises `<script> ... </script>`.

📌 **Exemple :**
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* Feuille de style CSS */
      body {
        font-family: Arial, sans-serif;
      }
    </style>
  </head>
  <body>

    <h1>Bienvenue sur ma page</h1>

    <button onclick="afficherMessage()">Cliquez-moi</button>

    <script>
      function afficherMessage() {
        alert("Bonjour ! Vous avez cliqué sur le bouton.");
      }
    </script>

  </body>
</html>
```

✅ **Explication** :  
- **Ligne 11 :** Un bouton HTML `<button>` déclenche une fonction **JavaScript** lorsqu'on clique dessus.  
- **Ligne 14-16 :** Une fonction JavaScript `afficherMessage()` affiche une boîte de dialogue (`alert()`).  

📌 **Résultat :** Lorsqu'on clique sur le bouton, une **alerte apparaît avec un message**.



### **<H3 STYLE="COLOR:GREEN;">2.2. Fichier<a name="_page1_x40.00_y558.92"></a> js externalisé**</H3>

Pour une **meilleure organisation**, on peut **séparer** le JavaScript dans un fichier `.js` externe.

📌 **HTML (index.html) :**
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <link rel="stylesheet" href="css/style.css" />
    <script src="js/script.js"></script>
    <title>Logique sur les passoires</title>
</head>
<body>
    <h1>Bienvenue sur ma page</h1>
    <button id="monBouton">Cliquez-moi</button>
</body>
</html>
```

📌 **JavaScript (script.js) :**
```js
// Fonction exécutée lorsque le bouton est cliqué
document.getElementById("monBouton").addEventListener("click", function() {
    alert("Bonjour ! Vous avez cliqué sur le bouton.");
});
```

✅ **Explication** :  
- **Ligne 5 :** On sélectionne le bouton avec `document.getElementById("monBouton")`.  
- **Ligne 6 :** On **écoute l’événement `click`** et on exécute une fonction **au clic**.  

📌 **Résultat :** Quand on clique sur le bouton, une **alerte apparaît avec un message**.


**<H3 STYLE="COLOR:red;">Activité n°1 : </H3> Ajouter un fichier JavaScript externe** 

1. **Dans `index.html`**, ajoutez cette ligne dans `<head>` :
```html
<script src="js/script.js"></script>
```
2. **Créez un fichier `script.js`** dans le dossier `js/` s'il n'existe pas encore.  
3. **Ajoutez ce code dans `script.js`** :
```js
document.getElementById("monBouton").addEventListener("click", function() {
    alert("Vous avez cliqué !");
});
```
4. **Enregistrez et testez la page `index.html` dans un navigateur**.

✅ **Vous avez maintenant un script JavaScript externe qui fonctionne !** 🎉


**📌 Pourquoi utiliser un fichier JavaScript externe ?**  

✔ **Meilleure organisation** → Séparer HTML, CSS et JavaScript.  

✔ **Réutilisation facile** → Un seul fichier `.js` peut être utilisé sur plusieurs pages. 

✔ **Chargement plus rapide** → Le navigateur met en cache les fichiers `.js` pour **accélérer l’affichage** des pages.  



## **<H2 STYLE="COLOR:BLUE;">3. Boite<a name="_page2_x40.00_y237.92"></a> de dialogue**</H2>

JavaScript propose **trois types de boîtes de dialogue** pour interagir avec l'utilisateur :  

| Type de boîte | Utilisation | Exemple |
|--------------|------------|---------|
| `alert()` | Affiche un **message d'information** | `alert("Bonjour !");` |
| `confirm()` | Demande une **confirmation (Oui/Non)** | `confirm("Voulez-vous continuer ?");` |
| `prompt()` | Demande **une saisie de l'utilisateur** | `prompt("Quel est votre nom ?");` |


**<H3 STYLE="COLOR:red;">Activité n°2 :**</H3>

1️⃣ **Créer un nouveau fichier HTML** appelé **`exo_JS.html`**  
2️⃣ **Ajouter ce code dans `exo_JS.html`** :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="utf-8" />
    <title>Page de tests JavaScript</title>
</head>
<body>
    <h1>Page de tests du code JavaScript</h1>
</body>
</html>
```

✅ **Enregistrer et ouvrir dans un navigateur**.



**<H3 STYLE="COLOR:red;">Activité n°3 :**</H3>

1️⃣ **Dans `exo_JS.html`**, ajouter ce code **dans `<body>`** :
```html
<script>
    alert('Hello world!');
</script>
```
2️⃣ **Enregistrer et observer** :  

➡ Une **boîte d’alerte** doit apparaître avec le message `"Hello world!"`.

 

**<H3 STYLE="COLOR:red;">Activité n°4 :**</H3> 

1️⃣ **Dans `exo_JS.html`**, modifier le code pour **ajouter un fichier externe `exo.js`** :
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="utf-8" />
    <script src="exo.js"></script>
    <title>Page de tests JavaScript</title>
</head>
<body>
    <h1>Page de tests du code JavaScript</h1>
</body>
</html>
```

2️⃣ **Créer un nouveau fichier `exo.js`** dans le même dossier.


**<H3 STYLE="COLOR:red;">Activité n°5 :**</H3> 

1️⃣ **Dans `exo.js`**, ajouter ce code :
```js
alert('Hello world!');
```
2️⃣ **Dans `exo_JS.html`**, **supprimer** l'ancien `<script>` qui contenait `alert()`.  
3️⃣ **Enregistrer et observer** :  
➡ L’alerte **s’affiche toujours**, mais maintenant grâce à **`exo.js`**.

✅ **Félicitations, vous avez relié un fichier JavaScript externe !** 🎉


## **<H2 STYLE="COLOR:BLUE;">4. La<a name="_page2_x40.00_y113.92"></a> console**</H2>

La **console JavaScript** permet d'afficher des messages utiles pour **déboguer** un programme.


**<H3 STYLE="COLOR:red;">Activité n°6 :**</H3> 

1️⃣ **Dans `exo.js`**, remplacez `alert()` par :
```js
console.log('Hello world!');
```
2️⃣ **Enregistrer et ouvrir `exo_JS.html` dans un navigateur**.  
3️⃣ **Ouvrir la console JavaScript** :  
   - **Firefox / Edge** : `Ctrl + Maj + I` puis **onglet "Console"**  
   - **Chrome** : `F12` puis **onglet "Console"**  

➡ **Résultat attendu** : `"Hello world!"` s’affiche dans la console.

---

**📌 Pourquoi utiliser `console.log()` ?**  

✔ **Affiche des messages sans interrompre la page (contrairement à `alert()`).**  

✔ **Permet de tester et corriger du code facilement.**  

✔ **Utile pour voir la valeur des variables en cours d'exécution.**  

📌 **Exemple :**  
```js
let nom = "Alice";
console.log("Bonjour " + nom + " !");
```
➡ `"Bonjour Alice !"` s’affichera dans la console.


![](image1.png)

## **<H2 STYLE="COLOR:BLUE;">5. Les<a name="_page2_x40.00_y641.92"></a> variables**</H2>
### **<H3 STYLE="COLOR:GREEN;">5.1. Déclarer<a name="_page2_x40.00_y663.92"></a> une variable**</H3>

Une variable est **un espace mémoire** permettant de stocker une valeur.  

📌 **Trois mots-clés pour déclarer une variable :**  
| Mot-clé | Portée | Peut être modifiée ? | Scope limité par bloc `{}` ? |
|---------|--------|-----------------|------------------|
| `var` | Globale ou locale (fonction) | ✅ Oui | ❌ Non |
| `let` | Bloc (limité à `{}`) | ✅ Oui | ✅ Oui |
| `const` | Bloc (limité à `{}`) | ❌ Non | ✅ Oui |

📌 **Exemples :**  
```js
var maVariable1 = 10;   // Déclarée avec var
let maVariable2 = "Bonjour";  // Déclarée avec let
const MA_CONSTANTE = 3.14;  // Déclarée avec const (non modifiable)
```

**<H3 STYLE="COLOR:red;">Activité n°7 :</H3> Déclarer et afficher une variable** 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var myVariable = 5.5;
alert(myVariable);
```
2️⃣ **Enregistrer et observer** dans `exo_JS.html`.

➡ **Résultat** : Une boîte d’alerte s’affiche avec la valeur **5.5**.
   
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.024.png)

📌 **Remplacez maintenant `alert()` par `console.log()`** :
```js
var myVariable = 5.5;
console.log(myVariable);
```
➡ **Résultat** : Ouvrez la console (`Ctrl + Maj + I`), la valeur **5.5** apparaît.



### **<H3 STYLE="COLOR:GREEN;">5.2. Les<a name="_page3_x40.00_y137.92"></a> types de variables**</H3>


JavaScript est **typé dynamiquement** 📌 **(on n’a pas besoin de préciser le type d’une variable)**.

| Type | Exemple |
|------|---------|
| `Number` | `let age = 25;` |
| `String` (texte) | `let nom = "Alice";` |
| `Boolean` (vrai/faux) | `let estConnecte = true;` |

📌 **Vérifier le type d’une variable avec `typeof`** :
```js
console.log(typeof 42);         // "number"
console.log(typeof "Bonjour");  // "string"
console.log(typeof true);       // "boolean"
```
 

### **<H3 STYLE="COLOR:GREEN;">5.3. Les<a name="_page3_x40.00_y247.92"></a> chaines de caractères**</H3>



**<H3 STYLE="COLOR:red;">Activité n°8 :</H3> Tester les chaînes de caractères et caractères spéciaux** 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var message1 = "Ceci est un \"petit\" test.";
var message2 = 'Un autre "petit" test (attention à l\'apostrophe).';
console.log(message1);
console.log(message2);
```
➡ **Résultat** : Les messages s’affichent dans la console.

📌 **Autres caractères spéciaux utiles :**  
- `\n` → retour à la ligne  
- `\t` → tabulation  
- `\uXXXX` → caractère Unicode (pour insérer le caractère donc la [valeur unicode](http://fr.wikipedia.org/wiki/Table_des_caractÃ¨res_Unicode) est XXXX (en hexadécimales). )



### **<H3 STYLE="COLOR:GREEN;">5.4. Tester<a name="_page3_x40.00_y503.92"></a> l’existence de variables avec typeof ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.029.png)**</H3>


**<H3 STYLE="COLOR:red;">Activité n°9 :**</H3> 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var number = 2;
console.log(typeof number); 

var text = 'Mon texte';
console.log(typeof text); 

var aBoolean = false;
console.log(typeof aBoolean);
```
➡ **Résultat attendu** :  
```
number
string
boolean
```

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.031.png) 

### **<H3 STYLE="COLOR:GREEN;">5.5. Les<a name="_page3_x40.00_y706.92"></a> calculs**</H3>

JavaScript permet **toutes les opérations classiques** :  
✔ Addition `+`  
✔ Soustraction `-`  
✔ Multiplication `*`  
✔ Division `/`  
✔ Modulo `%` (reste de la division)

📌 **Exemple :**
```js
var a = 10, b = 3;
console.log(a + b);  // 13
console.log(a - b);  // 7
console.log(a * b);  // 30
console.log(a / b);  // 3.33
console.log(a % b);  // 1
```


**<H3 STYLE="COLOR:red;">Activité n°10 :**</H3> 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var divisor = 3, result1, result2, result3; 
result1 = (16 + 8) / 2 - 2; 
result2 = result1 / divisor; 
result3 = result1 % divisor; 

console.log(result2); 
console.log(result3);
```
➡ **Résultat attendu** : Affichage des valeurs calculées.


### **<H3 STYLE="COLOR:GREEN;">5.6. La<a name="_page4_x40.00_y154.92"></a> concaténation**</H3>

📌 **Exemple :**  
```js
let salutation = "Bonjour";
let nom = "Alice";
console.log(salutation + " " + nom);  // Bonjour Alice
```


**<H3 STYLE="COLOR:red;">Activité n°11 :**</H3> 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var hi = 'Bonjour ', name = 'toi', result; 
result = hi + name;  
console.log(result);
```
➡ **Résultat attendu** : `Bonjour toi`

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.034.png)

 

### **<H3 STYLE="COLOR:GREEN;">5.7. Interagir<a name="_page4_x40.00_y286.92"></a> avec l’utilisateur**</H3>


📌 **Exemple :**
```js
var userName = prompt('Entrez votre prénom :');  
console.log("Bonjour " + userName);
```
➡ **L’utilisateur entre un texte, puis celui-ci est affiché.**



**<H3 STYLE="COLOR:red;">Activité n°12 :**</H3> 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var start = 'Bonjour ', name, end = ' !', result; 

name = prompt('Quel est votre prénom ?'); 
result = start + name + end; 
console.log(result);
```
➡ **Résultat attendu** : `Bonjour [Prénom] !`


![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.036.png)



### **<H3 STYLE="COLOR:GREEN;">5.8. Convertir une entrée utilisateur en nombre (`parseInt()` et `parseFloat()`)**</H3>

📌 **Problème** : `prompt()` **retourne toujours du texte**.  
📌 **Solution** : Convertir avec **`parseInt()` (entier)** ou **`parseFloat()` (nombre décimal)**.

📌 **Exemple :**
```js
var age = prompt("Quel est votre âge ?");
console.log(parseInt(age) + 5);  // Convertit l’entrée en nombre et ajoute 5
```


**<H3 STYLE="COLOR:red;">Activité n°13 :**</H3> 

1️⃣ **Dans `exo.js`**, ajoutez ce code :
```js
var first, second, result;  
first = prompt('Entrez le premier chiffre :');  
second = prompt('Entrez le second chiffre :');  
result = parseInt(first) + parseInt(second);  
console.log(result);
```
➡ **L’utilisateur entre deux nombres, la somme s’affiche dans la console.**



## **<H2 STYLE="COLOR:BLUE;">6. Les<a name="_page4_x40.00_y693.92"></a> conditions**</H2>
### **<H3 STYLE="COLOR:GREEN;">6.1. Les<a name="_page4_x40.00_y715.92"></a> opérateurs de condition**</H3>

Les opérations de comparaison classiques sont les mêmes : ```==``` ; ```!= ```; ```<``` ; ```<=``` etc.

Pour pouvoir comparer 4 en tant que ```number``` et 4 en tant que string il faut utiliser d’autres opérateurs :

**<H3 STYLE="COLOR:red;">Activité n°14 :**</H3> 

Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox.

```JS
var number = 4, text = '4', result;

result = number == text;
console.log(result); // Affiche  « true » alors que « number » est un nombre et « text » une chaîne de caractères

result = number === text;
console.log(result); // Affiche « false » car cet opérateur compare aussi les types des variables en plus de leurs valeurs
```


### **<H3 STYLE="COLOR:GREEN;">6.2. Les<a name="_page5_x40.00_y167.92"></a> structures conditionnelles**</H3>
#### **<H4 STYLE="COLOR:ORANGE;">6.2.1. La<a name="_page5_x40.00_y186.92"></a> condition « if else »</H4>****

**<H3 STYLE="COLOR:red;">Activité n°15 :**</H3> 

Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox.

```JS
var userName = prompt('Entrez votre prénom :');

if (2 < 8 && 8 >= 4) { // Cette condition renvoie « true », le code est donc exécuté     
console.log('La condition est bien vérifiée.');
}
console.log(userName);  
```

La fonction ```confirm()``` permet d'afficher une boîte de confirmation et retourne un booléen en fonction de l’action de l’utilisateur.
 

**<H3 STYLE="COLOR:red;">Activité n°16 :**</H3> 

Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox.

```JS
if (confirm('Voulez-vous exécuter le code JavaScript de cette page ?')) {
   console.log('Le code a bien été exécuté !')};
```

La structure ```else``` permet d’exécuter un certain code si la condition n’a pas été vérifiée.

```JS
if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```

La structure ```else if``` peut être utilisée ainsi :

```JS
if ( /* condition */ ) {
    // Du code…
} else if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```


#### **<H4 STYLE="COLOR:ORANGE;">6.2.2. La<a name="_page5_x40.00_y659.92"></a> condition ```switch```</H4>**


**<H3 STYLE="COLOR:red;">Activité n°17 :**</H3> 

Dans le fichier exo.js passer les lignes précédentes en commentaire et rajouter le script suivant.

```JS
var tiroir = parseInt(prompt('Choisissez le tiroir à ouvrir (1 à 4) :'));

switch (tiroir) {
    case 1:
        console.log('Contient divers outils pour dessiner : du papier, des crayons, etc.');
    break;

    case 2:
        console.log('Contient du matériel informatique : des câbles, des composants, etc.');
    break;

    case 3:
        console.log('Ah ? Ce tiroir est fermé à clé ! Dommage !');
    break;

    case 4:
        console.log('Contient des vêtements : des chemises, des pantalons, etc.');
    break;

    default:
        console.log("Le meuble ne contient que 4 tiroirs.");
}
```

Tout ce qui suit les deux points d’un ```case``` sera exécuté si la variable analysée par le ```switch``` contient la valeur du ```case```.



## **<H2 STYLE="COLOR:BLUE;">7. Les<a name="_page6_x40.00_y544.92"></a> opérateurs logiques**</H2>

- L’opérateur ET se note ```&&``` 
- L’opérateur OU se note ```||``` (Alt Gr + 6)  
- L’opérateur NON se note comme en Python avec ```!``` 

## **<H2 STYLE="COLOR:BLUE;">8. Les<a name="_page6_x40.00_y626.92"></a> boucles 🌀**</H2>

Les boucles permettent d'exécuter plusieurs fois un même bloc de code tant qu'une condition est remplie. Il existe plusieurs types de boucles en JavaScript.

### **<H3 STYLE="COLOR:GREEN;">8.1. L’incrémentation<a name="_page6_x40.00_y648.92"></a>**</H3>

L’incrémentation permet **d’ajouter une unité** à un nombre, tandis que la décrémentation permet **d’en soustraire une unité**. 

**<H3 STYLE="COLOR:red;">Activité n°18 :**</H3> 

```js
let number1 = 0, number2 = 10;

number1++;  // Ajoute 1 à number1
console.log(number1); // Affiche 1

number2--;  // Soustrait 1 à number2
console.log(number2); // Affiche 9
```

⚠️ Attention à la différence entre pré-incrémentation et post-incrémentation :**
```js
let number = 0;

// Pré-incrémentation : incrémente AVANT d'afficher
let result1 = ++number; 
console.log(result1); // Affiche 1

// Post-incrémentation : affiche PUIS incrémente
let number2 = 0;
let result2 = number2++; 
console.log(result2); // Affiche 0 (l’incrémentation se fait après)
console.log(number2); // Affiche 1 (valeur après incrémentation)
```


### **<H3 STYLE="COLOR:GREEN;">8.2. La<a name="_page7_x40.00_y168.92"></a> boucle while**</H3>

La boucle `while` permet d’exécuter du code tant qu’une condition est remplie.

**<H3 STYLE="COLOR:red;">Activité n°19 :**</H3> 

```js
let number = 1;

while (number < 5) {  
    console.log("Itération numéro : " + number);
    number++; // Incrémentation importante pour éviter une boucle infinie
}
console.log("Boucle terminée !");
```

**⚠️ Attention :** Toujours s'assurer que la condition de sortie est bien gérée pour éviter une **boucle infinie**.

### **<H3 STYLE="COLOR:GREEN;">8.3. La<a name="_page7_x40.00_y328.92"></a> boucle do while**</H3>

Contrairement à `while`, la boucle `do while` **s'exécute au moins une fois**, même si la condition n'est pas remplie.

**<H3 STYLE="COLOR:red;">Activité n°20 :**</H3>
```js
let count = 5;

do {
    console.log("Valeur actuelle : " + count);
    count++;
} while (count < 3); // Bien que la condition soit fausse, l'instruction s'exécute une fois
```

### **<H3 STYLE="COLOR:GREEN;">8.4. La<a name="_page7_x40.00_y446.92"></a> boucle for**</H3>

La boucle `for` est souvent utilisée lorsque l’on connaît **le nombre exact d’itérations**.


**<H3 STYLE="COLOR:red;">Activité n°21 :**</H3> 

```js
for (let i = 0; i < 5; i++) { 
    console.log('Itération n°' + i);
}
console.log("Boucle terminée !");
```

**Explication des paramètres :**
1️⃣ **Initialisation** → `let i = 0` (on initialise la variable `i`)  
2️⃣ **Condition** → `i < 5` (on continue tant que `i` est inférieur à 5)  
3️⃣ **Incrémentation** → `i++` (on ajoute 1 à `i` à chaque tour)


## **<H2 STYLE="COLOR:BLUE;">9. Les<a name="_page7_x40.00_y654.92"></a> fonctions 🛠️**</H2>

Une fonction est un **bloc de code réutilisable** qui exécute une tâche précise.

Une fonction peut être déclarée de la manière suivante :
```js
function nomDeLaFonction(arguments) { 
    // Code exécuté par la fonction
}
```


**<H3 STYLE="COLOR:red;">Activité n°22 : Exemple de fonction sans argument :**</H3> 

```js
function showMessage() { 
    console.log("Ceci est une fonction sans argument !");
} 

showMessage(); // On exécute la fonction
```

**Explication :**  
- `showMessage()` affiche un message fixe.
- Elle ne prend aucun argument. 

**<H3 STYLE="COLOR:red;">Activité n°23 : Exemple de fonction avec argument :**</H3> 

Une fonction peut recevoir des **arguments** pour traiter des valeurs différentes à chaque appel.
```js
function greetUser(name) { 
    console.log("Bonjour " + name + " !");
} 

greetUser("Alice"); // Affiche : Bonjour Alice !
greetUser("Bob");   // Affiche : Bonjour Bob !
```

**Explication :**  
- La fonction `greetUser()` prend un argument `name` et affiche un message personnalisé.



**<H3 STYLE="COLOR:red;">Activité n°24 : Exemple de fonction avec** ```prompt()``` :</h3> 

On peut utiliser `prompt()` pour **demander une saisie** à l’utilisateur.

```js
function askName() { 
    let userName = prompt("Quel est votre prénom ?");
    console.log("Bonjour " + userName + " !");
}

askName(); // Demande un nom à l'utilisateur et l'affiche
```

**Explication :**  
- `prompt()` récupère l’entrée de l’utilisateur.
- On stocke cette valeur dans `userName`.
- On l’affiche ensuite avec `console.log()`.



**<H3 STYLE="COLOR:red;">Activité n°25 : Exemple de fonction avec un ```return``` :**</H3> 

La fonction peut renvoyer une **valeur utilisable ailleurs** grâce à `return`.

### **Exemple 4️⃣ : Fonction avec `return`**
```js
function addition(a, b) {
    return a + b; // Retourne la somme des deux nombres
}

let resultat = addition(5, 7); // Stocke le résultat
console.log("Résultat de l'addition : " + resultat); // Affiche 12
```

**Explication :**  
- La fonction **additionne deux nombres** et retourne le résultat.
- Le `return` **renvoie la valeur**, qui est stockée dans `resultat`.

---

**⚠️ Attention : Un `return` met fin à l’exécution de la fonction !**

```js
function testReturn() {
    return "Bonjour !"; 
    console.log("Cette ligne ne sera jamais exécutée !");
}

console.log(testReturn()); // Affiche : Bonjour !
```
🚨 La ligne `console.log("Cette ligne ne sera jamais exécutée !");` **ne s'exécutera pas**, car `return` arrête la fonction immédiatement.



## **<H2 STYLE="COLOR:BLUE;">10. Modeler<a name="_page8_x40.00_y524.92"></a> des pages web avec js 🖥️**</H2>

Le **Document Object Model (DOM)** est une interface qui permet à JavaScript d'interagir avec une page HTML et de modifier son contenu ou son apparence en temps réel. 

### **<H3 STYLE="COLOR:GREEN;">10.1. Manipuler<a name="_page8_x40.00_y578.92"></a> les éléments HTML**</H3>

**<H3 STYLE="COLOR:red;">Activité n°26 :**</H3> 

📌 **Sélection d'un élément par son ID**
La méthode `getElementById()` permet de récupérer un élément HTML unique à partir de son **ID**.

```html
<body>
    <p id="titre">Je suis un titre</p>
    <script>
        var titre = document.getElementById("titre");
        titre.style.color = "blue"; // Change la couleur du texte
    </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°27 :**</H3> 
📌 **Sélection des éléments par leur classe**
La méthode `getElementsByClassName()` permet de récupérer **plusieurs éléments** qui partagent une même classe.

```html
<body>
    <p class="paragraphe">Premier paragraphe</p>
    <p class="paragraphe">Deuxième paragraphe</p>
    <script>
        var paragraphes = document.getElementsByClassName("paragraphe");
        for (var i = 0; i < paragraphes.length; i++) {
            paragraphes[i].style.backgroundColor = "yellow"; // Change le fond
        }
    </script>
</body>
```


**<H3 STYLE="COLOR:red;">Activité n°28 :</H3> Changer la couleur d'un texte au clic** 

Nous allons voir comment JavaScript peut réagir aux **événements** comme un **clic sur un bouton**.

**1️⃣ Créer un fichier `interaction.html` avec le code suivant :**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Interaction avec JS</title>
</head>
<body>
    <h1>Voici un titre</h1>
    <p id="important">Ceci est un texte important.</p>
    <button onclick="changeCouleur()">Cliquez ici</button>
</body>
<script src="interaction.js"></script>
</html>
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.081.png)


**2️⃣ Créer le fichier `interaction.js` et ajouter le code suivant :**
```js
function changeCouleur() {
    var paragraphe = document.getElementById("important");
    paragraphe.style.color = "red"; // Change la couleur en rouge
}
```

**3️⃣ Résultat :** En cliquant sur le bouton, le texte deviendra **rouge**.



![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.086.png)



**<H3 STYLE="COLOR:red;">Activité n°29 :</H3> Amélioration : Ajouter une classe CSS au lieu de modifier directement le style** 

**1️⃣ Créer un fichier `interaction.css` avec le code suivant :**
```css
.rouge { 
    color: red;
    font-size: 30px;
}
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.091.png)

**2️⃣ Modifier `interaction.html` pour inclure le fichier CSS :**
```html
<link rel="stylesheet" href="interaction.css">
```


**3️⃣ Modifier `interaction.js` :**
```js
function changeCouleur() {
    var paragraphe = document.getElementById("important");
    paragraphe.classList.add("rouge"); // Ajoute la classe CSS
}
```

**4️⃣ Ajouter un bouton pour réinitialiser la couleur :**
```html
<button onclick="resetCouleur()">Réinitialiser</button>
```

**5️⃣ Ajouter la fonction correspondante dans `interaction.js` :**
```js
function resetCouleur() {
    var paragraphe = document.getElementById("important");
    paragraphe.classList.remove("rouge"); // Supprime la classe CSS
}
```

✅ **Avantage** : Séparer la logique du design en utilisant **CSS** au lieu de modifier directement les styles avec JavaScript.

---


![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.094.png)





![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.097.png) ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.098.png)

### **<H3 STYLE="COLOR:GREEN;">10.2. Sélectionner<a name="_page10_x40.00_y701.92"></a> des éléments avec `querySelector` et `querySelectorAll`**</H3>



**<H3 STYLE="COLOR:red;">Activité n°30 :**</H3>  
📌 **Sélectionner le premier élément correspondant à une classe**
```html
<body>
    <p class="paragraphe">Paragraphe 1</p>
    <p class="paragraphe">Paragraphe 2</p>
    <script>
        var premierParagraphe = document.querySelector(".paragraphe");
        premierParagraphe.style.fontWeight = "bold"; // Met en gras le premier paragraphe
    </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°31 :**</H3> 
📌 **Sélectionner tous les éléments correspondants à une classe**
```html
<body>
    <p class="paragraphe">Paragraphe 1</p>
    <p class="paragraphe">Paragraphe 2</p>
    <p class="paragraphe">Paragraphe 3</p>
    <script>
        var tousLesParagraphes = document.querySelectorAll(".paragraphe");
        for (var i = 0; i < tousLesParagraphes.length; i++) {
            tousLesParagraphes[i].style.textAlign = "center"; // Centre tous les paragraphes
        }
    </script>
</body>
```


### **<H3 STYLE="COLOR:GREEN;">10.3. Modification<a name="_page11_x40.00_y265.92"></a> de contenu de la page HTML avec la propriété ```innerHTML```**</H3>

**<H3 STYLE="COLOR:red;">Activité n°32 :**</H3> 

📌 **Remplacer le contenu d’un élément**
```html
<body>
    <h1 id="titre">Ancien titre</h1>
    <script>
        var titre = document.getElementById("titre");
        titre.innerHTML = "Nouveau titre";
    </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°33 :**</H3> 

📌 **Ajouter du texte à un élément existant**
```html
<body>
    <p id="paragraphe">Texte original.</p>
    <script>
        var paragraphe = document.getElementById("paragraphe");
        paragraphe.innerHTML += " Texte ajouté.";
    </script>
</body>
```



### **<H3 STYLE="COLOR:GREEN;">10.4. Modification<a name="_page12_x40.00_y111.92"></a> de modification de style de la page HTML avec la propriété style**</H3>

**<H3 STYLE="COLOR:red;">Activité n°34 :**</H3> 

📌 **Changer la couleur de fond**
```html
<body>
    <p id="element">Paragraphe coloré</p>
    <script>
        var element = document.getElementById("element");
        element.style.backgroundColor = "yellow";
    </script>
</body>
```
**<H3 STYLE="COLOR:red;">Activité n°35 :**</H3> 

📌 **Changer plusieurs styles en même temps**
```html
<body>
    <p id="element">Paragraphe stylisé</p>
    <script>
        var element = document.getElementById("element");
        element.style.backgroundColor = "yellow";
        element.style.color = "blue";
        element.style.fontSize = "20px";
    </script>
</body>
```



### **<H3 STYLE="COLOR:GREEN;">10.5. Ajouter<a name="_page13_x40.00_y67.92"></a> et supprimer des classes CSS dynamiquement**</H3>

**<H3 STYLE="COLOR:red;">Activité n°36 :**</H3> 
 
📌 **Ajout d'une classe CSS**
```html
<body>
    <p id="element">Je vais devenir stylé !</p>
    <script>
        var element = document.getElementById("element");
        element.classList.add("nouveauStyle"); // Ajoute une classe CSS
    </script>
</body>
```
**<H3 STYLE="COLOR:red;">Activité n°37 :**</H3> 

📌 **Suppression d'une classe CSS**
```js
element.classList.remove("nouveauStyle");
```

### **<H3 STYLE="COLOR:GREEN;">10.6. Ajouter<a name="_page13_x40.00_y67.92"></a> des événements dynamiquement**</H3>



**<H3 STYLE="COLOR:red;">Activité n°38 :**</H3> 

📌 **Détecter un clic sur un bouton**
```html
<body>
    <button id="bouton">Cliquez-moi</button>
    <script>
        var bouton = document.getElementById("bouton");
        bouton.addEventListener("click", function() {
            console.log("Le bouton a été cliqué !");
        });
    </script>
</body>
```


## **<H2 STYLE="COLOR:BLUE;">11. Interactions<a name="_page14_x40.00_y95.92"></a> avec l’utilisateur 🖱️⌨️**</H2>

Les **événements** en JavaScript permettent de réagir aux actions de l'utilisateur. Ils peuvent être déclenchés par **un clic**, **le passage de la souris**, **une pression sur une touche**, **le remplissage d'un formulaire**, etc.



### **<H3 STYLE="COLOR:GREEN;">11.1. Liste<a name="_page14_x40.00_y174.92"></a> des événements en JS**</H3>

JavaScript propose **différents types d'événements** :

| **Événement**      | **Description** |
|--------------------|----------------|
| `click`          | L'utilisateur clique sur un élément. |
| `dblclick`       | Double-clique sur un élément. |
| `mouseover`      | La souris passe au-dessus d’un élément. |
| `mouseout`       | La souris sort d’un élément. |
| `mousedown`      | L'utilisateur appuie sur un bouton de la souris. |
| `mouseup`        | L'utilisateur relâche le bouton de la souris. |
| `mousemove`      | La souris se déplace au-dessus de l’élément. |
| `keydown`        | Une touche du clavier est enfoncée. |
| `keyup`          | Une touche du clavier est relâchée. |
| `keypress`       | Une touche du clavier est pressée et relâchée. |
| `focus`          | Un champ de formulaire reçoit le focus. |
| `blur`           | Un champ de formulaire perd le focus. |
| `change`         | La valeur d’un champ change. |
| `input`          | L'utilisateur modifie un champ en tapant du texte. |
| `select`         | Le texte est sélectionné dans un champ de texte. |
| `submit`        | Un formulaire est soumis. |
| `resize`        | La fenêtre est redimensionnée. |
| `scroll`        | L’utilisateur fait défiler la page. |

👉 Pour une **liste complète**, consultez la documentation :  
🔗 [Liste des événements JavaScript](https://www.lehtml.com/js/even.htm)

### **<H3 STYLE="COLOR:GREEN;">11.2. <a name="_page14_x40.00_y550.92"></a> Manipuler les événements en JavaScript**</H3>

**<H3 STYLE="COLOR:red;">Activité n°39 :**</H3> 

📌 **Exécuter une alerte lors d’un clic**  
Dans cet exemple, un simple **clic** sur le texte affichera une alerte.

🔹 **Créer un fichier `evenement.html` et y insérer le code suivant** :

```html
<body>
    <span onclick="alert('Hello')">Cliquez ici !</span>
</body>
```
✅ **Explication** : Lorsqu’on clique sur le texte, l’alerte `"Hello"` s’affiche.

---

**<H3 STYLE="COLOR:red;">Activité n°40 :**</H3> 

📌 **Utiliser `addEventListener()` pour un clic sur un bouton**
```html
<body>
    <button id="bouton">Cliquez ici !</button>
    <script>
        var bouton = document.getElementById("bouton");
        bouton.addEventListener("click", function() {
            console.log("Bouton cliqué !");
        });
    </script>
</body>
```
✅ **Explication** :  
- `getElementById("bouton")` cible le bouton.
- `addEventListener("click", function() {...})` écoute le clic et exécute la fonction.

**<H3 STYLE="COLOR:red;">Activité n°41 :**</H3> 

**Changer la couleur d’un élément lorsque la souris passe dessus**
```html
<body>
    <p id="maDiv">Passez la souris ici !</p>
    <script>
        var div = document.getElementById("maDiv");
        div.addEventListener("mouseover", function() {
            div.style.backgroundColor = "red";
        });
    </script>
</body>
```
✅ **Explication** : Lorsque la souris **survole** l'élément, son fond devient **rouge**.

**<H3 STYLE="COLOR:red;">Activité n°42 :**</H3> 

📌 **Détecter la touche appuyée sur le clavier**
```html
<body>
    <p>Appuyez sur une touche...</p>
    <script>
        document.addEventListener("keydown", function(event) {
            console.log("Touche pressée : " + event.key);
        });
    </script>
</body>
```
✅ **Explication** :  
- `keydown` détecte une touche **enfoncée**.
- `event.key` affiche la touche appuyée.

### **<H3 STYLE="COLOR:GREEN;">11.3. Le mot-clé `this` référence l’élément HTML qui a déclenché l’événement**.</H3>

**<H3 STYLE="COLOR:red;">Activité n°43 :**</H3> 

Le mot-clé `this` **référence l’élément HTML qui a déclenché l’événement**.

📌 **Modifier un champ de texte au focus et blur**
```html
<body>
    <input type="text" id="input" size="50" value="Cliquez ici"
           onfocus="this.value = 'Écrivez quelque chose...'"
           onblur="this.value = 'Cliquez ici !'">
</body>
```
✅ **Explication** :  
- **`onfocus`** → Quand l'utilisateur clique sur le champ, le texte change.
- **`onblur`** → Quand il quitte le champ, le texte revient à sa valeur initiale.

### **<H3 STYLE="COLOR:GREEN;">11.4. Ajouter plusieurs événements à un même élément**.</H3>

On peut attacher plusieurs événements **à un seul élément**.

**<H3 STYLE="COLOR:red;">Activité n°44 :**</H3> 

📌 **Ajouter plusieurs événements avec `addEventListener()`**
```html
<!DOCTYPE html>
<html>
<body>
    <button id="clickIt">Cliquez ici !</button> 
    <p id="hoverPara">Passez la souris sur ce texte !</p>
    <b id="effect"></b>

    <script>
        const bouton = document.getElementById("clickIt");
        const texte = document.getElementById("hoverPara");

        bouton.addEventListener("click", RespondClick);
        texte.addEventListener("mouseover", RespondMouseOver);
        texte.addEventListener("mouseout", RespondMouseOut);

        function RespondClick() {
            document.getElementById("effect").innerHTML += "Clic détecté !<br>";
        }

        function RespondMouseOver() {
            document.getElementById("effect").innerHTML += "MouseOver détecté !<br>";
        }

        function RespondMouseOut() {
            document.getElementById("effect").innerHTML += "MouseOut détecté !<br>";
        }
    </script>
</body>
</html>
```
✅ **Explication** :  
- **Le bouton** déclenche un message `"Clic détecté !"`.
- **Le texte** affiche `"MouseOver détecté !"` quand la souris passe dessus.
- **Le texte** affiche `"MouseOut détecté !"` quand la souris quitte.



### **<H3 STYLE="COLOR:GREEN;">11.5. Pour<a name="_page16_x40.00_y319.92"></a> aller plus loin : Supprimer un écouteur d’événement**</H3>

Avec `removeEventListener()`, on peut **désactiver un événement**.

**<H3 STYLE="COLOR:red;">Activité n°45 :**</H3>

📌 **Supprimer un événement après un clic**
```html
<body>
    <button id="desactiver">Désactiver le clic</button>
    <button id="bouton">Cliquez ici !</button>
    <script>
        var bouton = document.getElementById("bouton");
        var desactiver = document.getElementById("desactiver");

        function afficherMessage() {
            console.log("Bouton cliqué !");
        }

        bouton.addEventListener("click", afficherMessage);

        desactiver.addEventListener("click", function() {
            bouton.removeEventListener("click", afficherMessage);
            console.log("L'événement a été supprimé !");
        });
    </script>
</body>
```
✅ **Explication** :  
- `removeEventListener("click", afficherMessage)` **désactive l'événement**.

       

**Pour aller plus loin ou avoir plus de détails** : [https://www.w3schools.com/jsref/dom_obj_all.asp](https://www.w3schools.com/jsref/dom_obj_all.asp) ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)

## **<H2 STYLE="COLOR:BLUE;">12. Exercices<a name="_page18_x40.00_y36.92"></a>**</H2>

=> CAPYTALE Le code vous sera donné par votre enseignant 

**<H3 STYLE="COLOR:red;">Exercice 1 : Jeu de devinette de nombre**</H3>

**But du jeu :** L'utilisateur doit deviner un nombre aléatoire entre 1 et 100.

**Étapes :**
1. **HTML :** Créez une structure de base avec un champ de saisie pour entrer la supposition et un bouton pour soumettre la supposition.
2. **JavaScript :**
   - Générer un nombre aléatoire entre 1 et 100.
   - Ajouter un événement de clic au bouton de soumission.
   - Lorsque le bouton est cliqué, récupérer la supposition de l'utilisateur et vérifier si elle est correcte, trop élevée ou trop basse.
   - Afficher un message indiquant si la supposition est correcte, trop élevée ou trop basse.
   - Utiliser une boucle pour permettre plusieurs essais jusqu'à ce que l'utilisateur devine correctement.

**Code HTML de exo1.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Jeu de Devinette</title>
</head>
<body>
    <h1>Devinez le nombre</h1>
    <p>Je pense à un nombre entre 1 et 100. Pouvez-vous le deviner ?</p>
    <input type="number" id="guess" placeholder="Entrez votre supposition">
    <button id="submitGuess">Soumettre</button>
    <p id="result"></p>
    <script src="exo1.js"></script>
</body>
</html>
```

**Code JavaScript de exo1.js à trous à compléter**
```javascript
// exo1.js

// Question 1 : Quelle méthode permet de

 générer un nombre aléatoire entre 1 et 100 ?
// Remplissez le blanc avec la bonne méthode pour générer un nombre aléatoire.
// Indice : Utilisez Math.random() et Math.floor().
let randomNumber = ...(... * 100) + 1;

let guesses = 0;

// Question 2 : Comment ajouter un événement de clic au bouton "Soumettre" ?
document.getElementById('submitGuess').addEventListener(..., function() {

    let userGuess = parseInt(document.getElementById('guess').value);
    guesses++;
    
    // Question 3 : Où devons-nous afficher le résultat du jeu ?
    let result = document.getElementById(...);

    // Question 4 : Comment vérifier si la supposition de l'utilisateur est correcte ?
    if (... === randomNumber) {
        result.textContent = `Félicitations ! Vous avez deviné le nombre en ${guesses} essais.`;
    } else if (userGuess < randomNumber) {
        // Question 5 : Complétez le message à afficher lorsque la supposition est trop basse.
        result.textContent = ...;
    } else {
        // Question 6 : Complétez le message à afficher lorsque la supposition est trop haute.
        result.textContent = ...;
    }
});
```

**<H3 STYLE="COLOR:red;">Exercice 2 : Calculatrice de base**</H3>
**Concepts : Variables, opérateurs, fonctions**
- **Mise en contexte :** Développez une calculatrice simple où les utilisateurs peuvent entrer deux nombres et choisir une opération (addition, soustraction, multiplication, division) pour obtenir le résultat.

**Code HTML de exo2.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Calculatrice</title>
</head>
<body>
    <h1>Calculatrice Simple</h1>
    <input type="number" id="num1" placeholder="Nombre 1">
    <input type="number" id="num2" placeholder="Nombre 2">
    <select id="operation">
        <option value="add">Addition</option>
        <option value="subtract">Soustraction</option>
        <option value="multiply">Multiplication</option>
        <option value="divide">Division</option>
    </select>
    <button id="calculate">Calculer</button>
    <p id="result"></p>
    <script src="exo2.js"></script>
</body>
</html>
```

**Code JavaScript de exo2.js à trous à compléter**
```javascript
// exo2.js
document.getElementById('calculate').addEventListener('click', function() {
    let num1 = parseFloat(document.getElementById('num1').value);
    let num2 = parseFloat(document.getElementById('num2').value);
    let operation = document.getElementById('operation').value;
    let result;

    if (operation === 'add') {
        result = num1 + num2;
    } else if (operation === 'subtract') {
        result = num1 - num2;
    } else if (operation === 'multiply') {
        result = num1 * num2;
    } else if (operation === 'divide') {
        result = num1 / num2;
    }

    document.getElementById('result').textContent = 'Résultat : ' + result;
});
```

**<H3 STYLE="COLOR:red;">Exercice 3 : Liste de tâches (To-Do List)**</H3>
**Concepts : Manipulation du DOM, événements, boucles**
- **Mise en contexte :** Créez une application où les utilisateurs peuvent ajouter des tâches, les marquer comme complétées, et les supprimer.

**Code HTML de exo3.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Liste de Tâches</title>
</head>
<body>
    <h1>Liste de Tâches</h1>
    <input type="text" id="taskInput" placeholder="Nouvelle tâche">
    <button id="addTask">Ajouter</button>
    <ul id="taskList"></ul>
    <script src="exo3.js"></script>
</body>
</html>
```

**Code JavaScript de exo3.js à trous à compléter**
```javascript
// exo3.js
// Question 1 : Comment ajouter un événement de clic au bouton "Ajouter" ?
document.getElementById('addTask').addEventListener(..., function() {

    // Question 2 : Comment récupérer la valeur du champ de saisie ?
    let taskInput = document.getElementById('taskInput');
    let taskText = taskInput....;

    taskInput.value = '';

    // Question 3 : Comment créer un nouvel élément de liste (li) pour la nouvelle tâche ?
    let li = document.createElement(...);
    li.textContent = taskText;

    // Question 4 : Comment créer un bouton pour marquer la tâche comme complétée ?
    let completeButton = document.createElement(...);
    completeButton.textContent = 'Compléter';
    completeButton.addEventListener('click', function() {
        li.style.textDecoration = 'line-through';
    });

    // Question 5 : Comment créer un bouton pour supprimer la tâche ?
    let deleteButton = document.createElement(...);
    deleteButton.textContent = 'Supprimer';
    deleteButton.addEventListener('click', function() {
        li.remove();
    });

    // Question 6 : Comment ajouter les boutons à l'élément de liste ?
    li.appendChild(...);
    li.appendChild(...);

    // Question 7 : Comment ajouter l'élément de liste à la liste de tâches ?
    document.getElementById(...).appendChild(li);
});
```

**<H3 STYLE="COLOR:red;">Exercice 4 : Quiz interactif**</H3>
**Concepts : Conditions, boucles, manipulation du DOM**
- **Mise en contexte :** Créez un quiz où les utilisateurs répondent à une série de questions et reçoivent une note à la fin.

**Code HTML de exo4.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Quiz Interactif</title>
</head>
<body>
    <h1>Quiz Interactif</h1>
    <div id="quiz">
        <p>1. Quelle est la capitale de la France ?</p>
        <input type="radio" name="q1" value="Paris"> Paris<br>
        <input type="radio" name="q1" value="Londres"> Londres<br>
        <input type="radio" name="q1" value="Berlin"> Berlin<br>
        <p>2. Quelle est la capitale de l'Allemagne ?</p>
        <input type="radio" name="q2" value="Paris"> Paris<br>
        <input type="radio" name="q2" value="Londres"> Londres<br>
        <input type="radio" name="q2" value="Berlin"> Berlin<br>
        <button id="submitQuiz">Soumettre</button>
        <p id="result"></p>
    </div>
    <script src="exo4.js"></script>
</body>
</html>
```

**Code JavaScript de exo4.js à trous à compléter**
```javascript
// exo4.js
document.getElementById('submitQuiz').addEventListener('click', function() {
    let score = 0;
    let totalQuestions = 2;

    let q1 = document.querySelector('input[name="q1"]:checked');
    let q2 = document.querySelector('input[name="q2"]:checked');

    if (q1 && q1.value === 'Paris') {
        score++;
    }

    if (q2 && q2.value === 'Berlin') {
        score++;
    }

    let result = document.getElementById('result');
    result.textContent = `Vous avez obtenu ${score} sur ${totalQuestions}`;
});
```
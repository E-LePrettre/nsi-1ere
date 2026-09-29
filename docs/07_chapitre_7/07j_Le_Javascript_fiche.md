---
author: Elisabeth Le Prettre (LePrettre)
title: 07c 📜 Fiche Méthode - Le Javascript
---

# JavaScript : interactivité des pages

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 11"
    Fiche **compacte** pour **refaire seul les exercices** : scripts, variables,
    conditions, fonctions, manipulation du **DOM** et **événements**.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** où placer un script et les instructions de base ;
- **lire** du code JS et **prévoir** ses affichages / effets ;
- **expliquer** le rôle du DOM et des événements ;
- **compléter** et **programmer** : variables, conditions, fonctions, sélection et
  modification d'éléments, écouteurs d'événements.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **JavaScript** | Langage rendant les pages **interactives**. |
| **Côté client** | Exécuté dans le **navigateur**. |
| **Script** | Programme JS (`<script>`). |
| **Console** | Zone d'affichage / débogage du navigateur. |
| **Variable** | Donnée nommée modifiable (`let`). |
| **Constante** | Donnée non modifiable (`const`). |
| **Type** | Nature d'une valeur (nombre, chaîne, booléen). |
| **Concaténation** | Coller des chaînes avec `+`. |
| **Conversion** | Changer de type (`parseInt`…). |
| **Condition** | Test (`if`). |
| **Fonction** | Bloc réutilisable. |
| **Paramètre** | Entrée d'une fonction. |
| **Valeur retournée** | Résultat (`return`). |
| **DOM** | Représentation de la page manipulable par JS. |
| **Élément** | Nœud du DOM (une balise). |
| **Événement** | Action de l'utilisateur (clic, saisie…). |
| **Écouteur** | Fonction déclenchée par un événement. |

---

## 3. Fiches méthodes

??? note "Intégrer JavaScript dans HTML"
    ```html
    <script>
      console.log("Bonjour");
    </script>
    ```

??? note "Relier un fichier `.js` externe"
    ```html
    <script src="script.js"></script>
    ```
    À placer en **fin de `<body>`** (après les éléments).

??? note "Afficher avec `alert()` ou `console.log()`"
    ```javascript
    alert("Message");        // fenêtre
    console.log("Débug");    // console
    ```

??? note "Demander une saisie avec `prompt()`"
    ```javascript
    let nom = prompt("Ton nom ?");
    ```

??? note "Demander une confirmation avec `confirm()`"
    ```javascript
    let ok = confirm("Confirmer ?");   // true / false
    ```

??? note "Déclarer avec `var`, `let` ou `const`"
    ```javascript
    let age = 15;        // variable
    const PI = 3.14;     // constante
    ```

??? note "Chaîne avec caractères d'échappement"
    ```javascript
    let s = "Il dit \"bonjour\"\n";   // \" guillemet, \n retour ligne
    ```

??? note "Calcul ou concaténation"
    ```javascript
    let somme = a + b;               // calcul
    let txt = "Bonjour " + nom;      // concaténation
    ```

??? note "Convertir avec `parseInt()` ou `parseFloat()`"
    ```javascript
    let n = parseInt(prompt("Nombre ?"));    // entier
    let x = parseFloat("3.14");              // décimal
    ```
    - **Erreur :** oublier la conversion (`"3" + 2` donne `"32"`).

??? note "Condition `if / else if / else`"
    ```javascript
    if (note >= 10) {
      resultat = "Admis";
    } else {
      resultat = "Recalé";
    }
    ```

??? note "Opérateurs `===`, `!==`, `&&`, `||`, `!`"
    - `===` (égal, **type compris**), `!==` (différent) ;
    - `&&` (et), `||` (ou), `!` (non).

??? note "Créer et appeler une fonction"
    ```javascript
    function doubler(x) {
      return 2 * x;
    }
    let r = doubler(5);   // 10
    ```

??? note "Choisir les paramètres"
    Les **entrées** nécessaires au calcul (ex. `function imc(poids, taille)`).

??? note "Retourner une valeur avec `return`"
    `return resultat;` renvoie la valeur (réutilisable).

??? note "Sélectionner avec `getElementById()`"
    ```javascript
    let titre = document.getElementById("titre");
    ```

??? note "Sélectionner plusieurs éléments"
    ```javascript
    let items = document.getElementsByClassName("item");
    ```

??? note "Récupérer la valeur d'un champ avec `.value`"
    ```javascript
    let saisie = document.getElementById("champ").value;
    ```

??? note "Modifier `textContent` ou `innerHTML`"
    ```javascript
    el.textContent = "Texte brut";
    el.innerHTML = "<b>Texte en gras</b>";
    ```

??? note "Modifier un style avec `.style`"
    ```javascript
    el.style.color = "red";
    el.style.backgroundColor = "yellow";
    ```

??? note "Ajouter ou retirer une classe"
    ```javascript
    el.classList.add("actif");
    el.classList.remove("actif");
    ```

??? note "Ajouter un événement avec `addEventListener()`"
    ```javascript
    bouton.addEventListener("click", function() {
      alert("Cliqué !");
    });
    ```

??? note "Utiliser `this` ou l'objet `event`"
    ```javascript
    champ.addEventListener("input", function(event) {
      console.log(event.target.value);   // ou this.value
    });
    ```

??? note "Créer, ajouter et supprimer un élément"
    ```javascript
    let li = document.createElement("li");
    li.textContent = "Tâche";
    liste.appendChild(li);     // ajouter
    liste.removeChild(li);     // supprimer
    ```
    - **Erreur :** oublier d'**ajouter** l'élément créé à la page.

---

## 4. Tableaux comparatifs

!!! note "HTML / CSS / JavaScript"
    | Langage | Rôle |
    |---|---|
    | **HTML** | structure / contenu |
    | **CSS** | mise en forme |
    | **JavaScript** | comportement / interactivité |

!!! note "`alert` / `confirm` / `prompt`"
    | Fonction | Renvoie |
    |---|---|
    | `alert` | rien (message) |
    | `confirm` | `true` / `false` |
    | `prompt` | la **saisie** (chaîne) |

!!! note "`var` / `let` / `const`"
    | Mot-clé | Usage |
    |---|---|
    | `var` | ancien (à éviter) |
    | `let` | variable modifiable |
    | `const` | constante (non modifiable) |

!!! note "`==` / `===` et `!=` / `!==`"
    | Opérateur | Comparaison |
    |---|---|
    | `==` / `!=` | **avec** conversion de type |
    | `===` / `!==` | **sans** conversion (type compris) |

!!! note "`innerHTML` / `textContent`"
    | Propriété | Effet |
    |---|---|
    | `innerHTML` | interprète le **HTML** |
    | `textContent` | **texte brut** |

!!! note "Style direct / classe CSS"
    | Méthode | Quand |
    |---|---|
    | `.style.x` | modification **ponctuelle** |
    | `classList.add/remove` | style **réutilisable** (CSS) |

!!! note "Événements principaux"
    `click` · `input` · `change` · `mouseover` · `submit` · `keydown`.

---

## 5. Lecture et compréhension de code

!!! tip "Méthode"
    - **suivre les variables** (valeurs successives) ;
    - **prévoir les affichages** (`alert`, `console.log`) ;
    - **déterminer le bloc exécuté** (condition vraie) ;
    - **retrouver une valeur retournée** (`return`) ;
    - **identifier l'élément sélectionné** (`getElementById`) ;
    - **suivre un événement** (déclencheur → écouteur → effet) ;
    - **compléter un code à trous** ;
    - **expliquer les modifications du DOM**.

---

## 6. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Exécution**
    | Instruction | Variable | Valeur | Affichage |
    |---|---|---|---|

    **Saisie & condition**
    | Saisie | Conversion | Condition | Bloc exécuté |
    |---|---|---|---|

    **Événement & DOM**
    | Événement | Élément cible | Propriété modifiée | Résultat visible |
    |---|---|---|---|

---

## 7. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| **Script non relié** | vérifier `<script src="…">` |
| Script **avant** l'élément | placer le script en **fin de `<body>`** |
| **Oubli de guillemets** | entourer les chaînes |
| **Texte / nombre** confondus | convertir avec `parseInt` / `parseFloat` |
| Oubli de **conversion** | `"3" + 2 = "32"` au lieu de `5` |
| **`=` / `==` / `===`** confondus | `=` affecte ; `===` compare (type compris) |
| **Opérateur logique** incorrect | `&&` (et), `||` (ou), `!` (non) |
| **Accolade manquante** | fermer `{ … }` |
| **Fonction non appelée** | `f()` avec parenthèses |
| **Oubli de `return`** | renvoie `undefined` |
| **Mauvais `id`** | vérifier l'`id` dans le HTML |
| **`id` / classe** confondus | `getElementById` vs `getElementsByClassName` |
| **Oubli de `.value`** | récupérer la **valeur** du champ |
| **Mauvais nom d'événement** | `"click"`, `"input"`… |
| **`addEventListener` mal appelé** | `(\"click\", fonction)` sans `()` sur la fonction |
| **Élément inexistant** modifié | vérifier la sélection |
| Oubli d'**ajouter** l'élément créé | `appendChild` |

---

## 8. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Où s'exécute JavaScript ?"
    **Côté client**, dans le navigateur.

??? question "2. (N1) Que renvoie `prompt()` ?"
    La **saisie** de l'utilisateur (une chaîne).

??? question "3. (N2) Différence entre `let` et `const` ?"
    `let` est **modifiable** ; `const` est une **constante**.

??? question "4. (N2) Qu'est-ce que le DOM ?"
    La représentation de la page que JavaScript peut **manipuler**.

??? question "5. (N1) Qu'est-ce qu'un écouteur d'événement ?"
    Une fonction **déclenchée** par une action (clic, saisie…).

### Compréhension

??? question "6. (N1) Que vaut `\"3\" + 2` en JavaScript ?"
    `\"32\"` (concaténation, car `\"3\"` est une chaîne).

??? question "7. (N2) Pourquoi utiliser `parseInt(prompt(...))` ?"
    Car `prompt` renvoie une **chaîne** : il faut la **convertir** en nombre.

??? question "8. (N2) Différence entre `==` et `===` ?"
    `==` compare **avec** conversion ; `===` compare **sans** (type compris).

??? question "9. (N3) Différence entre `textContent` et `innerHTML` ?"
    `textContent` = texte **brut** ; `innerHTML` **interprète** le HTML.

??? question "10. (N2) Pourquoi placer le script en fin de `<body>` ?"
    Pour que les **éléments existent** déjà quand le script s'exécute.

### Lecture de code

??? question "11. (N1) Que fait `console.log(2 + 3)` ?"
    Affiche `5` dans la console.

??? question "12. (N2) Que vaut `doubler(4)` si `doubler(x){return 2*x;}` ?"
    `8`.

??? question "13. (N2) Que sélectionne `document.getElementById(\"titre\")` ?"
    L'élément ayant `id=\"titre\"`.

??? question "14. (N3) Que fait `el.style.color = \"red\"` ?"
    Met le texte de `el` en **rouge**.

??? question "15. (N2) Que récupère `champ.value` ?"
    La **valeur saisie** dans le champ.

### Conditions et fonctions

??? question "16. (N1) Écrire une condition « si x > 0 »."
    `if (x > 0) { … }`.

??? question "17. (N2) Écrire l'opérateur « et » logique."
    `&&`.

??? question "18. (N2) Créer une fonction `carre(x)`."
    `function carre(x) { return x * x; }`.

??? question "19. (N3) Que renvoie une fonction sans `return` ?"
    `undefined`.

??? question "20. (N3) Appeler `carre(5)` : comment récupérer le résultat ?"
    `let r = carre(5);` (vaut 25).

### DOM et événements

??? question "21. (N1) Sélectionner un élément `id=\"p1\"`."
    `document.getElementById(\"p1\")`.

??? question "22. (N2) Modifier le texte d'un élément `el`."
    `el.textContent = \"…\";`.

??? question "23. (N2) Ajouter un clic sur un bouton `btn`."
    `btn.addEventListener(\"click\", fonction);`.

??? question "24. (N3) Récupérer la valeur tapée lors d'un événement."
    `event.target.value` (ou `this.value`).

??? question "25. (N3) Créer un `<li>` et l'ajouter à `liste`."
    ```javascript
    let li = document.createElement(\"li\");
    liste.appendChild(li);
    ```

### Correction d'erreurs

??? question "26. (N1) `let nom = prompt(Ton nom)` : erreur ?"
    Guillemets manquants : `prompt(\"Ton nom\")`.

??? question "27. (N2) `if (x = 5)` : erreur ?"
    `=` affecte ; utiliser `===` : `if (x === 5)`.

??? question "28. (N2) Saisie additionnée sans `parseInt` : erreur ?"
    Concaténation de chaînes : convertir avec `parseInt`.

??? question "29. (N3) `getElementById(\".titre\")` : erreur ?"
    Pas de `.` : `getElementById(\"titre\")`.

??? question "30. (N3) Élément créé mais absent de la page : erreur ?"
    Oubli de `appendChild`.

### Programmation

??? question "31. (N1) Écrire un `console.log` affichant « Salut »."
    `console.log(\"Salut\");`.

??? question "32. (N2) Convertir une saisie en nombre entier."
    `let n = parseInt(prompt(\"Nombre ?\"));`.

??? question "33. (N2) Modifier la couleur d'un paragraphe `p1` en bleu."
    `document.getElementById(\"p1\").style.color = \"blue\";`.

??? question "34. (N3) Calculatrice : afficher la somme de deux saisies."
    ```javascript
    let a = parseInt(prompt(\"a ?\"));
    let b = parseInt(prompt(\"b ?\"));
    alert(a + b);
    ```

??? question "35. (N4) Devinette : comparer une saisie à un nombre secret."
    ```javascript
    let secret = 7;
    let essai = parseInt(prompt(\"Devine :\"));
    if (essai === secret) {
      alert(\"Gagné !\");
    } else {
      alert(\"Perdu\");
    }
    ```

---

## 9. Exercices flash corrigés

??? question "Écrire un `console.log` de 10 + 5"
    `console.log(10 + 5);` → `15`.

??? question "Convertir une saisie en décimal"
    `parseFloat(prompt(\"Nombre ?\"))`.

??? question "Compléter une condition « note ≥ 10 »"
    `if (note >= 10) { … }`.

??? question "Choisir `==` ou `===` pour comparer types compris"
    `===`.

??? question "Écrire une fonction `triple(x)`"
    `function triple(x) { return 3 * x; }`.

??? question "Sélectionner le paragraphe `id=\"intro\"`"
    `document.getElementById(\"intro\")`.

??? question "Modifier son texte"
    `…getElementById(\"intro\").textContent = \"…\";`.

??? question "Modifier sa couleur en vert"
    `…style.color = \"green\";`.

??? question "Ajouter un clic affichant « Coucou »"
    `btn.addEventListener(\"click\", () => alert(\"Coucou\"));`.

??? question "Créer un élément `<li>` (liste de tâches)"
    `let li = document.createElement(\"li\");` puis `liste.appendChild(li);`.

??? question "Prévoir le résultat : `el.innerHTML = \"<b>Hi</b>\"`"
    Affiche **Hi** en gras (HTML interprété).

---

## À retenir absolument

!!! success "Squelette JavaScript"
    ```html
    <script src="script.js"></script>   <!-- en fin de body -->
    ```
    ```javascript
    let x = parseInt(prompt("Nombre ?"));   // saisie + conversion
    if (x > 0) { console.log("positif"); }  // condition
    function f(a) { return a * 2; }          // fonction
    ```

!!! note "DOM & événements"
    - **sélection** : `document.getElementById("id")` ;
    - **valeur d'un champ** : `.value` ;
    - **modifier le contenu** : `textContent` (brut) / `innerHTML` (HTML) ;
    - **style** : `.style.color = "…"` ou `classList.add/remove` ;
    - **événement** : `el.addEventListener("click", fonction)` ;
    - **créer** : `createElement` + `appendChild`.

!!! quote "Réflexes"
    - relier le **fichier externe** et placer le script **après** les éléments ;
    - **convertir** les saisies (`parseInt` / `parseFloat`) ;
    - comparer avec **`===`** ; ne pas oublier **`return`** ni **`appendChild`**.
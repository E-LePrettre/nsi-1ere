---
author: Elisabeth Le Prettre (LePrettre)
title: 076b 📜 Fiche Méthode - Le CSS
---

# CSS : mise en forme des pages

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 10"
    Fiche **compacte** pour **refaire seul les exercices** : sélecteurs, règles,
    texte, couleurs, bordures, tableaux et **modèle des boîtes**.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** la syntaxe d'une règle CSS et les sélecteurs ;
- **lire** une feuille de style et **prévoir** les éléments concernés ;
- **expliquer** classe vs id, bloc vs en ligne, le **modèle des boîtes** ;
- **réaliser** : texte, couleurs, bordures, tableaux, mise en page de boîtes.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **CSS** | Langage de **mise en forme** des pages HTML. |
| **Feuille externe** | Fichier `.css` relié à la page. |
| **Sélecteur** | Cible les éléments à styliser. |
| **Propriété** | Aspect à modifier (`color`, `font-size`…). |
| **Valeur** | Réglage de la propriété. |
| **Règle** | `sélecteur { propriété: valeur; }`. |
| **Classe** | Style **réutilisable** (`.nom`). |
| **Identifiant** | Style pour **un seul** élément (`#nom`). |
| **Pseudo-classe** | État d'un élément (`:hover`…). |
| **Bloc** | Élément occupant toute la largeur (`<div>`). |
| **Élément en ligne** | Élément dans le flux du texte (`<span>`). |
| **Modèle des boîtes** | contenu + **padding** + **border** + **margin**. |
| **Contenu** | Texte / image de la boîte. |
| **Padding** | Espace **intérieur** (contenu ↔ bordure). |
| **Border** | **Bordure** de la boîte. |
| **Margin** | Espace **extérieur** (entre boîtes). |

---

## 3. Fiches méthodes

??? note "Créer et relier `style.css`"
    Dans `<head>` :
    ```html
    <link rel="stylesheet" href="style.css">
    ```
    - **Erreur :** oublier le `<link>` ou se tromper de **chemin**.

??? note "Écrire une règle CSS"
    ```css
    sélecteur {
      propriété: valeur;
    }
    ```
    - **Erreur :** oublier les **accolades**, le **`:`** ou le **`;`**.

??? note "Appliquer un style à une balise"
    ```css
    p { color: blue; }
    ```

??? note "Appliquer une règle à plusieurs balises"
    ```css
    h1, h2 { color: red; }
    ```

??? note "Créer et utiliser une classe"
    ```css
    .important { font-weight: bold; }
    ```
    ```html
    <p class="important">…</p>
    ```

??? note "Créer et utiliser un identifiant"
    ```css
    #haut { background-color: yellow; }
    ```
    ```html
    <div id="haut">…</div>
    ```

??? note "Choisir entre `class` et `id`"
    - **classe** : **réutilisable** (plusieurs éléments) ;
    - **id** : **unique** (un seul élément).

??? note "Utiliser `<div>` et `<span>`"
    - `<div>` : conteneur **bloc** ; `<span>` : conteneur **en ligne**.

??? note "Modifier taille, police, graisse, italique, décoration"
    ```css
    p {
      font-size: 16px;
      font-family: Arial, sans-serif;
      font-weight: bold;
      font-style: italic;
      text-decoration: underline;
    }
    ```

??? note "Aligner du texte"
    ```css
    h1 { text-align: center; }
    ```

??? note "Centrer une image"
    ```css
    img { display: block; margin: auto; }
    ```

??? note "Choisir une couleur (nom, hex, RGB, RGBA)"
    ```css
    color: red;
    color: #ff0000;
    color: rgb(255, 0, 0);
    color: rgba(255, 0, 0, 0.5);   /* avec transparence */
    ```

??? note "Couleur ou image de fond"
    ```css
    body { background-color: #eee; }
    body { background-image: url("fond.png"); }
    ```
    - **Erreur :** chemin incorrect dans `url()`.

??? note "Bordure et coins arrondis"
    ```css
    div { border: 2px solid black; border-radius: 10px; }
    ```

??? note "Ajouter une ombre"
    ```css
    div { box-shadow: 2px 2px 5px gray; }
    ```

??? note "Pseudo-classes `:hover`, `:active`, `:visited`"
    ```css
    a:hover   { color: red; }      /* survol */
    a:active  { color: orange; }   /* clic */
    a:visited { color: purple; }   /* déjà visité */
    ```

??? note "Mettre en forme un tableau"
    ```css
    table { border-collapse: collapse; }
    th, td { border: 1px solid black; padding: 4px; }
    ```

??? note "Utiliser width, height, padding, border, margin"
    ```css
    .boite {
      width: 200px;
      height: 100px;
      padding: 10px;     /* intérieur */
      border: 1px solid; /* bordure */
      margin: 20px;      /* extérieur */
    }
    ```

??? note "Centrer une boîte avec `margin: auto`"
    ```css
    .boite { width: 300px; margin: auto; }
    ```
    - **Erreur :** oublier la **largeur** (sinon `margin: auto` ne centre pas).

---

## 4. Tableaux récapitulatifs

!!! note "Emplacement du CSS"
    | Emplacement | Exemple |
    |---|---|
    | **Feuille externe** (recommandé) | `<link rel="stylesheet" href="style.css">` |
    | Interne | `<style>…</style>` dans `<head>` |
    | En ligne | attribut `style="…"` |

!!! note "Sélecteurs"
    | Sélecteur | Cible | Exemple |
    |---|---|---|
    | **balise** | tous les éléments | `p { }` |
    | **classe** | `class="…"` | `.menu { }` |
    | **id** | `id="…"` | `#haut { }` |

!!! note "Propriétés de texte"
    `font-size` · `font-family` · `font-weight` · `font-style` · `text-decoration` · `text-align` · `color`.

!!! note "Codages de couleurs"
    | Forme | Exemple (rouge) |
    |---|---|
    | nom | `red` |
    | hexadécimal | `#ff0000` |
    | RGB | `rgb(255, 0, 0)` |
    | RGBA | `rgba(255, 0, 0, 0.5)` |

!!! note "Bordures"
    `border: épaisseur style couleur;` (ex. `2px solid black`) · `border-radius` · `box-shadow`.

!!! note "Pseudo-classes"
    | Pseudo-classe | État |
    |---|---|
    | `:hover` | survol de la souris |
    | `:active` | élément cliqué |
    | `:visited` | lien déjà visité |

!!! note "Modèle des boîtes (de l'intérieur vers l'extérieur)"
    **contenu** → **padding** → **border** → **margin**.

---

## 5. Lecture et compréhension de code

!!! tip "Méthode"
    - **prévoir les éléments concernés** par une règle (lire le sélecteur) ;
    - **retrouver une erreur de sélecteur** (`.` vs `#`, nom différent) ;
    - **distinguer héritage** et **règle directe** (selon les exemples du cours) ;
    - **interpréter plusieurs propriétés** appliquées ensemble ;
    - **prévoir l'effet** d'un changement de **margin** ou de **padding**.

---

## 6. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| CSS écrit dans le **HTML** par erreur | le placer dans `style.css` |
| **Oubli du `<link>`** | relier la feuille |
| **Chemin incorrect** | vérifier l'emplacement de `style.css` |
| Oubli des **accolades** | `{ … }` autour des règles |
| Oubli du **`:`** ou du **`;`** | `propriété: valeur;` |
| Confusion **`.classe` / `#id`** | `.` pour classe, `#` pour id |
| **`id="#haut"`** en HTML | sans `#` : `id="haut"` |
| **Nom différent** HTML / CSS | mêmes noms |
| Même **`id` répété** | un id est **unique** (utiliser une classe) |
| **Mauvaise unité** | `px`, `%`… cohérentes |
| **Police sans solution de repli** | `font-family: Arial, sans-serif;` |
| Couleur **texte / fond** confondue | `color` vs `background-color` |
| **Chemin incorrect** dans `url()` | vérifier le chemin de l'image |
| **margin / padding** confondus | extérieur vs intérieur |
| **Oubli de largeur** avant `margin: auto` | définir `width` |

---

## 7. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'un sélecteur ?"
    Ce qui **cible** les éléments à styliser.

??? question "2. (N1) Quelle est la syntaxe d'une règle CSS ?"
    `sélecteur { propriété: valeur; }`.

??? question "3. (N2) Différence entre classe et identifiant ?"
    La **classe** est réutilisable ; l'**id** est **unique**.

??? question "4. (N2) Différence entre `<div>` et `<span>` ?"
    `<div>` est un **bloc** ; `<span>` est **en ligne**.

??? question "5. (N1) Citer les quatre zones du modèle des boîtes."
    contenu, **padding**, **border**, **margin**.

### Compréhension

??? question "6. (N1) À quoi sert `.menu` dans une feuille CSS ?"
    À styliser les éléments de **classe** `menu`.

??? question "7. (N2) Que cible `h1, h2 { … }` ?"
    **Tous** les `<h1>` **et** les `<h2>`.

??? question "8. (N2) Quelle est la différence entre `padding` et `margin` ?"
    `padding` = espace **intérieur** ; `margin` = espace **extérieur**.

??? question "9. (N3) Pourquoi `font-family: Arial, sans-serif;` ?"
    `sans-serif` sert de **solution de repli** si Arial est absente.

??? question "10. (N2) Que fait `a:hover { color: red; }` ?"
    Le lien devient rouge **au survol**.

### Lecture de règles

??? question "11. (N1) Que cible `p { color: blue; }` ?"
    Tous les paragraphes deviennent **bleus**.

??? question "12. (N2) Que cible `#haut` ?"
    L'élément ayant `id=\"haut\"`.

??? question "13. (N2) Que fait `text-align: center;` sur un titre ?"
    Il **centre** le texte.

??? question "14. (N3) `img { display: block; margin: auto; }` : effet ?"
    L'image est **centrée** horizontalement.

??? question "15. (N2) Que fait `border-radius: 10px;` ?"
    Il **arrondit** les coins de la bordure.

### Méthode

??? question "16. (N1) Comment relier une feuille externe ?"
    `<link rel=\"stylesheet\" href=\"style.css\">` dans `<head>`.

??? question "17. (N2) Comment écrire une couleur rouge en hexadécimal ?"
    `#ff0000`.

??? question "18. (N2) Comment créer une classe `.titre` en gras ?"
    `.titre { font-weight: bold; }`.

??? question "19. (N3) Comment centrer une boîte de 400 px ?"
    `width: 400px; margin: auto;`.

??? question "20. (N3) Comment mettre une couleur de fond à `<body>` ?"
    `body { background-color: …; }`.

### Modèle des boîtes

??? question "21. (N1) Quel est l'ordre des zones depuis le contenu ?"
    contenu → padding → border → margin.

??? question "22. (N2) Quelle propriété pour l'espace **intérieur** ?"
    `padding`.

??? question "23. (N2) Quelle propriété pour l'espace **entre deux boîtes** ?"
    `margin`.

??? question "24. (N3) Augmenter le `padding` : quel effet visuel ?"
    La boîte **grossit** (plus d'espace autour du contenu).

??? question "25. (N3) Pourquoi `margin: auto` ne centre-t-il pas sans `width` ?"
    Sans largeur fixée, la boîte occupe **toute** la largeur disponible.

### Correction d'erreurs

??? question "26. (N1) `p { color blue; }` : erreur ?"
    Il manque le `:` : `color: blue;`.

??? question "27. (N2) `.menu` en CSS mais `class=\"Menu\"` en HTML : erreur ?"
    Noms **différents** (casse) : harmoniser.

??? question "28. (N2) `id=\"#haut\"` en HTML : erreur ?"
    Le `#` ne va qu'en CSS : `id=\"haut\"`.

??? question "29. (N3) Même `id` utilisé deux fois : erreur ?"
    Un id est **unique** ; utiliser une **classe**.

??? question "30. (N2) `color` utilisé pour le fond : erreur ?"
    Le fond, c'est `background-color`.

### Production CSS

??? question "31. (N1) Écrire une règle mettant les `<h1>` en vert."
    `h1 { color: green; }`.

??? question "32. (N2) Créer une classe `.encadre` avec bordure noire."
    `.encadre { border: 1px solid black; }`.

??? question "33. (N2) Styliser un tableau avec bordures fusionnées."
    `table { border-collapse: collapse; } th, td { border: 1px solid; }`.

??? question "34. (N3) Donner une ombre à `.carte`."
    `.carte { box-shadow: 2px 2px 5px gray; }`.

??? question "35. (N4) Styliser le squelette `.header`, `.footer` (fond + centrage texte)."
    ```css
    .header, .footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 10px;
    }
    ```

---

## 8. Exercices flash corrigés

??? question "Relier une feuille externe `style.css`"
    `<link rel=\"stylesheet\" href=\"style.css\">`.

??? question "Corriger un sélecteur : `#menu` pour `class=\"menu\"`"
    Utiliser `.menu` (classe).

??? question "Créer une classe `.gras`"
    `.gras { font-weight: bold; }`.

??? question "Cibler un id `pied`"
    `#pied { … }`.

??? question "Modifier la police d'un paragraphe"
    `p { font-family: Arial, sans-serif; }`.

??? question "Choisir un code couleur bleu en RGB"
    `rgb(0, 0, 255)`.

??? question "Écrire une bordure rouge de 2 px"
    `border: 2px solid red;`.

??? question "Ajouter un effet de survol rouge sur les liens"
    `a:hover { color: red; }`.

??? question "Centrer une image"
    `img { display: block; margin: auto; }`.

??? question "Décrire les zones d'une boîte `padding:10px; border:1px; margin:20px`"
    10 px intérieurs, 1 px de bordure, 20 px extérieurs.

??? question "Styliser les cellules `<td>` avec bordure"
    `td { border: 1px solid black; }`.

---

## À retenir absolument

!!! success "Syntaxe d'une règle"
    ```css
    sélecteur {
      propriété: valeur;
    }
    ```

!!! note "Sélecteurs & propriétés clés"
    - **balise** `p { }`, **classe** `.nom { }`, **id** `#nom { }` ;
    - **classe** réutilisable ; **id** unique ;
    - **texte** : `color`, `font-size`, `font-family`, `font-weight`, `text-align` ;
    - **fond** : `background-color`, `background-image: url(…)` ;
    - **bordure** : `border`, `border-radius`, `box-shadow` ;
    - **pseudo-classes** : `:hover`, `:active`, `:visited`.

!!! quote "Modèle des boîtes"
    **contenu → padding (intérieur) → border → margin (extérieur)** ;
    pour centrer une boîte : **`width` + `margin: auto`**.
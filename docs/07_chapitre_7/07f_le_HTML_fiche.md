---
author: Elisabeth Le Prettre (LePrettre)
title: 07a 📜 Fiche Méthode - Le HTML
---

# HTML et les formulaires

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 9"
    Fiche **compacte** pour **refaire seul les exercices** : structure d'une page
    HTML, liens, images, tableaux, **formulaires** et requêtes **GET / POST**.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** la structure d'une page HTML et les balises principales ;
- **lire** du code HTML et **prévoir** son rendu ;
- **expliquer** la différence client / serveur et GET / POST ;
- **créer** : paragraphes, titres, listes, **liens**, **images**, **tableaux**, **formulaires**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Web** | Ensemble de pages reliées par des liens. |
| **Internet** | Réseau mondial reliant les machines. |
| **HTTP** | Protocole d'échange entre navigateur et serveur. |
| **URL** | Adresse d'une ressource. |
| **HTML** | Langage de **description** d'une page. |
| **Navigateur** | Logiciel qui **affiche** les pages. |
| **Balise** | Élément `<…>` structurant le contenu. |
| **Attribut** | Précision dans une balise (`href`, `src`…). |
| **Balise orpheline** | Balise **sans fermeture** (`<br>`, `<img>`). |
| **Chemin absolu / relatif** | Adresse complète / relative au fichier courant. |
| **Ancre** | Lien vers un endroit précis d'une page (`#id`). |
| **Formulaire** | Zone de **saisie** envoyée au serveur. |
| **Client / serveur** | Navigateur / machine qui répond. |
| **Requête** | Demande envoyée au serveur. |
| **GET / POST** | Données dans l'**URL** / dans le **corps** de la requête. |
| **Cookie** | Petite donnée stockée par le navigateur. |
| **HTTPS** | HTTP **sécurisé** (chiffré). |

---

## 3. Fiches méthodes

??? note "Créer la structure minimale d'une page"
    ```html
    <!DOCTYPE html>
    <html lang="fr">
      <head>
        <meta charset="utf-8">
        <title>Titre</title>
      </head>
      <body>
        <!-- contenu -->
      </body>
    </html>
    ```
    - **Erreur :** oublier `<!DOCTYPE html>` ou le `charset`.

??? note "Indenter et commenter"
    - **Indenter** les balises imbriquées ; **commenter** avec `<!-- … -->`.

??? note "Paragraphe, retour à la ligne, titres"
    ```html
    <h1>Titre 1</h1>
    <h2>Titre 2</h2>
    <p>Un paragraphe.<br>Nouvelle ligne.</p>
    ```
    - **Erreur :** plusieurs `<h1>` mal utilisés (un seul titre principal).

??? note "Mettre un texte en valeur"
    `<strong>important</strong>`, `<em>en italique</em>`.

??? note "Liste à puces ou numérotée"
    ```html
    <ul><li>puce</li></ul>     <!-- à puces -->
    <ol><li>numéro</li></ol>   <!-- numérotée -->
    ```
    - **Erreur :** confondre `<ul>` / `<ol>` ou oublier `<li>`.

??? note "Lien absolu"
    `<a href="https://exemple.fr">Lien</a>`.

??? note "Lien relatif (fichier, sous-dossier, parent)"
    ```html
    <a href="page.html">même dossier</a>
    <a href="dossier/page.html">sous-dossier</a>
    <a href="../page.html">dossier parent</a>
    ```
    - **Erreur :** mauvais **chemin**.

??? note "Créer une ancre"
    ```html
    <h2 id="partie1">Partie 1</h2>
    <a href="#partie1">Aller à la partie 1</a>
    <a href="autre.html#partie1">Autre page, partie 1</a>
    ```
    - **Erreur :** oublier le `#` dans le lien, ou mettre `#` dans la valeur de `id`.

??? note "Insérer une image"
    `<img src="photo.png" alt="description" title="info-bulle">`.
    - **Erreur :** oublier `alt` (accessibilité).

??? note "Choisir un format d'image"
    | Format | Usage |
    |---|---|
    | **JPEG** | photos (compression avec pertes) |
    | **PNG** | sans perte, **transparence** |
    | **GIF** | 256 couleurs, **animation** |
    | **BMP** | non compressé (lourd) |

??? note "Créer un tableau"
    ```html
    <table>
      <tr><th>Nom</th><th>Note</th></tr>
      <tr><td>Alice</td><td>15</td></tr>
    </table>
    ```
    `<tr>` = ligne, `<th>` = en-tête, `<td>` = cellule.

??? note "Créer un formulaire"
    ```html
    <form action="traitement.php" method="post">
      <input type="submit" value="Envoyer">
    </form>
    ```

??? note "Associer un `<label>` à un champ"
    ```html
    <label for="nom">Nom :</label>
    <input type="text" id="nom" name="nom">
    ```
    Le `for` du label = `id` du champ.

??? note "Choisir le bon type d'`input`"
    `text`, `password`, `email`, `number`, `date`, `checkbox`, `radio`, `submit`.

??? note "Boutons radio ou cases à cocher"
    ```html
    <input type="radio" name="choix" value="a"> A
    <input type="radio" name="choix" value="b"> B
    <input type="checkbox" name="opt" value="x"> X
    ```
    - **Erreur :** des boutons radio avec des **noms différents** (ils ne s'excluent plus).

??? note "Créer une liste déroulante"
    ```html
    <select name="pays">
      <option value="fr" selected>France</option>
      <option value="be">Belgique</option>
    </select>
    ```

??? note "Utiliser name, value, checked, selected, required"
    - `name` : **nom** de la donnée envoyée ; `value` : sa **valeur** ;
    - `checked` : case/radio **cochée** ; `selected` : option **choisie** ;
    - `required` : champ **obligatoire**.

??? note "Choisir entre GET et POST"
    - **GET** : données dans l'**URL** (visibles, recherches) ;
    - **POST** : données dans le **corps** (mots de passe, gros volumes).

??? note "Lire les paramètres d'une URL"
    `page.html?nom=Alice&age=15` → `nom = Alice`, `age = 15`.

---

## 4. Tableaux récapitulatifs

!!! note "Balises et rôles"
    | Balise | Rôle |
    |---|---|
    | `<html>` | racine de la page |
    | `<head>` | métadonnées |
    | `<body>` | contenu visible |
    | `<h1>`…`<h6>` | titres |
    | `<p>` | paragraphe |
    | `<a>` | lien |
    | `<img>` | image |
    | `<table>` | tableau |
    | `<form>` | formulaire |

!!! note "Paires vs orphelines"
    | Type | Exemples |
    |---|---|
    | **Paire** | `<p>…</p>`, `<a>…</a>`, `<ul>…</ul>` |
    | **Orpheline** | `<br>`, `<img>`, `<meta>`, `<input>` |

!!! note "Liens"
    | Type | Exemple |
    |---|---|
    | Absolu | `href="https://…"` |
    | Relatif | `href="page.html"`, `href="../page.html"` |
    | Ancre | `href="#id"`, `href="autre.html#id"` |

!!! note "Éléments de formulaire"
    | Élément | Rôle |
    |---|---|
    | `<input>` | champ de saisie |
    | `<label>` | étiquette |
    | `<select>` / `<option>` | liste déroulante |
    | `<textarea>` | texte long |
    | bouton `submit` | envoi |

!!! note "Types d'`input`"
    `text` · `password` · `email` · `number` · `date` · `checkbox` · `radio` · `submit`.

!!! note "GET vs POST"
    | | **GET** | **POST** |
    |---|---|---|
    | Données | dans l'**URL** | dans le **corps** |
    | Visibilité | **visibles** | non visibles dans l'URL |
    | Usage | recherches, liens | mots de passe, gros volumes |
    | Sécurité | faible (ni l'un ni l'autre ne **chiffre**) | idem (chiffrement = **HTTPS**) |

!!! note "Client / serveur"
    | Côté | Rôle |
    |---|---|
    | **Client** | le **navigateur** envoie la requête |
    | **Serveur** | **répond** et renvoie la page |

---

## 5. Lecture et compréhension de code

!!! tip "Méthode"
    - **repérer l'arborescence** des balises (imbrication) ;
    - **retrouver le parent** d'un élément (la balise englobante) ;
    - **identifier un attribut** (`href`, `src`, `name`…) ;
    - **prévoir le rendu** (titre, liste, lien, image…) ;
    - **corriger une fermeture** manquante ;
    - **vérifier un chemin** (relatif / absolu) ;
    - **retrouver les données envoyées** (attributs `name` / `value`) ;
    - **distinguer** le **texte affiché** et la **`value`** transmise.

---

## 6. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Balise **non fermée** | fermer (`</p>`, `</a>`…) |
| Mauvaise **imbrication** | fermer dans l'ordre inverse de l'ouverture |
| Contenu **hors de `<body>`** | placer le visible dans `<body>` |
| Oubli de **`<!DOCTYPE html>`** | l'ajouter en première ligne |
| Mauvais **encodage** | `<meta charset="utf-8">` |
| Plusieurs **`<h1>`** mal utilisés | un seul titre principal |
| Confusion **`<ul>` / `<ol>`** | puces vs numéros |
| Oubli de **`<li>`** | chaque élément dans un `<li>` |
| **Mauvais chemin** | vérifier dossier / `../` |
| Oubli du **`#`** dans un lien d'ancre | `href="#id"` |
| **`#`** dans la valeur de `id` | `id="partie1"` (sans `#`) |
| Oubli de **`alt`** | toujours décrire l'image |
| Oubli de **`name`** | sinon la donnée n'est **pas envoyée** |
| Radios à **noms différents** | même `name` pour s'exclure |
| Confusion **`checked` / `selected`** | radio/case vs option de liste |
| **GET** pour un mot de passe | utiliser **POST** |
| Croire que **POST chiffre** | seul **HTTPS** chiffre |

---

## 7. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'une balise orpheline ?"
    Une balise **sans fermeture** (`<br>`, `<img>`).

??? question "2. (N1) Que fait l'attribut `href` ?"
    Il indique la **destination** d'un lien.

??? question "3. (N2) Différence entre client et serveur ?"
    Le **client** (navigateur) envoie la requête ; le **serveur** répond.

??? question "4. (N1) Qu'est-ce qu'une ancre ?"
    Un lien vers un endroit **précis** d'une page (`#id`).

??? question "5. (N2) Que fait HTTPS de plus que HTTP ?"
    Il **chiffre** les échanges.

### Compréhension

??? question "6. (N1) Où place-t-on le contenu visible d'une page ?"
    Dans `<body>`.

??? question "7. (N2) Pourquoi mettre l'attribut `alt` sur une image ?"
    Pour l'**accessibilité** (texte de remplacement).

??? question "8. (N2) Pourquoi des boutons radio doivent-ils partager le même `name` ?"
    Pour qu'ils s'**excluent** mutuellement (un seul choix).

??? question "9. (N3) Pourquoi ne pas envoyer un mot de passe en GET ?"
    Il apparaîtrait **dans l'URL** (visible).

??? question "10. (N2) POST suffit-il à sécuriser des données ?"
    Non : POST **ne chiffre pas** ; il faut **HTTPS**.

### Lecture de code

??? question "11. (N1) Que produit `<ol><li>A</li><li>B</li></ol>` ?"
    Une liste **numérotée** : 1. A 2. B.

??? question "12. (N2) Quel est le parent de `<li>` dans une liste ?"
    `<ul>` ou `<ol>`.

??? question "13. (N2) Que vaut la donnée envoyée par `<input name=\"age\" value=\"15\">` ?"
    `age = 15`.

??? question "14. (N3) `<a href=\"#bas\">` mène où ?"
    À l'élément ayant `id=\"bas\"` dans la **même page**.

??? question "15. (N2) Différence entre le texte d'un `<option>` et sa `value` ?"
    Le texte est **affiché** ; la `value` est **envoyée**.

### Liens et images

??? question "16. (N1) Écrire un lien vers `https://exemple.fr`."
    `<a href=\"https://exemple.fr\">Lien</a>`.

??? question "17. (N2) Lien relatif vers le dossier parent ?"
    `<a href=\"../page.html\">…</a>`.

??? question "18. (N2) Insérer une image `chat.png` avec description."
    `<img src=\"chat.png\" alt=\"un chat\">`.

??? question "19. (N3) Quel format choisir pour une photo ?"
    **JPEG**.

??? question "20. (N3) Quel format pour une image avec transparence ?"
    **PNG**.

### Formulaires

??? question "21. (N1) Quelle balise crée un formulaire ?"
    `<form>`.

??? question "22. (N2) Comment rendre un champ obligatoire ?"
    Ajouter l'attribut `required`.

??? question "23. (N2) Associer un label au champ `id=\"mail\"`."
    `<label for=\"mail\">…</label>`.

??? question "24. (N3) Pré-cocher un bouton radio ?"
    Ajouter `checked`.

??? question "25. (N3) Pré-sélectionner une option de liste ?"
    Ajouter `selected` sur l'`<option>`.

### Correction d'erreurs

??? question "26. (N1) `<p>Texte` : erreur ?"
    Balise non fermée : `<p>Texte</p>`.

??? question "27. (N2) `<img src=\"x.png\">` sans `alt` : erreur ?"
    Ajouter `alt=\"…\"`.

??? question "28. (N2) `id=\"#section\"` : erreur ?"
    Le `#` ne va **que** dans le lien : `id=\"section\"`.

??? question "29. (N3) Deux radios `name=\"a\"` et `name=\"b\"` : erreur ?"
    Même `name` requis pour s'exclure.

??? question "30. (N2) Mot de passe envoyé en GET : erreur ?"
    Utiliser **POST** (et HTTPS pour chiffrer).

### Production

??? question "31. (N1) Écrire un titre de niveau 2 « Menu »."
    `<h2>Menu</h2>`.

??? question "32. (N2) Créer une liste à puces de deux fruits."
    `<ul><li>pomme</li><li>poire</li></ul>`.

??? question "33. (N2) Créer un champ texte nommé `pseudo`."
    `<input type=\"text\" name=\"pseudo\">`.

??? question "34. (N3) Créer une liste déroulante de deux pays."
    ```html
    <select name=\"pays\">
      <option value=\"fr\">France</option>
      <option value=\"be\">Belgique</option>
    </select>
    ```

??? question "35. (N4) Écrire un mini-formulaire de paiement en POST (nom + carte)."
    ```html
    <form action=\"paiement.php\" method=\"post\">
      <label for=\"nom\">Nom :</label>
      <input type=\"text\" id=\"nom\" name=\"nom\" required>
      <label for=\"carte\">Carte :</label>
      <input type=\"text\" id=\"carte\" name=\"carte\" required>
      <input type=\"submit\" value=\"Payer\">
    </form>
    ```

---

## 8. Exercices flash corrigés

??? question "Compléter une balise : `<a ____=\"page.html\">`"
    `href`.

??? question "Fermer une structure : `<ul><li>A`"
    `<ul><li>A</li></ul>`.

??? question "Choisir un titre : titre principal de la page"
    `<h1>`.

??? question "Créer une liste numérotée de 3 étapes"
    `<ol><li>1</li><li>2</li><li>3</li></ol>`.

??? question "Corriger un lien : `<a href=\"bas\">` vers une ancre"
    `<a href=\"#bas\">`.

??? question "Écrire une ancre cible « contact »"
    `<h2 id=\"contact\">Contact</h2>`.

??? question "Insérer une image `logo.png`"
    `<img src=\"logo.png\" alt=\"logo\">`.

??? question "Compléter un tableau : ligne d'en-têtes"
    `<tr><th>Nom</th><th>Âge</th></tr>`.

??? question "Choisir un type d'input pour un email"
    `type=\"email\"`.

??? question "Prévoir l'URL d'un GET avec `nom=Zoe`"
    `page.html?nom=Zoe`.

??? question "Transformer un formulaire GET en POST"
    Remplacer `method=\"get\"` par `method=\"post\"`.

---

## À retenir absolument

!!! success "Squelette HTML"
    ```html
    <!DOCTYPE html>
    <html lang=\"fr\">
      <head><meta charset=\"utf-8\"><title>…</title></head>
      <body> … </body>
    </html>
    ```

!!! note "Balises & éléments clés"
    - **titres** `<h1>`…`<h6>`, **paragraphe** `<p>`, **listes** `<ul>`/`<ol>` + `<li>` ;
    - **lien** `<a href=\"…\">` (absolu / relatif / ancre `#id`) ;
    - **image** `<img src=\"…\" alt=\"…\">` ;
    - **tableau** `<table>` + `<tr>` + `<th>`/`<td>` ;
    - **formulaire** `<form>` + `<label>` + `<input>` ; l'attribut **`name`** nomme la donnée envoyée.

!!! quote "GET vs POST"
    - **GET** : données dans l'**URL** (visibles) ;
    - **POST** : données dans le **corps** (mots de passe, gros volumes) ;
    - aucun des deux ne **chiffre** : le chiffrement, c'est **HTTPS**.
---
author: Elisabeth Le Prettre (LePrettre)
title: 07d 📜 Fiche Méthode - Les formulaires et le protocole HTTP
---

# Les formulaires HTML

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 12"
    Fiche **compacte** pour **créer, lire et corriger** un formulaire : champs de
    saisie, choix, **envoi des données** et requêtes **GET / POST**. Complète la
    fiche « HTML et les formulaires ».

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les éléments d'un formulaire et leurs attributs ;
- **comprendre** comment les données sont **envoyées** au serveur ;
- **lire** un formulaire et retrouver les **données transmises** ;
- **expliquer** la différence **GET / POST** ;
- **programmer** un formulaire complet et fonctionnel.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Formulaire** | Zone de **saisie** envoyée au serveur. |
| **Champ** | Élément de saisie (`<input>`, `<textarea>`…). |
| **Label** | Étiquette décrivant un champ. |
| **Attribut** | Précision dans une balise. |
| **Identifiant (`id`)** | Nom **unique** d'un élément. |
| **Paramètre** | Donnée envoyée (nom = `name`). |
| **Valeur** | Contenu transmis (`value`). |
| **Requête** | Demande envoyée au serveur. |
| **Client / serveur** | Navigateur / machine qui répond. |
| **GET** | Données dans l'**URL**. |
| **POST** | Données dans le **corps** de la requête. |
| **HTTPS** | HTTP **chiffré**. |

---

## 3. Éléments d'un formulaire

| Élément | Rôle | Exemple |
|---|---|---|
| `<form>` | conteneur du formulaire | `<form method="post" action="t.php">…</form>` |
| `<label>` | étiquette d'un champ | `<label for="nom">Nom</label>` |
| `<input>` | champ de saisie | `<input type="text" name="nom">` |
| `<textarea>` | texte **long** | `<textarea name="msg"></textarea>` |
| `<select>` | liste déroulante | `<select name="pays">…</select>` |
| `<option>` | choix d'une liste | `<option value="fr">France</option>` |
| `<optgroup>` | **groupe** d'options | `<optgroup label="Europe">…</optgroup>` |
| `<fieldset>` | regroupe des champs | `<fieldset>…</fieldset>` |
| `<legend>` | titre d'un `fieldset` | `<legend>Identité</legend>` |
| `<button>` | bouton | `<button type="submit">Envoyer</button>` |

---

## 4. Types d'`input`

| Type | Usage | Choix | Donnée transmise |
|---|---|---|---|
| `text` | saisie libre | — | le texte saisi |
| `password` | mot de passe **masqué** | — | le texte saisi |
| `radio` | choix dans un groupe | **unique** | `value` du sélectionné |
| `checkbox` | cases à cocher | **multiple** | `value` de chaque cochée |
| `submit` | **envoie** le formulaire | — | déclenche l'envoi |
| `reset` | **réinitialise** | — | rien |
| `button` | bouton générique | — | rien (sauf via JS) |

---

## 5. Attributs

| Attribut | Rôle |
|---|---|
| `method` | `GET` ou `POST` |
| `action` | **URL** de destination |
| `id` | identifiant **unique** (lié au label) |
| `for` | relie le `<label>` à l'`id` du champ |
| `name` | **nom du paramètre** envoyé |
| `value` | **valeur** envoyée |
| `required` | champ **obligatoire** |
| `checked` | case / radio **cochée** par défaut |
| `selected` | option **sélectionnée** par défaut |

!!! warning "À ne pas confondre"
    **`name`** donne le **nom** du paramètre ; **`value`** donne la **valeur** envoyée.
    Sans `name`, la donnée **n'est pas transmise**.

---

## 6. Fiches méthodes

??? note "Créer un formulaire"
    ```html
    <form method="post" action="traitement.php">
      <!-- champs -->
      <input type="submit" value="Envoyer">
    </form>
    ```

??? note "Ajouter un champ texte"
    ```html
    <input type="text" name="nom">
    ```

??? note "Ajouter un mot de passe"
    ```html
    <input type="password" name="mdp">
    ```

??? note "Associer un label à un champ"
    ```html
    <label for="nom">Nom :</label>
    <input type="text" id="nom" name="nom">
    ```
    Le `for` du label = `id` du champ.

??? note "Créer un groupe de boutons radio"
    ```html
    <input type="radio" name="genre" value="f"> Fille
    <input type="radio" name="genre" value="g"> Garçon
    ```
    - **Erreur :** `name` différents → ils ne s'excluent plus.

??? note "Créer plusieurs cases à cocher"
    ```html
    <input type="checkbox" name="option" value="a"> A
    <input type="checkbox" name="option" value="b"> B
    ```

??? note "Créer une zone de texte"
    ```html
    <textarea name="message"></textarea>
    ```

??? note "Créer une liste déroulante"
    ```html
    <select name="pays">
      <option value="fr">France</option>
      <option value="be">Belgique</option>
    </select>
    ```

??? note "Regrouper des options"
    ```html
    <select name="ville">
      <optgroup label="France">
        <option value="paris">Paris</option>
      </optgroup>
    </select>
    ```

??? note "Organiser avec `fieldset` et `legend`"
    ```html
    <fieldset>
      <legend>Identité</legend>
      <!-- champs -->
    </fieldset>
    ```

??? note "Rendre un champ obligatoire"
    ```html
    <input type="text" name="nom" required>
    ```

??? note "Valeur cochée / sélectionnée par défaut"
    ```html
    <input type="radio" name="g" value="f" checked> Fille
    <option value="fr" selected>France</option>
    ```

??? note "Ajouter un bouton d'envoi"
    ```html
    <input type="submit" value="Envoyer">
    <!-- ou -->
    <button type="submit">Envoyer</button>
    ```

??? note "Choisir entre GET et POST"
    - **GET** : recherches, données non sensibles (apparaissent dans l'URL) ;
    - **POST** : mots de passe, gros volumes.

??? note "Lire les paramètres d'une URL GET"
    `page.php?nom=Alice&age=15` → `nom = Alice`, `age = 15`.

??? note "Retrouver les données réellement envoyées"
    Repérer les couples **`name` / `value`** des champs **renseignés** (cochés / sélectionnés).

---

## 7. Méthode complète pour construire un formulaire

!!! tip "10 étapes"
    1. **lister** les informations demandées ;
    2. **choisir** les champs (texte, radio, select…) ;
    3. **écrire** les labels ;
    4. **définir** les `id` ;
    5. **ajouter** les `name` ;
    6. **choisir** les `value` ;
    7. **ajouter** les contraintes (`required`, `checked`…) ;
    8. **choisir** GET ou POST ;
    9. **ajouter** le bouton d'envoi ;
    10. **tester** chaque cas.

---

## 8. GET vs POST

| Critère | **GET** | **POST** |
|---|---|---|
| Emplacement des données | dans l'**URL** | dans le **corps** |
| Visibilité | **visibles** | non visibles dans l'URL |
| Usage | recherches, liens | mots de passe, gros volumes |
| Présence dans l'URL | **oui** (`?nom=…`) | non |
| Confidentialité | faible | meilleure (mais **pas chiffrée**) |
| Rôle de HTTPS | chiffre les échanges | chiffre les échanges |

!!! warning
    Ni GET ni POST ne **chiffrent** : seul **HTTPS** sécurise les données.

---

## 9. Lecture de code

!!! tip "Comment retrouver…"
    - **le texte affiché** : contenu du `<label>` / de l'`<option>` ;
    - **le type du champ** : attribut `type` ;
    - **le nom du paramètre** : attribut `name` ;
    - **la valeur envoyée** : attribut `value` (ou texte saisi) ;
    - **le champ obligatoire** : présence de `required` ;
    - **le choix par défaut** : `checked` / `selected` ;
    - **la méthode** : attribut `method` ;
    - **l'adresse de destination** : attribut `action`.

---

## 10. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Champs & données envoyées**
    | Champ | Type | `name` | `value` | Choix effectué | Donnée envoyée |
    |---|---|---|---|---|---|

    **Paramètres d'une URL GET**
    | URL | Paramètres | Noms | Valeurs |
    |---|---|---|---|

    **Validation**
    | Saisie | Correcte ? | Contrainte respectée ? | Envoi possible ? |
    |---|---|---|---|

---

## 11. Erreurs fréquentes

| Erreur | Conséquence / correction |
|---|---|
| Oublier `<form>` | les champs ne forment pas un formulaire |
| Oublier `method` ou `action` | envoi mal défini : préciser les deux |
| `for` et `id` non associés | le label ne cible aucun champ |
| Oublier `name` | la donnée **n'est pas envoyée** |
| Confondre `id`, `name`, `value` | `id` (cible le label) ≠ `name` (paramètre) ≠ `value` (donnée) |
| Radios à `name` **différents** | ils ne s'excluent plus : même `name` |
| `checked` sur une **option** | utiliser `selected` |
| `selected` sur une **case** | utiliser `checked` |
| Oublier `value` | aucune valeur transmise |
| **GET** pour un mot de passe | utiliser **POST** |
| Croire que **POST chiffre** | seul **HTTPS** chiffre |
| Bouton **hors** du formulaire | le placer **dans** `<form>` |
| Oublier une balise fermante | fermer `</form>`, `</select>`… |
| Même `id` utilisé plusieurs fois | un `id` est **unique** |

---

## 12. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Quel élément contient tout le formulaire ?"
    `<form>`.

??? question "2. (N1) Que désigne l'attribut `action` ?"
    L'**URL** de destination des données.

??? question "3. (N2) Différence entre `name` et `value` ?"
    `name` = **nom** du paramètre ; `value` = **valeur** envoyée.

??? question "4. (N2) À quoi sert `<label>` ?"
    À **étiqueter** un champ (lié par `for` / `id`).

??? question "5. (N1) Que fait `required` ?"
    Rend le champ **obligatoire**.

### Compréhension

??? question "6. (N1) Pourquoi associer `for` et `id` ?"
    Pour **lier** le label au champ (clic sur le label = focus sur le champ).

??? question "7. (N2) Pourquoi un même `name` pour un groupe de radios ?"
    Pour qu'ils s'**excluent** (un seul choix possible).

??? question "8. (N2) Que se passe-t-il sans `name` sur un champ ?"
    La donnée **n'est pas envoyée**.

??? question "9. (N3) Pourquoi POST pour un mot de passe ?"
    Pour ne pas l'afficher **dans l'URL**.

??? question "10. (N2) POST garantit-il la confidentialité ?"
    Non : seul **HTTPS** chiffre.

### Lecture de formulaire

??? question "11. (N1) `<input type=\"password\" name=\"mdp\">` : quel type ?"
    Mot de passe (masqué).

??? question "12. (N2) Quelle valeur envoie `<option value=\"fr\">France</option>` si choisie ?"
    `fr` (et non « France »).

??? question "13. (N2) Comment savoir qu'un champ est obligatoire ?"
    Présence de `required`.

??? question "14. (N3) `<input type=\"radio\" name=\"g\" value=\"f\" checked>` : que signifie `checked` ?"
    Ce bouton est **coché par défaut**.

??? question "15. (N2) Où lit-on la méthode d'envoi ?"
    Dans l'attribut `method` de `<form>`.

### Attributs

??? question "16. (N1) Quel attribut rend un champ obligatoire ?"
    `required`.

??? question "17. (N2) Quel attribut pré-coche une case ?"
    `checked`.

??? question "18. (N2) Quel attribut pré-sélectionne une option ?"
    `selected`.

??? question "19. (N3) Quel attribut relie un label à son champ ?"
    `for` (égal à l'`id` du champ).

??? question "20. (N2) Quel attribut donne le nom du paramètre ?"
    `name`.

### GET / POST

??? question "21. (N1) Où vont les données en GET ?"
    Dans l'**URL**.

??? question "22. (N2) Où vont les données en POST ?"
    Dans le **corps** de la requête.

??? question "23. (N2) Quelle méthode pour une barre de recherche ?"
    **GET**.

??? question "24. (N3) URL `panier.php?article=12` : quelle méthode et quel paramètre ?"
    **GET** ; paramètre `article = 12`.

??? question "25. (N3) Comment chiffrer réellement les données envoyées ?"
    Utiliser **HTTPS**.

### Correction d'erreurs

??? question "26. (N1) Champ sans `name` : conséquence ?"
    Sa valeur n'est **pas envoyée**.

??? question "27. (N2) `selected` sur une case à cocher : erreur ?"
    Utiliser `checked` (case) ; `selected` est pour les `<option>`.

??? question "28. (N2) Radios `name=\"a\"` et `name=\"b\"` : erreur ?"
    Même `name` requis pour s'exclure.

??? question "29. (N3) Bouton placé après `</form>` : erreur ?"
    Le placer **dans** le `<form>`.

??? question "30. (N2) Deux champs avec le même `id` : erreur ?"
    Un `id` est **unique**.

### Création de code

??? question "31. (N1) Écrire un champ texte nommé `pseudo`."
    `<input type=\"text\" name=\"pseudo\">`.

??? question "32. (N2) Associer un label « Email » à un champ `id=\"mail\"`."
    `<label for=\"mail\">Email</label>`.

??? question "33. (N2) Créer un bouton d'envoi."
    `<input type=\"submit\" value=\"Envoyer\">`.

??? question "34. (N3) Créer une liste déroulante de deux nationalités."
    ```html
    <select name=\"nationalite\">
      <option value=\"fr\">Française</option>
      <option value=\"be\">Belge</option>
    </select>
    ```

??? question "35. (N4) Écrire un mini-formulaire de paiement en POST (nom + carte)."
    ```html
    <form method=\"post\" action=\"paiement.php\">
      <label for=\"nom\">Nom :</label>
      <input type=\"text\" id=\"nom\" name=\"nom\" required>
      <label for=\"carte\">Carte :</label>
      <input type=\"text\" id=\"carte\" name=\"carte\" required>
      <input type=\"submit\" value=\"Payer\">
    </form>
    ```

---

## 13. Exercices flash corrigés

??? question "Compléter `<form ____=\"post\" ____=\"t.php\">`"
    `method` et `action`.

??? question "Associer un label au champ `id=\"age\"`"
    `<label for=\"age\">Âge</label>`.

??? question "Choisir un type d'input pour un mot de passe"
    `type=\"password\"`.

??? question "Créer trois boutons radio d'un même groupe `taille`"
    ```html
    <input type=\"radio\" name=\"taille\" value=\"s\"> S
    <input type=\"radio\" name=\"taille\" value=\"m\"> M
    <input type=\"radio\" name=\"taille\" value=\"l\"> L
    ```

??? question "Créer deux cases à cocher `option`"
    ```html
    <input type=\"checkbox\" name=\"option\" value=\"a\"> A
    <input type=\"checkbox\" name=\"option\" value=\"b\"> B
    ```

??? question "Compléter une liste déroulante avec une option « France »"
    `<option value=\"fr\">France</option>`.

??? question "Ajouter `required` à un champ nom"
    `<input type=\"text\" name=\"nom\" required>`.

??? question "Déterminer la valeur envoyée par `<option value=\"be\">Belgique</option>`"
    `be`.

??? question "Lire l'URL GET `form.php?nom=Zoe&age=16`"
    `nom = Zoe`, `age = 16`.

??? question "Transformer un formulaire GET en POST"
    Remplacer `method=\"get\"` par `method=\"post\"`.

??? question "Corriger un formulaire sans bouton d'envoi"
    Ajouter `<input type=\"submit\" value=\"Envoyer\">` dans le `<form>`.

---

## À retenir absolument

!!! success "Structure d'un formulaire"
    ```html
    <form method=\"post\" action=\"traitement.php\">
      <label for=\"nom\">Nom :</label>
      <input type=\"text\" id=\"nom\" name=\"nom\" required>
      <input type=\"submit\" value=\"Envoyer\">
    </form>
    ```

!!! note "Rôle des attributs"
    - **`id`** : identifie le champ (cible du label) ;
    - **`for`** : relie le label à l'`id` ;
    - **`name`** : nom du **paramètre** envoyé ;
    - **`value`** : **valeur** transmise.

!!! note "Champs & envoi"
    - **types** : `text`, `password`, `radio` (unique), `checkbox` (multiple),
      `submit`, `reset` ; listes : `<select>` / `<option>` ;
    - **GET** : données dans l'**URL** ; **POST** : dans le **corps** ;
    - chiffrement = **HTTPS** (ni GET ni POST ne chiffrent).
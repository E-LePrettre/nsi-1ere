---
author: Elisabeth Le Prettre (LePrettre)
title: 05b 📜 Fiche Méthode - Types construits
---

# Les types construits

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 6"
    Fiche **compacte** pour **refaire seul les exercices** : **tuples**, **listes**,
    **matrices** et **dictionnaires** — création, accès, parcours, compréhensions,
    copie et opérations essentielles. Les points marqués **« Approfondissement »**
    ne sont pas indispensables.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** tuples, listes, matrices, dictionnaires et leurs différences ;
- **lire** un accès par indice, un slice, une compréhension, un parcours ;
- **expliquer** mutabilité, copie vs alias, ligne vs colonne ;
- **programmer** : parcours, recherche, calculs (somme, max…), matrices et dictionnaires.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Séquence** | Suite **ordonnée** d'éléments (tuple, liste, chaîne). |
| **Indice** | Position d'un élément (à partir de **0**). |
| **Tuple** | Séquence **non modifiable** : `(1, 2, 3)`. |
| **Immutabilité** | On **ne peut pas** modifier (tuple, chaîne). |
| **Liste** | Séquence **modifiable** : `[1, 2, 3]`. |
| **Mutabilité** | On **peut** modifier (liste, dictionnaire). |
| **Slice** | Tranche `L[a:b]` (borne `b` **exclue**). |
| **Compréhension** | Construction concise : `[x*2 for x in L]`. |
| **Copie** | Nouvelle structure indépendante. |
| **Alias** | Deux noms pour **la même** structure. |
| **Matrice** | Liste de listes (tableau à 2 dimensions). |
| **Ligne / colonne** | `M[i]` (ligne) / éléments d'indice `j` de chaque ligne. |
| **Dictionnaire** | Associe des **clés** à des **valeurs** : `{...}`. |
| **Clé / valeur** | Identifiant / donnée associée. |
| **Paire clé-valeur** | Couple `clé: valeur`. |

---

## 3. Tableau comparatif

| | **Tuple** | **Liste** | **Dictionnaire** |
|---|---|---|---|
| Délimiteurs | `( )` | `[ ]` | `{ }` |
| Accès | par **indice** | par **indice** | par **clé** |
| Ordre | oui | oui | oui (insertion) |
| Modification | **non** | oui | oui |
| Ajout | non | `append`, `insert` | `d[k] = v` |
| Suppression | non | `remove`, `pop` | `del d[k]` |
| Parcours | par valeurs | valeurs / indices | `keys`, `values`, `items` |
| Usage | données **fixes** | collection **modifiable** | **associations** clé→valeur |

---

## 4. Fiches méthodes

??? note "Créer un tuple ou une liste"
    - `t = (1, 2, 3)` (tuple, non modifiable) ; `L = [1, 2, 3]` (liste, modifiable).
    - **Tuple à un élément :** `(5,)` (la virgule est obligatoire).

??? note "Accéder par indice positif, négatif ou slice"
    - `L[0]` (premier), `L[-1]` (dernier), `L[1:3]` (indices 1 et 2).
    - **Erreur :** indice **hors limites** (`L[len(L)]` n'existe pas).

??? note "Accéder dans une structure imbriquée"
    - **Matrice :** `M[i][j]` (ligne `i`, colonne `j`).
    - **Exemple :** `[[1, 2], [3, 4]][1][0]` → `3`.

??? note "Concaténer ou répéter une séquence"
    - `[1, 2] + [3]` → `[1, 2, 3]` ; `[0] * 3` → `[0, 0, 0]`.

??? note "Parcourir par valeurs"
    ```python
    for x in L:
        print(x)
    ```

??? note "Parcourir par indices"
    ```python
    for i in range(len(L)):
        print(i, L[i])
    ```

??? note "Utiliser une boucle `while`"
    ```python
    i = 0
    while i < len(L):
        print(L[i])
        i += 1
    ```

??? note "Choisir entre valeurs et indices"
    - **Valeurs** : on a juste besoin de l'élément.
    - **Indices** : on a besoin de la **position** (ou de modifier `L[i]`).

??? note "Retourner plusieurs valeurs"
    ```python
    def min_max(L):
        return min(L), max(L)   # renvoie un tuple
    a, b = min_max([3, 1, 8])   # a=1, b=8
    ```

??? note "Créer une liste par compréhension (filtre, double boucle)"
    - **Simple :** `[x*2 for x in L]`.
    - **Avec filtre :** `[x for x in L if x > 0]`.
    - **Double boucle :** `[i*j for i in range(3) for j in range(3)]`.

??? note "Copier une liste sans créer d'alias"
    - `L2 = L[:]` (ou `L.copy()` ou `list(L)`).
    - **Erreur :** `L2 = L` crée un **alias** (modifier l'un modifie l'autre).

??? note "Méthodes de liste"
    | Méthode | Effet |
    |---|---|
    | `append(x)` | ajoute en fin |
    | `insert(i, x)` | insère à l'indice `i` |
    | `remove(x)` | retire la **première** occurrence |
    | `pop(i)` | retire et **renvoie** l'élément `i` |
    | `sort()` | trie en place |
    | `reverse()` | inverse en place |

??? note "Utiliser `split` et `join`"
    - `"a,b,c".split(",")` → `['a', 'b', 'c']` ;
    - `",".join(['a', 'b', 'c'])` → `"a,b,c"`.

??? note "Calculer somme, moyenne, produit, min, max, occurrences"
    ```python
    s = 0
    for x in L:
        s += x                 # somme (sans sum)
    moyenne = s / len(L)
    L.count(valeur)            # occurrences
    ```
    - **min/max :** initialiser avec `L[0]` puis comparer.

??? note "Rechercher une valeur et ses positions"
    ```python
    positions = [i for i in range(len(L)) if L[i] == cible]
    ```

??? note "Créer et parcourir une matrice"
    ```python
    M = [[1, 2, 3],
         [4, 5, 6]]
    for ligne in M:
        for valeur in ligne:
            print(valeur)
    ```

??? note "Récupérer une ligne ou une colonne"
    - **Ligne `i`** : `M[i]`.
    - **Colonne `j`** : `[M[i][j] for i in range(len(M))]`.
    - **Erreur :** confondre **ligne** et **colonne**.

??? note "Parcourir une matrice par double boucle"
    ```python
    for i in range(len(M)):           # lignes
        for j in range(len(M[0])):    # colonnes
            print(M[i][j])
    ```

??? note "Créer, ajouter, modifier, supprimer dans un dictionnaire"
    ```python
    d = {}
    d["a"] = 1        # ajout
    d["a"] = 2        # modification
    del d["a"]        # suppression
    ```

??? note "Créer un dictionnaire par compréhension ou avec `dict()`"
    - `{x: x*x for x in range(4)}` → `{0:0, 1:1, 2:4, 3:9}` ;
    - `dict([("a", 1), ("b", 2)])` → `{'a': 1, 'b': 2}`.

??? note "Parcourir avec `keys`, `values`, `items`"
    ```python
    for cle in d.keys(): ...
    for val in d.values(): ...
    for cle, val in d.items(): ...
    ```

??? note "Tester une clé, une valeur, une paire"
    - `cle in d` ; `valeur in d.values()` ; `(cle, valeur) in d.items()`.

??? note "Accéder avec `get()` (sans `KeyError`)"
    - `d.get("x")` → `None` si absent ; `d.get("x", 0)` → `0` si absent.

---

## 5. Lecture et compréhension de code

!!! tip "Méthode"
    - **prévoir le contenu final** d'une structure (simuler les opérations) ;
    - **suivre indices et variables** (tableau de trace) ;
    - **distinguer affichage** (`print`) et **valeur retournée** (`return`) ;
    - **repérer une modification en place** (`append`, `sort`, `d[k] = …`) ;
    - **détecter un alias** (`L2 = L`) ;
    - **compléter** une compréhension, une double boucle, un parcours de dictionnaire.

---

## 6. Tableaux de trace

!!! example "Modèles de tableaux"
    **Parcours de liste**
    | Itération | `i` | `L[i]` | Action |
    |---|---|---|---|

    **Compteur / accumulateur**
    | Élément | Condition | `c` après |
    |---|---|---|

    **Recherche de maximum**
    | Élément | `> maxi` ? | `maxi` |
    |---|---|---|

    **Matrice (double boucle)**
    | `i` | `j` | `M[i][j]` |
    |---|---|---|

    **Dictionnaire**
    | Clé | Valeur | Action |
    |---|---|---|

---

## 7. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| **Indice hors limites** | dernier indice = `len(L) - 1` |
| **Borne finale incluse** | dans un slice, `b` est **exclue** |
| **Valeur / indice confondus** | choisir `for x in L` ou `range(len(L))` |
| **Modifier un tuple** | impossible : utiliser une **liste** |
| **Oubli de copie** | `L2 = L[:]` (sinon **alias**) |
| **Supprimer un élément absent** | `remove` lève une erreur : tester `in` avant |
| **Modifier une liste pendant le parcours** | parcourir une **copie** ou construire une nouvelle liste |
| **Mauvaise initialisation du minimum** | initialiser avec `L[0]`, pas `0` |
| **Ligne / colonne confondues** | `M[i]` = ligne ; colonne = `M[i][j]` pour tout `i` |
| **Oubli de la double boucle** | une boucle par dimension |
| **Clé / valeur confondues** | `keys` ≠ `values` |
| **Accès à une clé absente** | `KeyError` → utiliser `get()` |
| **Mauvais parcours d'`items()`** | `for cle, val in d.items()` (deux variables) |
| **`append` vs concaténation** | `append(x)` ajoute **un** élément ; `+ [x]` concatène |

---

## 8. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Quelle est la différence entre un tuple et une liste ?"
    Le **tuple** est **non modifiable** ; la **liste** est **modifiable**.

??? question "2. (N1) Qu'est-ce qu'un slice ?"
    Une **tranche** `L[a:b]` (la borne `b` est **exclue**).

??? question "3. (N2) Différence entre copie et alias ?"
    Une **copie** est indépendante ; un **alias** est un autre nom pour la **même** structure.

??? question "4. (N1) Comment accède-t-on à une valeur d'un dictionnaire ?"
    Par sa **clé** : `d[cle]`.

??? question "5. (N2) Qu'est-ce qu'une matrice en Python ?"
    Une **liste de listes** (tableau à deux dimensions).

### Compréhension

??? question "6. (N1) Que vaut `[0] * 3` ?"
    `[0, 0, 0]`.

??? question "7. (N2) Pourquoi ne peut-on pas faire `t[0] = 5` sur un tuple ?"
    Le tuple est **immuable** (non modifiable).

??? question "8. (N2) Que fait `L2 = L` puis `L2.append(9)` ?"
    `L` est **aussi** modifiée : `L2` est un **alias** de `L`.

??? question "9. (N3) Que renvoie `d.get('x', 0)` si `'x'` est absent ?"
    `0` (valeur par défaut, **sans** `KeyError`).

??? question "10. (N2) Pourquoi une double boucle pour une matrice ?"
    Une boucle pour les **lignes**, une pour les **colonnes**.

### Lecture de code

??? question "11. (N1) Que vaut `[1, 2, 3, 4][1:3]` ?"
    `[2, 3]`.

??? question "12. (N2) Que vaut `[x*2 for x in [1,2,3]]` ?"
    `[2, 4, 6]`.

??? question "13. (N2) Que vaut `[x for x in range(5) if x % 2 == 0]` ?"
    `[0, 2, 4]`.

??? question "14. (N3) Pour `M = [[1,2],[3,4]]`, que vaut `[M[i][0] for i in range(2)]` ?"
    `[1, 3]` (la **colonne** 0).

??? question "15. (N2) Que vaut `\"a,b,c\".split(',')` ?"
    `['a', 'b', 'c']`.

### Méthode

??? question "16. (N1) Comment copier une liste `L` ?"
    `L2 = L[:]` (ou `L.copy()`).

??? question "17. (N2) Comment calculer la somme d'une liste sans `sum` ?"
    Initialiser `s = 0` puis `s += x` pour chaque `x`.

??? question "18. (N2) Comment récupérer la colonne `j` d'une matrice ?"
    `[M[i][j] for i in range(len(M))]`.

??? question "19. (N3) Comment compter les occurrences d'une valeur ?"
    `L.count(valeur)` (ou une boucle avec compteur).

??? question "20. (N3) Comment parcourir clés **et** valeurs d'un dictionnaire ?"
    `for cle, val in d.items():`.

### Correction d'erreurs

??? question "21. (N1) `L[len(L)]` provoque une erreur. Pourquoi ?"
    Indice **hors limites** : le dernier est `len(L) - 1`.

??? question "22. (N2) `t = (1, 2); t[0] = 9` : erreur ?"
    Un **tuple** est immuable : utiliser une **liste**.

??? question "23. (N2) `d['x']` plante si `'x'` absent : comment éviter ?"
    Utiliser `d.get('x')` (ou tester `'x' in d`).

??? question "24. (N3) `maxi = 0` pour chercher le max d'une liste de négatifs : erreur ?"
    Faux : initialiser avec `L[0]`, sinon le résultat reste `0`.

??? question "25. (N2) `L.append([3, 4])` pour ajouter 3 et 4 : erreur ?"
    `append` ajoute **un** élément (ici une sous-liste). Utiliser `L += [3, 4]`.

### Programmation / code à compléter

??? question "26. (N1) Écrire une compréhension donnant les carrés de 0 à 4."
    `[x*x for x in range(5)]`.

??? question "27. (N2) Carnet de notes : ajouter la note 15 pour `\"Alice\"`."
    `notes[\"Alice\"] = 15`.

??? question "28. (N2) Écrire la moyenne d'une liste `L`."
    ```python
    s = 0
    for x in L:
        s += x
    moyenne = s / len(L)
    ```

??? question "29. (N3) Construire la liste des positions de `cible` dans `L`."
    `[i for i in range(len(L)) if L[i] == cible]`.

??? question "30. (N4) Jeu de 32 cartes : générer tous les couples (valeur, couleur)."
    ```python
    valeurs = ["7", "8", "9", "10", "V", "D", "R", "As"]
    couleurs = ["♠", "♥", "♦", "♣"]
    jeu = [(v, c) for c in couleurs for v in valeurs]
    ```

---

## 9. Exercices flash corrigés

??? question "Accès et slice : `\"PYTHON\"[1:4]`"
    `\"YTH\"`.

??? question "Choisir la structure : associer un nom à une note"
    Un **dictionnaire** (`nom → note`).

??? question "Résultat d'une méthode : `[3,1,2].sort()` puis la liste"
    La liste devient `[1, 2, 3]` (`sort` modifie en place, renvoie `None`).

??? question "Copie ou alias : `L2 = L[:]`"
    Une **copie** indépendante.

??? question "Compréhension : pairs de 0 à 9"
    `[x for x in range(10) if x % 2 == 0]`.

??? question "Somme sans `sum` de `[2, 4, 6]`"
    `s = 0` puis `s += x` → `12`.

??? question "Maximum de `[3, 7, 2]` (méthode)"
    Initialiser `maxi = 3`, comparer → `7`.

??? question "Occurrences de `\"a\"` dans `\"banana\"`"
    `\"banana\".count(\"a\")` → `3`.

??? question "Colonne 1 de `[[1,2],[3,4]]`"
    `[2, 4]`.

??? question "Ajouter puis supprimer la clé `\"x\"`"
    `d[\"x\"] = 1` ; `del d[\"x\"]`.

??? question "Parcourir `items()` d'un carnet de notes"
    `for nom, note in notes.items(): print(nom, note)`.

---

!!! info "Approfondissements (hors essentiel)"
    Les exercices de **graphiques**, lecture **EXIF**, chiffrement de **Vigenère** et
    **séquences nucléiques** sont des **approfondissements**. Les exercices de base
    (tuples, listes, matrices, **carnet de notes**, **carré magique**, **cartes**,
    **César**, **jeu de 32 cartes**) suffisent pour maîtriser le chapitre.

---

## À retenir absolument

!!! success "Syntaxes & choix"
    | Structure | Délimiteurs | Modifiable ? | Accès |
    |---|---|---|---|
    | **Tuple** | `( )` | non | indice |
    | **Liste** | `[ ]` | oui | indice |
    | **Dictionnaire** | `{ }` | oui | clé |

!!! note "Réflexes clés"
    - **indices à partir de 0** ; slice : borne finale **exclue** ;
    - **parcours** : par valeurs (`for x in L`) ou indices (`range(len(L))`) ;
    - **compréhension** : `[expr for x in L if condition]` ;
    - **copie** : `L[:]` (jamais `L2 = L` qui crée un **alias**) ;
    - **matrice** : double boucle ; ligne `M[i]`, colonne `[M[i][j] for i in …]` ;
    - **dictionnaire** : `d[k] = v`, `del d[k]`, `k in d`, `d.get(k, defaut)`,
      `for k, v in d.items()`.
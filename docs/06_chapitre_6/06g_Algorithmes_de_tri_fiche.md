---
author: Elisabeth Le Prettre (LePrettre)
title: 06b 📜 Fiche Méthode - Algorithmes de tri
---

# Les tris : sélection et insertion

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 7"
    Fiche **compacte** pour **dérouler et programmer** le **tri par sélection** et le
    **tri par insertion** : principe, code, traces, complexités, stabilité,
    invariant et terminaison.

!!! note "Exemple filé"
    Liste de départ : `[5, 2, 4, 1]` → triée : `[1, 2, 4, 5]`.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les algorithmes de tri par **sélection** et par **insertion** ;
- **expliquer** le rôle de la partie triée / non triée ;
- **tracer** un tri à la main (tableau de suivi) ;
- **compléter** et **programmer** les deux tris ;
- **comparer** leurs complexités et leur **stabilité**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Tri** | Ranger des éléments dans un **ordre**. |
| **Classement** | Résultat ordonné. |
| **Ordre croissant / décroissant** | Du plus petit au plus grand / l'inverse. |
| **Partie triée** | Portion déjà en ordre. |
| **Partie non triée** | Portion restant à traiter. |
| **Indice du minimum** | Position du plus petit élément. |
| **Échange** | Permuter deux valeurs. |
| **Décalage** | Déplacer des éléments d'une case. |
| **Insertion** | Placer une valeur à sa bonne position. |
| **Stabilité** | Conserve l'ordre des éléments **égaux**. |
| **Invariant** | Propriété vraie à chaque tour de boucle. |
| **Correction partielle** | Si l'algo s'arrête, le résultat est trié. |
| **Terminaison** | L'algo s'arrête toujours. |
| **Meilleur / pire cas** | Situation la moins / la plus coûteuse. |

---

## 3. Tri par sélection

!!! abstract "Principe"
    On sépare la liste en **partie triée** (à gauche) et **non triée** (à droite). À
    chaque tour, on **cherche le minimum** de la partie non triée et on l'**échange**
    avec le premier élément non trié.

```python
def tri_selection(T):
    n = len(T)
    for i in range(n - 1):
        mini = i
        for j in range(i + 1, n):
            if T[j] < T[mini]:
                mini = j
        T[i], T[mini] = T[mini], T[i]   # échange final
```

- **boucle extérieure** sur `i` (début de la partie non triée) ;
- **`mini = i`** (on suppose le minimum au début) ;
- recherche dans **`T[i+1:n]`**, **mise à jour de `mini`** si plus petit ;
- **échange** `T[i]` ↔ `T[mini]` ; la **zone triée** grandit d'une case.

!!! note "Propriétés"
    - **Complexité : `O(n²)`** (toujours, même si déjà triée) ;
    - **non stable** dans la version classique (l'échange peut inverser des égaux) ;
    - **invariant** : après le tour `i`, `T[0..i]` contient les `i+1` plus petits, **triés** ;
    - **terminaison** : deux boucles `for` **bornées**.

---

## 4. Échanger deux valeurs

```python
temp = T[a]
T[a] = T[b]
T[b] = temp
# version courte : T[a], T[b] = T[b], T[a]
```

- une **variable temporaire** évite d'écraser une valeur ;
- **vérifier** : avant `T[a]=x, T[b]=y` → après `T[a]=y, T[b]=x`.

---

## 5. Tri par insertion

!!! abstract "Principe"
    La **première** valeur est considérée comme triée. On prend chaque valeur
    suivante (`tmp`) et on la **glisse** à sa place en **décalant** vers la droite les
    éléments plus grands.

```python
def tri_insertion(T):
    n = len(T)
    for i in range(1, n):
        tmp = T[i]
        j = i - 1
        while j >= 0 and T[j] > tmp:
            T[j + 1] = T[j]   # décalage
            j -= 1
        T[j + 1] = tmp        # insertion
```

- **`tmp = T[i]`** : valeur à insérer ; **`j = i - 1`** ;
- **décalage tant que** `T[j] > tmp` (et `j >= 0`), avec **`j -= 1`** ;
- **insertion en `j + 1`**.

!!! note "Propriétés"
    - **Meilleur cas `O(n)`** (déjà triée) ; **pire cas `O(n²)`** (ordre inverse) ;
    - **stable** ;
    - **invariant** : après le tour `i`, `T[0..i]` est **trié** ;
    - **terminaison** : `for` borné ; dans le `while`, `j` **décroît**.

---

## 6. Tableau comparatif

| Critère | **Sélection** | **Insertion** |
|---|---|---|
| Principe | chercher le **minimum** | **insérer** à sa place |
| Partie triée | à **gauche** | à **gauche** |
| Opérations | recherche + **échange** | **décalages** + insertion |
| Boucles | deux `for` | `for` + `while` |
| Stabilité | **non** (version classique) | **oui** |
| Meilleur cas | `O(n²)` | **`O(n)`** |
| Pire cas | `O(n²)` | `O(n²)` |
| Avantage | peu d'échanges | rapide si **presque trié** |
| Limite | toujours `O(n²)` | lent si ordre inverse |

---

## 7. Méthodes

??? note "Dérouler un tri à la main"
    - **Étapes :** appliquer l'algorithme tour par tour, **réécrire la liste** à chaque étape.
    - **Vérif :** la partie triée grandit d'une case par tour.

??? note "Rechercher le minimum d'une sous-liste"
    - Supposer le minimum au **début** (`mini = i`), parcourir, mettre à jour si plus petit.

??? note "Mémoriser l'indice du minimum"
    - Stocker **l'indice** (`mini`), pas la valeur : c'est lui qui sert à l'échange.

??? note "Choisir les bornes de `range`"
    - Sélection : extérieure `range(n-1)`, intérieure `range(i+1, n)`.
    - **Erreur :** oublier le **dernier** élément (mauvaise borne).

??? note "Réaliser un tri décroissant"
    - Sélection : chercher le **maximum** (`T[j] > T[mini]`).
    - Insertion : décaler tant que `T[j] < tmp`.

??? note "Trier en partant de la fin"
    - Variante : faire progresser la zone triée **depuis la droite** (adapter les bornes).

??? note "Suivre `i`, `j`, `mini` ou `tmp`"
    - Tenir un **tableau de trace** avec ces variables à chaque tour.

??? note "Compléter un code à trous"
    - Repérer : init (`mini=i` / `tmp=T[i]`), condition, mise à jour (`j-=1`), placement final.

??? note "Calculer le nombre de comparaisons"
    - **Sélection** : `n(n-1)/2` comparaisons (toujours).

??? note "Justifier un invariant"
    - Énoncer la propriété vraie **à chaque tour** (partie gauche triée).

??? note "Prouver la terminaison"
    - Boucles `for` **bornées** ; dans l'insertion, `j` **décroît** strictement.

---

## 8. Tableaux de trace

!!! example "Sélection sur `[5, 2, 4, 1]`"
    | Tour `i` | `mini` final | Échange | Liste après |
    |---|---|---|---|
    | 0 | 3 (valeur 1) | T[0]↔T[3] | `[1, 2, 4, 5]` |
    | 1 | 1 (valeur 2) | T[1]↔T[1] | `[1, 2, 4, 5]` |
    | 2 | 2 (valeur 4) | T[2]↔T[2] | `[1, 2, 4, 5]` |

    *Modèle complet :* tour · `i` · `j` · `mini` · comparaison · échange · liste.

!!! example "Insertion sur `[5, 2, 4, 1]`"
    | Tour `i` | `tmp` | Décalages | Liste après |
    |---|---|---|---|
    | 1 | 2 | 5 → droite | `[2, 5, 4, 1]` |
    | 2 | 4 | 5 → droite | `[2, 4, 5, 1]` |
    | 3 | 1 | 5, 4, 2 → droite | `[1, 2, 4, 5]` |

    *Modèle complet :* tour · `i` · `tmp` · `j` · condition · décalage · liste.

---

## 9. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Confondre **minimum** et **indice** | mémoriser l'**indice** `mini` |
| Réinitialiser `mini` au mauvais endroit | `mini = i` **au début** de chaque tour |
| Échanger à **chaque comparaison** | échanger **une fois**, à la fin du tour |
| **Mauvaise borne** de boucle | `range(i+1, n)` (intérieure) |
| **Oublier le dernier** élément | vérifier les bornes |
| **Écraser la valeur à insérer** | sauver `tmp = T[i]` d'abord |
| **Oublier `j -= 1`** | sinon boucle infinie |
| Insérer en **`j`** au lieu de **`j+1`** | la position correcte est `j + 1` |
| Confondre **échange** et **décalage** | sélection = échange ; insertion = décalage |
| Dire que la **sélection est stable** | la version classique ne l'est **pas** |
| Oublier les **cas** de l'insertion | meilleur `O(n)`, pire `O(n²)` |
| Modifier une **copie** au lieu de la liste | trier la liste **attendue** (en place) |

---

## 10. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce que la partie triée ?"
    La portion de la liste déjà **en ordre** (à gauche).

??? question "2. (N1) Qu'est-ce que la stabilité d'un tri ?"
    Il **conserve l'ordre** des éléments **égaux**.

??? question "3. (N2) Qu'est-ce qu'un invariant de boucle ?"
    Une propriété **vraie à chaque tour** (ici, partie gauche triée).

??? question "4. (N1) Différence entre échange et décalage ?"
    L'**échange** permute deux valeurs ; le **décalage** déplace des éléments d'une case.

??? question "5. (N2) Que signifie « trier en place » ?"
    Modifier **directement** la liste, sans en créer une copie.

### Compréhension

??? question "6. (N1) Quelle complexité a le tri par sélection ?"
    `O(n²)`, **toujours**.

??? question "7. (N2) Pourquoi le tri par insertion est-il `O(n)` au meilleur cas ?"
    Si la liste est **déjà triée**, le `while` ne décale jamais.

??? question "8. (N2) Le tri par sélection classique est-il stable ?"
    **Non** : l'échange peut inverser des éléments égaux.

??? question "9. (N3) Pourquoi le tri par insertion termine-t-il ?"
    Le `for` est borné et, dans le `while`, `j` **décroît** strictement.

??? question "10. (N2) Quand l'insertion est-elle plus avantageuse que la sélection ?"
    Quand la liste est **presque triée**.

### Traces

??? question "11. (N1) Sélection sur `[5,2,4,1]`, tour 0 : quel indice de minimum ?"
    `3` (la valeur `1`).

??? question "12. (N2) Liste après le tour 0 de la sélection ?"
    `[1, 2, 4, 5]`.

??? question "13. (N2) Insertion sur `[5,2,4,1]`, tour 1 : `tmp` et liste ?"
    `tmp = 2`, liste `[2, 5, 4, 1]`.

??? question "14. (N3) Insertion, tour 3 : combien de décalages ?"
    Trois (5, 4, 2 décalés) pour insérer `1`.

??? question "15. (N3) Combien de comparaisons pour la sélection sur 4 éléments ?"
    `4 × 3 / 2 = 6`.

### Lecture de code

??? question "16. (N1) Dans la sélection, que vaut `mini` au début de chaque tour ?"
    `i`.

??? question "17. (N2) Dans l'insertion, à quoi sert `tmp` ?"
    À **sauver** la valeur à insérer avant les décalages.

??? question "18. (N2) Pourquoi `T[j+1] = tmp` et non `T[j] = tmp` ?"
    Parce qu'après le `while`, `j` a été décrémenté une fois de trop.

??? question "19. (N3) Que se passe-t-il si on oublie `j -= 1` ?"
    **Boucle infinie** (la condition reste vraie).

??? question "20. (N2) Que fait `T[i], T[mini] = T[mini], T[i]` ?"
    Un **échange** des deux valeurs.

### Méthode

??? question "21. (N1) Comment trouver l'indice du minimum d'une sous-liste ?"
    Supposer `mini = i`, parcourir, mettre à jour si `T[j] < T[mini]`.

??? question "22. (N2) Comment passer la sélection en tri décroissant ?"
    Chercher le **maximum** (`T[j] > T[mini]`).

??? question "23. (N2) Comment passer l'insertion en tri décroissant ?"
    Décaler tant que `T[j] < tmp`.

??? question "24. (N3) Comment justifier l'invariant de la sélection ?"
    Après le tour `i`, `T[0..i]` contient les `i+1` plus petits, triés.

??? question "25. (N3) Combien de comparaisons fait la sélection sur `n` éléments ?"
    `n(n-1)/2`.

### Correction d'erreurs

??? question "26. (N1) `mini = 0` placé avant la boucle extérieure : erreur ?"
    Il faut `mini = i` **à chaque** tour.

??? question "27. (N2) Échanger à chaque fois que `T[j] < T[mini]` : erreur ?"
    On ne fait qu'**un seul** échange, à la **fin** du tour.

??? question "28. (N2) `range(i, n)` pour la boucle intérieure de la sélection : erreur ?"
    `range(i+1, n)` (on part **après** `i`).

??? question "29. (N3) `T[j] = tmp` au lieu de `T[j+1] = tmp` : erreur ?"
    On insère à la mauvaise position : c'est `j + 1`.

??? question "30. (N2) Oublier `tmp = T[i]` dans l'insertion : conséquence ?"
    La valeur à insérer est **écrasée** par le décalage.

### Programmation / code à compléter

??? question "31. (N1) Compléter l'init de la sélection : `____ = i`."
    `mini = i`.

??? question "32. (N2) Compléter la condition du `while` de l'insertion."
    `while j >= 0 and T[j] > tmp:`.

??? question "33. (N2) Écrire l'échange de `T[i]` et `T[mini]`."
    `T[i], T[mini] = T[mini], T[i]`.

??? question "34. (N3) Compléter l'insertion finale."
    `T[j + 1] = tmp`.

??? question "35. (N4) Écrire un tri par sélection **décroissant**."
    ```python
    for i in range(len(T) - 1):
        maxi = i
        for j in range(i + 1, len(T)):
            if T[j] > T[maxi]:
                maxi = j
        T[i], T[maxi] = T[maxi], T[i]
    ```

---

## 11. Exercices flash corrigés

??? question "Trouver le minimum et son indice de `[4, 1, 3]`"
    Minimum `1`, indice `1`.

??? question "Effectuer un échange de `T[0]` et `T[2]` dans `[4,1,3]`"
    `[3, 1, 4]`.

??? question "Compléter les bornes : boucle intérieure de la sélection"
    `range(i + 1, n)`.

??? question "Donner un tour de sélection sur `[3, 1, 2]` (i=0)"
    Minimum à l'indice 1 → échange → `[1, 3, 2]`.

??? question "Décaler pour insérer `2` dans `[1, 3, 5 | …]`"
    `3` et `5` décalés ; `2` inséré après `1` → `[1, 2, 3, 5]`.

??? question "Prévoir l'état de `[2,1]` après un tour d'insertion"
    `[1, 2]`.

??? question "Identifier le tri : « on décale puis on insère »"
    Tri par **insertion**.

??? question "Déterminer stabilité et complexité de l'insertion"
    **Stable** ; meilleur `O(n)`, pire `O(n²)`.

---

## À retenir absolument

!!! success "Les deux algorithmes"
    ```python
    # SÉLECTION : chercher le min, échanger
    for i in range(n-1):
        mini = i
        for j in range(i+1, n):
            if T[j] < T[mini]: mini = j
        T[i], T[mini] = T[mini], T[i]

    # INSERTION : décaler, insérer
    for i in range(1, n):
        tmp = T[i]; j = i - 1
        while j >= 0 and T[j] > tmp:
            T[j+1] = T[j]; j -= 1
        T[j+1] = tmp
    ```

!!! note "Variables, invariants, complexités, stabilité"
    | | **Sélection** | **Insertion** |
    |---|---|---|
    | Variables | `i`, `j`, `mini` | `i`, `j`, `tmp` |
    | Invariant | `T[0..i]` = `i+1` plus petits triés | `T[0..i]` trié |
    | Meilleur / pire | `O(n²)` / `O(n²)` | `O(n)` / `O(n²)` |
    | Stable | **non** | **oui** |

!!! quote "Réflexes"
    - sélection = **min + échange** ; insertion = **décalage + insertion en `j+1`** ;
    - ne pas oublier `mini = i` à chaque tour, ni `j -= 1` dans le `while` ;
    - **terminaison** : boucles bornées ; dans l'insertion, `j` décroît.
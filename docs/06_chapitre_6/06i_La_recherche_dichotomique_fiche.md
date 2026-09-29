---
author: Elisabeth Le Prettre (LePrettre)
title: 06c 📜 Fiche Méthode - La recherche dichotomique
---

# La recherche dichotomique

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 8"
    Fiche **compacte** pour **refaire seul les exercices** : principe de la recherche
    dichotomique, code, traces, **complexité `O(log n)`**, invariant et terminaison.

!!! note "Exemple filé"
    Tableau **trié** `T = [2, 7, 12, 19, 27, 35, 41, 50]` (indices 0 à 7).

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** le principe de la recherche dichotomique ;
- **expliquer** pourquoi le tableau doit être **trié** ;
- **tracer** une recherche (tableau de suivi) ;
- **calculer** le nombre d'étapes (`log₂ n`) ;
- **compléter** et **programmer** la fonction ;
- comparer `O(n)` et **`O(log n)`**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Recherche séquentielle** | Parcourir un à un (coût `O(n)`). |
| **Recherche dichotomique** | Diviser l'intervalle **par deux** à chaque étape. |
| **Tableau trié** | Éléments rangés en ordre (croissant). |
| **Cible** | Valeur `x` recherchée. |
| **Borne gauche / droite** | Indices `gauche` / `droite` de l'intervalle. |
| **Milieu** | `(gauche + droite) // 2`. |
| **Intervalle de recherche** | `T[gauche..droite]`. |
| **Invariant** | Si `x` est présent, il est **dans l'intervalle**. |
| **Variant** | La **taille** de l'intervalle (qui décroît). |
| **Correction partielle** | Si l'algo s'arrête, la réponse est juste. |
| **Terminaison** | L'algo s'arrête toujours. |
| **Complexité logarithmique** | `O(log n)`. |

---

## 3. Précondition

!!! warning "Le tableau doit être trié"
    La recherche dichotomique **exige** un tableau **trié** : c'est ce qui permet de
    déduire **quelle moitié** conserver après chaque comparaison. Sur un tableau
    **non trié**, l'élimination d'une moitié n'est plus justifiée : l'algorithme peut
    **rater** la cible et renvoyer un résultat **faux**.

---

## 4. Fiche méthode principale

```python
def recherche_dichotomique(T, x):
    gauche = 0
    droite = len(T) - 1
    while gauche <= droite:
        milieu = (gauche + droite) // 2
        if T[milieu] == x:
            return milieu
        elif T[milieu] < x:
            gauche = milieu + 1
        else:
            droite = milieu - 1
    return None
```

| Étape | Rôle | Justification | Erreur possible |
|---|---|---|---|
| `gauche = 0`, `droite = len(T)-1` | délimiter l'intervalle | tout le tableau au départ | écrire `droite = len(T)` (hors limites) |
| `while gauche <= droite` | continuer tant qu'il reste des éléments | `<=` garde le cas **un seul** élément | `gauche < droite` rate ce cas |
| `milieu = (gauche+droite)//2` | élément central | division **entière** | utiliser `/` (donne un flottant) |
| comparer `T[milieu]` à `x` | décider | trois cas possibles | confondre **valeur** et **indice** |
| `return milieu` si égalité | trouvé | renvoie l'**indice** | renvoyer `True` au lieu de l'indice |
| `gauche = milieu+1` si trop petit | garder la **moitié droite** | `x` est plus grand | oublier le **`+1`** (boucle infinie) |
| `droite = milieu-1` si trop grand | garder la **moitié gauche** | `x` est plus petit | oublier le **`-1`** |
| `return None` | intervalle **vide** | `x` absent | renvoyer `None` **trop tôt** |

---

## 5. Méthodes

??? note "Vérifier qu'une liste est triée"
    Parcourir et vérifier `T[i] <= T[i+1]` pour tout `i` ; sinon, la dichotomie n'est pas applicable.

??? note "Réaliser une recherche à la main"
    Calculer le milieu, comparer, **éliminer une moitié**, recommencer jusqu'à trouver ou intervalle vide.

??? note "Construire un tableau de trace"
    Colonnes : étape · `gauche` · `droite` · `milieu` · `T[milieu]` · comparaison · action · nouvel intervalle.

??? note "Choisir la moitié à conserver"
    - `T[milieu] < x` → garder **à droite** (`gauche = milieu+1`) ;
    - `T[milieu] > x` → garder **à gauche** (`droite = milieu-1`).

??? note "Traiter une valeur absente"
    La boucle s'arrête quand `gauche > droite` (intervalle vide) → `return None`.

??? note "Compléter le pseudo-code"
    Repérer : initialisation, condition `<=`, calcul du milieu, trois cas, retour final.

??? note "Compléter la fonction Python"
    Vérifier `//`, les `+1`/`-1`, et que le `return None` est **hors** de la boucle.

??? note "Prévoir la valeur retournée"
    L'**indice** si trouvé, `None` sinon.

??? note "Calculer le nombre d'étapes (divisions par 2)"
    Diviser `n` par 2 jusqu'à 1 : le nombre de divisions ≈ `log₂(n)`.

??? note "Comparer `O(n)` et `O(log n)`"
    Pour `n` grand, `O(log n)` est **bien plus rapide** (ex. 30 000 → ~15 étapes).

??? note "Prouver la correction (invariant)"
    **Invariant :** si `x` est présent, alors il est dans `T[gauche..droite]`. Il reste vrai à chaque tour.

??? note "Prouver la terminaison (variant)"
    **Variant :** `droite - gauche` **diminue strictement** à chaque tour et finit par devenir négatif.

---

## 6. Tableau de trace

!!! example "Cible trouvée : `x = 35`"
    | Étape | `gauche` | `droite` | `milieu` | `T[milieu]` | Comparaison | Action | Nouvel intervalle |
    |---|---|---|---|---|---|---|---|
    | 1 | 0 | 7 | 3 | 19 | `19 < 35` | `gauche = 4` | [4, 7] |
    | 2 | 4 | 7 | 5 | 35 | `= 35` | **return 5** | trouvé |

!!! example "Cible absente : `x = 30`"
    | Étape | `gauche` | `droite` | `milieu` | `T[milieu]` | Comparaison | Action | Nouvel intervalle |
    |---|---|---|---|---|---|---|---|
    | 1 | 0 | 7 | 3 | 19 | `19 < 30` | `gauche = 4` | [4, 7] |
    | 2 | 4 | 7 | 5 | 35 | `35 > 30` | `droite = 4` | [4, 4] |
    | 3 | 4 | 4 | 4 | 27 | `27 < 30` | `gauche = 5` | [5, 4] |
    | — | 5 | 4 | — | — | `gauche > droite` | **return None** | vide |

---

## 7. Complexité

À chaque étape, l'intervalle est **divisé par 2**. On s'arrête quand il ne reste
plus qu'un élément :

```
n / 2^a = 1   →   2^a = n   →   a = log₂(n)
```

!!! example "Annuaire de 30 000 noms (pire cas)"
    | Étape | Éléments restants |
    |---|---|
    | 0 | 30 000 |
    | 1 | 15 000 |
    | 2 | 7 500 |
    | … | … |
    | 14 | 2 |
    | 15 | 1 |

    `2^15 = 32 768 > 30 000` → **environ 15 étapes** au pire cas.

!!! tip "Comparaison avec la recherche séquentielle"
    - **séquentielle** : jusqu'à **30 000** comparaisons (`O(n)`) ;
    - **dichotomique** : **~15** comparaisons (`O(log n)`).
    Les mesures avec **`%timeit`** confirment ce gain énorme sur de grands tableaux **triés**.

---

## 8. Lecture et compréhension de code

!!! tip "Méthode"
    - repérer les **paramètres** (`T`, `x`) ;
    - lire la **condition** du `while` (`gauche <= droite`) ;
    - identifier les **trois cas** (égal / plus petit / plus grand) ;
    - vérifier la **mise à jour des bornes** (`+1` / `-1`) ;
    - repérer les **`return`** (indice trouvé / `None`) ;
    - tester le **cas d'une liste vide** ;
    - repérer ce qui pourrait causer une **boucle infinie** (oubli de `+1`/`-1`).

---

## 9. Erreurs fréquentes

| Erreur | Conséquence / correction |
|---|---|
| Liste **non triée** | résultat **faux** : trier d'abord |
| `droite = len(T)` | **index hors limites** : `len(T) - 1` |
| `/` au lieu de `//` | milieu **flottant** : utiliser `//` |
| **Inverser** les mises à jour | on garde la mauvaise moitié |
| `gauche = milieu` / `droite = milieu` | **boucle infinie** : ajouter `+1` / `-1` |
| Oublier `+1` ou `-1` | **boucle infinie** |
| `gauche < droite` | rate le cas **un seul** élément : `<=` |
| Oublier le cas « une valeur reste » | cible manquée : garder `<=` |
| `return None` **dans** la boucle | sortie **trop tôt** : le mettre **après** |
| Confondre **valeur** et **indice** | renvoyer le mauvais résultat |
| Annoncer **`O(n)`** | c'est **`O(log n)`** |

---

## 10. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'exige la recherche dichotomique ?"
    Un tableau **trié**.

??? question "2. (N1) Comment calcule-t-on le milieu ?"
    `milieu = (gauche + droite) // 2`.

??? question "3. (N2) Qu'est-ce que l'invariant ici ?"
    Si `x` est présent, il est **dans l'intervalle** `T[gauche..droite]`.

??? question "4. (N2) Qu'est-ce que le variant ?"
    La **taille** de l'intervalle, qui **diminue** à chaque tour.

??? question "5. (N1) Que renvoie la fonction si `x` est absent ?"
    `None`.

### Compréhension

??? question "6. (N1) Pourquoi le tableau doit-il être trié ?"
    Pour pouvoir **éliminer une moitié** selon la comparaison.

??? question "7. (N2) Pourquoi `gauche <= droite` et non `<` ?"
    Pour traiter le cas où il reste **un seul** élément.

??? question "8. (N2) Pourquoi `gauche = milieu + 1` et non `gauche = milieu` ?"
    Sinon l'intervalle ne **diminue pas** → boucle infinie.

??? question "9. (N3) Combien d'étapes au pire pour 1 000 éléments ?"
    `log₂(1000) ≈ 10` étapes.

??? question "10. (N2) Quelle est la complexité de la recherche dichotomique ?"
    `O(log n)`.

### Traces

??? question "11. (N1) `x = 35` : quel est le premier milieu et `T[milieu]` ?"
    Milieu `3`, `T[3] = 19`.

??? question "12. (N2) `x = 35` : à quel indice est-elle trouvée ?"
    À l'indice **5**.

??? question "13. (N2) `x = 30` : que vaut l'intervalle après l'étape 2 ?"
    `[4, 4]`.

??? question "14. (N3) `x = 30` : pourquoi la recherche s'arrête-t-elle ?"
    `gauche (5) > droite (4)` → intervalle **vide** → `None`.

??? question "15. (N3) `x = 2` dans le tableau filé : combien d'étapes ?"
    Étape 1 milieu 19 (>2 → d=2), étape 2 milieu `T[1]=7` (>2 → d=0), étape 3 `T[0]=2` → trouvé : **3 étapes**.

### Lecture de code

??? question "16. (N1) Quels sont les paramètres de la fonction ?"
    Le tableau `T` et la cible `x`.

??? question "17. (N2) Quels sont les trois cas comparés ?"
    `T[milieu]` égal, plus petit ou plus grand que `x`.

??? question "18. (N2) Que renvoie la fonction quand elle trouve `x` ?"
    L'**indice** `milieu`.

??? question "19. (N3) Que se passe-t-il si on écrit `gauche = milieu` ?"
    **Boucle infinie** (l'intervalle ne diminue plus).

??? question "20. (N2) Sur une liste vide, que renvoie la fonction ?"
    `None` (la boucle n'est jamais exécutée).

### Méthode

??? question "21. (N1) Comment vérifier qu'une liste est triée ?"
    Vérifier `T[i] <= T[i+1]` pour tout `i`.

??? question "22. (N2) Quelle moitié garde-t-on si `T[milieu] < x` ?"
    La **moitié droite** (`gauche = milieu + 1`).

??? question "23. (N2) Comment calculer le nombre d'étapes pour `n` ?"
    `log₂(n)` (divisions successives par 2).

??? question "24. (N3) Comment prouver la terminaison ?"
    L'intervalle (`droite - gauche`) **décroît** strictement.

??? question "25. (N3) Comment prouver la correction ?"
    Par l'**invariant** : la cible, si présente, reste dans l'intervalle.

### Correction d'erreurs

??? question "26. (N1) `droite = len(T)` : conséquence ?"
    **Index hors limites** : utiliser `len(T) - 1`.

??? question "27. (N2) `milieu = (gauche + droite) / 2` : erreur ?"
    Donne un **flottant** : utiliser `//`.

??? question "28. (N2) `gauche < droite` : conséquence ?"
    Rate le cas d'**un seul** élément restant.

??? question "29. (N3) `return None` placé dans la boucle : erreur ?"
    On sort **trop tôt** : le placer **après** la boucle.

??? question "30. (N2) Chercher dans une liste non triée : conséquence ?"
    Résultat **faux** (la dichotomie n'est plus valide).

### Programmation / code à compléter

??? question "31. (N1) Compléter l'initialisation des bornes."
    `gauche = 0` ; `droite = len(T) - 1`.

??? question "32. (N2) Compléter la condition de boucle."
    `while gauche <= droite:`.

??? question "33. (N2) Compléter la mise à jour si `T[milieu] < x`."
    `gauche = milieu + 1`.

??? question "34. (N3) Compléter le retour quand la valeur est absente."
    `return None` (après la boucle).

??? question "35. (N4) Écrire une version renvoyant `True`/`False` au lieu de l'indice."
    ```python
    def present(T, x):
        gauche, droite = 0, len(T) - 1
        while gauche <= droite:
            m = (gauche + droite) // 2
            if T[m] == x:
                return True
            elif T[m] < x:
                gauche = m + 1
            else:
                droite = m - 1
        return False
    ```

---

## 11. Exercices flash corrigés

??? question "Calculer un milieu : `gauche=2, droite=9`"
    `(2 + 9) // 2 = 5`.

??? question "Choisir la moitié : `T[milieu]=8 < x=12`"
    Garder la **moitié droite** (`gauche = milieu + 1`).

??? question "Mettre à jour une borne : `T[milieu]=20 > x=14`, milieu=6"
    `droite = 5`.

??? question "Compléter une trace : intervalle `[4,7]`, milieu ?"
    `(4 + 7) // 2 = 5`.

??? question "Prévoir un retour : cible absente"
    `None`.

??? question "Corriger une boucle : `gauche = milieu`"
    `gauche = milieu + 1`.

??? question "Nombre maximal d'étapes pour 1 000 000 d'éléments"
    `log₂(10⁶) ≈ 20` étapes.

??? question "Comparer avec la séquentielle pour 1 000 000 d'éléments"
    Séquentielle : jusqu'à **1 000 000** ; dichotomique : **~20**.

---

## À retenir absolument

!!! success "L'algorithme"
    ```python
    gauche, droite = 0, len(T) - 1
    while gauche <= droite:
        milieu = (gauche + droite) // 2
        if T[milieu] == x:    return milieu
        elif T[milieu] < x:   gauche = milieu + 1
        else:                 droite = milieu - 1
    return None
    ```

!!! note "Réflexes clés"
    - **précondition** : tableau **trié** ;
    - **init** : `gauche = 0`, `droite = len(T) - 1` ;
    - **boucle** : `while gauche <= droite` ; **milieu** : `(gauche+droite)//2` ;
    - **mises à jour** : `milieu + 1` (droite) / `milieu - 1` (gauche) ;
    - **cas absent** : `return None` (intervalle vide) ;
    - **complexité** : **`O(log n)`**.

!!! quote "Preuves"
    - **invariant** : si `x` est présent, il est dans `T[gauche..droite]` ;
    - **variant** : la taille de l'intervalle **décroît** → terminaison.
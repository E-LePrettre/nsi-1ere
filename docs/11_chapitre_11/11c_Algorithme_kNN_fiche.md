---
author: Elisabeth Le Prettre (LePrettre)
title: 11 📜 Fiche Méthode - Algorithme des k plus proches voisins
---

# L'algorithme des k plus proches voisins (k-NN)

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 16"
    Fiche **compacte** pour **refaire seul les exercices** : apprentissage supervisé,
    **distances**, algorithme **k-NN**, choix de `k`, vote majoritaire et limites.

!!! note "Exemple filé"
    Cible `(2, 3)`. Exemples : `P1(3,4) pomme`, `P2(2,5) poire`, `P3(1,1) pomme`,
    `P4(4,2) poire`, `P5(5,5) poire`.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les types d'apprentissage et le principe de k-NN ;
- **comprendre** le rôle des distances et de `k` ;
- **calculer** une distance, **lire** un graphique de données ;
- **expliquer** le **vote majoritaire** ;
- **programmer** k-NN et **critiquer** un résultat.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Apprentissage automatique** | La machine apprend à partir de **données**. |
| **Supervisé** | Données **étiquetées** (classe connue). |
| **Non supervisé** | Données **sans étiquette** (on cherche des groupes). |
| **Par renforcement** | Apprentissage par **récompense**. |
| **Jeu de données** | Ensemble d'exemples. |
| **Exemple** | Une donnée du jeu. |
| **Caractéristique** | Une mesure d'un exemple (taille, masse…). |
| **Classe / étiquette (label)** | Catégorie d'un exemple. |
| **Cible** | Le point à **classer**. |
| **Voisin** | Exemple **proche** de la cible. |
| **k** | Nombre de voisins considérés. |
| **Distance** | Mesure d'écart entre deux points. |
| **Classification** | Attribuer une **classe**. |
| **Vote majoritaire** | Classe la **plus fréquente** parmi les voisins. |
| **Donnée bruitée** | Donnée erronée / aberrante. |
| **Biais** | Déséquilibre du jeu de données. |
| **Normalisation** | Ramener les échelles à un domaine comparable. |

---

## 3. Distances

| Distance | Formule | Usage | Python |
|---|---|---|---|
| **Euclidienne** | `√((x1-x2)²+(y1-y2)²)` | à vol d'oiseau | `((x1-x2)**2+(y1-y2)**2)**0.5` |
| **Manhattan** | `|x1-x2|+|y1-y2|` | déplacements en grille | `abs(x1-x2)+abs(y1-y2)` |
| **Tchebychev** | `max(|x1-x2|,|y1-y2|)` | plus grand écart | `max(abs(x1-x2),abs(y1-y2))` |
| **Hamming** | nombre de positions différentes | chaînes / codes | boucle de comparaison |

```python
def euclidienne(p, q):
    return ((p[0]-q[0])**2 + (p[1]-q[1])**2) ** 0.5

def manhattan(p, q):
    return abs(p[0]-q[0]) + abs(p[1]-q[1])

def tchebychev(p, q):
    return max(abs(p[0]-q[0]), abs(p[1]-q[1]))

def hamming(a, b):
    n = 0
    for i in range(len(a)):
        if a[i] != b[i]:
            n += 1
    return n
```

---

## 4. Calculer une distance

!!! tip "Étapes"
    1. relever les **coordonnées** ;
    2. calculer les **écarts** ;
    3. appliquer la **formule** choisie ;
    4. **vérifier** le résultat et les **unités** ;
    5. **comparer** les distances.

!!! example "Cible `(2,3)` (euclidienne)"
    `P1(3,4)` → `√2 ≈ 1.41` · `P2(2,5)` → `2.00` · `P3(1,1)` → `√5 ≈ 2.24`.

!!! warning "Erreurs"
    Oublier la **valeur absolue** (Manhattan), **mélanger** les coordonnées,
    oublier la **racine** (euclidienne), utiliser une distance **inadaptée**.

---

## 5. Rechercher le plus proche voisin

```python
def plus_proche(exemples, cible):       # exemples = [((x,y), classe), ...]
    dmin = float("inf")
    voisin = None
    for coord, classe in exemples:
        d = euclidienne(coord, cible)
        if d < dmin:
            dmin = d
            voisin = classe
    return voisin
```

- **`dmin`** : distance minimale (initialisée à l'**infini**) ; **`voisin`** : classe retenue.
- **Coût linéaire** `O(n)` : on parcourt tous les exemples.

---

## 6. Appliquer k-NN

!!! tip "10 étapes"
    1. vérifier que les exemples sont **étiquetés** ;
    2. choisir la **cible** ;
    3. choisir une **distance** ;
    4. choisir **`k`** ;
    5. calculer **toutes** les distances ;
    6. **trier** par ordre croissant ;
    7. garder les **`k` premiers** ;
    8. **compter** les classes ;
    9. choisir la classe **majoritaire** ;
    10. annoncer la **prédiction**.

---

## 7. Tableau de trace (cible `(2,3)`, euclidienne)

| Exemple | Caract. | Classe | Distance | Rang | Voisin (k=3) ? |
|---|---|---|---|---|---|
| P1 | (3,4) | pomme | 1.41 | 1 | ✅ |
| P2 | (2,5) | poire | 2.00 | 2 | ✅ |
| P3 | (1,1) | pomme | 2.24 | 3 | ✅ |
| P4 | (4,2) | poire | 2.24 | 4 | ❌ |
| P5 | (5,5) | poire | 3.61 | 5 | ❌ |

**Vote (k=3)** : pomme ×2, poire ×1 → **prédiction : pomme**.

---

## 8. Programmer k-NN

```python
def cle(couple):              # clé de tri = la distance
    return couple[0]

def knn(exemples, cible, k):  # exemples = [((x,y), classe), ...]
    distances = []
    for coord, classe in exemples:
        distances.append((euclidienne(coord, cible), classe))
    distances = sorted(distances, key=cle)   # tri croissant
    voisins = distances[:k]                   # k premiers
    comptes = {}
    for d, classe in voisins:
        comptes[classe] = comptes.get(classe, 0) + 1
    meilleure = voisins[0][1]
    for classe in comptes:
        if comptes[classe] > comptes[meilleure]:
            meilleure = classe
    return meilleure
```

- **paramètres** : exemples, cible, `k` ; **résultat** : la classe prédite ;
- **tests** : vérifier sur un petit jeu dont on connaît la réponse.

---

## 9. Choisir k

| Valeur de `k` | Effet |
|---|---|
| **petit** | décision **locale**, sensible au **bruit** |
| **grand** | décision plus **lissée** |
| **pair** | risque d'**égalité** |
| **impair** | souvent choisi pour **deux** classes |

!!! note
    Tester plusieurs valeurs **près des frontières**. Il n'existe **pas** de `k` idéal
    valable pour tous les jeux de données.

!!! example "Effet de k (exemple filé)"
    `k=1` → **pomme** · `k=3` → **pomme** · `k=5` → **poire** (poire ×3, pomme ×2).

---

## 10. Choisir les caractéristiques

!!! tip "Méthode"
    - identifier les **données utiles** ;
    - vérifier **unités** et **échelles** ;
    - éviter qu'une caractéristique **domine** les autres ;
    - **normaliser** si les échelles sont très différentes ;
    - supprimer une caractéristique = **perdre de l'information**.

---

## 11. Lire un graphique de données

!!! tip "Méthode"
    - identifier les **axes** ;
    - lire les **classes** (légende) ;
    - repérer les **groupes** ;
    - **localiser** la cible ;
    - **estimer** les voisins ;
    - repérer une cible proche d'une **frontière** (cas incertain).

---

## 12. Utiliser scikit-learn

```python
from sklearn.neighbors import KNeighborsClassifier
donnees = list(zip(xs, ys))                  # couples de caractéristiques
modele = KNeighborsClassifier(n_neighbors=k)
modele.fit(donnees, labels)                  # apprentissage
prediction = modele.predict([cible])         # prédiction
print(prediction[0])                         # classe prédite
```

- `zip` assemble les caractéristiques en couples ;
- `fit` enregistre données + labels ; `predict` classe la cible ;
- `prediction[0]` est la **classe** prédite.

---

## 13. Critiquer un résultat k-NN

!!! tip "Questions à se poser"
    - la valeur de **`k`** est-elle justifiée ?
    - la **distance** est-elle adaptée ?
    - les **échelles** sont-elles comparables ?
    - les données sont-elles **nombreuses, fiables, représentatives** ?
    - la cible est-elle proche d'une **frontière** ?
    - existe-t-il une **égalité** ?
    - le **coût** est-il acceptable ?

---

## 14. Forces et limites

| Forces | Limites |
|---|---|
| simple et **intuitif** | sensible à **`k`** |
| adapté aux données **numériques** | sensible aux **échelles** |
| presque **aucun entraînement** | sensible au **bruit** et aux **biais** |
| | coût **`O(n)`** par prédiction |
| | dépend de la **qualité** du jeu de données |

---

## 15. Lecture de code

!!! tip "Comment retrouver…"
    - **la cible** : argument passé à la fonction ;
    - **`k`** : nombre de voisins gardés (`[:k]`) ;
    - **la distance** : la fonction appelée ;
    - **la clé de tri** : argument `key=` de `sorted` ;
    - **les k voisins** : `distances[:k]` ;
    - **la classe majoritaire** : la plus comptée ;
    - **la valeur retournée** : la classe prédite ;
    - **l'effet d'un changement** de `k` ou de distance : refaire tri / vote.

---

## 16. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Distances**
    | Exemple | Coordonnées | Distance |
    |---|---|---|

    **Tri & sélection**
    | Rang | Exemple | Distance | Retenu (k) ? |
    |---|---|---|---|

    **Comptage des classes**
    | Classe | Nombre parmi les k |
    |---|---|

    **Prédiction selon k**
    | k | Voisins | Prédiction |
    |---|---|---|

    **Comparaison de distances**
    | Exemple | Euclidienne | Manhattan | Tchebychev |
    |---|---|---|---|

---

## 17. Erreurs fréquentes

| Erreur | Conséquence / correction |
|---|---|
| Données **non étiquetées** | k-NN exige des exemples **classés** |
| Confondre **caractéristique** et **classe** | la classe est l'étiquette |
| Oublier de calculer **toutes** les distances | comparaison faussée |
| Trier en ordre **décroissant** | trier **croissant** |
| Garder **≠ k** voisins | utiliser `[:k]` |
| Compter **tous** les exemples | ne compter que les **voisins** |
| Confondre **plus proche** et **majoritaire** | k-NN vote, ne prend pas le seul plus proche |
| **`k` > nombre d'exemples** | choisir un `k` valide |
| Ignorer une **égalité** | la traiter (k impair, distance…) |
| Croire **`k=1` toujours meilleur** | `k=1` est sensible au **bruit** |
| Oublier l'effet des **unités** | normaliser si besoin |
| Annoncer une **certitude** | k-NN donne une **prédiction**, pas une preuve |

---

## 18. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce que l'apprentissage supervisé ?"
    Un apprentissage à partir de données **étiquetées**.

??? question "2. (N1) Que désigne `k` dans k-NN ?"
    Le **nombre de voisins** considérés.

??? question "3. (N2) Différence entre caractéristique et classe ?"
    La **caractéristique** est une mesure ; la **classe** est l'étiquette.

??? question "4. (N2) Qu'est-ce que le vote majoritaire ?"
    La classe **la plus fréquente** parmi les k voisins.

??? question "5. (N1) Qu'est-ce qu'une donnée bruitée ?"
    Une donnée **erronée** ou aberrante.

### Distances

??? question "6. (N1) Donner la formule de la distance de Manhattan."
    `|x1-x2| + |y1-y2|`.

??? question "7. (N2) Distance euclidienne entre (0,0) et (3,4) ?"
    `√(9+16) = 5`.

??? question "8. (N2) Distance de Tchebychev entre (2,3) et (5,4) ?"
    `max(3,1) = 3`.

??? question "9. (N3) Distance de Hamming entre `10110` et `10011` ?"
    `2` (positions 3 et 5 diffèrent).

??? question "10. (N2) Manhattan entre (2,3) et (4,2) ?"
    `|2-4|+|3-2| = 3`.

### Compréhension

??? question "11. (N1) k-NN a-t-il besoin de données étiquetées ?"
    **Oui** (apprentissage supervisé).

??? question "12. (N2) Pourquoi normaliser les caractéristiques ?"
    Pour éviter qu'une échelle **domine** les distances.

??? question "13. (N2) Pourquoi un k impair pour deux classes ?"
    Pour éviter les **égalités**.

??? question "14. (N3) Quel est le coût d'une prédiction k-NN ?"
    **`O(n)`** (toutes les distances calculées).

??? question "15. (N2) k-NN donne-t-il une certitude ?"
    Non : une **prédiction**, qui peut être fausse.

### Traces k-NN

??? question "16. (N1) Cible (2,3), k=1 : prédiction (exemple filé) ?"
    **pomme** (P1, le plus proche).

??? question "17. (N2) k=3 : quels voisins ?"
    P1, P2, P3.

??? question "18. (N2) k=3 : prédiction ?"
    **pomme** (2 contre 1).

??? question "19. (N3) k=5 : prédiction ?"
    **poire** (3 contre 2).

??? question "20. (N3) Pourquoi la prédiction change-t-elle entre k=3 et k=5 ?"
    On inclut **plus** de voisins, ce qui modifie la majorité.

### Lecture de code

??? question "21. (N1) Où lit-on `k` dans le code ?"
    Dans `distances[:k]`.

??? question "22. (N2) Que fait `sorted(distances, key=cle)` ?"
    Trie les couples par **distance croissante**.

??? question "23. (N2) Que renvoie `knn(...)` ?"
    La **classe majoritaire**.

??? question "24. (N3) Que donne `distances[:3]` ?"
    Les **3 plus proches** voisins.

??? question "25. (N2) Quelle structure pour compter les classes ?"
    Un **dictionnaire** (`comptes`).

### Méthode

??? question "26. (N1) Première étape de k-NN ?"
    Vérifier que les exemples sont **étiquetés**.

??? question "27. (N2) Comment sélectionner les k voisins ?"
    Trier par distance puis prendre `[:k]`.

??? question "28. (N2) Comment trouver la classe majoritaire ?"
    Compter les classes des voisins et prendre la plus fréquente.

??? question "29. (N3) Comment tester l'effet de k ?"
    Refaire la prédiction pour plusieurs valeurs de `k`.

??? question "30. (N3) Comment gérer une égalité de votes ?"
    Choisir un `k` impair (ou départager par distance).

### Esprit critique

??? question "31. (N1) Une seule donnée par classe : fiable ?"
    Non : jeu **trop petit**.

??? question "32. (N2) Caractéristiques d'échelles très différentes : risque ?"
    Une caractéristique **domine** → normaliser.

??? question "33. (N2) Cible sur une frontière : conséquence ?"
    Prédiction **incertaine**.

??? question "34. (N3) `k=1` sur des données bruitées : risque ?"
    Très **sensible** au bruit.

??? question "35. (N3) Jeu de données biaisé : conséquence ?"
    Prédictions **faussées**.

### Programmation

??? question "36. (N1) Écrire la distance euclidienne entre `p` et `q`."
    `((p[0]-q[0])**2 + (p[1]-q[1])**2) ** 0.5`.

??? question "37. (N2) Compléter une fonction de Hamming."
    ```python
    def hamming(a, b):
        n = 0
        for i in range(len(a)):
            if a[i] != b[i]:
                n += 1
        return n
    ```

??? question "38. (N2) Sélectionner les 3 plus proches d'une liste triée."
    `distances[:3]`.

??? question "39. (N3) Compter les classes des voisins."
    `comptes[classe] = comptes.get(classe, 0) + 1`.

??? question "40. (N4) Lire le résultat d'un `predict` scikit-learn."
    `prediction[0]`.

---

## 19. Exercices flash corrigés

??? question "Reconnaître le type d'apprentissage : données étiquetées"
    **Supervisé**.

??? question "Identifier caractéristiques et labels (fruits : masse, type)"
    Caractéristique = **masse** ; label = **type**.

??? question "Calculer les 4 distances entre (0,0) et (3,4)"
    Euclidienne `5`, Manhattan `7`, Tchebychev `4`, Hamming (codes) selon positions.

??? question "Trouver le plus proche voisin de (2,3) (exemple filé)"
    **P1** (distance ≈ 1.41).

??? question "Classer avec k=1, 3, 5 (exemple filé)"
    pomme, pomme, poire.

??? question "Résoudre une égalité de votes"
    Utiliser un `k` **impair** (ou départager par distance).

??? question "Compléter un tri par distance"
    `sorted(distances, key=cle)`.

??? question "Déterminer la classe majoritaire de [pomme, poire, pomme]"
    **pomme**.

??? question "Prévoir l'effet d'augmenter k"
    Décision plus **lissée** (moins sensible au bruit).

??? question "Repérer un problème d'échelle"
    Une caractéristique aux **grandes valeurs** domine → normaliser.

??? question "Compléter une fonction de Hamming"
    Compter les positions où `a[i] != b[i]`.

??? question "Lire un résultat `predict` valant `['poire']`"
    `prediction[0]` = **poire**.

---

## 20. Activités & annexe fichiers

!!! note "Activités du chapitre"
    Marché aux **fruits**, points **aléatoires**, jeu **Iris**, **cible-frontière**,
    distances de **Manhattan** et **Tchebychev**, **archéologie**.

!!! info "Annexe — manipuler des fichiers (support de l'analyse de texte)"
    | Élément | Rôle |
    |---|---|
    | `open(nom, mode)` | ouvre un fichier |
    | mode `"r"` / `"w"` / `"a"` | lecture / écriture / ajout |
    | `read()` | tout le contenu (chaîne) |
    | `readlines()` | liste des lignes |
    | `write(texte)` | écrire une chaîne |
    | `writelines(liste)` | écrire une liste de lignes |
    | `close()` | fermer le fichier |

---

## À retenir absolument

!!! success "Les 5 temps de k-NN"
    1. **distances** de la cible à tous les exemples ;
    2. **tri** croissant ;
    3. **k premiers** voisins ;
    4. **vote majoritaire** ;
    5. **prédiction**.

!!! note "Distances & k"
    - **euclidienne** `√((Δx)²+(Δy)²)`, **Manhattan** `|Δx|+|Δy|`,
      **Tchebychev** `max(|Δx|,|Δy|)`, **Hamming** (positions différentes) ;
    - **k** : petit = local/bruité, grand = lissé ; **impair** pour éviter les égalités.

!!! quote "Conditions & limites"
    - k-NN exige des **données étiquetées** (supervisé) ;
    - **coût `O(n)`** par prédiction ;
    - sensible aux **échelles** (normaliser) et à la **qualité** du jeu de données ;
    - fournit une **prédiction**, jamais une certitude.
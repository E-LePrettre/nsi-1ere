---
author: Elisabeth Le Prettre (LePrettre)
title: 09 📜 Fiche Méthode - Algorithme glouton
---

# Les algorithmes gloutons

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 14"
    Fiche **compacte** pour **refaire seul les exercices** : principe **glouton**,
    rendu de monnaie, **sac à dos**, stations-service et **TSP** (plus proche voisin).

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** le principe d'un algorithme glouton ;
- **expliquer** choix local, optimum local / global, optimalité non garantie ;
- **dérouler** les algorithmes (monnaie, sac, stations, TSP) ;
- **comparer** glouton et force brute, fournir un **contre-exemple** ;
- **choisir** une heuristique (valeur, poids, ratio) et connaître ses limites ;
- **évaluer** le coût d'un glouton (**tri compris**) ;
- **programmer** et **justifier** terminaison et correction.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Problème d'optimisation** | Chercher la **meilleure** solution sous contraintes. |
| **Algorithme glouton** | Fait à chaque étape le **meilleur choix immédiat**. |
| **Choix local** | Décision prise sans voir la suite. |
| **Optimum local / global** | Meilleur **proche** / meilleur **absolu**. |
| **Force brute** | Teste **toutes** les possibilités. |
| **Contrainte** | Condition à respecter (capacité, autonomie…). |
| **Solution réalisable** | Respecte les contraintes. |
| **Solution optimale** | La **meilleure** réalisable. |
| **Ratio valeur/poids** | Critère du sac à dos. |
| **Distancier** | Tableau des distances entre villes. |
| **Correction partielle** | Si l'algo s'arrête, le résultat est **valide**. |
| **Terminaison** | L'algo **s'arrête** toujours. |
| **Correction totale** | Partielle **+** terminaison. |
| **Heuristique** | **Critère** de choix glouton (valeur, poids, ratio…). |
| **Système canonique** | Système de pièces où le glouton est **toujours** optimal (ex : euro). |
| **Système non canonique** | Système où le glouton est **parfois** non optimal (ex : `{1,3,4}`). |
| **Sac 0/1** | Objets **indivisibles** : on prend tout l'objet ou rien (notre cas). |
| **Sac fractionnaire** | Objets **sécables** : le glouton par **ratio** y est optimal. |
| **Variant** | Quantité **entière ≥ 0 qui décroît** → prouve la **terminaison**. |
| **Invariant** | Propriété **préservée** à chaque tour → prouve la **correction partielle**. |

---

## 3. Force brute vs glouton

| | **Force brute** | **Glouton** |
|---|---|---|
| Principe | explore les possibilités | choix immédiat |
| Coût | **élevé** | **faible** (rapide) |
| Retour en arrière | oui | **non** |
| Optimum | peut le trouver | **non garanti** |

---

## 4. Rendu de monnaie

!!! tip "Étapes"
    1. **trier** les pièces par ordre **décroissant** ;
    2. **initialiser** une liste de compteurs ;
    3. **parcourir** les pièces ;
    4. **prendre** une pièce tant qu'elle **ne dépasse pas** la somme restante ;
    5. **diminuer** la somme ;
    6. **augmenter** le compteur ;
    7. **vérifier** que le reste final vaut **0** ;
    8. **compter** les pièces pour juger la qualité.

```python
def rendu(somme, pieces):          # pieces triées décroissant
    choisies = [0] * len(pieces)
    for i in range(len(pieces)):
        while pieces[i] <= somme:
            somme = somme - pieces[i]
            choisies[i] += 1
    return choisies                # le reste 'somme' doit valoir 0
```

- **`somme`** : reste à rendre ; **`pieces`** : liste triée ; **`i`** : indice courant ;
  **`choisies`** : compteurs par pièce.

!!! example "Comparaisons"
    - **Système européen** : le glouton donne **toujours** l'optimum.
    - **`{4, 3, 1}` pour 6** : glouton `4 + 1 + 1` (**3 pièces**) ; optimal `3 + 3` (**2 pièces**) → glouton **non optimal**.
    - **`{10, 5, 2}` pour 31** : glouton prend `10 + 10 + 10`, reste `1` → **bloqué** (échec),
      alors qu'une solution existe (`10 + 10 + 5 + 2 + 2 + 2`).

---

## 5. Tester l'optimalité

!!! tip "Méthode"
    - calculer la **solution gloutonne** ;
    - chercher une **autre combinaison** sur un petit exemple ;
    - **comparer** (nombre de pièces / valeur totale) ;
    - si le glouton est moins bon → fournir un **contre-exemple**.

!!! note "Trois situations à distinguer"
    - **résultat valide** (réalisable) ;
    - **résultat optimal** (le meilleur) ;
    - **problème sans solution** (le glouton se bloque).

---

## 6. Sac à dos simple

!!! tip "Étapes"
    Identifier valeur, poids, **capacité** → trier selon le critère → parcourir → **prendre**
    si le poids **rentre** → enregistrer → renvoyer les objets choisis.

```python
def sac_simple(objets, capacite):     # objets = [(nom, poids), ...]
    poids_total = 0
    choisis = []
    for nom, poids in objets:
        if poids_total + poids <= capacite:
            choisis.append(nom)
            poids_total += poids
    return choisis
```

---

## 7. Sac à dos avec dictionnaire

```python
pris = {}
for nom, poids in objets:
    if poids_total + poids <= capacite:
        pris[nom] = 1          # ajout d'une paire clé-valeur
        poids_total += poids
```

- `pris[nom] = 1` **ajoute** la paire `nom: 1` (objet sélectionné).

---

## 8. Sac à dos avec ratio

!!! tip "Étapes"
    1. calculer **`valeur / poids`** ;
    2. **ajouter** le ratio aux données de chaque objet ;
    3. **trier** par ratio **décroissant** ;
    4. **parcourir** la liste triée ;
    5. **ajouter** les objets compatibles ;
    6. calculer **masse** et **valeur** totales.

```python
# objets triés par ratio décroissant : [(nom, valeur, poids, ratio), ...]
masse = 0
valeur_totale = 0
for nom, valeur, poids, ratio in objets_tries:
    if masse + poids <= capacite:
        masse += poids
        valeur_totale += valeur
```

!!! warning
    Le **meilleur ratio local** ne garantit **pas** toujours la meilleure combinaison globale.

---

## 9. Choix de l'heuristique (sac à dos)

!!! tip "Trois critères de tri"
    - **par valeur** décroissante — « le plus de valeur d'abord » ;
    - **par poids** croissant — « le plus léger d'abord » ;
    - **par ratio** `valeur/poids` décroissant — « le plus rentable par kilo ».

!!! example "Les heuristiques peuvent diverger (capacité 50)"
    | Objet | Valeur | Poids | Ratio |
    |---|---|---|---|
    | A | 60 | 10 | 6,0 |
    | B | 100 | 20 | 5,0 |
    | C | 120 | 30 | 4,0 |

    - **valeur** → C+B = **220** (= optimum) ;
    - **poids** / **ratio** → A+B = **160** → le **ratio rate l'optimum**.

!!! example "Aucune heuristique n'est toujours la meilleure (capacité 10)"
    Gros (11, 10), Petit1 (6, 5), Petit2 (6, 5) :

    - **valeur** → Gros = **11** ;
    - **ratio** → Petit1+Petit2 = **12** (= optimum) → la **valeur rate l'optimum**.

!!! warning
    Pour le **sac 0/1**, **aucun glouton n'est garanti optimal**.

---

## 10. Glouton optimal : sous quelles conditions ?

| Problème | Glouton optimal | Glouton non optimal |
|---|---|---|
| **Monnaie** | système **canonique** (euro) | système **non canonique** (`{1,3,4}`) |
| **Sac à dos** | sac **fractionnaire** (sécable) | sac **0/1** (indivisible) |

!!! note "Montrer qu'un système est non canonique"
    Exhiber **une seule** somme où une autre combinaison fait **moins de pièces**.
    Ex : `{1,3,4}` pour 6 → glouton `4+1+1` (3 pièces) vs `3+3` (2 pièces).

!!! tip "Sac fractionnaire vs sac 0/1"
    - **fractionnaire** (on peut prendre une *fraction* d'objet) → le **ratio est optimal** ;
    - **0/1** (objet entier ou rien — notre cas) → le ratio peut **échouer**.

---

## 11. Coût des gloutons

!!! info "Coût mesuré selon n (types de pièces / objets)"
    | Algorithme | Meilleur cas | Pire cas |
    |---|---|---|
    | **Monnaie** (division `//` et `%`) | O(n) | O(n) |
    | **Sac à dos** (tri **sélection** + parcours) | O(n²) | O(n²) |
    | **Sac à dos** (tri **natif** + parcours) | O(n log n) | O(n log n) |

!!! warning "Le tri domine"
    Le parcours du sac est en **O(n)**, mais le **tri préalable domine** :
    **O(n log n)** (tri natif) ou **O(n²)** (tri sélection) — **et non O(n)**.
    C'est ce coût qui compte « dans le cas de données nombreuses ».

---

## 12. Voyage avec stations-service

!!! tip "Étapes"
    1. connaître les **distances** entre étapes et l'**autonomie** ;
    2. **cumuler** les distances depuis le dernier plein ;
    3. vérifier si l'étape suivante reste **accessible** ;
    4. sinon, **s'arrêter** à la dernière station accessible ;
    5. **enregistrer** son numéro (et la distance) ;
    6. **poursuivre** jusqu'à la fin ;
    7. **détecter** une étape **supérieure à l'autonomie** (impossible).

```python
cumul = 0
arrets = []
for i in range(len(distances)):
    if cumul + distances[i] > autonomie:
        arrets.append(i - 1)     # dernière station accessible
        cumul = 0
    cumul += distances[i]
```

---

## 13. TSP par plus proche voisin

!!! tip "Étapes"
    1. choisir une **ville de départ** ;
    2. lister les **villes non visitées** ;
    3. lire les **distances** depuis la ville actuelle (distancier) ;
    4. choisir la **plus proche** non visitée ;
    5. l'**ajouter** au trajet ;
    6. **mettre à jour** la distance totale ;
    7. **recommencer** ;
    8. **revenir** au départ.

```python
def ppv(depart, villes, distancier):
    trajet = [depart]
    actuelle = depart
    non_visitees = [v for v in villes if v != depart]
    total = 0
    while non_visitees:
        proche = non_visitees[0]                       # pas de lambda
        for v in non_visitees:
            if distancier[actuelle][v] < distancier[actuelle][proche]:
                proche = v
        total += distancier[actuelle][proche]
        trajet.append(proche)
        non_visitees.remove(proche)
        actuelle = proche
    total += distancier[actuelle][depart]              # retour au départ
    trajet.append(depart)
    return trajet, total
```

!!! note "Pourquoi tester plusieurs départs ?"
    Le résultat **dépend de la ville de départ** : en essayer **plusieurs** augmente
    la chance d'obtenir un bon trajet (le glouton n'est **pas** garanti optimal).

---

## 14. Construire un distancier

!!! tip "Étapes"
    - utiliser les **coordonnées** ;
    - appliquer `√((x₂−x₁)² + (y₂−y₁)²)` ;
    - mettre **0** sur la **diagonale** ;
    - utiliser la **symétrie** (`d[i][j] = d[j][i]`) ;
    - vérifier **unités** et **calculs**.

```python
import math
d = math.sqrt((x2 - x1)**2 + (y2 - y1)**2)
```

---

## 15. Pseudo-code et programmation

!!! tip "Identifier dans un algorithme glouton"
    - les **entrées** et la **sortie** ;
    - les **structures** utilisées (listes, dictionnaire, distancier) ;
    - l'**initialisation** ;
    - la **boucle** et le **choix glouton** ;
    - les **mises à jour** (somme, poids, total…) ;
    - la **condition d'arrêt**.

!!! note "Documenter et tester"
    Ajouter une **docstring** (rôle, paramètres, résultat) et des **tests** (`assert`)
    sur de **petits exemples** dont on connaît la solution.

---

## 16. Terminaison

| Problème | Pourquoi l'algorithme termine |
|---|---|
| **Rendu de monnaie** | la **somme diminue** (ou l'indice avance) |
| **Sac à dos** | le parcours des objets est **fini** |
| **Voyage** | l'**indice des stations avance** |
| **TSP** | le nombre de villes **non visitées diminue** |

!!! note "Correction"
    - **correction partielle** : si l'algo s'arrête, le résultat est **valide** ;
    - **terminaison** : il **s'arrête** toujours ;
    - **correction totale** : les deux à la fois (mais **pas** forcément optimal !).

!!! tip "Variant (terminaison) et invariant (correction)"
    - **variant** = quantité **entière ≥ 0 qui décroît strictement** → utile pour une **boucle non bornée** (`while`) ; une boucle `for` finie termine **d'office** ;
    - **invariant** = propriété **vraie avant** la boucle et **préservée** à chaque tour.

    **Monnaie** (`while`) : variant = `somme` (décroît) ; invariant = `somme_initiale = somme + pièces déjà choisies`.
    **Sac** (`for` borné) : termine d'office ; invariant = `poids_total ≤ capacité` → solution **réalisable**.

---

## 17. Tableaux de trace

!!! example "Modèles de tableaux"
    **Monnaie**
    | Pièce | Somme avant | Nombre pris | Somme après |
    |---|---|---|---|

    **Sac à dos**
    | Objet | Ratio | Poids courant | Décision | Valeur totale |
    |---|---|---|---|---|

    **Voyage**
    | Station | Distance cumulée | Prochaine étape | Arrêt ? |
    |---|---|---|---|

    **TSP**
    | Ville actuelle | Villes restantes | Distances | Ville choisie | Total |
    |---|---|---|---|---|

---

## 18. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Pièces dans le **mauvais ordre** | trier **décroissant** |
| **Valeur / indice** confondus | `pieces[i]` ≠ `i` |
| Oubli de **mettre à jour le reste** | `somme -= pieces[i]` |
| **Boucle infinie** | la pièce doit faire **diminuer** la somme |
| Ne pas vérifier que la somme atteint **0** | tester le **reste final** |
| Croire le glouton **toujours optimal** | fournir un **contre-exemple** |
| **Dépasser la capacité** du sac | tester `poids_total + poids <= capacite` |
| Trier sur la **mauvaise donnée** | trier selon le **critère** demandé |
| Calculer **`poids/valeur`** | c'est **`valeur/poids`** |
| Oublier le **retour** à la ville de départ | ajouter `distancier[actuelle][depart]` |
| **Revisiter** une ville | la retirer des non visitées |
| Oublier la **dernière station accessible** | s'arrêter **avant** de tomber en panne |
| Ne pas **détecter** une étape impossible | étape > autonomie → pas de solution |

---

## 19. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'un algorithme glouton ?"
    Un algorithme qui fait à chaque étape le **meilleur choix immédiat**, sans retour en arrière.

??? question "2. (N1) Différence entre optimum local et global ?"
    Le **local** est le meilleur **proche** ; le **global** est le meilleur **absolu**.

??? question "3. (N2) Qu'est-ce qu'une solution réalisable ?"
    Une solution qui **respecte les contraintes** (sans être forcément la meilleure).

??? question "4. (N2) Qu'est-ce que le ratio dans le sac à dos ?"
    `valeur / poids` : l'intérêt d'un objet par unité de poids.

??? question "5. (N1) Le glouton garantit-il l'optimum ?"
    **Non**.

### Compréhension

??? question "6. (N1) Pourquoi trier les pièces avant le rendu ?"
    Pour prendre d'abord les **plus grandes** (choix glouton).

??? question "7. (N2) Pourquoi `{4,3,1}` pour 6 met-il le glouton en défaut ?"
    Il donne `4+1+1` (3 pièces) au lieu de `3+3` (2 pièces).

??? question "8. (N2) Pourquoi tester plusieurs villes de départ au TSP ?"
    Le trajet **dépend du départ** ; cela améliore le résultat.

??? question "9. (N3) Pourquoi le meilleur ratio ne garantit-il pas le meilleur sac ?"
    Un bon choix **local** peut empêcher une **meilleure** combinaison globale.

??? question "10. (N2) Que signifie « le glouton se bloque » (monnaie) ?"
    Le reste final n'est **pas 0** : pas de solution trouvée.

### Traces

??? question "11. (N1) Rendu de 6 avec `{4,3,1}` : pièces prises ?"
    `4`, `1`, `1` (3 pièces).

??? question "12. (N2) Rendu de 31 avec `{10,5,2}` glouton : que se passe-t-il ?"
    `10+10+10` puis reste `1` → **bloqué**.

??? question "13. (N2) Sac capacité 5, objets de poids 3 puis 3 : que prend-on ?"
    Le **premier** (3) ; le second dépasse (`3+3>5`).

??? question "14. (N3) TSP depuis A : comment choisit-on la 2ᵉ ville ?"
    La **non visitée la plus proche** de A dans le distancier.

??? question "15. (N3) Voyage : étape de 120 km, autonomie 100 : conclusion ?"
    **Impossible** (étape > autonomie).

### Méthode

??? question "16. (N1) Comment vérifier qu'un rendu est complet ?"
    Le **reste** final doit valoir **0**.

??? question "17. (N2) Comment décider si un objet entre dans le sac ?"
    Si `poids_total + poids <= capacite`.

??? question "18. (N2) Comment calculer un ratio ?"
    `valeur / poids`.

??? question "19. (N3) Comment trouver un contre-exemple au glouton ?"
    Sur un petit système, exhiber une solution **meilleure** que le glouton.

??? question "20. (N3) Comment construire un distancier ?"
    Distance euclidienne entre coordonnées ; 0 sur la diagonale ; matrice symétrique.

### Correction d'erreurs

??? question "21. (N1) Pièces triées croissant : conséquence ?"
    Le glouton prend les **petites** d'abord : résultat incorrect.

??? question "22. (N2) Oubli de `somme -= piece` : conséquence ?"
    **Boucle infinie** (la somme ne diminue pas).

??? question "23. (N2) `poids / valeur` au lieu de `valeur / poids` : erreur ?"
    Le tri est faussé : utiliser `valeur / poids`.

??? question "24. (N3) Oubli du retour au départ (TSP) : conséquence ?"
    La distance totale est **fausse** (trajet non bouclé).

??? question "25. (N2) Revisiter une ville au TSP : erreur ?"
    La **retirer** des villes non visitées après l'avoir choisie.

### Programmation

??? question "26. (N1) Initialiser les compteurs de pièces."
    `choisies = [0] * len(pieces)`.

??? question "27. (N2) Compléter la condition du `while` de rendu."
    `while pieces[i] <= somme:`.

??? question "28. (N2) Tester si un objet rentre dans le sac."
    `if poids_total + poids <= capacite:`.

??? question "29. (N3) Écrire la distance euclidienne entre deux points."
    `math.sqrt((x2 - x1)**2 + (y2 - y1)**2)`.

??? question "30. (N4) Choisir la ville la plus proche (sans `lambda`)."
    ```python
    proche = non_visitees[0]
    for v in non_visitees:
        if distancier[actuelle][v] < distancier[actuelle][proche]:
            proche = v
    ```

---

### Heuristique, coût et preuve

??? question "31. (N2) Citer trois heuristiques pour le sac à dos."
    Par **valeur** décroissante, par **poids** croissant, par **ratio** valeur/poids décroissant.

??? question "32. (N3) Le ratio garantit-il l'optimum du sac 0/1 ?"
    **Non** (capacité 50 : ratio → 160, optimum → 220). Il est optimal pour le sac **fractionnaire**.

??? question "33. (N2) Quel est le coût du sac à dos glouton ?"
    **O(n log n)** : le **tri** domine le parcours en O(n) (O(n²) avec un tri par sélection).

??? question "34. (N2) Quel est le coût du rendu de monnaie (version division) ?"
    **O(n)**, identique au meilleur et au pire des cas.

??? question "35. (N3) À quoi servent un variant et un invariant ?"
    Le **variant** prouve la **terminaison** (quantité ≥ 0 décroissante) ; l'**invariant** prouve la **correction partielle** (propriété préservée).

??? question "36. (N3) Comment montrer qu'un système est non canonique ?"
    Donner **un** contre-exemple : `{1,3,4}` pour 6 → glouton 3 pièces, optimum 2.

---

## 20. Exercices flash corrigés

??? question "Choisir la pièce suivante : reste 7, pièces `{5,2,1}`"
    La pièce `5` (la plus grande ≤ 7).

??? question "Compléter un tableau de monnaie : rendre 8 avec `{5,2,1}`"
    `5 + 2 + 1` → 3 pièces.

??? question "Trouver un contre-exemple : système `{4,3,1}`, somme 6"
    Glouton `4+1+1` (3) vs optimal `3+3` (2).

??? question "Calculer un ratio : valeur 12, poids 4"
    `12 / 4 = 3`.

??? question "Décider si un objet tient : poids 4, courant 3, capacité 5"
    Non (`3 + 4 = 7 > 5`).

??? question "Choisir une station : cumul 90, étape 20, autonomie 100"
    S'**arrêter** : `90 + 20 = 110 > 100`.

??? question "Compléter un pseudo-code : mise à jour de la somme"
    `somme = somme - pieces[i]`.

??? question "Justifier la terminaison du sac à dos"
    Le **parcours des objets est fini**.

??? question "Calculer une distance entre (0,0) et (3,4)"
    `√(9 + 16) = 5`.

??? question "Choisir la ville la plus proche de A : B=5, C=2, D=8"
    **C** (distance 2).

---

## À retenir absolument

!!! success "Principe glouton"
    - **choix local** optimal à chaque étape, **sans retour en arrière** ;
    - **rapide**, mais **optimalité non garantie** (toujours pouvoir donner un **contre-exemple**).

!!! note "Méthode de chaque problème"
    - **Monnaie** : pièces triées décroissant, prendre tant que ≤ somme, reste = 0 ;
    - **Sac à dos** : trier (souvent par **ratio `valeur/poids`**), prendre si le poids rentre ;
    - **Stations** : cumuler les distances, s'arrêter à la **dernière station accessible** ;
    - **TSP** : **plus proche voisin**, revenir au départ, tester plusieurs départs.

!!! quote "Outils & terminaison"
    - **distancier** : distance euclidienne, 0 sur la diagonale, symétrique ;
    - **terminaison** : une quantité **diminue** (somme, objets, stations, villes restantes) ;
    - **correction totale** = correction partielle **+** terminaison (≠ optimalité).

!!! info "Prolongements (non étudiés)"
    Les autres méthodes d'optimisation (programmation dynamique, exploration complète…)
    ne sont **pas** au programme de ce chapitre.
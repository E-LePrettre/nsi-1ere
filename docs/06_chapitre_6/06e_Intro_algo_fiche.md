---
author: Elisabeth Le Prettre (LePrettre)
title: 06a 📜 Fiche Méthode - Introduction à l’algorithmique
---

# Algorithmique et complexité

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 6"
    Fiche **compacte** pour **refaire seul les exercices** : pseudo-code, trace
    d'exécution, **correction** et **terminaison**, calcul du **coût `T(n)`** et
    **ordres de complexité** (`O(1)`, `O(log n)`, `O(n)`, `O(n log n)`, `O(n²)`).

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** : pseudo-code, correction (partielle / totale), terminaison, complexité ;
- **expliquer** le rôle d'une variable, d'une boucle, d'une condition d'arrêt ;
- **suivre** une **trace d'exécution** ;
- **calculer** le coût `T(n)` d'un algorithme (avec le modèle du cours) ;
- **comparer** deux complexités et l'effet du **doublement de `n`**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Algorithme** | Suite finie d'étapes résolvant un problème. |
| **Pseudo-code** | Description d'un algorithme indépendante d'un langage. |
| **Entrée** | Données fournies. |
| **Sortie** | Résultat produit. |
| **Processus itératif** | Répétition d'étapes (boucle). |
| **Trace d'exécution** | Suivi des **valeurs** des variables, pas à pas. |
| **Correction partielle** | **Si** l'algorithme s'arrête, il donne le bon résultat. |
| **Terminaison** | L'algorithme **s'arrête** toujours. |
| **Correction totale** | Correction partielle **+** terminaison. |
| **Taille `n`** | Mesure de la quantité de données. |
| **Opération élémentaire** | Action de base (affectation, comparaison…). |
| **Coût `T(n)`** | Nombre d'opérations selon `n`. |
| **Complexité temporelle** | Évolution du **temps** selon `n`. |
| **Complexité spatiale** | Évolution de la **mémoire** selon `n`. |
| **Ordre de complexité** | Comportement dominant : `O(n)`, `O(n²)`… |

---

## 3. Fiches méthodes

??? note "Décrire un algorithme en pseudo-code"
    - **Repérer :** entrées, traitement, sortie.
    - **Modèle :** `Fonction nom(entrées) : initialisation → boucle → résultat`.

??? note "Identifier entrées, sortie, initialisation, boucle, condition d'arrêt"
    - **Entrées** : paramètres ; **sortie** : `return` ;
    - **initialisation** : avant la boucle ; **condition d'arrêt** : test du `while` / borne du `for`.

??? note "Construire une trace d'exécution"
    - **Étapes :** noter, ligne par ligne, les **valeurs** des variables et la **condition**.
    - **Modèle :** colonnes *ligne · variables · condition · action*.

??? note "Vérifier la terminaison"
    - **Idée :** montrer qu'une quantité **diminue** strictement vers une valeur d'arrêt.
    - **Erreur :** affirmer qu'un algorithme termine **sans justification**.

??? note "Compter les opérations d'une instruction"
    - Appliquer le **modèle de coût** (voir §4).
    - **Exemple :** `s = s + i` → lecture `s` (1) + lecture `i` (1) + addition (1) + affectation (1) = **4**.

??? note "Coût d'un algorithme sans boucle"
    - **Additionner** les coûts des instructions (chacune exécutée **une fois**).
    - **Exemple (aire) :** `aire = L * l` → quelques opérations → **`O(1)`**.

??? note "Coût d'une condition"
    - Coût du **test** + coût du **bloc exécuté** (penser au **pire cas**).

??? note "Coût d'une boucle"
    - **Coût total = coût du corps × nombre d'itérations**.

??? note "Coût de boucles imbriquées"
    - **Multiplier** les nombres d'itérations : deux boucles de `n` → **`n²`** exécutions du corps.

??? note "Écrire et simplifier `T(n)`"
    - Écrire `T(n)` exactement, puis **garder le terme dominant** et **supprimer**
      constantes et termes faibles.
    - **Exemple :** `T(n) = 4n + 2` → **`O(n)`**.

??? note "Reconnaître les ordres de complexité"
    | Ordre | Description |
    |---|---|
    | `O(1)` | constant |
    | `O(log n)` | divise le problème (ex. par 2) |
    | `O(n)` | une boucle linéaire |
    | `O(n log n)` | tri efficace |
    | `O(n²)` | deux boucles imbriquées |

??? note "Comparer l'évolution de deux complexités"
    - Comparer les **termes dominants** : pour `n` grand, `O(n²)` dépasse `O(n)`, qui
      dépasse `O(log n)`.

??? note "Expliquer l'effet du doublement de `n`"
    | Complexité | `n` → `2n` |
    |---|---|
    | `O(1)` | inchangé |
    | `O(log n)` | + une étape |
    | `O(n)` | **× 2** |
    | `O(n²)` | **× 4** |

---

## 4. Modèle de coût du cours

!!! note "Coûts unitaires"
    - **affectation** : 1 ;
    - **comparaison** : 1 ;
    - **lecture mémoire** (valeur d'une variable) : 1 ;
    - **opération arithmétique** : 1 ;
    - **affichage** : **2**.

!!! warning "Règle importante"
    On compte les opérations **à l'exécution**, **pas** à la définition d'une fonction
    (une fonction non appelée ne coûte rien).

---

## 5. Exemples étudiés

!!! info "Note"
    Les programmes exacts de tes notebooks ne sont pas joints : les versions
    ci-dessous suivent la **logique du chapitre**. Les **complexités** sont stables ;
    le détail des coûts peut varier selon la rédaction exacte.

??? example "`sommeEntiers(n)` — somme de 1 à n"
    ```python
    def sommeEntiers(n):
        s = 0
        for i in range(1, n + 1):
            s = s + i
        return s
    ```
    | Instruction | Coût unitaire | Fréquence | Coût total |
    |---|---|---|---|
    | `s = 0` | 1 | 1 | 1 |
    | `s = s + i` | 4 | `n` | `4n` |
    | `return s` | 1 | 1 | 1 |

    `T(n) = 4n + 2` → **`O(n)`**.

??? example "`conversion(n)` — décimal → binaire"
    ```python
    def conversion(n):
        b = ""
        while n > 0:
            b = str(n % 2) + b
            n = n // 2
        return b
    ```
    | Instruction | Coût | Fréquence | Coût total |
    |---|---|---|---|
    | `b = ""` | 1 | 1 | 1 |
    | corps de boucle | `c` | `≈ log₂(n)` | `c · log₂(n)` |
    | `return b` | 1 | 1 | 1 |

    Le nombre d'itérations est `≈ log₂(n)` → **`O(log n)`**.

??? example "`puissanceMoinsUn(n)` — calcule (−1)^n par une boucle"
    ```python
    def puissanceMoinsUn(n):
        r = 1
        for i in range(n):
            r = -r
        return r
    ```
    | Instruction | Coût | Fréquence | Coût total |
    |---|---|---|---|
    | `r = 1` | 1 | 1 | 1 |
    | `r = -r` | 3 | `n` | `3n` |
    | `return r` | 1 | 1 | 1 |

    `T(n) = 3n + 2` → **`O(n)`**.

??? example "`trouvemot(mot, liste)` — recherche"
    ```python
    def trouvemot(mot, liste):
        for m in liste:
            if m == mot:
                return True
        return False
    ```
    | Instruction | Coût | Fréquence (pire cas) | Coût total |
    |---|---|---|---|
    | `m == mot` | 1 | `n` | `n` |
    | `return` | 1 | 1 | 1 |

    **Pire cas** : mot **absent** → `n` comparaisons → **`O(n)`**.

---

## 6. Lecture et compréhension de code

!!! tip "Méthode"
    - **identifier les instructions répétées** (corps de boucle) ;
    - **déterminer le nombre d'itérations** (borne du `for`, condition du `while`) ;
    - **repérer le pire cas** (la situation la plus coûteuse) ;
    - **distinguer coût fixe et coût dépendant de `n`** ;
    - **détecter une boucle infinie** (la condition n'évolue pas) ;
    - **expliquer le rôle d'une variable** (compteur, accumulateur…).

---

## 7. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Trace d'exécution**
    | Ligne | Variables | Condition | Action |
    |---|---|---|---|

    **Calcul de coût**
    | Instruction | Coût unitaire | Fréquence | Coût total |
    |---|---|---|---|

    **Comparaison de complexités**
    | Taille `n` | `O(1)` | `O(log n)` | `O(n)` | `O(n²)` |
    |---|---|---|---|---|
    | 10 | 1 | ≈ 3 | 10 | 100 |
    | 100 | 1 | ≈ 7 | 100 | 10 000 |

---

## 8. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Compter la **définition** au lieu de l'**exécution** | une fonction non appelée ne coûte rien |
| Oublier les **accès mémoire** | lire une variable coûte 1 |
| **Oublier une affectation** | chaque `=` compte |
| Compter une **condition une seule fois** | elle est testée à **chaque** tour |
| Confondre **nombre de boucles** et **complexité** | le nombre d'**itérations** compte |
| Oublier que les boucles sont **imbriquées** | multiplier les itérations (`n²`) |
| Conserver **constantes / termes faibles** | garder le **terme dominant** |
| Confondre **temps réel** et **complexité** | la complexité décrit la **croissance** |
| **Oublier le pire cas** | analyser la situation la plus coûteuse |
| Affirmer qu'un algo **termine sans justification** | montrer qu'une quantité **décroît** |

---

## 9. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce que la terminaison d'un algorithme ?"
    La garantie qu'il **s'arrête** toujours.

??? question "2. (N1) Que signifie `T(n)` ?"
    Le **coût** (nombre d'opérations) en fonction de la taille `n`.

??? question "3. (N2) Différence entre correction partielle et totale ?"
    **Partielle** : juste **s'il s'arrête** ; **totale** : partielle **+ terminaison**.

??? question "4. (N1) Qu'est-ce qu'une trace d'exécution ?"
    Le suivi pas à pas des **valeurs** des variables.

??? question "5. (N2) Différence entre complexité temporelle et spatiale ?"
    L'une concerne le **temps**, l'autre la **mémoire**.

### Compréhension

??? question "6. (N1) Combien d'exécutions du corps pour deux boucles de `n` imbriquées ?"
    `n × n = n²`.

??? question "7. (N2) Pourquoi supprimer les constantes dans `O()` ?"
    On ne garde que le **terme dominant**, qui décrit la croissance pour `n` grand.

??? question "8. (N2) Pourquoi analyser le pire cas ?"
    Pour garantir une borne **maximale** du coût.

??? question "9. (N3) Si `n` double, comment évolue un algo en `O(n²)` ?"
    Le coût est **multiplié par 4**.

??? question "10. (N2) Une boucle qui divise `n` par 2 à chaque tour : quelle complexité ?"
    `O(log n)`.

### Calcul de coût

??? question "11. (N1) Coût d'`aire = L * l` (modèle du cours) ?"
    Constant → **`O(1)`**.

??? question "12. (N2) Coût d'une boucle `for i in range(n): print(i)` ?"
    `print` coûte 2 → `2n` → **`O(n)`**.

??? question "13. (N2) `T(n) = 5n + 7` : quelle complexité ?"
    `O(n)`.

??? question "14. (N3) `T(n) = 3n² + 2n + 1` : quelle complexité ?"
    `O(n²)` (terme dominant).

??? question "15. (N3) Deux boucles imbriquées affichant `(i, j)` : complexité ?"
    `O(n²)` (corps exécuté `n²` fois).

### Lecture de code

??? question "16. (N1) Dans `sommeEntiers`, combien de fois s'exécute `s = s + i` ?"
    `n` fois.

??? question "17. (N2) Dans `trouvemot`, quel est le pire cas ?"
    Le mot est **absent** : `n` comparaisons.

??? question "18. (N2) `conversion(n)` : combien d'itérations environ ?"
    `≈ log₂(n)`.

??? question "19. (N3) `puissanceMoinsUn(n)` : quelle complexité ?"
    `O(n)`.

??? question "20. (N2) Une boucle `while` dont la variable n'évolue jamais : que se passe-t-il ?"
    **Boucle infinie** (pas de terminaison).

### Méthode

??? question "21. (N1) Comment calculer le coût d'une boucle ?"
    `coût du corps × nombre d'itérations`.

??? question "22. (N2) Comment simplifier `T(n) = 4n + 10` en notation de Landau ?"
    `O(n)`.

??? question "23. (N2) Comment justifier la terminaison d'une boucle `while n > 0`?"
    Montrer que `n` **diminue** strictement et atteint `0`.

??? question "24. (N3) Comment trouver la complexité de boucles imbriquées ?"
    **Multiplier** les nombres d'itérations.

??? question "25. (N3) Comment comparer `O(n)` et `O(n²)` pour `n` grand ?"
    `O(n²)` croît **beaucoup plus vite** : il finit par dépasser `O(n)`.

### Correction d'erreurs

??? question "26. (N1) Compter le coût d'une fonction jamais appelée : erreur ?"
    On compte l'**exécution**, pas la définition.

??? question "27. (N2) Donner `O(2n)` comme complexité : erreur ?"
    On supprime la constante : c'est `O(n)`.

??? question "28. (N2) Dire « 2 boucles donc O(2) » : erreur ?"
    C'est le **nombre d'itérations** qui compte, pas le nombre de boucles.

??? question "29. (N3) Oublier que deux boucles sont imbriquées : conséquence ?"
    On annonce `O(n)` au lieu de `O(n²)`.

??? question "30. (N2) Dire « l'algorithme est rapide donc O(1) » : erreur ?"
    Le **temps réel** ≠ la **complexité** (qui décrit la croissance).

---

## 10. Exercices flash corrigés

??? question "Reconnaître entrée/sortie d'`aire(L, l)`"
    Entrées : `L`, `l` ; sortie : l'aire `L * l`.

??? question "Compléter un pseudo-code : initialiser une somme"
    `s ← 0` avant la boucle.

??? question "Suivre une boucle : `for i in range(3)` affiche quoi ?"
    `0`, `1`, `2`.

??? question "Compter une ligne : coût de `x = a + b`"
    lecture `a` (1) + lecture `b` (1) + addition (1) + affectation (1) = **4**.

??? question "Coût constant : prix de 5 livres à prix fixe `p`"
    `5 * p` → **`O(1)`**.

??? question "Coût linéaire : somme d'une liste de `n` éléments"
    `O(n)`.

??? question "Coût quadratique : afficher toutes les paires `(i, j)`"
    Deux boucles imbriquées → `O(n²)`.

??? question "Choisir la notation : `T(n) = 7n + 3`"
    `O(n)`.

??? question "Effet du doublement de `n` en `O(n)`"
    Le coût **double**.

??? question "Effet du doublement de `n` en `O(n²)`"
    Le coût est **multiplié par 4**.

---

## À retenir absolument

!!! success "Correction & terminaison"
    - **correction totale** = correction partielle **+** terminaison ;
    - **terminaison** : une quantité **décroît** strictement vers la valeur d'arrêt.

!!! note "Modèle de coût"
    affectation · comparaison · lecture mémoire · opération arithmétique = **1** ;
    **affichage = 2** ; on compte l'**exécution**, pas la définition.

!!! abstract "Calcul de `T(n)`"
    coût de chaque instruction × sa **fréquence**, puis **somme**, puis on garde le
    **terme dominant** (sans constantes ni termes faibles).

!!! quote "Échelle des complexités"
    `O(1)` < `O(log n)` < `O(n)` < `O(n log n)` < `O(n²)`.
    Doubler `n` : `O(n)` **× 2**, `O(n²)` **× 4**.
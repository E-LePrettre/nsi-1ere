---
author: Elisabeth Le Prettre (LePrettre)
title: 05a 📜 Fiche Méthode - Les booléens
---

# Booléens, portes logiques et circuits

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 5"
    Fiche **compacte** pour **refaire seul les exercices** : expressions booléennes,
    **portes logiques**, **tables de vérité**, circuits combinatoires (MUX,
    additionneurs) et lois de **De Morgan**.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les six portes (NOT, AND, OR, XOR, NAND, NOR) et leurs tables ;
- **lire** une expression booléenne et un **circuit** ;
- **expliquer** le rôle de chaque porte et des résultats intermédiaires ;
- **calculer** la valeur d'une expression et **construire** une table de vérité ;
- **construire** un circuit à partir d'une expression (et l'inverse) ;
- **vérifier** l'équivalence de deux expressions ; appliquer **De Morgan**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Booléen** | Valeur `0` / `1` (faux / vrai). |
| **Algèbre de Boole** | Calcul sur les valeurs `0` et `1`. |
| **Entrée** | Valeur fournie à un circuit / une porte. |
| **Sortie** | Valeur produite. |
| **Porte logique** | Composant réalisant une opération booléenne. |
| **Circuit combinatoire** | Assemblage de portes dont la sortie ne dépend que des entrées. |
| **Expression booléenne** | Combinaison de variables et d'opérateurs (ET, OU, NON…). |
| **Table de vérité** | Tableau donnant la sortie pour **toutes** les combinaisons d'entrées. |
| **Équivalence** | Deux expressions ayant la **même** table de vérité. |
| **Multiplexeur (MUX)** | Sélectionne une entrée parmi plusieurs selon une **commande**. |
| **Demi-additionneur** | Additionne **2 bits** (somme + retenue). |
| **Additionneur complet** | Additionne **2 bits + une retenue** entrante. |

---

## 3. Les six portes

| Porte | Notation | Python | Table |
|---|---|---|---|
| **NOT** | ¬a | `not a` | `0→1`, `1→0` |
| **AND** | a · b | `a and b` | `1` **seulement** si `a=b=1` |
| **OR** | a + b | `a or b` | `1` si **au moins** un `1` |
| **XOR** | a ⊕ b | `a != b` | `1` si les bits **diffèrent** |
| **NAND** | ¬(a · b) | `not (a and b)` | inverse de AND |
| **NOR** | ¬(a + b) | `not (a or b)` | inverse de OR |

!!! example "Tables à deux entrées"
    | a | b | AND | OR | XOR | NAND | NOR |
    |---|---|---|---|---|---|---|
    | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
    | 0 | 1 | 0 | 1 | 1 | 1 | 0 |
    | 1 | 0 | 0 | 1 | 1 | 1 | 0 |
    | 1 | 1 | 1 | 1 | 0 | 0 | 0 |

---

## 4. Fiches méthodes

??? note "Traduire une phrase en expression booléenne"
    - **Repérer :** « et » → AND, « ou » → OR, « non / pas » → NOT, « ou exclusif » → XOR.
    - **Exemple :** « la barrière s'ouvre **si** le badge est valide **et** le feu n'est
      pas rouge » → `badge and not feu_rouge`.
    - **Erreur :** confondre **et** (AND) et **ou** (OR).

??? note "Calculer une expression"
    - **Étapes :** remplacer les variables par `0`/`1`, calculer **les parenthèses
      d'abord**, puis NOT, puis AND, puis OR.
    - **Exemple :** `a=1, b=0` → `a and not b` = `1 and 1` = `1`.

??? note "Construire une table de vérité (1 à 4 variables)"
    - **Nombre de lignes = `2^n`** (`n` = nombre de variables) : 2, 4, 8 ou 16.
    - **Étapes :** lister **toutes** les combinaisons (ordre binaire croissant), calculer la sortie.
    - **Erreur :** **oublier** des combinaisons.

??? note "Ajouter les colonnes intermédiaires"
    - **Idée :** une colonne par **sous-expression** (résultat partiel) avant la sortie.
    - **Exemple :** pour `(a and b) or c`, créer une colonne `a and b`, puis la sortie.

??? note "Lire un circuit et écrire sa sortie"
    - **Étapes :** partir des **entrées**, **nommer** chaque résultat intermédiaire,
      remonter porte par porte jusqu'à la **sortie**.

??? note "Construire un circuit à partir d'une expression"
    - **Étapes :** repérer l'opérateur **principal**, dessiner sa porte, puis câbler
      récursivement les sous-expressions vers ses entrées.

??? note "Utiliser Capytale pour dessiner et tester un circuit"
    - **Étapes :** placer les **entrées**, ajouter les **portes**, **relier**, puis
      **tester** toutes les combinaisons pour vérifier la table.

??? note "Vérifier l'équivalence de deux expressions"
    - **Méthode :** construire la **table de vérité** de chacune ; elles sont
      **équivalentes** si les colonnes de sortie sont **identiques**.

??? note "Appliquer les lois de De Morgan"
    - `not (a and b) = (not a) or (not b)` ;
    - `not (a or b) = (not a) and (not b)`.
    - **Usage :** « faire entrer » une négation dans une parenthèse.

??? note "Analyser MUX, demi-additionneur, additionneur complet"
    - **MUX (2→1) :** `sortie = (not s and a) or (s and b)` (la commande `s` choisit).
    - **Demi-additionneur :** `S = a ⊕ b`, retenue `C = a · b`.
    - **Additionneur complet :** `S = a ⊕ b ⊕ cin`, `cout = (a·b) or (cin·(a⊕b))`.

---

## 5. Lecture de circuit

!!! tip "Méthode"
    On part des **entrées**, on **nomme chaque résultat intermédiaire** (sortie de
    chaque porte), et on **termine par la porte reliée à la sortie**.

!!! example "Modèle de tableau"
    | Entrées (a, b, c) | Sous-expression 1 | Sous-expression 2 | Sortie |
    |---|---|---|---|
    | 1, 0, 1 | `a and b` = 0 | `… or c` | 1 |

---

## 6. Propriétés

| Loi | Exemple |
|---|---|
| **Commutativité** | `a and b = b and a` ; `a or b = b or a` |
| **Associativité** | `(a and b) and c = a and (b and c)` |
| **Distributivité** | `a and (b or c) = (a and b) or (a and c)` |
| **De Morgan** | `not (a and b) = not a or not b` ; `not (a or b) = not a and not b` |

---

## 7. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Confondre **ET** et **OU** | « et » = AND (les deux) ; « ou » = OR (au moins un) |
| Confondre **OU** et **XOR** | OR vrai si `1,1` ; XOR **faux** si `1,1` |
| **Oublier une négation** | relire chaque « non / pas » |
| **Oublier des parenthèses** | NOT, puis AND, puis OR : parenthéser si besoin |
| Pas de **colonnes intermédiaires** | créer une colonne par sous-expression |
| **Oublier des combinaisons** | `2^n` lignes exactement |
| **Inverser 0 et 1** | relire la table de la porte |
| **Lire un circuit depuis la sortie** | partir des **entrées**, nommer les sous-circuits |
| Conclure une **équivalence sans vérifier** | comparer les **tables** complètes |

---

## 8. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'une table de vérité ?"
    Un tableau donnant la sortie pour **toutes** les combinaisons d'entrées.

??? question "2. (N1) Que fait une porte NOT ?"
    Elle **inverse** : `0 → 1`, `1 → 0`.

??? question "3. (N2) Quand deux expressions sont-elles équivalentes ?"
    Quand elles ont **exactement la même** table de vérité.

??? question "4. (N1) À quoi sert un multiplexeur ?"
    À **choisir** une entrée parmi plusieurs selon une **commande**.

??? question "5. (N2) Différence entre demi-additionneur et additionneur complet ?"
    Le demi additionne **2 bits** ; le complet additionne **2 bits + une retenue** entrante.

### Compréhension

??? question "6. (N1) Combien de lignes pour une table à 3 variables ?"
    `2³ = 8`.

??? question "7. (N2) Pourquoi ajouter des colonnes intermédiaires ?"
    Pour **décomposer** le calcul et limiter les erreurs.

??? question "8. (N2) En quoi OR et XOR diffèrent-ils ?"
    Pour `1,1` : OR vaut `1`, XOR vaut `0`.

??? question "9. (N3) Que devient `not (a and b)` par De Morgan ?"
    `not a or not b`.

??? question "10. (N2) Pourquoi lire un circuit depuis les entrées ?"
    Parce que chaque porte a besoin des **résultats précédents** pour produire le sien.

### Tables de vérité

??? question "11. (N1) Compléter AND pour `a=1, b=0`."
    `0`.

??? question "12. (N1) Compléter XOR pour `a=1, b=1`."
    `0`.

??? question "13. (N2) Que vaut `(a or b) and not c` pour `a=0, b=1, c=0` ?"
    `(0 or 1) and not 0` = `1 and 1` = `1`.

??? question "14. (N3) Donner la sortie `S` d'un demi-additionneur pour `a=1, b=1`."
    `S = a ⊕ b = 0`, retenue `C = 1`.

??? question "15. (N3) Additionneur complet, `a=1, b=1, cin=1` : `S` et `cout` ?"
    `S = 1 ⊕ 1 ⊕ 1 = 1` ; `cout = 1`.

### Lecture de circuits

??? question "16. (N1) Un circuit applique NOT puis AND. Sortie pour `a=1, b=0` (`not a and b`) ?"
    `not 1 and 0` = `0 and 0` = `0`.

??? question "17. (N2) MUX `(not s and a) or (s and b)`, `s=0, a=1, b=0` : sortie ?"
    `s=0` → on prend `a` → `1`.

??? question "18. (N2) Même MUX avec `s=1, a=1, b=0` : sortie ?"
    `s=1` → on prend `b` → `0`.

??? question "19. (N3) Une porte donne `1` uniquement si les entrées diffèrent : laquelle ?"
    **XOR**.

??? question "20. (N2) Une porte vaut `0` seulement si `a=b=1` : laquelle ?"
    **NAND**.

### Méthode

??? question "21. (N1) Traduire « a et non b » en Python."
    `a and not b`.

??? question "22. (N2) Comment vérifier que deux circuits sont équivalents ?"
    Comparer leurs **tables de vérité** complètes.

??? question "23. (N2) Écrire `SSi` (a équivaut à b) en booléen."
    `a == b`, soit `not (a ⊕ b)` (ou `(a and b) or (not a and not b)`).

??? question "24. (N3) Traduire `not (a or b)` sans parenthèse de négation (De Morgan)."
    `not a and not b`.

??? question "25. (N3) Construire la table de `a xor b` : combien de `1` en sortie ?"
    Deux (`01` et `10`).

### Correction d'erreurs

??? question "26. (N1) « a ou b » traduit par `a and b` : erreur ?"
    « ou » = `or`, pas `and`.

??? question "27. (N2) `a or b` donné `0` pour `a=1, b=0` : erreur ?"
    Faux : `1 or 0 = 1`.

??? question "28. (N2) Table à 2 variables avec 3 lignes : erreur ?"
    Il en faut `2² = 4`.

??? question "29. (N3) `not (a and b)` simplifié en `not a and not b` : erreur ?"
    Faux : De Morgan donne `not a or not b`.

??? question "30. (N2) Conclure « équivalents » après une seule ligne identique : erreur ?"
    Il faut comparer **toutes** les lignes des deux tables.

---

## 9. Exercices flash corrigés

??? question "Compléter une table : NOR pour `a=0, b=0`"
    `1`.

??? question "Calculer une sortie : `a and (b or c)` pour `1, 0, 1`"
    `1 and (0 or 1)` = `1`.

??? question "Retrouver une porte : sortie `1` sauf si `a=b=1`"
    **NAND**.

??? question "Traduire en Python : `a ⊕ b`"
    `a != b` (ou `a ^ b`).

??? question "Appliquer De Morgan : `not (a and b)`"
    `not a or not b`.

??? question "Comparer deux circuits : `a or b` et `not (not a and not b)`"
    **Équivalents** (De Morgan).

??? question "Déterminer la commande d'un MUX : sortie = `a` quand…"
    …la commande `s = 0`.

??? question "Interpréter un additionneur : `a=1, b=0, cin=1`"
    `S = 0`, `cout = 1` (1 + 0 + 1 = 10).

---

## À retenir absolument

!!! success "Les six portes"
    | Porte | `1` en sortie quand… | Python |
    |---|---|---|
    | NOT | l'entrée est `0` | `not a` |
    | AND | **les deux** sont `1` | `a and b` |
    | OR | **au moins un** est `1` | `a or b` |
    | XOR | les bits **diffèrent** | `a != b` |
    | NAND | **pas** (`a=b=1`) | `not (a and b)` |
    | NOR | **aucun** n'est `1` | `not (a or b)` |

!!! note "Méthodes clés"
    - **table de vérité** : `2^n` lignes, toutes les combinaisons, colonnes intermédiaires ;
    - **circuit → expression** : partir des **entrées**, nommer chaque sortie de porte ;
    - **expression → circuit** : repérer l'opérateur **principal**, câbler les sous-expressions ;
    - **équivalence** : **mêmes** tables de vérité.

!!! quote "Lois de De Morgan"
    - `not (a and b) = not a or not b` ;
    - `not (a or b) = not a and not b`.

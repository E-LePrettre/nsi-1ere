---
author: Elisabeth Le Prettre (LePrettre)
title: 13 📜 Fiche Méthode - Architecture de l’ordinateur
---


# Architecture de l'ordinateur

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 18"
    Fiche **compacte** pour **refaire seul les activités** : histoire de l'informatique,
    **mémoires**, architecture de **Von Neumann**, **CPU** et **assembleur**.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** la hiérarchie des mémoires et l'architecture de Von Neumann ;
- **expliquer** le rôle du CPU, des bus, de l'horloge ;
- **comparer** les mémoires (vitesse, volatilité, capacité) ;
- **calculer** une capacité mémoire (`2^n`) ;
- **traduire** entre Python, langage naturel et **assembleur** ; **simuler** un programme.

---

## 2. Repères historiques

!!! note "Grandes étapes"
    Machines **mécaniques / électromécaniques** → **tubes à vide** (électronique) →
    **programme enregistré** → **transistor** → **circuit intégré** →
    **microprocesseur** → **micro-ordinateur** → évolution des **langages** et **OS**.

    *L'idée clé : miniaturisation croissante et passage au **programme enregistré**.*

---

## 3. Définitions essentielles

| Terme | Définition |
|---|---|
| **Programme enregistré** | Programme **stocké en mémoire** comme les données. |
| **Mémoire volatile / non volatile** | Perdue / **conservée** hors tension. |
| **Accès direct** | Accès à n'importe quelle case directement. |
| **Registre** | Mémoire **interne au CPU**, ultra-rapide. |
| **Cache** | Mémoire rapide pour données **réutilisées**. |
| **RAM / ROM** | Vive (volatile) / morte (non volatile). |
| **Stockage secondaire** | Disque (HDD/SSD), durable. |
| **Processeur / CPU** | Unité qui **exécute** les instructions. |
| **UAL / ALU** | Unité **arithmétique et logique** (calculs). |
| **Unité de contrôle** | Pilote l'exécution des instructions. |
| **Bus** | Liaison transportant adresses, données ou commandes. |
| **Adresse mémoire** | Numéro d'une case. |
| **Horloge / fréquence** | Rythme du CPU (cycles/s). |
| **Multicœur** | Plusieurs cœurs de calcul. |
| **Assembleur** | Langage bas niveau (mnémoniques). |
| **Mnémonique** | Nom d'une instruction (`MOV`…). |
| **Opérande** | Donnée d'une instruction. |
| **Valeur immédiate** | Valeur fixe (notée `#`). |
| **Instruction** | Une opération du programme. |
| **PC** | Compteur de programme (prochaine instruction). |

---

## 4. Les mémoires

| Mémoire | Emplacement | Rôle | Volatile | Rapidité | Capacité | Coût |
|---|---|---|---|---|---|---|
| **Registre** | dans le CPU | donnée immédiate | oui | ★★★★★ | minuscule | très élevé |
| **Cache L1/L2/L3** | proche / dans CPU | données réutilisées | oui | ★★★★ | petite | élevé |
| **RAM** | carte mère | programmes en cours | oui | ★★★ | moyenne | moyen |
| **ROM** | carte mère | programme **permanent** | **non** | ★★ | petite | faible |
| **HDD / SSD** | stockage secondaire | conservation durable | **non** | ★ | grande | faible/Go |

---

## 5. Choisir ou reconnaître une mémoire

| Besoin | Mémoire |
|---|---|
| donnée utilisée **immédiatement** par le CPU | **registre** |
| donnée **souvent réutilisée** | **cache** |
| programme **en cours** | **RAM** |
| programme essentiel **permanent** | **ROM** |
| conservation **durable** | **stockage secondaire** |

---

## 6. Lire l'architecture de Von Neumann

!!! tip "Méthode"
    1. repérer **CPU**, **mémoire** et **entrées-sorties** ;
    2. identifier **UAL**, **unité de contrôle** et **registres** ;
    3. suivre les **bus** ;
    4. distinguer **adresse**, **donnée** et **commande** ;
    5. retenir que **programmes et données partagent la mémoire**.

---

## 7. Les bus

| Bus | Transporte |
|---|---|
| **Adresses** | l'**adresse** de la case visée |
| **Données** | une **instruction** ou une **donnée** |
| **Contrôle** | la **commande** (lecture / écriture) |

---

## 8. Calculer une capacité mémoire

!!! tip "Méthode"
    1. relever la largeur du bus d'adresses **`n`** ;
    2. calculer **`2^n`** adresses ;
    3. relever la **taille d'une case** ;
    4. calculer la **capacité totale** ;
    5. **convertir** (octets, Kio…).

!!! example "Bus de 16 bits, case d'un octet"
    `2^16 = 65 536` adresses → `65 536` octets = **64 Kio** (1 Kio = 1024 octets).

!!! warning
    `2^16 = 65 536`, **pas** `16² = 256`.

---

## 9. Lire les caractéristiques du CPU

!!! note "À repérer"
    **fréquence**, **taille des registres**, **nombre de cœurs**, **caches**, rôle de
    l'**horloge** (cadence les cycles).

!!! warning
    `2 GHz` = **2 milliards de cycles/seconde** — pas forcément 2 milliards d'**instructions**
    (une instruction peut prendre plusieurs cycles).

---

## 10. Les instructions (assembleur)

| Instruction | Effet | Exemple |
|---|---|---|
| `MOV Rd, #valeur` | place une **valeur** dans `Rd` | `MOV R0, #42` |
| `MOV Rd, Rs` | copie `Rs` dans `Rd` | `MOV R1, R0` |
| `LDR Rd, adresse` | **charge** la mémoire dans `Rd` | `LDR R0, 150` |
| `STR Rs, adresse` | **stocke** `Rs` en mémoire | `STR R0, 150` |
| `ADD Rd, Rs, #v` / `Rd, Rs1, Rs2` | addition | `ADD R0, R1, #42` |
| `SUB ...` | soustraction | `SUB R0, R1, #1` |
| `CMP Rn, valeur/Rm` | **compare** (drapeaux) | `CMP R0, #75` |
| `B étiquette` | saut **inconditionnel** | `B fin` |
| `BEQ` / `BNE` / `BGT` | saut si **=** / **≠** / **>** | `BEQ egal` |
| `HALT` | **arrête** le programme | `HALT` |

---

## 11. Traduire l'assembleur en langage naturel

!!! tip "Méthode"
    1. identifier le **mnémonique** ;
    2. repérer le **registre destination** ;
    3. repérer les **sources** ;
    4. distinguer **valeur immédiate** (`#`) et **adresse** ;
    5. décrire l'**effet final**.

!!! example
    `ADD R0, R1, #42` → « place dans `R0` la valeur de `R1` **augmentée de 42** ».

---

## 12. Traduire une phrase en assembleur

!!! tip "Méthode"
    - **charger / placer** les valeurs nécessaires ;
    - **effectuer** l'opération ;
    - choisir le **registre résultat** ;
    - **stocker** en mémoire si demandé ;
    - terminer par **`HALT`** (programme complet).

---

## 13. Traduire une affectation Python

`x = 4` devient :

```text
MOV R0, #4        ; placer 4 dans un registre
STR R0, 100       ; stocker à l'adresse choisie pour x
```

- une **adresse mémoire** représente l'**emplacement** choisi pour la variable.

---

## 14. Traduire un `if / else`

!!! tip "Étapes"
    1. **charger** la variable ;
    2. utiliser **`CMP`** ;
    3. choisir le **saut conditionnel** ;
    4. écrire le bloc **`if`** ;
    5. ajouter un **saut vers la fin** ;
    6. placer l'**étiquette du `else`** ;
    7. écrire le bloc **`else`** ;
    8. placer l'**étiquette de fin**.

```text
        LDR R0, 30      ; charger x
        CMP R0, #75     ; comparer
        BEQ egal        ; si égal -> bloc if
        MOV R1, #0      ; bloc else
        B fin
egal:   MOV R1, #1      ; bloc if
fin:    STR R1, 23      ; stocker le résultat
        HALT
```

---

## 15. Suivre un programme assembleur

!!! example "Modèle de tableau"
    | Adresse | Instruction | PC avant | Registres avant | Opération | Registres après | Mémoire modifiée | PC après |
    |---|---|---|---|---|---|---|---|

---

## 16. Utiliser le simulateur CPU

!!! tip "Procédure"
    1. choisir la **représentation** de la mémoire ;
    2. **saisir** le programme ;
    3. cliquer sur **Submit** ;
    4. vérifier les **adresses** des instructions ;
    5. lancer **Run** ;
    6. observer **registres**, **PC**, unité de contrôle, **mémoire** ;
    7. **ralentir** si nécessaire ;
    8. vérifier la **cellule attendue** ;
    9. **Reset** avant un nouveau test.

---

## 17. Programmes expliqués

??? example "Stocker 42 à l'adresse 150 (avec R0)"
    ```text
    MOV R0, #42
    STR R0, 150
    HALT
    ```
    **Initial :** `R0 = 0`. **Effet :** 42 va dans `R0`, puis en mémoire[150].
    **Final :** `R0 = 42`, mémoire[150] = 42.

??? example "Stocker 54 à l'adresse 50 (avec R1)"
    ```text
    MOV R1, #54
    STR R1, 50
    HALT
    ```
    **Final :** `R1 = 54`, mémoire[50] = 54.

??? example "if / else (adresses 30, 75, 23)"
    ```text
            LDR R0, 30      ; x
            CMP R0, #75
            BEQ egal
            MOV R1, #0      ; else
            B fin
    egal:   MOV R1, #1      ; if
    fin:    STR R1, 23
            HALT
    ```
    **Effet :** si `x` (adresse 30) vaut 75 → `R1 = 1`, sinon `R1 = 0` ; le résultat
    est stocké à l'adresse 23.

---

## 18. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Mémoire**
    | Technologie | Vitesse | Capacité | Volatilité |
    |---|---|---|---|

    **Von Neumann**
    | Composant | Rôle | Reçoit | Envoie |
    |---|---|---|---|

    **Assembleur**
    | Instruction | Registres lus | Registre écrit | Mémoire lue/écrite |
    |---|---|---|---|

    **Simulation**
    | PC | Instruction | Registres | Mémoire |
    |---|---|---|---|

---

## 19. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Confondre **RAM** et **stockage** | RAM volatile / disque durable |
| Croire que la RAM **conserve** hors tension | elle est **volatile** |
| Confondre **cache** et **registre** | registre **dans** le CPU |
| Confondre **UAL** et **unité de contrôle** | calculs / pilotage |
| Mélanger bus **adresses** et **données** | adresse de case / contenu |
| Calculer **`16²`** au lieu de **`2^16`** | c'est `2^n` |
| Confondre **adresse** et **valeur** | la case ≠ son contenu |
| Oublier **`#`** (valeur immédiate) | `#42` = valeur, `42` = adresse |
| **Inverser** source et destination | `MOV Rd, Rs` : `Rd` reçoit |
| `LDR` au lieu de `STR` | charger / stocker |
| **Comparer** sans avoir **chargé** | `LDR` avant `CMP` |
| Oublier le **saut de fin** d'un if/else | `B fin` avant le `else` |
| Oublier **`HALT`** | le programme ne s'arrête pas |
| Croire que **PC** contient une donnée | il pointe l'**instruction** suivante |
| Pas de **Reset** avant une simulation | états résiduels faussent le test |

---

## 20. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'un registre ?"
    Une mémoire **interne au CPU**, ultra-rapide.

??? question "2. (N1) Que contient le PC ?"
    L'adresse de la **prochaine instruction**.

??? question "3. (N2) Différence RAM / ROM ?"
    RAM **volatile** ; ROM **non volatile**.

??? question "4. (N2) Que fait l'UAL ?"
    Les **calculs** arithmétiques et logiques.

??? question "5. (N1) Qu'est-ce qu'une valeur immédiate ?"
    Une valeur **fixe**, notée `#`.

### Histoire

??? question "6. (N1) Qu'a apporté le programme enregistré ?"
    Stocker le **programme en mémoire** comme les données.

??? question "7. (N2) Qu'a permis le transistor ?"
    La **miniaturisation** (remplace les tubes).

??? question "8. (N2) Qu'est-ce qu'un circuit intégré ?"
    De nombreux composants **sur une même puce**.

??? question "9. (N3) Qu'est-ce que le microprocesseur a changé ?"
    Le CPU **sur une seule puce** → micro-ordinateurs.

??? question "10. (N2) Quelle tendance traverse l'histoire de l'informatique ?"
    La **miniaturisation** et l'augmentation des performances.

### Mémoires

??? question "11. (N1) Quelle mémoire est la plus rapide ?"
    Le **registre**.

??? question "12. (N2) Quelle mémoire conserve un programme permanent ?"
    La **ROM**.

??? question "13. (N2) Quelle mémoire pour un programme en cours ?"
    La **RAM**.

??? question "14. (N3) Pourquoi un cache ?"
    Accélérer l'accès aux données **réutilisées**.

??? question "15. (N2) Le SSD est-il volatile ?"
    **Non**.

### Von Neumann

??? question "16. (N1) Citer les trois grands ensembles."
    CPU, mémoire, entrées-sorties.

??? question "17. (N2) Que partagent programmes et données ?"
    La **même mémoire**.

??? question "18. (N2) Rôle de l'unité de contrôle ?"
    **Piloter** l'exécution des instructions.

??? question "19. (N3) Quel bus transporte l'adresse d'une case ?"
    Le bus d'**adresses**.

??? question "20. (N2) Quel bus indique lecture ou écriture ?"
    Le bus de **contrôle**.

### Calcul mémoire

??? question "21. (N1) Combien d'adresses avec un bus de 8 bits ?"
    `2^8 = 256`.

??? question "22. (N2) Et avec un bus de 16 bits ?"
    `2^16 = 65 536`.

??? question "23. (N2) Capacité avec 16 bits et case d'1 octet ?"
    `65 536` octets = **64 Kio**.

??? question "24. (N3) Bus de 10 bits : combien d'adresses ?"
    `2^10 = 1024`.

??? question "25. (N3) `2 GHz`, est-ce 2 milliards d'instructions/s ?"
    Non : 2 milliards de **cycles**/s.

### Lecture d'assembleur

??? question "26. (N1) Que fait `MOV R0, #5` ?"
    Place **5** dans `R0`.

??? question "27. (N2) Que fait `LDR R0, 150` ?"
    Charge mémoire[150] dans `R0`.

??? question "28. (N2) Que fait `STR R0, 150` ?"
    Stocke `R0` en mémoire[150].

??? question "29. (N3) Que fait `ADD R0, R1, #3` ?"
    `R0 = R1 + 3`.

??? question "30. (N2) Que fait `BEQ etiq` ?"
    Saute à `etiq` **si égalité**.

### Traduction

??? question "31. (N1) Traduire `x = 7`."
    `MOV R0, #7` puis `STR R0, adresse_x`.

??? question "32. (N2) Traduire « ajouter 1 à R0 »."
    `ADD R0, R0, #1`.

??? question "33. (N2) Quelle instruction avant un saut conditionnel ?"
    `CMP`.

??? question "34. (N3) Traduire « si x == 0 alors … »."
    `LDR R0, adr` ; `CMP R0, #0` ; `BEQ …`.

??? question "35. (N3) Comment terminer un programme complet ?"
    Par `HALT`.

### Simulation

??? question "36. (N1) Quel bouton lance le programme ?"
    **Run**.

??? question "37. (N2) Que faut-il faire avant un nouveau test ?"
    **Reset**.

??? question "38. (N2) Qu'observe-t-on pendant l'exécution ?"
    Registres, **PC**, mémoire, unité de contrôle.

??? question "39. (N3) Comment voir chaque étape ?"
    **Ralentir** l'exécution.

??? question "40. (N3) Comment vérifier le résultat ?"
    Lire la **cellule mémoire attendue**.

### Correction d'erreurs

??? question "41. (N1) Oublier `#` dans `MOV R0, 42` : conséquence ?"
    `42` est lu comme une **adresse**, pas une valeur.

??? question "42. (N2) `MOV R1, R0` pour mettre `R1` dans `R0` : erreur ?"
    La destination est `R1` : écrire `MOV R0, R1`.

??? question "43. (N2) `CMP` sans `LDR` préalable : erreur ?"
    On compare un registre **non chargé**.

??? question "44. (N3) Oublier `B fin` dans un if/else : conséquence ?"
    Le bloc `else` s'exécute **aussi**.

??? question "45. (N2) Oublier `HALT` : conséquence ?"
    Le CPU continue sur des cases **non prévues**.

---

## 21. Exercices flash corrigés

??? question "Classer par vitesse : RAM, registre, SSD"
    registre > RAM > SSD.

??? question "Reconnaître le composant qui calcule"
    L'**UAL**.

??? question "Choisir le bus transportant une adresse"
    Le bus d'**adresses**.

??? question "Nombre d'adresses pour un bus de 12 bits"
    `2^12 = 4096`.

??? question "Décrire `ADD R0, R1, #42`"
    `R0 = R1 + 42`.

??? question "Écrire une instruction stockant `R0` à l'adresse 200"
    `STR R0, 200`.

??? question "Compléter une condition : sauter si différent"
    `BNE etiquette`.

??? question "Déterminer R0 après `MOV R0, #5` puis `ADD R0, R0, #3`"
    `R0 = 8`.

??? question "Trouver la cellule modifiée par `STR R1, 50`"
    mémoire[50].

??? question "Suivre PC : après une instruction simple, PC ?"
    Pointe l'**instruction suivante**.

??? question "Corriger `MOV R0, 9` (valeur immédiate)"
    `MOV R0, #9`.

??? question "Traduire `y = 3` en assembleur"
    `MOV R0, #3` ; `STR R0, adresse_y`.

---

## À retenir absolument

!!! success "Mémoires & Von Neumann"
    - **hiérarchie** : registre > cache > RAM > ROM > stockage (vitesse ↓, capacité ↑) ;
    - **volatile** : registre, cache, RAM ; **non volatile** : ROM, HDD/SSD ;
    - **Von Neumann** : CPU (UAL + contrôle + registres) + mémoire + E/S, reliés par les **bus** ;
      programmes et données **partagent la mémoire**.

!!! note "CPU, bus, capacité"
    - **bus** : adresses / données / contrôle ;
    - **capacité** = `2^n` cases × taille d'une case (ex. 16 bits → 64 Kio) ;
    - **horloge** : `2 GHz` = 2 milliards de **cycles**/s.

!!! quote "Assembleur"
    - `MOV` (valeur/registre), `LDR`/`STR` (mémoire), `ADD`/`SUB`, `CMP`,
      `B`/`BEQ`/`BNE`/`BGT`, `HALT` ;
    - **valeur immédiate** notée `#` ; **PC** = prochaine instruction ;
    - **if/else** : `CMP` + saut conditionnel + `B fin` + étiquettes ;
    - **simulation** : saisir → Submit → Run → observer → **Reset**.
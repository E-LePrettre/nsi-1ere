---
author: Elisabeth Le Prettre (LePrettre)
title: 02 📜 Fiche Méthode - Les bases de Python
---

# Les bases de Python

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 2"
Fiche compacte pour refaire seul les exercices : fonctions, conditions,
booléens, chaînes, boucles et portée des variables. Les points marqués
« Approfondissement » ne sont pas indispensables.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **écrire** une fonction avec des **paramètres** et un **`return`** ;
- utiliser **conditions** (`if` / `elif` / `else`) et **booléens** (`and`, `or`, `not`) ;
- manipuler les **chaînes** (parcours par valeurs et par indices, tranches) ;
- écrire des **boucles** `for` (avec `range`) et `while` ;
- utiliser un **compteur** / un **accumulateur** ;
- distinguer **variable locale** et **variable globale** ;
- **lire** et **expliquer** un code, **prévoir** ses affichages et sa valeur retournée ;
- *(approfondissement)* paramètre **par défaut**, argument **nommé**, fonction **`lambda`**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Fonction** | Bloc de code nommé, réutilisable (`def`). |
| **Paramètre** | Variable d'entrée **dans la définition** de la fonction. |
| **Argument** | Valeur **fournie** lors de l'appel. |
| **Valeur retournée** | Résultat renvoyé par `return`. |
| **Booléen** | Valeur `True` ou `False`. |
| **Condition** | Test renvoyant un booléen (`if …`). |
| **Indice** | Position d'un caractère / élément (à partir de **0**). |
| **Tranche** | Sous-partie `chaine[a:b]` (borne `b` **exclue**). |
| **Itération** | Un tour de boucle. |
| **Compteur** | Variable qui **compte** (incrémentée). |
| **Accumulateur** | Variable qui **cumule** (somme, concaténation…). |
| **Boucle bornée** | `for` : nombre de tours **connu**. |
| **Boucle non bornée** | `while` : on répète **tant qu'une condition** est vraie. |
| **Variable locale** | Définie **dans** une fonction, invisible à l'extérieur. |
| **Variable globale** | Définie **hors** des fonctions. |

---

## 3. Fiches méthodes pas à pas

??? note "Écrire une fonction"
    - **Quand ?** Une tâche à réutiliser, qui produit un résultat.
    - **Repérer :** les **entrées** et le **résultat** attendu.
    - **Étapes :** entrées → paramètres → `def` → indenter → calculer → `return` → appeler/tester.
    - **Modèle :**
      ```python
      def aire(longueur, largeur):
          return longueur * largeur
      ```
    - **Exemple (IMC) :**
      ```python
      def imc(poids, taille):
          return poids / taille**2
      ```
    - **Erreurs :** oublier `return`, oublier les `:` ou l'indentation.
    - **Vérif :** appeler avec une valeur simple et contrôler le résultat.

??? note "Distinguer `return` et `print`"
    - **`return`** : renvoie un résultat **réutilisable** (`x = aire(2, 3)`).
    - **`print`** : **affiche** seulement (ne renvoie rien).
    - Une fonction **sans `return`** renvoie **`None`**.
    - **Vérif :** `resultat = f(...)` puis `print(resultat)` → si `None`, il manque un `return`.

??? note "Écrire `if`, `if/else`, `if/elif/else`"
    - **Repérer :** les **cas** à distinguer et le **cas restant**.
    - **Modèle :**
      ```python
      if note >= 10:
          etat = "Admis"
      else:
          etat = "Recalé"
      ```
    - **Exemple (mention) :**
      ```python
      if note >= 16: return "Très bien"
      elif note >= 14: return "Bien"
      elif note >= 10: return "Admis"
      else: return "Recalé"
      ```
    - **Erreurs :** mauvais **ordre** des tests (du plus restrictif au plus large).

??? note "Construire une expression booléenne"
    - **Comparateurs :** `==`, `!=`, `<`, `>`, `<=`, `>=`.
    - **Opérateurs :** `and`, `or`, `not`.
    - **Intervalle :** `0 <= x <= 20` (ou `x >= 0 and x <= 20`).
    - **Erreurs :** confondre `=` (affectation) et `==` (égalité) ; confondre `and`/`or`.

??? note "Vérifier la parité ou un multiple avec `%`"
    - **`n % 2 == 0`** → `n` est **pair** ; **`n % k == 0`** → `n` est **multiple** de `k`.
    - **Exemple (bissextile) :**
      ```python
      bissextile = (a % 4 == 0 and a % 100 != 0) or (a % 400 == 0)
      ```

??? note "Parcourir une chaîne par valeurs"
    - **Modèle :**
      ```python
      for car in chaine:
          print(car)
      ```
    - **Quand ?** On a besoin du **caractère**, pas de sa position.

??? note "Parcourir une chaîne par indices"
    - **Modèle :**
      ```python
      for i in range(len(chaine)):
          print(i, chaine[i])
      ```
    - **Quand ?** On a besoin de la **position** (indice).

??? note "Accéder à un caractère"
    - **Indice positif :** `chaine[0]` (premier) ; **négatif :** `chaine[-1]` (dernier).
    - **Tranche :** `chaine[1:4]` (indices 1, 2, 3) ; **pas :** `chaine[::2]` (un sur deux).
    - **Erreurs :** dépassement d'indice (`chaine[len(chaine)]` n'existe pas).

??? note "Parcourir une liste par valeurs"
    - **Modèle :**
      ```python
      for element in liste:
          print(element)
      ```

??? note "Écrire une boucle `for` avec `range`"
    - **`range(debut, fin)`** : de `debut` à `fin − 1` (**borne finale exclue**).
    - **Exemple (table) :**
      ```python
      for i in range(1, 11):
          print(n, "x", i, "=", n * i)
      ```
    - **Erreurs :** mauvaise **borne** (`range(10)` = 0→9, pas 1→10).

??? note "Écrire une boucle `while`"
    - **Étapes :** **initialiser** → **condition** → **corps** → **mise à jour** → arrêt.
    - **Modèle :**
      ```python
      i = 0
      while i < 5:
          print(i)
          i = i + 1        # mise à jour INDISPENSABLE
      ```
    - **Erreurs :** oublier la mise à jour → **boucle infinie**.

??? note "Choisir entre `for` et `while`"
    - **`for`** : nombre de tours **connu** (parcours, répétitions comptées).
    - **`while`** : on s'arrête sur une **condition** (devinette, saisie…).

??? note "Utiliser un compteur ou un accumulateur"
    - **Étapes :** **initialiser** (`c = 0`) → **mettre à jour** (`c += 1`) → **résultat**.
    - **Exemple (comptage de lettres) :**
      ```python
      c = 0
      for car in chaine:
          if car == lettre:
              c += 1
      ```

??? note "Utiliser `while True` et `break`"
    - **Modèle :**
      ```python
      while True:
          rep = input("Mot de passe : ")
          if rep == "secret":
              break       # on sort de la boucle
      ```
    - **Erreurs :** `break` mal placé → on sort trop tôt / jamais.

??? note "Distinguer variable locale et globale"
    - **Locale** : créée **dans** une fonction, disparaît à la fin de l'appel.
    - **Globale** : créée **hors** des fonctions.
    - **Prudence :** ne pas modifier une globale par mégarde depuis une fonction.

??? note "Lire un prototype avec annotations de type"
    - **Modèle :**
      ```python
      def imc(poids: float, taille: float) -> float:
          ...
      ```
    - Les annotations indiquent les **types** attendus (entrée) et **retourné** (`->`).

??? note "Approfondissement — défaut, nommé, lambda"
    - **Paramètre par défaut :** `def f(x, pas=1): ...` → `pas` vaut 1 si non fourni.
    - **Argument nommé :** `f(10, pas=2)`.
    - **`lambda` :** `carre = lambda x: x*x` (petite fonction anonyme).

---

## 4. Lecture et compréhension de code

!!! tip "Méthode"
    - **prévoir les affichages** : repérer chaque `print` et son ordre ;
    - **déterminer la valeur retournée** : suivre le `return` atteint ;
    - **suivre les variables** ligne par ligne (tableau de trace) ;
    - **repérer le bloc exécuté** dans une condition (premier test vrai) ;
    - **compléter un code à trous** : identifier ce qui manque (init, mise à jour, `return`) ;
    - **corriger l'indentation** (les blocs sont délimités par les espaces) ;
    - **repérer une boucle infinie** (la condition n'évolue pas) ;
    - **corriger une borne de `range`** (borne finale **exclue**) ;
    - **vérifier les cas limites** (chaîne vide, `n = 0`, premier / dernier indice).

---

## 5. Tableaux de trace

!!! example "Modèles de tableaux"
    **`if/elif/else`**
    | Valeur testée | Test vrai | Bloc exécuté | Résultat |
    |---|---|---|---|
    | `note = 13` | `note >= 12` | « Assez bien » | … |

    **Boucle `for`**
    | Itération | `i` | Élément | Affichage / résultat partiel |
    |---|---|---|---|
    | 1 | 0 | … | … |

    **Boucle `while`**
    | Tour | Condition | Avant | Après | Sortie ? |
    |---|---|---|---|---|
    | 1 | `i < 5` (vrai) | `i = 0` | `i = 1` | non |

    **Compteur de lettres**
    | Caractère | `car == lettre` ? | `c` après |
    |---|---|---|
    | `a` | oui | 1 |

    **Construction d'une chaîne**
    | Itération | Caractère ajouté | Chaîne en cours |
    |---|---|---|
    | 1 | `b` | `"b"` |

    **Variables locale / globale**
    | Ligne | Variable | Portée | Valeur |
    |---|---|---|---|
    | … | `x` | locale | … |

---

## 6. Erreurs fréquentes

| Erreur | Pourquoi c'est faux | Correction / éviter |
|---|---|---|
| **Mauvaise indentation** | le bloc n'est pas reconnu | aligner avec 4 espaces |
| **Oubli des `:`** | syntaxe invalide | `:` après `def`, `if`, `for`, `while` |
| **`=` au lieu de `==`** | `=` affecte, ne teste pas | utiliser `==` dans une condition |
| **Mauvais ordre des conditions** | un test large « avale » les autres | du plus restrictif au plus large |
| **Intervalle incorrect** | `0 < x and 20` n'a pas de sens | `0 <= x <= 20` |
| **Confusion `and`/`or`** | logique inversée | `and` = les deux ; `or` = au moins un |
| **Oubli de `return`** | la fonction renvoie `None` | ajouter `return resultat` |
| **`return` vs `print`** | `print` n'est pas réutilisable | renvoyer avec `return` |
| **Appel sans `()`** | la fonction n'est pas exécutée | `f()` et non `f` |
| **Mauvaise borne de `range`** | borne finale **exclue** | `range(1, 11)` pour 1→10 |
| **Indice / valeur confondus** | on parcourt l'un pour l'autre | choisir `for x in …` ou `range(len())` |
| **Dépassement d'indice** | l'indice n'existe pas | dernier indice = `len(c) - 1` |
| **Compteur mal géré** | non initialisé / non mis à jour | `c = 0` puis `c += 1` |
| **Boucle infinie** | la condition n'évolue pas | mettre à jour la variable testée |
| **`break` mal placé** | on sort trop tôt / jamais | placer `break` dans le bon test |
| **Globale modifiée par erreur** | effet de bord inattendu | préférer paramètres et `return` |

---

## 7. Questions-réponses corrigées

### Vocabulaire

??? question "1. Quelle est la différence entre paramètre et argument ?"
    Le **paramètre** est dans la **définition** (`def f(x)`) ; l'**argument** est la
    **valeur** donnée à l'appel (`f(5)`).

??? question "2. Que renvoie une fonction sans `return` ?"
    **`None`**.

??? question "3. À partir de quel nombre commencent les indices ?"
    À partir de **0**.

??? question "4. Qu'est-ce qu'un accumulateur ?"
    Une variable qui **cumule** un résultat (somme, concaténation…) au fil de la boucle.

??? question "5. Différence entre boucle bornée et non bornée ?"
    **Bornée** (`for`) : nombre de tours connu ; **non bornée** (`while`) : on répète
    **tant qu'une condition** est vraie.

### Compréhension

??? question "6. Pourquoi l'ordre des `elif` est-il important ?"
    Le **premier test vrai** est exécuté : un test trop large placé avant masque les
    suivants.

??? question "7. Pourquoi `range(1, 11)` et non `range(1, 10)` pour une table jusqu'à 10 ?"
    Parce que la **borne finale est exclue** : `range(1, 11)` donne 1 à 10.

??? question "8. Quand préférer `while` à `for` ?"
    Quand on **ne connaît pas** le nombre de tours (saisie, devinette…).

??? question "9. Que se passe-t-il si on oublie de mettre à jour la variable d'un `while` ?"
    La condition reste vraie → **boucle infinie**.

??? question "10. Pourquoi `print` ne suffit-il pas pour réutiliser un résultat ?"
    `print` **affiche** seulement ; pour réutiliser une valeur, il faut **`return`**.

### Lecture de code

??? question "11. Que vaut `\"BONJOUR\"[1:4]` ?"
    `\"ONJ\"` (indices 1, 2, 3 ; la borne 4 est exclue).

??? question "12. Que vaut `\"PYTHON\"[-1]` ?"
    `\"N\"` (dernier caractère).

??? question "13. Que vaut `c` après ce code ? `c=0` puis `for x in \"abba\": if x=='a': c+=1`"
    `c = 2`.

??? question "14. Que renvoie `f(4)` ? `def f(n): return n % 2 == 0`"
    `True` (4 est pair).

??? question "15. Combien de fois s'affiche `*` ? `for i in range(3): print('*')`"
    **3** fois.

### Méthode

??? question "16. Comment vérifier qu'un nombre est multiple de 3 ?"
    Tester **`n % 3 == 0`**.

??? question "17. Comment écrire la condition d'une année bissextile ?"
    `(a % 4 == 0 and a % 100 != 0) or (a % 400 == 0)`.

??? question "18. Comment compter les voyelles d'une chaîne ?"
    Initialiser un compteur, parcourir la chaîne, incrémenter si le caractère est une
    voyelle.

??? question "19. Comment parcourir une chaîne en ayant besoin de l'indice ?"
    `for i in range(len(chaine)):` puis utiliser `chaine[i]`.

??? question "20. Comment trouver le maximum de deux nombres avec un `if` ?"
    ```python
    if a > b: return a
    else: return b
    ```

### Correction d'erreurs

??? question "21. Corriger : `if x = 5:`"
    `if x == 5:` (comparaison, pas affectation).

??? question "22. Corriger : `def f(n) return n*2`"
    Il manque les `:` : `def f(n): return n*2`.

??? question "23. Pourquoi `while i < 5: print(i)` boucle-t-il à l'infini ?"
    `i` n'est **jamais mis à jour** : ajouter `i += 1`.

??? question "24. Corriger : `for i in range(1,10): print(i)` pour aller jusqu'à 10."
    `range(1, 11)` (borne finale exclue).

??? question "25. Pourquoi `resultat = print(aire(2,3))` donne-t-il `None` ?"
    `print` ne **renvoie** rien : il faut `resultat = aire(2, 3)`.

### Programmation / code à compléter

??? question "26. Compléter : `def carre(x): return ____`"
    `return x * x`.

??? question "27. Écrire une fonction `est_pair(n)`."
    ```python
    def est_pair(n):
        return n % 2 == 0
    ```

??? question "28. Écrire un compteur de la lettre `e` dans `mot`."
    ```python
    c = 0
    for car in mot:
        if car == "e":
            c += 1
    ```

??? question "29. (Approfondissement) Écrire `factorielle(n)` itérative."
    ```python
    def factorielle(n):
        f = 1
        for i in range(2, n + 1):
            f = f * i
        return f
    ```

??? question "30. (Approfondissement) Écrire `est_premier(n)`."
    ```python
    def est_premier(n):
        if n < 2:
            return False
        for d in range(2, n):
            if n % d == 0:
                return False
        return True
    ```

---

## 8. Exercices flash corrigés

??? question "Compléter une fonction : `def double(x): return ____`"
    `return 2 * x`.

??? question "Choisir la bonne condition : « x est entre 0 et 20 inclus »"
    `0 <= x <= 20`.

??? question "Corriger `and`/`or` : « admis si note ≥ 10 ET présence »"
    `note >= 10 and present` (et non `or`).

??? question "Prévoir une valeur booléenne : `7 % 2 == 0`"
    `False`.

??? question "Retrouver une tranche : `\"NSI\"[0:2]`"
    `\"NS\"`.

??? question "Compléter un `range` : répéter 5 fois"
    `for i in range(5):`.

??? question "Écrire un compteur de caractères d'une chaîne `s`"
    ```python
    c = 0
    for car in s:
        c += 1
    ```

??? question "Corriger une boucle infinie : `i=0; while i<3: print(i)`"
    Ajouter `i += 1` dans la boucle.

??? question "Choisir `for` ou `while` : « demander un mot jusqu'à 'fin' »"
    **`while`** (nombre de tours inconnu).

??? question "Écrire une courte fonction avec `return` : somme de deux nombres"
    ```python
    def somme(a, b):
        return a + b
    ```

??? question "Tracer : `for i in range(3): print(i)`"
    Affiche `0`, `1`, `2`.

??? question "Expliquer la portée : variable créée dans une fonction"
    Elle est **locale** : elle n'existe **pas** en dehors de la fonction.

---

## 9. À retenir absolument

!!! success "Syntaxes indispensables"
    ```python
    def f(x):          if c1:           for i in range(n):     while cond:
        return x           ...              ...                    ...
                       elif c2:                                    # faire évoluer cond
                           ...
                       else:
                           ...
    ```

!!! note "Réflexes clés"
    - **`return`** renvoie (réutilisable) ; **`print`** affiche seulement ;
    - dans `range` et les **tranches**, la **borne finale est exclue** ;
    - **`for`** = nombre de tours connu ; **`while`** = arrêt sur condition ;
    - **compteur** : initialiser (`c = 0`) → mettre à jour (`c += 1`) → résultat ;
    - un **`while`** doit faire **évoluer sa condition** (sinon boucle infinie) ;
    - les **indices commencent à 0** ;
    - **ordre des conditions** : du plus restrictif au plus large ;
    - **prudence** avec les variables **globales** (préférer paramètres + `return`).
---
author: Elisabeth Le Prettre (LePrettre)
title: 03 📜 Fiche Méthode - Mise au point
---

# Mise au point des scripts et gestion des exceptions

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 3"
    Fiche **progressive et compacte** pour **spécifier** et **mettre au point** ses
    programmes : prototype, docstrings, **jeux de tests** (`assert`, `doctest`),
    pré/postconditions, modules et **gestion des exceptions**
    (`try / except / else / finally`, `raise`).

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** : prototype, spécification, docstrings, `help`, `assert`, `doctest`, **jeux de tests**, pré/postconditions, modules, exceptions ;
- **comprendre** : à quoi sert un test, pourquoi **le succès d'un jeu de tests ne garantit pas la correction d'un programme**, quand une exception est levée ;
- **lire** : une docstring, un rapport `doctest`, un bloc `try/except` ;
- **expliquer** : le chemin d'exécution d'un programme protégé ;
- **compléter** : un test, une importation, un bloc d'exception ;
- **programmer** : une fonction **prototypée**, documentée et testée par un **jeu de tests bien choisi**, une saisie sécurisée.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Prototype** | « Carte d'identité » d'une fonction : **nom**, **paramètres** (types) et **type du résultat**. Ex. `factorielle(n: int) -> int`. |
| **Annotation de type** | Indication de type dans l'en-tête (`n: int`, `-> int`) ; **non vérifiée** par Python. |
| **Spécification** | Description de **ce que fait** la fonction (sans dire comment) : prototype + rôle + préconditions + postconditions. |
| **Documentation** | Texte expliquant ce que fait un programme / une fonction. |
| **Docstring** | Chaîne de documentation placée **juste après** le `def`, entre `"""…"""`. |
| **Condition d'utilisation** | Ce que l'appelant doit respecter pour un usage correct. |
| **Test** | Vérification qu'une fonction donne le **résultat attendu**. |
| **Assertion** | Test qui **doit** être vrai (`assert`), sinon le programme s'arrête. |
| **Cas de test** | Une entrée précise associée à son résultat attendu. |
| **Jeu de tests** | **Ensemble de cas de test** (ordinaires, limites, particuliers). Son **succès ne garantit pas la correction** du programme. |
| **Résultat attendu** | Valeur correcte **calculée à l'avance**. |
| **Précondition** | Condition vraie **avant** le calcul (sur les entrées). |
| **Postcondition** | Propriété vraie **après** le calcul (sur le résultat). |
| **Module** | Fichier de fonctions réutilisables (`math`, `random`). |
| **Bibliothèque** | Ensemble de modules. |
| **Importation** | Action de rendre un module disponible (`import …`). |
| **Exception** | Erreur signalée pendant l'exécution. |
| **`ValueError`** | Valeur de **mauvais type / invalide** (ex. `int("abc")`). |
| **`ZeroDivisionError`** | **Division par zéro**. |
| **Capture d'une exception** | L'**intercepter** avec `except` pour éviter l'arrêt. |
| **Déclenchement d'une exception** | La **provoquer** volontairement avec `raise`. |

---

## 3. Méthodes pas à pas

??? note "A. Prototyper et spécifier une fonction"
    - **Quand ?** **Avant** d'écrire le corps de la fonction.
    - **Étapes :** choisir le **nom** → lister les **paramètres** et leurs **types** →
      indiquer le **type du résultat** → décrire le **rôle** → les **préconditions** →
      les **postconditions**.
    - **Modèle (prototype avec annotations) :**
      ```python
      def factorielle(n: int) -> int:
      ```
    - **Règle :** une spécification **rapide mais précise** suffit pour vos programmes.
    - **Erreurs :** croire que Python **vérifie** les annotations (elles sont indicatives).

??? note "B. Rédiger une docstring"
    - **Quand ?** Dès qu'on écrit une fonction.
    - **Étapes :** placer la docstring **juste après** le `def` → décrire le **rôle** →
      les **paramètres** → le **résultat** → les **conditions d'utilisation** →
      éventuellement des exemples `>>>`.
    - **Modèle :**
      ```python
      def carre(x):
          """Renvoie le carré de x.
          >>> carre(3)
          9
          """
          return x * x
      ```
    - **Afficher :** `help(carre)`.
    - **Erreurs :** docstring placée **avant** le `def` ou hors de la fonction.

??? note "C. Construire un jeu de tests"
    - **Repérer :** les **cas représentatifs** à couvrir pour former un **jeu de tests**.
    - **Cas à prévoir :** ordinaire · valeur **nulle** · **négative** · **limite** ·
      **décimale** (si autorisé) · **mauvais type** · donnée **hors conditions d'utilisation**.
    - **Règle :** **calculer le résultat attendu AVANT** d'écrire le test.
    - **Qualité et nombre :** un cas mal choisi peut laisser passer un bug
      (ex. `somme(2, 2)` ne distingue pas `a + b` de `a * b` !).
    - ⚠️ **Limite (programme officiel) :** un test qui **échoue** prouve un **bug**, mais
      **le succès d'un jeu de tests ne garantit pas la correction du programme** —
      il ne prouve rien en dehors des cas testés.

??? note "D. Écrire un test avec `assert`"
    - **Syntaxe :** `assert condition, "message"`.
    - **Comportement :** **aucun affichage** si réussi ; **arrêt** (`AssertionError`) si échec.
    - **Exemples :**
      ```python
      assert carre(3) == 9
      assert division_euclidienne(17, 5) == (3, 2)
      ```
    - **Vérif :** si le programme ne s'arrête pas, tous les `assert` sont passés.

??? note "E. Utiliser `if __name__ == '__main__':`"
    - **Rôle (dans ce chapitre) :** **regrouper les tests** qui s'exécutent **quand le
      fichier est lancé directement**.
    - **Modèle :**
      ```python
      if __name__ == '__main__':
          assert carre(3) == 9
      ```

??? note "F. Écrire un test avec `doctest`"
    - **Étapes :** `import doctest` → placer les exemples **dans la docstring** avec
      `>>>` → écrire le **résultat attendu exactement** → `doctest.testmod()`.
    - **Modèle :**
      ```python
      import doctest

      def carre(x):
          """
          >>> carre(3)
          9
          """
          return x * x

      doctest.testmod()        # verbose=True pour le détail
      ```
    - **Échec :** `doctest` affiche `Expected` (attendu) vs `Got` (obtenu).

??? note "G. Distinguer `assert` et `doctest`"
    | | **`assert`** | **`doctest`** |
    |---|---|---|
    | Emplacement | dans le code / les tests | dans la **docstring** |
    | Syntaxe | `assert cond` | `>>>` + résultat attendu |
    | Objectif | vérifier une condition | vérifier des exemples |
    | Réussite | aucun affichage | rien (ou détail si `verbose`) |
    | Échec | `AssertionError` (arrêt) | rapport `Expected / Got` |

??? note "H. Écrire une précondition"
    - **Repérer :** une condition qui doit être vraie **avant** le calcul.
    - **Modèle :** `assert x >= 0, "x doit être positif"` **au début** de la fonction.

??? note "I. Écrire une postcondition"
    - **Idée :** vérifier **après** le calcul une propriété du **résultat**.
    - **Exemple (racine carrée) :**
      ```python
      def racine(x):
          assert x >= 0            # précondition
          r = x ** 0.5
          assert r >= 0            # postcondition
          return r
      ```

??? note "J. Importer un module"
    | Forme | Appel |
    |---|---|
    | `import math` | `math.sqrt(2)` |
    | `import random as rd` | `rd.randint(1, 6)` |
    | `from random import randrange` | `randrange(10)` |

    - `from module import *` : forme **rencontrée** dans les sources, à **éviter**
      (on ne sait plus d'où viennent les noms).

??? note "K. Identifier une exception"
    - **Repérer :** la **ligne** qui peut échouer, le **type** d'erreur, la **donnée**
      responsable, le **moment** d'arrêt.
    - **Exemples :** `int("abc")` → `ValueError` ; `1 / 0` → `ZeroDivisionError`.

??? note "L. Écrire un bloc `try / except`"
    - **Étapes :** mettre dans `try` **seulement** la ligne risquée → choisir le **type**
      d'exception → écrire un **message adapté** → **poursuivre** sans arrêt brutal.
    - **Modèle :**
      ```python
      try:
          x = int(input("Nombre : "))
      except ValueError:
          print("Entier attendu.")
      ```

??? note "M. Gérer plusieurs exceptions"
    ```python
    try:
        print(a / b)
    except ZeroDivisionError:
        print("Division par zéro.")
    except ValueError:
        print("Valeur invalide.")
    ```
    Chaque `except` traite **un type** d'erreur avec **son** message.

??? note "N. Utiliser `else` dans un bloc d'exception"
    - **Rôle :** s'exécute **uniquement si aucune exception** n'a été levée.
      ```python
      try:
          r = a / b
      except ZeroDivisionError:
          print("Erreur")
      else:
          print("Résultat :", r)   # seulement si pas d'erreur
      ```

??? note "O. Utiliser `finally`"
    - **Rôle :** s'exécute **toujours** (erreur ou non).
    - **`else` vs `finally` :** `else` = si **pas** d'exception ; `finally` = **dans tous les cas**.

??? note "P. Déclencher une exception avec `raise`"
    - **Étapes :** vérifier une condition incorrecte → choisir le type →
      `raise ValueError("message")` → capturer → récupérer le message avec `as e`.
    - **Modèle :**
      ```python
      def verifier_annee(a):
          if a < 0:
              raise ValueError("année négative")
          return a

      try:
          verifier_annee(-5)
      except ValueError as e:
          print("Erreur :", e)
      ```

??? note "Q. Redemander une saisie jusqu'à validité"
    - **Étapes :** boucle **infinie** → demander la valeur → tenter conversion + calcul →
      **traiter** les erreurs → **ne pas quitter** après une erreur → `break` **après succès**.
    - **Exemple (inverse) :**
      ```python
      while True:
          try:
              x = float(input("Nombre : "))
              print(1 / x)
              break                      # uniquement si tout a réussi
          except ValueError:
              print("Ce n'est pas un nombre.")
          except ZeroDivisionError:
              print("Division par zéro impossible.")
      ```

---

## 4. Lecture et compréhension de code

!!! tip "Méthode"
    - **écrire ou lire le prototype** d'une fonction (nom, types des paramètres, type du résultat) ;
    - **juger un jeu de tests** : repérer le **cas manquant** qui révélerait un bug ;
    - **prévoir si un `assert` réussit** : calculer la condition ;
    - **retrouver le test qui échoue** : repérer le premier `assert` faux ;
    - **lire un rapport `doctest`** : comparer `Expected` et `Got` ;
    - **distinguer pré/postcondition** : entrée (avant) vs résultat (après) ;
    - **retrouver le nom d'appel** d'une fonction importée (selon la forme d'import) ;
    - **identifier la ligne** qui lève une exception ;
    - **déterminer le bloc `except`** exécuté (selon le type d'erreur) ;
    - **prévoir si `else` s'exécute** (seulement sans exception) ;
    - **vérifier si `finally` s'exécute** (toujours) ;
    - **déterminer la fin d'une boucle** (`break` après succès) ;
    - **repérer un `break` mal placé** (après un message d'erreur).

---

## 5. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Conception d'un jeu de tests**
    | Type de cas | Entrée | Résultat attendu (calculé avant) |
    |---|---|---|
    | ordinaire | `carre(3)` | 9 |
    | limite | `carre(0)` | 0 |
    | particulier | `carre(-2)` | 4 |

    **Série de tests `assert`**
    | Test | Condition | Résultat attendu | Réussi ? |
    |---|---|---|---|
    | `carre(3)` | `== 9` | 9 | oui |

    **Test `doctest`**
    | Exemple | Attendu (`Expected`) | Obtenu (`Got`) | Réussi ? |
    |---|---|---|---|
    | `carre(3)` | 9 | 9 | oui |

    **Division `try/except/else/finally`**
    | `a`, `b` | Exception levée | Bloc exécuté | `else` ? | `finally` ? | Affichage |
    |---|---|---|---|---|---|
    | 10, 2 | aucune | `try` | oui | oui | résultat + fin |
    | 10, 0 | `ZeroDivisionError` | `except` | non | oui | erreur + fin |

    **Boucle de ressaisie**
    | Saisie | Conversion | Exception | Message | Valeur calculée | Sortie (`break`) ? |
    |---|---|---|---|---|---|
    | `abc` | échec | `ValueError` | « pas un nombre » | — | non |
    | `0` | ok | `ZeroDivisionError` | « div. par zéro » | — | non |
    | `4` | ok | aucune | — | `0.25` | **oui** |

---

## 6. Erreurs fréquentes

| Erreur | Pourquoi c'est faux | Correction / éviter |
|---|---|---|
| Confondre prototype et docstring | rôles différents | prototype = en-tête ; docstring = description |
| Croire que Python vérifie `n: int` | annotations **indicatives** | vérifier soi-même (assert / try) |
| Docstring au mauvais endroit | non reconnue par `help` | la placer **juste après** `def` |
| Documentation incomplète | usage ambigu | décrire rôle, paramètres, résultat |
| Résultat attendu faux dans un `assert` | test invalide | **calculer** le résultat avant |
| Un seul cas testé | bugs non détectés | couvrir cas limites / erreurs |
| « Tests réussis donc programme correct » | **faux** : rien n'est prouvé hors des cas testés | enrichir le **jeu de tests**, rester prudent |
| Test ≠ condition d'utilisation confondus | rôles différents | tester ≠ restreindre l'usage |
| Exemple `doctest` mal écrit | échec systématique | copier la sortie **exacte** |
| Oubli d'`import doctest` | `testmod` indéfini | `import doctest` |
| Pré/postcondition confondues | mauvaise vérification | entrée (avant) / résultat (après) |
| `sqrt` sans import adapté | `NameError` | `from math import sqrt` ou `math.sqrt` |
| Module / fonction confondus | mauvais appel | `math.sqrt`, pas `math()` |
| `try` trop large | masque d'autres erreurs | n'y mettre que la ligne risquée |
| Mauvais type d'exception | erreur non capturée | choisir `ValueError` / `ZeroDivisionError` |
| `except` mal indenté | syntaxe / logique fausse | aligner `try` et `except` |
| `else` / `finally` confondus | exécution inattendue | `else` = sans erreur ; `finally` = toujours |
| Exception trop générale | masque les vraies causes | viser le **bon** type |
| Oubli de `raise` | l'erreur n'est pas levée | `raise ValueError(...)` |
| Mauvais intervalle avant `raise` | rejette de bonnes valeurs | revoir la condition |
| Boucle infinie sans sortie | jamais de `break` | `break` après succès |
| `break` après un message d'erreur | on sort à tort | `break` **après le calcul** réussi |
| Pas de nouvelle saisie dans la boucle | redemande impossible | placer `input` **dans** la boucle |

---

## 7. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'une docstring ?"
    Une chaîne de **documentation** placée juste après le `def`, entre `"""…"""`,
    affichable avec `help`.

??? question "1 bis. (N1) Qu'est-ce que le prototype d'une fonction ?"
    Son **nom**, ses **paramètres** (avec leurs types) et le **type du résultat**,
    ex. `factorielle(n: int) -> int`.

??? question "1 ter. (N2) Que contient la spécification d'une fonction ?"
    Le **prototype**, le **rôle**, les **préconditions** et les **postconditions** :
    elle dit **ce que fait** la fonction, pas **comment**.

??? question "2. (N1) Que fait `assert` en cas de réussite ? d'échec ?"
    Réussite : **aucun affichage** ; échec : **`AssertionError`** et arrêt du programme.

??? question "2 bis. (N1) Qu'est-ce qu'un jeu de tests ?"
    Un **ensemble de cas de test** : pour chaque cas, une **entrée** et le
    **résultat attendu** calculé à l'avance.

??? question "3. (N2) Différence entre précondition et postcondition ?"
    La **précondition** porte sur les **entrées** (avant le calcul) ; la
    **postcondition** sur le **résultat** (après le calcul).

??? question "4. (N1) Quand obtient-on une `ZeroDivisionError` ?"
    Lors d'une **division par zéro** (ex. `1 / 0`).

??? question "5. (N2) Différence entre module et bibliothèque ?"
    Un **module** est un fichier de fonctions ; une **bibliothèque** regroupe plusieurs modules.

### Compréhension

??? question "6. (N2) Pourquoi un `assert` réussi n'affiche-t-il rien ?"
    Parce qu'il ne signale que les **problèmes** : pas de nouvelle = tout va bien.

??? question "7. (N2) Quand le bloc `else` d'un `try` s'exécute-t-il ?"
    **Uniquement si aucune exception** n'a été levée dans le `try`.

??? question "8. (N2) Quand `finally` s'exécute-t-il ?"
    **Toujours**, qu'une exception ait été levée ou non.

??? question "9. (N1) À quoi sert `doctest` ?"
    À **vérifier automatiquement** les exemples `>>>` écrits dans les docstrings.

??? question "10. (N3) Pourquoi ne met-on que la ligne risquée dans `try` ?"
    Pour **cibler** l'erreur attendue et ne pas **masquer** d'autres problèmes.

??? question "10 bis. (N3) Le succès d'un jeu de tests garantit-il la correction du programme ?"
    **Non.** Il prouve seulement que le programme est correct **sur les cas testés**.
    Ex. : `somme` codée avec `a * b` passe les tests `somme(2, 2) == 4` et
    `somme(0, 0) == 0`… mais échoue sur `somme(2, 3)`. Un test qui **échoue**
    prouve un bug ; un jeu de tests qui **réussit** ne prouve pas l'absence de bug.

### Lecture de code

??? question "11. (N1) `assert carre(3) == 9` réussit-il ?"
    Oui : `carre(3)` vaut `9`, la condition est vraie.

??? question "12. (N1) Quel `except` pour `1 / 0` ?"
    `except ZeroDivisionError`.

??? question "13. (N1) Quel `except` pour `int(\"abc\")` ?"
    `except ValueError`.

??? question "14. (N2) Dans `try/except/else`, `else` s'exécute-t-il si une exception est levée ?"
    **Non** : `else` n'est exécuté **que sans** exception.

??? question "15. (N3) Un `doctest` affiche `Expected: 9 / Got: 6`. Que conclut-on ?"
    La fonction renvoie **`6`** au lieu de `9` : il y a un **bug** (ou un attendu mal écrit).

### Méthode

??? question "16. (N1) Écrire une précondition « x positif »."
    `assert x >= 0, "x doit être positif"`.

??? question "17. (N1) Importer `sqrt` et l'utiliser."
    `from math import sqrt` puis `sqrt(2)`.

??? question "18. (N3) Comment redemander une saisie valide ?"
    Boucle `while True`, `input` + conversion dans un `try`, `except` pour les erreurs,
    `break` **après** un calcul réussi.

??? question "19. (N2) Comment refuser une année négative ?"
    `if a < 0: raise ValueError(\"année négative\")`.

??? question "20. (N2) Comment tester une valeur limite de `factorielle` ?"
    Tester `factorielle(0)` ou `factorielle(1)` (attendu `1`).

??? question "20 bis. (N1) Écrire le prototype de `carre` (entier → entier)."
    `def carre(x: int) -> int:`

### Correction d'erreurs

??? question "21. (N2) Corriger un `try` contenant tout le programme."
    N'y laisser **que** la ligne susceptible de lever l'exception, sortir le reste.

??? question "22. (N2) Pourquoi éviter `except:` tout seul ?"
    Trop **général** : il masque toutes les erreurs. Préciser le **type** attendu.

??? question "23. (N3) Pourquoi `break` après un message d'erreur est-il faux ?"
    On **sort** alors que la saisie était invalide : placer `break` **après le succès**.

??? question "24. (N1) Le code utilise `doctest.testmod()` mais plante. Pourquoi ?"
    Il manque sans doute `import doctest`.

??? question "25. (N1) `sqrt(2)` provoque `NameError`. Pourquoi ?"
    `sqrt` n'a pas été importé : `from math import sqrt` (ou `math.sqrt`).

### Programmation / code à compléter

??? question "26. (N1) Compléter la docstring de `carre` avec un exemple `doctest`."
    ```python
    """Renvoie le carré de x.
    >>> carre(3)
    9
    """
    ```

??? question "27. (N2) Ajouter une assertion à `division_euclidienne(a, b)`."
    `assert b != 0, "le diviseur doit être non nul"`.

??? question "28. (N3) Écrire un `try/except` pour l'inverse d'un nombre saisi."
    ```python
    try:
        x = float(input("Nombre : "))
        print(1 / x)
    except ValueError:
        print("Pas un nombre.")
    except ZeroDivisionError:
        print("Division par zéro.")
    ```

??? question "29. (N2) Compléter `multiplier_par_deux` avec une postcondition simple."
    ```python
    def multiplier_par_deux(x):
        r = 2 * x
        assert r == x + x      # postcondition
        return r
    ```

??? question "30. (N4) Écrire une racine carrée sécurisée par ressaisie."
    ```python
    from math import sqrt
    while True:
        try:
            x = float(input("Nombre : "))
            if x < 0:
                raise ValueError("nombre négatif")
            print(sqrt(x))
            break
        except ValueError as e:
            print("Erreur :", e)
    ```

---

## 8. Exercices flash corrigés

??? question "Écrire le prototype de `factorielle` avec annotations"
    `def factorielle(n: int) -> int:`

??? question "Compléter une docstring (rôle + résultat)"
    `"""Renvoie le double de x."""` au début de la fonction.

??? question "Choisir quatre cas de test pour `carre`"
    `0`, un positif (`3`), un négatif (`-2`), un décimal (`1.5`).

??? question "Écrire un `assert` pour `factorielle(4)`"
    `assert factorielle(4) == 24`.

??? question "Corriger un résultat attendu : `assert factorielle(3) == 9`"
    Faux : `factorielle(3) == 6`.

??? question "`somme` codée avec `a * b` passe `somme(2, 2) == 4`. Conclusion ?"
    Le jeu de tests est **mal choisi** : ajouter `somme(2, 3) == 5` révèle le bug.
    Le **succès d'un jeu de tests ne garantit pas la correction**.

??? question "Compléter un exemple `doctest` pour `factorielle`"
    ```
    >>> factorielle(5)
    120
    ```

??? question "Reconnaître une précondition : `assert n >= 0`"
    C'est une **précondition** (porte sur l'entrée, avant le calcul).

??? question "Écrire une postcondition pour une racine `r` de `x`"
    `assert r >= 0` (ou `r * r` proche de `x`).

??? question "Choisir la forme d'import pour `randint`"
    `from random import randint` puis `randint(1, 6)`.

??? question "Prévoir le type d'exception : `float(\"\")`"
    `ValueError`.

??? question "Compléter un `try/except` pour une conversion"
    ```python
    try:
        n = int(s)
    except ValueError:
        print("Entier attendu.")
    ```

??? question "Choisir entre `else` et `finally` : « toujours fermer »"
    `finally` (s'exécute dans tous les cas).

??? question "Écrire une instruction `raise` si `b == 0`"
    `raise ZeroDivisionError("diviseur nul")`.

??? question "Corriger une boucle de ressaisie sans `input` interne"
    Déplacer `input(...)` **à l'intérieur** de la boucle `while True`.

??? question "Placer correctement `break` dans la ressaisie"
    Après le **calcul réussi**, jamais après un message d'erreur.

---

## 9. À retenir absolument

!!! success "Modèles indispensables"
    ```python
    # Prototype : nom, paramètres (types), type du résultat
    def f(x: int) -> int:
        ...

    # Docstring : rôle, paramètres, résultat, exemples
    def f(x):
        """Renvoie ... .  >>> f(3) \n 9"""
        ...

    assert f(3) == 9              # test : rien si OK, AssertionError sinon

    try:                         # gestion d'exception
        ...                      # ligne risquée
    except ValueError:
        ...
    else:                        # si AUCUNE exception
        ...
    finally:                     # TOUJOURS
        ...

    raise ValueError("message")  # déclencher une exception
    ```

!!! note "Réflexes clés"
    - **spécification** = prototype + rôle + préconditions + postconditions ;
    - **docstring** : rôle + paramètres + résultat (+ exemples `>>>`) ;
    - **jeu de tests** : cas **ordinaires + limites + particuliers**, résultats attendus
      calculés **avant** ; son **succès ne garantit pas la correction du programme** ;
    - **`doctest`** vérifie les exemples de la docstring (`import doctest` + `testmod()`) ;
    - **précondition** (entrée, avant) ≠ **postcondition** (résultat, après) ;
    - **3 imports** : `import math` · `import random as rd` · `from math import sqrt` ;
    - **`else`** = si pas d'exception ; **`finally`** = toujours ;
    - **`raise`** déclenche une erreur ; on récupère son message avec `as e` ;
    - **ressaisie** : `while True` + `try` + `break` **après** un calcul réussi.
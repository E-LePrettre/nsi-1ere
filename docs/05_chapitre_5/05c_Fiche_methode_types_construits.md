---
author: ELP
title: 05c Fiche méthode Types construits
---


## <span style="color:blue;">Les Listes et Tuples en Python</span>

???+ question "1. Qu'est-ce qu'une liste et un tuple ?"

    En **Python**, les *listes* et les *tuples* sont des structures de données permettant de stocker des collections d'éléments.

    - Une **liste** est une collection **modifiable** d'éléments.
    - Un **tuple** est une collection **non modifiable** (immuable).

    **Syntaxe :**

    ```python
    # Liste
    ma_liste = [1, 2, 3, 4, 5]

    # Tuple
    mon_tuple = (1, 2, 3, 4, 5)
    ```

    ??? success "Exemple"

        ```python
        fruits = ["pomme", "banane", "cerise"]
        couleurs = ("rouge", "vert", "bleu")
        print(fruits)
        print(couleurs)
        ```
        *Affiche :*
        ```
        ['pomme', 'banane', 'cerise']
        ('rouge', 'vert', 'bleu')
        ```
        {{ IDE() }}

## <span style="color:blue;">Accéder aux éléments d'une liste/tuple</span>

???+ question "2. Accéder aux éléments avec `liste[nombre]`"

    Vous pouvez accéder à un élément en utilisant son **indice**. En Python, l'indexation commence à 0.

    **Syntaxe :**
    ```python
    element = liste[indice]
    ```

    ??? success "Exemple"

        ```python
        nombres = [10, 20, 30, 40, 50]
        print(nombres[0])  # Premier élément
        print(nombres[3])  # Quatrième élément
        ```
        *Affiche :*
        ```
        10
        40
        ```
        {{ IDE() }}


???+ question "3. Accéder aux éléments avec `liste[-nombre]`"

    L'utilisation d'un indice **négatif** permet d'accéder aux éléments à partir de la fin de la liste.

    **Syntaxe :**
    ```python
    element = liste[-indice]
    ```

    ??? success "Exemple"

        ```python
        nombres = [10, 20, 30, 40, 50]
        print(nombres[-1])  # Dernier élément
        print(nombres[-3])  # Troisième élément à partir de la fin
        ```
        *Affiche :*
        ```
        50
        30
        ```
        {{ IDE() }}


???+ question "4. Accéder à des sous-parties avec un slicing"

    Le **slicing** permet d'extraire une sous-liste en spécifiant un intervalle d'indices.

    **Syntaxe :**
    ```python
    sous_liste = liste[debut:fin]
    ```
    L'élément à l'indice **debut** est inclus, mais celui à l'indice **fin** est exclu.

    ??? success "Exemple"

        ```python
        nombres = [10, 20, 30, 40, 50]
        print(nombres[1:4])  # Éléments des indices 1 à 3
        print(nombres[:3])   # Du début à l'indice 2
        print(nombres[2:])   # De l'indice 2 à la fin
        ```
        *Affiche :*
        ```
        [20, 30, 40]
        [10, 20, 30]
        [30, 40, 50]
        ```
        {{ IDE() }}


???+ question "5. Utiliser un pas dans le slicing avec `liste[debut:fin:pas]`"

    Vous pouvez spécifier un **pas** pour sauter des éléments dans le slicing.

    **Syntaxe :**
    ```python
    sous_liste = liste[debut:fin:pas]
    ```

    ??? success "Exemple"

        ```python
        nombres = [10, 20, 30, 40, 50, 60, 70]
        print(nombres[::2])  # Tous les 2 éléments
        print(nombres[1:6:2])  # De l'indice 1 à 5 avec un pas de 2
        print(nombres[::-1])  # Liste inversée
        ```
        *Affiche :*
        ```
        [10, 30, 50, 70]
        [20, 40, 60]
        [70, 60, 50, 40, 30, 20, 10]
        ```
        {{ IDE() }}


???+ question "7. Accéder aux éléments de listes de listes ou tuples de tuples"

    Vous pouvez accéder aux éléments imbriqués en utilisant plusieurs indices.

    ??? success "Exemple"

        ```python
        liste_de_listes = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        print(liste_de_listes[1][2])  # Accède à 6

        tuple_de_tuples = ((10, 20), (30, 40), (50, 60))
        print(tuple_de_tuples[2][0])  # Accède à 50
        ```
        *Affiche :*
        ```
        6
        50
        ```
        {{ IDE() }}

## <span style="color:blue;">Opérations sur les listes/tuples</span>

???+ question "8. Méthodes `pop`, `append` et opérateur `in`"

    - **`append`** ajoute un élément à la fin de la liste.
    - **`pop`** retire et retourne le dernier élément de la liste.
    - **`in`** vérifie la présence d'un élément dans la liste.

    ??? success "Exemple"

        ```python
        fruits = ["pomme", "banane", "cerise"]
        fruits.append("orange")
        print(fruits)

        dernier = fruits.pop()
        print("Élément supprimé:", dernier)
        print(fruits)

        print("pomme" in fruits)  # Vérifie si "pomme" est dans la liste
        print("kiwi" in fruits)
        ```
        *Affiche :*
        ```
        ['pomme', 'banane', 'cerise', 'orange']
        Élément supprimé: orange
        ['pomme', 'banane', 'cerise']
        True
        False
        ```
        {{ IDE() }}

## <span style="color:blue;">La boucle for sur les chaines/listes/tuples</span>

???+ question "9. Boucles `for` sur des chaînes de caractères, sur les listes, sur les tuples"

  **❤️ Boucle `for` sur chaque élément d'une chaîne : ❤️**

    ```python
    for elmt in chaine_de_caractere:
        print(elmt)
    ```

    ??? success "Exemple"

      ```python
      texte = "Python"
      for elmt in texte:
          print(elmt)
      ```
      *Affiche :*
      ```
      P
      y
      t
      h
      o
      n
      ```
      {{ IDE() }}

**❤️ Boucle `for` sur chaque élément d'une liste : ❤️**

  ```python
  for elmt in [10, 20, 30, 40]:
      print(elmt)
  ```

  ??? success "Exemple"

      ```python
      nombres = [10, 20, 30, 40]
      for elmt in nombres:
          print(elmt)
      ```
      *Affiche :*
      ```
      10
      20
      30
      40
      ```
      {{ IDE() }}

**❤️ Boucle `for` sur chaque élément d'un tuple : ❤️**

  ```python
  for elmt in ("rouge", "vert", "bleu"):
      print(elmt)
  ```

  ??? success "Exemple"

      ```python
      couleurs = ("rouge", "vert", "bleu")
      for elmt in couleurs:
          print(elmt)
      ```
      *Affiche :*
      ```
      rouge
      vert
      bleu
      ```
      {{ IDE() }}

## <span style="color:blue;">La boucle while les listes/tuples</span>

???+ question "10. Boucle `while`"

  La boucle `while` répète des instructions tant qu'une condition est vraie.

  ```python
  while condition:
      # Code à répéter tant que la condition est vraie
  ```

  ??? success "Exemple avec une liste"

      ```python
      nombres = [1, 2, 3, 4, 5]
      i = 0
      while i < len(nombres):
          print(nombres[i])
          i += 1
      ```
      *Affiche :*
      ```
      1
      2
      3
      4
      5
      ```
      {{ IDE() }}

  ??? success "Exemple avec un tuple"

      ```python
      couleurs = ("rouge", "vert", "bleu")
      i = 0
      while i < len(couleurs):
          print(couleurs[i])
          i += 1
      ```
      *Affiche :*
      ```
      rouge
      vert
      bleu
      ```
      {{ IDE() }}

---
author: ELP
title: 01d Révision Les conditions et les boucles
---





## <span style="color:blue;">Les conditions</span>


Une *instruction conditionnelle* est composée d’un **test** puis d'un **bloc d'instructions**.

En **Python**, le *test* commence par le mot clef `if condition` et se termine par le symbole `:`.

Le bloc d’instructions qui suit s'exécute si et seulement si le **test** a pour valeur `True` (est vraie).

En **Python**, un *bloc d'instructions* commence à la première ligne suivant le symbole `:` et son imbrication dans le reste du programme est caractérisée par son niveau d'*indentation*. Toutes les instructions d'un même bloc doivent avoir le **même niveau d'indentation**.

```python
# Bloc conditions 

if condition:
    # bloc d'instructions exécuté si la valeur de condition est True
```

C'est **l'indentation** (=décalage) qui délimite le bloc d'instructions.

Si la condition du **test** est `False` (n'est pas vérifiée), on peut prévoir l'exécution d'un bloc d'instructions alternatif après un `else:`.

```python
# Bloc conditions si ... sinon : 

if condition:
    # bloc d'instructions exécuté si la valeur de condition est True
else:
    # bloc d'instructions exécuté si la valeur de condition est False
```

_Remarque :_ Le bloc `else` n'est pas obligatoire.

???+ question "Activité n°1 :"

    Avec l'éditeur de script, **testez le code suivant :**

    

    ```python
    a = int(input("Entrer un nombre entier : "))
    if a >= 0:
        print("Vous avez entré un nombre positif ou nul", a)
    else:
        print("Vous avez entré un nombre négatif", a)
    ```
  

    **Alors, que se passe-t-il ?**

    - Avec `a = 8` ?  
    - Avec `a = -6` ?  
    - Avec `a = 0` ?  
    - Avec `a = "positif"` ? 

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        **Résultats attendus :**

        - Avec `a = 8` : "Vous avez entré un nombre positif ou nul 8"

        - Avec `a = -6` : "Vous avez entré un nombre négatif -6"

        - Avec `a = 0` : "Vous avez entré un nombre positif ou nul 0"

        - Avec `a = "positif"` : Erreur, car l'entrée n'est pas un entier.



On peut aussi tester d'autres conditions : chaque condition testée dans un `elif condition:` commande un bloc d'instructions.

```python
# Bloc conditions si ... sinon si ... sinon :

if condition1:
    # bloc d'instructions exécuté si la valeur de condition1 est True
elif condition2:
    # bloc d'instructions exécuté si condition2 est True (et condition1 est False)
elif condition3:
    # bloc d'instructions exécuté si condition3 est True (et condition1 et condition2 sont False)
else:
    # bloc d'instructions exécuté si toutes les conditions précédentes sont False
```

???+ question "Activité n°2 :"

    Avec l'éditeur de script, **testez le code suivant :**

   

    ```python
    a = int(input("Entrer un nombre entier : "))
    if a > 0:
        print("Vous avez entré un nombre positif", a)
    elif a == 0:
        print("Vous avez entré un nombre nul", a)
    else:
        print("Vous avez entré un nombre strictement négatif", a)
    ```

    **Alors, que se passe-t-il ?**

    - Avec `a = 8` ?  
    - Avec `a = -6` ?  
    - Avec `a = 0` ?  
    - Avec `a = "positif"` ? 

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        **Résultats attendus :**

        - Avec `a = 8` : "Vous avez entré un nombre positif 8"

        - Avec `a = -6` : "Vous avez entré un nombre strictement négatif -6"

        - Avec `a = 0` : "Vous avez entré un nombre nul 0"

        - Avec `a = "positif"` : Erreur, car l'entrée n'est pas un entier.

 

## <span style="color:blue;"> Opérateurs de test</span>

Un *test* peut être le résultat d'une *comparaison arithmétique* entre deux valeurs numériques `a` et `b` :

- **Égalité** : `a == b`
- **Différence** : `a != b`
- **Inégalités** : `a < b`, `a > b`, `a <= b`, `a >= b`

_Remarque : Attention à ne pas confondre :_

- `a = 2` stocke la valeur 2 dans la variable `a`.
- `a == 2` teste si `a` est égal à l'entier 2.

???+ question "Activité n°3 :"

    **Écrire un script** qui demande à l’utilisateur sa note en informatique.


    - Si elle est supérieure ou égale à 16, on affichera "Tu es un dieu/déesse en info".
    - Sinon si elle est comprise entre 12 inclus et 16 exclus, on affichera "C’est bien".
    - Sinon si elle est inférieure à 12, on affichera "Il faut travailler".
    - Sinon si elle est égale à 0, on affichera "OH LA LA".

    **Tester avec :** 17, 16, 14, 7, 0.

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        ```python
        note = int(input("Entrez votre note en informatique : "))
        if note >= 16:
            print("Tu es un dieu/deesse en info")
        elif 12 <= note < 16: 
            print("C’est bien")
        elif 0 < note < 12>:
            print("Il faut travailler")
        elif note == 0:
            print("OH LA LA")
        ```

        on aurait pu aussi écrire
        ```python
        note = int(input("Entrez votre note en informatique : "))
        if note >= 16:
            print("Tu es un dieu/deesse en info")
        elif 12 <= note : 
            print("C’est bien")
        elif 0 < note :
            print("Il faut travailler")
        elif note == 0:
            print("OH LA LA")
        ```

        **Résultats attendus :**

        - Avec `note = 17` : "Tu es un dieu/deesse en info"

        - Avec `note = 16` : "Tu es un dieu/deesse en info"

        - Avec `note = 14` : "C’est bien"

        - Avec `note = 7` : "Il faut travailler"

        - Avec `note = 0` : "OH LA LA"

    

???+ question "A faire vous-même Activité n°4 :"

    **Écrire un script** qui demande une couleur à l’utilisateur.


    - Si c’est "bleu", "rouge" ou "vert", on affichera "C’est gagné".
    - Sinon, on affichera "C’est perdu".

    **Tester avec :** rouge, bleu, vert, noir.

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        ```python
        couleur = input("Entrez une couleur : ")
        if couleur == "bleu" or couleur == "rouge" or couleur == "vert":
            print("C’est gagné")
        else:
            print("C’est perdu")
        ```
        
        **Résultats attendus :**

        - Avec `couleur = "rouge"` : "C’est gagné"

        - Avec `couleur = "bleu"` : "C’est gagné"

        - Avec `couleur = "vert"` : "C’est gagné"

        - Avec `couleur = "noir"` : "C’est perdu"



## <span style="color:blue;"> Exercices sur les conditions </span>

???+ question "Exercice 1 : Couleur et Nombre"

    Écrire un script qui demande une couleur et un nombre à l’utilisateur.


    - Si c’est **bleu** et que le nombre est supérieur à 20, on affichera "C’est gagné".
    - S’il est inférieur à 20, on affichera "Presque".
    - Sinon, si c'est **rouge** et que le nombre est supérieur à 10, on affichera "Super".
    - Mais si le nombre est inférieur à 10, on affichera "Presque".
    - Sinon, on affichera "C’est perdu".

    **Tester :**

    - Une couleur valide comme `bleu` ou `rouge`.
    - Un nombre supérieur ou inférieur aux seuils donnés.

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        ```python
        couleur = input("Entrez une couleur : ")
        nombre = int(input("Entrez un nombre : "))

        if couleur == "bleu" and nombre > 20:
            print("C’est gagné")
        elif couleur == "bleu" and nombre < 20:
            print("Presque")
        elif couleur == "rouge" and nombre > 10:
            print("Super")
        elif couleur == "rouge" and nombre < 10:
            print("Presque")
        else:
            print("C’est perdu")
        ```    

        **Résultats attendus :**

        - `couleur = "bleu"`, `nombre = 25` : "C’est gagné"

        - `couleur = "bleu"`, `nombre = 15` : "Presque"

        - `couleur = "rouge"`, `nombre = 12` : "Super"

        - `couleur = "rouge"`, `nombre = 8` : "Presque"

        - `couleur = "vert"`, `nombre = 30` : "C’est perdu"




???+ question "Exercice 2 : Triangle"

    1. Écrire un programme qui demande à l'utilisateur les longueurs des côtés d'un triangle (ces longueurs étant entières) et qui indique si ce triangle est **équilatéral** ou pas.

    ??? success "Python"
        {{ IDE() }}
    
    ??? success "Solution"
        ```python
        a = int(input("Longueur du côté a : "))
        b = int(input("Longueur du côté b : "))
        c = int(input("Longueur du côté c : "))

        if a == b and b == c:
            print("Le triangle est équilatéral")
        else:
            print("Le triangle n'est pas équilatéral")
        ```




    2 Modifier le programme pour qu'il indique si le triangle est **isocèle** ou pas.


    ??? success "Python"
        {{ IDE() }}
    
    ??? success "Solution"
        ```python
        if a == b or b == c or a == c:
            print("Le triangle est isocèle")
        else:
            print("Le triangle n'est pas isocèle")
        ```



    3 Modifier le programme pour qu'il indique si le triangle est **équilatéral**, et s'il ne l'est pas, vérifier s'il est **isocèle**.

    ??? success "Python"
        {{ IDE() }}
    
    ??? success "Solution"
        ```python
        if a == b and b == c:
            print("Le triangle est équilatéral")
        elif a == b or b == c or a == c:
            print("Le triangle est isocèle")
        else:
            print("Le triangle n'est ni équilatéral ni isocèle")
        ```
        **Résultats attendus :**

        - `a = 3, b = 3, c = 3` : "Le triangle est équilatéral"

        - `a = 4, b = 4, c = 5` : "Le triangle est isocèle"
        
        - `a = 3, b = 4, c = 5` : "Le triangle n'est ni équilatéral ni isocèle"



## <span style="color:blue;">La boucle itérative for</span>



### Boucle `for` avec `range`

Une *boucle* **pour** permet de répéter un bloc d'instructions **un certain nombre de fois**.

```python
# Bloc pour
for i in range(n):
    # bloc d'instructions
```

Dans cette boucle, `i` prendra les valeurs de `0` à `n-1`. Toutes les instructions dans la boucle seront appliquées pour chaque valeur de `i`.

Dans cette structure, on connait à l'avance le nombre de répétitions. Dans notre cas, il est égal à `n`.

???+ question "Activité n°5 : ❤️ Boucle avec compteur i ❤️"

    Avec l'éditeur de script, **testez le code suivant :**

    

    ```python
    for i in range(11):
        print(i)
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Alors, que se passe-t-il ?**

        Le programme affiche les nombres de 0 à 10. La fonction `range(11)` génère une séquence de 11 nombres, allant de 0 à 10.

        **Explication :**
        - `i` commence à 0 et augmente de 1 à chaque itération.
        - Le bloc `print(i)` s'exécute à chaque itération.

_Remarque :_ On note `range(11)` pour indiquer que la boucle `print(i)` va s'exécuter 11 fois, mais `i` prendra toutes les valeurs entières entre `0` et `10` inclus.

???+ question "Activité n°6 : ❤️ Algorithme donnant une somme ❤️"

    Avec l'éditeur de script, **testez le code suivant :**

    

    ```python
    s = 0
    for i in range(11):
        s = s + i
    print(s)
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Alors, que se passe-t-il ?**

        Le programme affiche la somme des nombres de 0 à 10, soit 55.

        **Explication :**
        - La variable `s` est initialisée à 0.
        - À chaque itération, la valeur de `i` est ajoutée à `s`.
        - Finalement, `print(s)` affiche la somme totale.

_Remarque :_ Lors de l'instruction `for i in range(m, n)`, `i` prend toutes les valeurs entières entre `m` et `n-1`. Avec `for i in range(m, n, p)`, `i` prend les valeurs entre `m` et `n-1` en sautant de `p` à chaque fois.

Exemple : ❤️`for i in range(2, 10, 2)` donne `2, 4, 6, 8`❤️.

###  Boucle `for` avec `in`

```python
for elmt in iterable:
    # instructions
```

Dans cette boucle, `elmt` va parcourir les éléments de `iterable`. `iterable` peut être une chaîne de caractères ou une liste.

???+ question "Activité n°7 : ❤️ Boucle de parcours de chaîne ❤️.

    Avec l'éditeur de script, **testez le code suivant :**


    ```python
    ch = "Bonjour à tou.te.s"
    for elmt in ch:
        print(elmt)
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Que fait ce code ?**

        Il affiche chaque caractère de la chaîne `ch` un par un sur des lignes séparées.

        **Explication :**
        - La boucle `for` parcourt chaque caractère de la chaîne `ch`.
        - À chaque itération, `elmt` prend la valeur d'un caractère et l'affiche avec `print(elmt)`.

_Modifiez la chaîne pour tester d'autres phrases._

???+ question "A faire vous-même Activité n°8 :"

    Avec l'éditeur de script, **testez le code suivant :**

    

    ```python
    citation = "Je ne cherche pas à connaître les réponses, je cherche à comprendre les questions."
    compteur = 0
    for elt in citation:
        if elt == "e":
            compteur = compteur + 1
    print(compteur)
    ```
    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Que fait ce code ?**

        Il compte le nombre de fois que la lettre "e" apparaît dans la chaîne `citation` et affiche le résultat.

        **Explication :**
        - La boucle parcourt chaque caractère de la chaîne.
        - Si le caractère est un "e", le compteur est incrémenté de 1.

    **Transformer le code pour qu'il compte le nombre de "a" :**

    ??? success "Python"
        {{ IDE() }}
    
    ?? success "Solution"
        ```python
        compteur = 0
        for elt in citation:
            if elt == "a":
                compteur = compteur + 1
        print(compteur)
        ```

## <span style="color:blue;">Exercices sur la boucle for</span>

???+ question "Exercice 1 : Afficher les 100 premiers nombres entiers"

    Écrire un script qui permet d’afficher les 100 premiers nombres entiers NON NULS.

    ??? success "Python"
        {{ IDE() }}
    
    ??? success "Solution"
        ```python
        for i in range(1, 101):
            print(i)
        ```


        Ce code affiche les nombres de 1 à 100.

        **Explication :**
        - La boucle commence à 1 et s'arrête à 100.

???+ question "Exercice 2 : Calculer des sommes"

    Écrire un programme en Python pour calculer :

    - **a)** `1 + 2 + 3 + ... + 100`
    - **b)** `1 + 3 + 5 + ... + 99`

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        
        a)
        ```python
        somme = 0
        for i in range(1, 101):
            somme = somme + i
        print(somme)
        ```
        b)
        ```python
        somme_impairs = 0
        for i in range(1, 100, 2):
            somme_impairs = somme_impairs + i
        print(somme_impairs)
            ```

        **a)** Le programme affiche 5050.
        **b)** Le programme affiche 2500.

        **Explication :**
        - Pour **a)**, on additionne tous les nombres de 1 à 100.
        - Pour **b)**, on additionne tous les nombres impairs de 1 à 99.

???+ question "Exercice 3 : Construire une pyramide"

    Inès veut construire une pyramide à base carrée. La pyramide sur la photo a 7 étages.

    ![image de la pyramide](Image1.png)

    Écrire un programme en Python pour répondre au problème : Combien de billes faut-il pour une pyramide à 7 étages ? puis à 100 étages

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        Il suffit de modifier l'algorithme de somme que l'on a déjà vu
        ```python
        s = 0
        for i in range(11):
            s = s + i
        print(s)
        ```

        **Explication :**
        - Chaque étage est un carré de billes, donc on additionne les carrés des nombres de 1 à 7.

        ```python
        s = 0
        for i in range(1,8):
            s = s + i
        print(s)
        ```

        pour 100 étages on fait la même chose

        ```python
        s = 0
        for i in range(1,101):
            s = s + i
        print(s)
        ```

    **Modifier le programme pour que l'utilisateur puisse choisir le nombre d'étages :**

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"
        ```python
        etages = int(input("Entrez le nombre d'étages : "))
        s = 0
        for i in range(1, etages+1):
            s = s + i
        print(s)
        ```



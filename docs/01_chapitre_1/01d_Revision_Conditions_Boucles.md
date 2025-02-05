---
author: ELP
title: 01d Révision Les conditions et les boucles
---


## <span style="color:blue;">Programmer un ordinateur c'est quoi ?</span>

**Programmer**, c'est **créer des programmes** (suite d'ordres donnés à l'ordinateur). Un ordinateur sans programme ne sait rien faire.





## <span style="color:blue;">Débuter avec Basthon </span>
Dans un nouvel onglet du navigateur internet, aller sur [basthon.fr](https://basthon.fr) et choisir "Console".


1. Aller sur le site [Basthon](https://basthon.fr).
2. Choisir l'option "Console" pour exécuter du code Python.
3. Vous pouvez également utiliser l'éditeur de scripts pour écrire des programmes plus complexes.

## <span style="color:blue;">Affichage</span>

???+ question "Activité n° 1 :"

    Recopiez la ligne suivante dans l'éditeur de script exécutez-la :
    ```python
    print("Hello World!")
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        Lorsque vous exécutez ce script, le message "Hello World!" doit apparaître dans la console. Vous venez d'écrire votre premier programme en Python !
        
        Remarque : Vous pouvez utiliser des guillemets simples ou doubles pour délimiter les chaînes de caractères en Python.



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
        elif note >= 12:
            print("C’est bien")
        elif note > 0:
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



### <span style="color:blue;"> Exercices sur les conditions </span>

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

        if couleur == "bleu":
            if nombre > 20:
                print("C’est gagné")
            else:
                print("Presque")
        elif couleur == "rouge":
            if nombre > 10:
                print("Super")
            else:
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




    2. Modifier le programme pour qu'il indique si le triangle est **isocèle** ou pas.

     ??? success "Python"
        {{ IDE() }}
    
    ??? success "Solution"
        ```python
        if a == b or b == c or a == c:
            print("Le triangle est isocèle")
        else:
            print("Le triangle n'est pas isocèle")
        ```



    3. Modifier le programme pour qu'il indique si le triangle est **équilatéral**, et s'il ne l'est pas, vérifier s'il est **isocèle**.

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





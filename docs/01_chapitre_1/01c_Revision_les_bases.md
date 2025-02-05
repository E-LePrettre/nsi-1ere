---
author: ELP
title: 01c Révision Les bases
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

    {{ IDE() }}

    ??? success "Solution"

        Lorsque vous exécutez ce script, le message "Hello World!" doit apparaître dans la console. Vous venez d'écrire votre premier programme en Python !
        
        Remarque : Vous pouvez utiliser des guillemets simples ou doubles pour délimiter les chaînes de caractères en Python.


???+ question "Activité n° 2 :"

    Essayez d'écrire un programme qui affichera votre prénom à l'écran. Testez-le.

    {{ IDE() }}

    ??? success "Solution"

        Exemple de solution si votre prénom est Alice :
        ```python
        print("Alice")
        ```

 ## <span style="color:blue;">Les variables et les affectations</span>


Une **variable** est l'association d'un espace de la mémoire de l'ordinateur, accessible par son **nom**, et d'une **valeur** que l'on y **stocke**. En Python, l'affectation se réalise avec l'opérateur `=`.

```python
a = 5
```

Cela met en mémoire l'entier 5 dans la variable `a`.

```python
a = "easy"
```

Cela met en mémoire la chaîne de caractères "easy" dans la variable `a`.

???+ question "Activité n°3 :"

    Avec l'éditeur de script, **testez le code suivant :**

    ```python
    tartempion = 15
    print(tartempion)
    ```

    {{ IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        15
        ```

        L'instruction `print` permet **d'afficher la valeur contenue** dans la variable `tartempion`.

    **Modifier le code comme ceci :**

    ```python
    tartempion = 15
    print("tartempion")
    ```
    {{ IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        tartempion
        ```

        **Alors, que se passe-t-il ?**
        En plaçant `tartempion` entre guillemets, Python affiche la chaîne de caractères "tartempion" au lieu de la valeur de la variable.

???+ question "Activité n°4 :"

    Écrire un programme dans lequel on attribue la valeur 12 à la variable `moyenne`. La valeur de `moyenne` doit ensuite s'afficher à l'écran.

    {{ IDE() }}

    ??? success "Solution"

        ```python
        moyenne = 12
        print(moyenne)
        ```

        **Résultat :**
        ```
        12
        ```

## <span style="color:blue;">Faire des calculs</span>

???+ question "A faire vous-même Activité n°5 :"

    Que vaut `a` à la fin de ce script :

    ```python
    a = 1
    b = -1
    a = a * b
    a = a + b
    ```
    {{ IDE() }}

    ??? success "Solution"

        **Résultat :**
        Il faut rajouter print(a) à la fin du script et on obtient :
        ```
        -2
        ```

        **Explication :**
        - `a = 1 * -1` donne `a = -1`
        - `a = -1 + (-1)` donne `a = -2`

???+ question "Activité n° 6 : ❤️ Echange de valeurs entre 2 variables ❤️"

    Proposer un programme qui permet d'échanger les valeurs stockées dans les variables `a` et `b`.

    {{ IDE() }}

    ??? success "Solution"

        Utilisation d'une variable temporaire :
        ```python
        a = 8
        b = -3
        temp = a
        a = b
        b = temp
        print(a, b)
        ```
        Ce programme échangera les valeurs : `a` devient -3 et `b` devient 8.

        **Ou en Python plus simple :**

        ```python
        a, b = b, a
        print(a, b)
        ```


???+ question "Activité n°7 :"

    Compléter le programme suivant pour que la variable `total` contienne le résultat de la **division** de `dividende` par `diviseur`.

    ```python
    dividende = 13
    diviseur = 4
    total = dividende / diviseur
    print(total)
    ```
    { IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        3.25
        ```

???+ question "Activité n°8 :"

    La division précédente n'est pas entière. Pour faire calculer la division euclidienne, il faut utiliser `//`. Testez maintenant ce code :

    ```python
    a = 13
    b = 4
    resultat = a // b
    print(resultat)
    ```
    { IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        3
        ```

???+ question "Activité n°9 :"

    Pour faire calculer le reste de la division euclidienne, il faut utiliser `%`. Testez maintenant ce code :

    ```python
    a = 13
    b = 4
    resultat = a % b
    print(resultat)
    ```
    { IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        1
        ```

???+ question "Activité n°10 : Incrémentation d'une variable"

    **Que fait ce programme ?**

    ```python
    a = 11
    print(a)
    a = a + 1  # incrémentation de la variable a
    print(a)
    ```
    { IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        11
        12
        ```

        La variable `a` est incrémentée de 1, c'est-à-dire que sa valeur passe de 11 à 12.

## <span style="color:blue;">Affichage en Python</span>

???+ question "Activité n°11 :"

    **Tester :**

    ```python
    print("Vivement les vacances !")
    prenom = "Bob"
    print("Mon prénom est :", prenom)
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        Vivement les vacances !
        Mon prénom est : Bob
        ```

???+ question "A faire vous-même Activité n°12 :"

    Réalisez un script qui contient trois variables : `prenom`, `nom` et `age` et qui doit afficher :

    ```
    Bonjour je m'appelle Alphonse Dansletas, j'ai 358 ans.
    ```

    ??? success "Solution"

        ```python
        prenom = "Alphonse"
        nom = "Dansletas"
        age = 358
        print(f"Bonjour je m'appelle {prenom} {nom}, j'ai {age} ans.")
        ```

        **Résultat :**
        ```
        Bonjour je m'appelle Alphonse Dansletas, j'ai 358 ans.
        ```





???+ question "Activité n° 3 :"

    Attribuer la valeur 12 à la variable `moyenne` et afficher cette valeur.

    {{ IDE() }}

    ??? success "Solution"

        ```python
        moyenne = 12
        print(moyenne)
        ```
        Ce programme stocke la valeur 12 dans la variable `moyenne` et affiche cette valeur.

---

???+ question "Activité n° 4 :"

    Que vaut `a` à la fin de ce script ?
    ```python
    a = 1
    b = -1
    a = a * b
    a = a + b
    ```
    {{ IDE() }}

    ??? success "Solution"

        1. `a = 1`
        2. `b = -1`
        3. `a = 1 * -1` donc `a = -1`
        4. `a = -1 + (-1)` donc `a = -2`

        La valeur finale de `a` est -2.

---


---

???+ question "Activité n° 6 :"

    Compléter le programme suivant pour que la variable `total` contienne le résultat de la division de `dividende` par `diviseur`.
    ```python
    dividende = 13
    diviseur = 4
    ?
    print(total)
    ```
    {{ IDE() }}

    ??? success "Solution"

        ```python
        dividende = 13
        diviseur = 4
        total = dividende / diviseur
        print(total)
        ```
        Le programme affiche : `3.25`.

---

???+ question "Activité n° 7 :"

    Tester maintenant la division entière avec l'opérateur `//`.
    ```python
    a = 13
    b = 4
    resultat = a // b
    print(resultat)
    ```
    {{ IDE() }}

    ??? success "Solution"

        Ce programme affiche `3` car `//` effectue une division entière.

---

???+ question "Activité n° 8 :"

    Calculer le reste de la division euclidienne avec `%`.
    ```python
    a = 13
    b = 4
    resultat = a % b
    print(resultat)
    ```
    {{ IDE() }}

    ??? success "Solution"

        Ce programme affiche `1` car 13 divisé par 4 donne un reste de 1.

---

???+ question "Activité n° 9 :"

    Que fait ce programme ?
    ```python
    a = 11
    print(a)
    a = a + 1  # incrémentation de la variable a
    print(a)
    ```
    {{ IDE() }}

    ??? success "Solution"

        Le programme affiche :
        ```
        11
        12
        ```
        Il incrémente la valeur de `a` de 1.

---

???+ question "Activité n° 10 :"

    Réaliser un script qui contient trois variables : `prenom`, `nom` et `age` et qui doit afficher :
    "Bonjour je m'appelle Alphonse Dansletas, j'ai 358 ans."

    {{ IDE() }}

    ??? success "Solution"

        ```python
        prenom = "Alphonse"
        nom = "Dansletas"
        age = 358
        print("Bonjour je m'appelle", prenom, nom, ", j'ai", age, "ans.")
        ```

---

???+ question "Activité n° 11 :"

    Demander à l'utilisateur son prénom et l'afficher.
    ```python
    prenom = input("Quel est ton prénom ? ")
    print(prenom)
    ```
    {{ IDE() }}

    ??? success "Solution"

        Lorsque vous exécutez ce programme, il vous demande votre prénom et l'affiche ensuite.

---

???+ question "Activité n° 12 :"

    Ecrire un script qui demande à l'utilisateur son prénom, son nom et son âge, puis affiche :
    "Bonjour je m'appelle Alain Térieur, j'ai 217 ans."

    {{ IDE() }}

    ??? success "Solution"

        ```python
        prenom = input("Quel est ton prénom ? ")
        nom = input("Quel est ton nom ? ")
        age = input("Quel est ton âge ? ")
        print("Bonjour je m'appelle", prenom, nom, ", j'ai", age, "ans.")
        ```

---

???+ question "Activité n° 13 :"

    Créer un programme pour un boulanger qui demande le nombre de baguettes et affiche le prix total.

    {{ IDE() }}

    ??? success "Solution"

        Correction du script pour convertir l'entrée en entier :
        ```python
        nombre = int(input("Combien de baguettes désirez-vous ? "))
        prix = nombre * 1.1
        print("Vous avez à payer", prix, "euros.")
        ```

        Ce programme calcule le prix en fonction du nombre de baguettes achetées.

---

???+ question "Activité n° 14 :"

    Calculer le prix à payer pour une entrée dans un parc d'attraction en fonction du nombre d'adultes et d'enfants.

    {{ IDE() }}

    ??? success "Solution"

        ```python
        A = int(input("Combien d'adultes ? "))
        E = int(input("Combien d'enfants ? "))
        P = A * 21 + E * 13
        print("Le prix total à payer est", P, "euros.")
        ```

## Les chaines de caractères

???+ question "Activité n°17 :"
    
    Affichez des chaînes de caractères délimitées par des apostrophes et des guillemets.

    ```python
    a = 'une chaine délimitée par des apostrophes'
    print(a)                    

    b = "une chaine délimitée par des guillemets"
    print(b)
    ```

    ??? success "Solution"

        ```python
        une chaine délimitée par des apostrophes
        une chaine délimitée par des guillemets
        ```

???+ question "A faire vous-même Activité n°18 :"

    Faire afficher exactement :
    - C'est bientôt Noël
    - Bonjour se dit "Hello"

    ??? success "Solution"

        ```python
        print("C'est bientôt Noël")
        print('Bonjour se dit "Hello"')
        ```

        **Résultat :**
        ```
        C'est bientôt Noël
        Bonjour se dit "Hello"
        ```

## Opérateurs sur les chaînes de caractères

???+ question "Activité n°19 :"

    Testez l'appartenance d'un caractère dans une chaîne avec l'opérateur `in`.

    ```python
    chaine = 'Bonjour'

    print('b' in chaine)  # affichera False
    print('B' in chaine)  # affichera True
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        False
        True
        ```

        **Pourquoi ?**
        La recherche est sensible à la casse. 'b' minuscule n'est pas dans "Bonjour", tandis que 'B' majuscule l'est.

???+ question "Activité n°20 :"

    Concaténez deux chaînes de caractères avec l'opérateur `+`.

    ```python
    chaine1 = 'Bonjour'
    chaine2 = ' à tous.'

    print(chaine1 + chaine2)
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        Bonjour à tous.
        ```

???+ question "A faire vous-même Activité n°21 :"

    À partir de deux chaînes de caractères :
    - Aujourd'hui
    - se dit "Today"

    Faites afficher la phrase complète par concaténation.

    ??? success "Solution"

        ```python
        chaine1 = "Aujourd'hui"
        chaine2 = ' se dit "Today"'

        print(chaine1 + chaine2)
        ```

        **Résultat :**
        ```
        Aujourd'hui se dit "Today"
        ```

???+ question "Activité n°22 :"

    Utilisez la fonction `len` pour obtenir le nombre de caractères dans une chaîne.

    ```python
    chaine = 'Bonjour à tous.'

    print(len(chaine))  # affichera 15
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        15
        ```

        Les espaces et la ponctuation comptent également comme des caractères.

???+ question "Activité n°23 :"

    Lisez un caractère dans une chaîne avec `chaine[index]`.

    ```python
    chaine = 'Bonjour'

    print(chaine[0])   # B
    print(chaine[1])   # o
    print(chaine[-1])  # r
    print(chaine[-2])  # u
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        B
o
r
u
        ```

???+ question "A faire vous-même Activité n°24 :"

    À partir de :
    ```python
    chaine = 'Bonjour'
    ```
    Faire afficher **Bnu**.

    ??? success "Solution"

        ```python
        print(chaine[0] + chaine[2] + chaine[5])
        ```

        **Résultat :**
        ```
        Bnu
        ```

???+ question "Activité n°25 :"

    Utilisez le **slicing** pour lire une sous-chaîne avec `chaine[debut:fin:pas]`.

    ```python
    chaine = 'Bonjour'

    print(chaine[0:2])    # Bo
    print(chaine[2:5])    # njo
    print(chaine[:])      # Bonjour
    print(chaine[1:])     # onjour
    print(chaine[::2])    # Bnor
    print(chaine[::-1])   # ruojnoB
    ```

    ??? success "Solution"

        **Résultat :**
        ```
        Bo
njo
Bonjour
onjour
Bnor
ruojnoB
        ```

???+ question "A faire vous-même Activité n°26 :"

    À partir de :
    ```python
    a = "C'est bientôt Noël"
    ```

    Faire afficher :
    - bientôt
    - Csbnto
    - tôtneib
    - Noël
    - lëoN

    ??? success "Solution"

        ```python
        print(a[6:13])        # bientôt
        print(a[0] + a[2] + a[3] + a[6] + a[8] + a[10])  # Csbnto
        print(a[12:5:-1])    # tôtneib
        print(a[-4:])        # Noël
        print(a[-1::-1][:4]) # lëoN
        ```

        **Résultat :**
        ```
        bientôt
Csbnto
tôtneib
Noël
lëoN
        ```






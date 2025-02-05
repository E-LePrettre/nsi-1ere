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

    ??? success "Solution"

        Exemple de solution si votre prénom est Alice :
        ```python
        print("Alice")
        ```

???+ question "Faire ce qui est proposé"

    {{ IDE() }}


???+ question "Activité n° 5 :"

    Attribuer la valeur 12 à la variable `moyenne` et afficher cette valeur.

    ??? success "Solution"

        ```python
        moyenne = 12
        print(moyenne)
        ```
        Ce programme stocke la valeur 12 dans la variable `moyenne` et affiche cette valeur.

---

???+ question "Activité n° 6 :"

    Que vaut `a` à la fin de ce script ?
    ```python
    a = 1
    b = -1
    a = a * b
    a = a + b
    ```

    ??? success "Solution"

        1. `a = 1`
        2. `b = -1`
        3. `a = 1 * -1` donc `a = -1`
        4. `a = -1 + (-1)` donc `a = -2`

        La valeur finale de `a` est -2.

---

???+ question "Activité n° 7 :"

    Proposer un programme qui permet d'échanger les valeurs stockées dans les variables `a` et `b`.

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

---

???+ question "Activité n° 8 :"

    Compléter le programme suivant pour que la variable `total` contienne le résultat de la division de `dividende` par `diviseur`.
    ```python
    dividende = 13
    diviseur = 4
    ?
    print(total)
    ```

    ??? success "Solution"

        ```python
        dividende = 13
        diviseur = 4
        total = dividende / diviseur
        print(total)
        ```
        Le programme affiche : `3.25`.

---

???+ question "Activité n° 9 :"

    Tester maintenant la division entière avec l'opérateur `//`.
    ```python
    a = 13
    b = 4
    resultat = a // b
    print(resultat)
    ```

    ??? success "Solution"

        Ce programme affiche `3` car `//` effectue une division entière.

---

???+ question "Activité n° 10 :"

    Calculer le reste de la division euclidienne avec `%`.
    ```python
    a = 13
    b = 4
    resultat = a % b
    print(resultat)
    ```

    ??? success "Solution"

        Ce programme affiche `1` car 13 divisé par 4 donne un reste de 1.

---

???+ question "Activité n° 11 :"

    Que fait ce programme ?
    ```python
    a = 11
    print(a)
    a = a + 1  # incrémentation de la variable a
    print(a)
    ```

    ??? success "Solution"

        Le programme affiche :
        ```
        11
        12
        ```
        Il incrémente la valeur de `a` de 1.

---

???+ question "Activité n° 12 :"

    Réaliser un script qui contient trois variables : `prenom`, `nom` et `age` et qui doit afficher :
    "Bonjour je m'appelle Alphonse Dansletas, j'ai 358 ans."

    ??? success "Solution"

        ```python
        prenom = "Alphonse"
        nom = "Dansletas"
        age = 358
        print(f"Bonjour je m'appelle {prenom} {nom}, j'ai {age} ans.")
        ```

---

???+ question "Activité n° 13 :"

    Demander à l'utilisateur son prénom et l'afficher.
    ```python
    prenom = input("Quel est ton prénom ? ")
    print(prenom)
    ```

    ??? success "Solution"

        Lorsque vous exécutez ce programme, il vous demande votre prénom et l'affiche ensuite.

---

???+ question "Activité n° 14 :"

    Ecrire un script qui demande à l'utilisateur son prénom, son nom et son âge, puis affiche :
    "Bonjour je m'appelle Alain Térieur, j'ai 217 ans."

    ??? success "Solution"

        ```python
        prenom = input("Quel est ton prénom ? ")
        nom = input("Quel est ton nom ? ")
        age = input("Quel est ton âge ? ")
        print(f"Bonjour je m'appelle {prenom} {nom}, j'ai {age} ans.")
        ```

---

???+ question "Activité n° 15 :"

    Créer un programme pour un boulanger qui demande le nombre de baguettes et affiche le prix total.

    ??? success "Solution"

        Correction du script pour convertir l'entrée en entier :
        ```python
        nombre = int(input("Combien de baguettes désirez-vous ? "))
        prix = nombre * 1.1
        print("Vous avez à payer", prix, "euros.")
        ```

        Ce programme calcule le prix en fonction du nombre de baguettes achetées.

---

???+ question "Activité n° 16 :"

    Calculer le prix à payer pour une entrée dans un parc d'attraction en fonction du nombre d'adultes et d'enfants.

    ??? success "Solution"

        ```python
        A = int(input("Combien d'adultes ? "))
        E = int(input("Combien d'enfants ? "))
        P = A * 21 + E * 13
        print(f"Le prix total à payer est {P} euros.")
        ```





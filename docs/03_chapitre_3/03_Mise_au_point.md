---
author: ELP
title: 03 Mise au point des scripts et gestion des exceptions
---


**Table des matières**

1. [Les bonnes pratiques : documenter les fonctions ](#_page0_x40.00_y447.92)
2. [Les tests](#_page1_x40.00_y350.92)
3. [Les préconditions et les postconditions](#_page5_x40.00_y567.92)
4. [Les bibliothèques ou modules](#_page6_x40.00_y233.92)
5. [Gestion des exceptions](#_page9_x40.00_y401.92)
6. [Exercices](#_page13_x40.00_y375.92)

## **<H2 STYLE="COLOR:BLUE;">1.  Les bonnes pratiques : <a name="_page0_x40.00_y447.92"></a>documenter les fonctions</h2>** 

### **<H3 STYLE="COLOR:GREEN;">1.1. Qu’est-ce qu’une docstring ?</h3>**

Une **docstring** est un texte placé juste après l’en-tête d’une fonction en Python. Elle sert à expliquer :

1. **Ce que fait la fonction** ;

2. **Comment l’utiliser** (informations sur les paramètres et le résultat attendu) ;

3. **Les conditions d’utilisation pour éviter les erreurs**.

Elle est essentielle pour rendre le code **plus lisible** et **plus compréhensible**.




### **<H3 STYLE="COLOR:GREEN;">1.2. Comment écrire une docstring ?</h3>**

???+ question "Activité n°1 : Ajouter une docstring"

    **Tester :**

    ```python
    def factorielle(n):
        """
        Fonction qui retourne la factorielle d'un nombre.
        :param n: int
        :return: int
        CU (conditions d'utilisation) : n >= 0
        >>> factorielle(0)
        1
        >>> factorielle(4)
        24
        """
        resultat = 1
        for i in range(2, n + 1):
            resultat = resultat * i
        return resultat
    ```

    **Exécuter :**
    
    ```python
    help(factorielle)
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Résultat :**
        ```
        Help on function factorielle in module __main__:

        factorielle(n)
            Fonction qui retourne la factorielle d'un nombre.
            :param n: int
            :return: int
            CU (conditions d'utilisation) : n >= 0
            >>> factorielle(0)
            1
            >>> factorielle(4)
            24
        ```

    **Explication :**

    - La **docstring** est affichée avec la commande `help(factorielle)`.

    - Elle décrit clairement **l’objectif** et **les conditions d’utilisation**.




## **<H2 STYLE="COLOR:BLUE;">2. Les<a name="_page1_x40.00_y350.92"></a> tests</h2>** 

Les tests permettent de **vérifier** qu’un programme ne produit pas d’erreur et qu’il effectue bien la tâche attendue.
  

### **<H3 STYLE="COLOR:GREEN;">2.1. Les<a name="_page1_x40.00_y523.92"></a> tests simples avec assert</h3>**

L’instruction `assert` est utilisée pour **vérifier rapidement** que le programme fonctionne correctement.

???+ question "Activité n°2 : Vérifier une fonction avec `assert`"

    **Tester :**

    ```python
    def carre(x):
        return x * x

    assert carre(3) == 9  # Vérifie que le carré de 3 est bien 9
    assert carre(0) == 0  # Vérifie que le carré de 0 est bien 0
    assert carre(-2) == 4 # Vérifie que le carré de -2 est bien 4
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Résultat :** *(Aucune sortie si tout est correct !)*

    **Explication :**

    - Si **tous les tests passent**, le programme continue.

    - Si **un test échoue**, Python affiche une **erreur** et s’arrête.



???+ question "Activité n°3 : Vérifier une division euclidienne"

    **Tester :**

    ```python
    def division_euclidienne(a, b):   
        if a >= 0 and b > 0 and type(a) == int and type(b) == int:   
            return a // b, a % b   # Quotient et reste
        else:   
            return -1   # Code d'erreur si les valeurs ne sont pas correctes

    if __name__ == '__main__':
        assert division_euclidienne(10, 2) == (5, 0)
        assert division_euclidienne(-10, 7) == -1
        assert division_euclidienne(10.3, 4) == -1
        assert division_euclidienne(3, 0) == -1
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Explication :**

        - `assert` teste plusieurs cas et arrête le programme **si un test échoue**.

        - La condition `if __name__ == '__main__':` garantit que ces tests ne s’exécutent **que si le fichier est exécuté directement**.

???+ question "Activité n°3 : Vérifier une division euclidienne"

    **Tester :**

    ```python
    def division_euclidienne(a, b):   
        if a >= 0 and b > 0 and type(a) == int and type(b) == int:   
            return a // b, a % b   # Quotient et reste
        else:   
            return -1   # Code d'erreur si les valeurs ne sont pas correctes

    if __name__ == '__main__':
        assert division_euclidienne(10, 2) == (5, 1)
        assert division_euclidienne(-10, 7) == -1
        assert division_euclidienne(10.3, 4) == -1
        assert division_euclidienne(3, 0) == -1
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Explication :**

        assert division_euclidienne(10, 2) == (5, 1)  # Test invalide, Python montre une erreur, car le reste de `10 divisé par 2` est `0` et non `1`.


   


### **<H3 STYLE="COLOR:GREEN;">2.2. Les<a name="_page2_x40.00_y650.92"></a> tests avec doctest</h3>** 



`doctest` permet de **vérifier automatiquement** que les exemples donnés dans la docstring sont corrects.

???+ question "Activité n°4 : Tester avec `doctest`"

    **Tester :**

    ```python
    import doctest

    def factorielle(n):
        """
        Fonction qui retourne la factorielle d'un nombre.
        :param n: int
        :return: int
        CU (conditions d'utilisation) : n >= 0

        >>> factorielle(0)
        1
        >>> factorielle(4)
        24
        """
        resultat = 1
        for i in range(2, n + 1):
            resultat = resultat * i
        return resultat

    doctest.testmod()
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Explication :**
        - `doctest` recherche les **triples chevrons `>>>`** dans la docstring.
        - Il exécute les exemples et compare le **résultat attendu** et **le résultat réel**.
        - Si tout est correct, **rien ne s’affiche**.

---

???+ question "Activité n°5 : Introduire une erreur dans `doctest`"

    **Tester :**

    ```python
    import doctest

    def factorielle(n):
        """
        Fonction qui retourne la factorielle d'un nombre.
        :param n: int
        :return: int
        CU (conditions d'utilisation) : n >= 0

        >>> factorielle(0)
        100000  # ERREUR VOLONTAIRE
        >>> factorielle(4)
        24
        """
        resultat = 1
        for i in range(2, n + 1):
            resultat = resultat * i
        return resultat

    doctest.testmod()
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Explication :**
        - Doctest va signaler une erreur, car `factorielle(0)` ne renvoie **pas** `100000`.
        - C’est une **façon rapide de vérifier** si les résultats des tests sont corrects.

---

???+ question "Activité n°6 : Activer le mode `verbose` dans `doctest`"

    **Tester :**

    ```python
    import doctest

    def factorielle(n):
        """
        Fonction qui retourne la factorielle d'un nombre.
        :param n: int
        :return: int
        CU (conditions d'utilisation) : n >= 0

        >>> factorielle(0)
        1
        >>> factorielle(4)
        24
        """
        resultat = 1
        for i in range(2, n + 1):
            resultat = resultat * i
        return resultat

    doctest.testmod(verbose=True)
    ```

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **Explication :**
        - En mode **verbose**, doctest affiche **tous les tests**, qu’ils réussissent ou échouent.
        - **Utile pour voir ce qui est testé**.



### **<H4 STYLE="COLOR:fuchsia;">2.2.2. Pourquoi utiliser doctest ?</h4>**

Doctest est utile car il :

- **Vérifie automatiquement** que les exemples de la docstring donnent les bons résultats ;

- **Aide à repérer rapidement les erreurs** dans le code ;

- Permet d’**écrire des tests directement dans la docstring**, ce qui rend le code et ses tests plus faciles à lire et à comprendre.

### **<H4 STYLE="COLOR:fuchsia;">2.2.3. Exemple d’utilisation de doctest</h4>**

Prenons la fonction **factorielle** avec des exemples de tests dans la docstring :

**<H3 STYLE="COLOR:red;">Activité n° 5.:</H3>** 

```python
def factorielle(n):
   """
   Fonction qui retourne la factorielle d'un nombre.
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0

   >>> factorielle(0)
   1
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n + 1):
      resultat = resultat * i
   return resultat

# Pour exécuter les tests, il suffit d’écrire :

import doctest
doctest.testmod()
```

doctest vérifie que les valeurs données en exemple renvoient bien les résultats attendus.

**TESTER l'activité** [ALLER SUR BASTHON](https://console.basthon.fr/)


Lorsque tous les tests réussissent, doctest ne renvoie aucun message. Cela peut être surprenant, mais c’est un bon signe : cela signifie que tout est correct.

### **<H4 STYLE="COLOR:fuchsia;">2.2.4. Introduire une erreur pour observer doctest</h4>**

Si on introduit une erreur volontaire dans la docstring, doctest signale cette erreur. Par exemple :

**<H3 STYLE="COLOR:red;">Activité n° 6.:</H3>** 

```python
def factorielle(n):
   """
   Fonction qui retourne la factorielle d'un nombre.
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0

   >>> factorielle(0)
   100000000000000  # Fausse valeur pour tester doctest
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n + 1):
      resultat = resultat * i
   return resultat

import doctest
doctest.testmod()
```

**TESTER l'activité** [ALLER SUR BASTHON](https://console.basthon.fr/)

**Doctest signale l’erreur** et montre quel résultat était attendu et quel résultat a été trouvé.

### **<H4 STYLE="COLOR:fuchsia;">2.2.5. Activer le mode verbose</h4>**

Par défaut, doctest ne montre rien si tous les tests réussissent. Si on veut voir les tests même en cas de succès, on peut ajouter `verbose=True` dans `testmod` :

**<H3 STYLE="COLOR:red;">Activité n° 7.:</H3>** 

```python
def factorielle(n):
   """
   Fonction qui retourne la factorielle d'un nombre.
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0

   >>> factorielle(0)
   1
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n + 1):
      resultat = resultat * i
   return resultat


import doctest
doctest.testmod(verbose=True)
```

**TESTER l'activité** [ALLER SUR BASTHON](https://console.basthon.fr/)

En mode verbose, doctest affiche chaque test, qu’il réussisse ou échoue.




La  fonction testmod du module doctest est  allée  chercher  dans  les docstring des  fonctions  du  module actuellement chargé,  tous les exemples (reconnaissables à la présence des triples chevrons >>>   **à mettre un espace après** ), et a vérifié que la fonction documentée satisfait bien ces exemples. Dans le cas présent, une seule fonction dont la documentation contient deux exemples (attempted = 2 ) a été testée, et il n’y a eu aucun échec (failed  = 0 )  






## **<H2 STYLE="COLOR:BLUE;">3. Les<a name="_page5_x40.00_y567.92"></a> préconditions et les postconditions</h2>** 

Les assertions sont utilisées pour vérifier un résultat lorsque le test se fait, **test par test**. Donc un seul test à la fois. 

Mais les assertions peuvent aussi être dans le programme **pour vérifier tous les résultats** 



 **<H3 STYLE="COLOR:red;">Activité n° 8. : Utilisation de l’assertion dans une fonction</H3>**  

```python
from math import sqrt

def square_root(x):     # racine carrée ...
    assert x >= 0     # on veut ici être sur que x est positive ou nul avant tout calcul
    racine = sqrt(x)
    assert racine**2 == x # on vérifie qu'on a bien trouvé la racine carrée
    return racine
```

Tester
```python
print(square_root(25))
print(square_root(-25))
``` 

La ligne assert x >=0 s’appelle une **précondition**, puisqu’elle est appelée au début de la fonction et vérifie les propriétés des arguments passés dans la fonction  
La ligne assert solution \*\*2 == x s’appelle une **postcondition**, puisqu’elle et appelée juste avant le retour.  
Les préconditions et les postconditions permettent de trouver très rapidement les bugs.   

Pour plus de précisions :[ https://www.youtube.com/watch?v=DRVoh5XiAZo ](https://www.youtube.com/watch?v=DRVoh5XiAZo)

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

## **<H2 STYLE="COLOR:BLUE;">4. Les<a name="_page6_x40.00_y233.92"></a> bibliothèques ou modules</h2>** 
### **<H3 STYLE="COLOR:GREEN;">4.1. Qu’est<a name="_page6_x40.00_y255.92"></a> ce que c’est ?</h3>** 

Une bibliothèque en Python est un fichier contenant du **code réutilisable**. Ce code peut être sous forme de fonctions, classes ou variables. Pour utiliser une bibliothèque, on doit **l’importer** dans notre programme. 

Une bibliothèque est une **collection de modules**. C'est un ensemble plus large qui peut contenir **plusieurs fichiers** Python, **chacun étant un module**.

### **<H3 STYLE="COLOR:GREEN;">4.2. Importer des bibliothèques (modules) standards<a name="_page6_x40.00_y498.92"></a>r</h3>** 

Voici un exemple d’utilisation d’une bibliothèque Python standard, le module ```math``` qui contient des fonctions mathématiques comme sqrt() (racine carrée) ou ```random``` qui contient randint.
On peut noter les 2 manières d’importer le module : 

- import nom_du_module 

- from nom_du_module import nom_de_la_fonction


```
>>> import math as m
>>> m.sqrt(25) 

>>> import math
>>> math.sqrt(25) 

>>> from math import sqrt
>>> m.sqrt(25) 

>>> import random 
>>> x = random.randint(0,10)  

>>> from random import randint 
>>> randint(0,10) 

>>> from random import * 
>>> randint(0,10) 
>>> randrange(10,20,3) #retourne un entier entre 10 et 19 et un pas =3 
```
Tester 
???+ question "Faire ce qui est proposé"

    {{ IDE() }} 




  
## **<H2 STYLE="COLOR:BLUE;">5. Gestion<a name="_page9_x40.00_y401.92"></a> des exceptions</h2>** 

Ce sont les erreurs que peut rencontrer Python en exécutant le programme. Ces erreurs peuvent être **interceptées** très facilement et dans certains cas indispensables. 

### **<H3 STYLE="COLOR:GREEN;">5.1. Lever<a name="_page9_x40.00_y467.92"></a> d’exception</h3>** 

Quand Python rencontre une erreur dans le code, il lève **une exception**.  



**<H3 STYLE="COLOR:red;">Activité n° 9. :</H3>**Tester  

> 1/0 
  
  
On obtient deux informations :  
-  ZeroDivisionError : le type de l’exception  
-  division by zero : le message qu’envoie Python pour aider à comprendre l’erreur qui vient de se produire.  

A chaque fois qu’il y a une levée d’exception, Python **arrête** l’exécution du programme. Si on teste le programme en faisant un double-clic directement dans l'explorateur, il va se fermer tout de suite (en fait, il affiche bel et bien l'erreur mais se referme aussitôt). 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

### **<H3 STYLE="COLOR:GREEN;">5.2. Gestions<a name="_page9_x40.00_y734.92"></a> des exceptions</h3>**

Il  est  possible  de  gérer  les  exceptions  pour  éviter  l’arrêt  brutal  du  programme.  Pour  cela,  on  utilise conjointement les instructions try et except. 

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.1. Forme<a name="_page10_x40.00_y106.92"></a> minimale du bloc try</h4>**

Syntaxe : 

```
try: 
   # Bloc à essayer 
except: 
   # Bloc qui sera exécuté en cas d'erreur
```

**TRÈS UTILISÉS AUSSI** 



**<H3 STYLE="COLOR:red;">Activité n° 10. :</H3>**On suppose que l’utilisateur entre une année. Ici il peut fournir une valeur impossible à convertir en entier.  
  
```python
annee = input('Entrer une année ')  
try: # On essaye de convertir l'année en entier  
   annee = int(annee)
   print("Pas de problème.")  
except:  
   print("Erreur lors de la conversion de l'année.")
```  
  
Si l'utilisateur saisit une année impossible à convertir, le système affiche certes **une erreur** mais finit par **planter** (puisque l'année, au final, n'a pas été convertie).   
Une des solutions envisageables est d'attribuer **une valeur par défaut** à l'année, en cas d'erreur, ou de redemander à l'utilisateur de saisir l'année.  

Tester:

- avec  => 2024

- relancer le programme et tester avec => nous sommes en 2024
 
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

Ensuite et surtout, **cette méthode est assez grossière** : elle essaye une instruction et **intercepte n'importe quelle exception** liée à cette instruction. Ici, c'est acceptable car nous n'avons pas énormément d'erreurs possibles sur cette instruction. Mais c'est une **mauvaise habitude. On va voir une méthode plus fine dans la suite.** 

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.2. Interception<a name="_page10_x40.00_y547.92"></a> d’exceptions particulières</h4> Dans le cas d’une division :** 

resultat = numerateur / denominateur 

Ici plusieurs erreurs sont susceptibles d’intervenir, chacune levant une exception différente. 

- TypeError : l’une des variables *numerateur* ou *denominateur*  n’a peut diviser ou être divisée (les chaines de caractères ne peuvent être divisées, ni diviser d’autres types) 
- ZeroDivisionError* : si *denominateur* vaut 0. 



 **<H3 STYLE="COLOR:red;">Activité n°11. :</H3>**On peut ainsi intercepter ces erreurs possibles à l’exécution du code  

```python 
numerateur = input('Numérateur ?')  
denominateur = input('Dénominateur ?')  

try:  
   resultat = int(numerateur) / int(denominateur)   
except ValueError:   
   print("La variable numérateur ou dénominateur possède un type incompatible avec la division.")   
except ZeroDivisionError:    
   print("La valeur entrée au dénominateur est égale à 0.")   
```  
Tester avec 

- 20 et 0 

- relancer le programme et tester avec => 20 et 'a'

- relancer le programme et tester avec => 'a' et 3

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.3. Le<a name="_page11_x40.00_y338.92"></a> bloc try/except et les mots clés else et finally</h4>**



**<H3 STYLE="COLOR:red;">Activité n°12. :</H3>**L’instruction else se déroule **s’il n’y a pas d’exceptions** de lever   

```python 
numerateur = input('Numérateur ?')   
denominateur = input('Dénominateur ?')   

try:   
   resultat = int(numerateur) / int(denominateur)   
except ValueError:   
   print("La variable numérateur ou dénominateur possède un type incompatible avec la division.")   
except ZeroDivisionError as division_par_zero : # ici on renomme l’exception   
   print("La valeur entrée au dénominateur est égale à 0.")   
else:   
   print("Le résultat obtenu est", resultat)   
```  
   
Dans les faits, on utilise assez peu else. La plupart des codeurs préfère mettre la ligne contenant le print directement dans le bloc try. 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**<H3 STYLE="COLOR:red;">Activité n°13. :</H3>**L’instruction finally permet d'exécuter du code après un bloc try, **quel que soit le résultat** de l'exécution du bloc. 

```python
numerateur = input('Numérateur ?')  
denominateur = input('Dénominateur ?')  

try:   
   resultat = int(numerateur) / int(denominateur)   
except ValueError:   
   print("La variable numérateur ou dénominateur possède un type incompatible avec la division.")   
except ZeroDivisionError as division_par_zero : # ici on renomme l’exception   
   print("La valeur entrée au dénominateur est égale à 0.")   
else:   
   print("Le résultat obtenu est", resultat)   
finally:   
   print('Ligne qui sera toujours affichée')   
```   
Tester avec:

- 20 et 4

- relancer le programme et tester avec => 20 et 0

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.4. Avec<a name="_page12_x40.00_y346.92"></a> les assertions</h4>**

L’utilisation de* assert* permet de faire des tests Si le test renvoie True*,* l’exécution se poursuit normalement. Sinon, une exception AssertionError* est levée. 

**<H3 STYLE="COLOR:red;">Activité n°14. :</H3>**Dans le programme testant si une année est bissextile, on pourrait vouloir s’assurer que l’utilisateur ne  saisit pas une année inférieure ou égale à 0 par exemple : 

```python
annee = input("Saisissez une année supérieure à 0 :")   
try:   
   annee = int(annee) # Conversion de l'année   
   assert annee > 0   
except ValueError:   
   print("Vous n'avez pas saisi un nombre entier.")   
except AssertionError:   
   print("L'année saisie est inférieure ou égale à 0.")   
```  
Tester avec :

- 2000

- relancer le programme et tester avec => 'a'

- relancer le programme et tester avec => -1999


???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.5. Déclencher<a name="_page12_x40.00_y748.92"></a> une exception</h4>**

L’instruction raise permet au programmeur de déclencher une exception spécifique.

**<H3 STYLE="COLOR:red;">Activité n°15. :</H3>**Si l’utilisateur entre une année trop grande par exemple supérieure à 3000, on peut estimer qu’il s’agit d’une erreur 

```python
annee = input("Saisissez une année supérieure à 0 :")   
try:   
   annee = int(annee) # Conversion de l'année   
   if annee >=3000 or annee < 0:   
      raise ValueError   
except ValueError:   
   print("L'année entrée n'est pas dans l'intervalle [0, 2999]")   
except AssertionError:   
   print("L'année saisie est inférieure ou égale à 0.")
```   
Tester avec :

- 3000   
   
N’oubliez pas : un programme bien écrit doit **gérer proprement les exceptions.** 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}
    
## **<H2 STYLE="COLOR:BLUE;">6. Exercices<a name="_page13_x40.00_y375.92"></a></h2>** 
=> **CAPYTALE Le code vous sera donné par votre enseignant**

**<H3 STYLE="COLOR:red;">Exercice 1 :</H3>** On considère la fonction multiplier_par_deux(x) qui prend en paramètre x et qui renvoie son double. Ecrire un script de cette fonction avec : 


- Sa documentation dans le docstring comme dans le cours. Ne pas mettre d’exemples 

- 4 tests en assert  : avec 0, avec -1, avec 3.2 et avec ‘a’ 



**<H3 STYLE="COLOR:red;">Exercice 2:</H3>** : On considère une fonction somme_carres(x) qui prend en paramètre x (entier strictement positif) et renvoie la somme des x premiers carrés non nuls.  

Ecrire un script de cette fonction avec : 


- Sa documentation dans le docstring comme dans l’activité 1. Ne pas mettre d’exemples 

- 3 tests en assert (comme dans l’activité 3) : avec 1, avec 2 et avec 3 



**<H3 STYLE="COLOR:red;">Exercice 3:</H3>** : La fonction précédente à pour condition d’utilisation : x doit être strictement positif. Déclencher une exception et capturer là si le nombre entrée est 0 ou négatif. 

Exemple : 
```
>>> somme_carres(5)
55

>>> somme_carres(0)
Le nombre entré est nul ou négatif

>>> somme_carres(-2)
Le nombre entré est nul ou négatif
```



**<H3 STYLE="COLOR:red;">Exercice 4 :</H3>** On part du script suivant qui permet d’inverser un nombre 

```python
try:
    chaine = input('Entrer un nombre : ') # permet de pouvoir gérer l’exception ValueError
    nombre = float(chaine)
    inverse = 1.0/nombre
except ValueError:
    #ce bloc est exécuté si une exception de type ValueError est levée dans le bloc try
    print(chaine, "n'est pas un nombre !")

except ZeroDivisionError:
#ce bloc est exécuté si une exception de type ZeroDivisionError est levée dans le bloc try
    print("Division par zéro !")
else:
    #on arrive ici si aucune exception n'est levée dans le bloc try
    print("L'inverse de", nombre, "est :", inverse) 
```


Compléter le script précédent de manière à ressaisir le nombre en cas d’erreur. On pourra englober le script dans une boucle while. Par exemple : 

Tester avec :

- 'a'

- relancer le programme et tester avec => 'salut !'

- relancer le programme et tester avec => 0

- relancer le programme et tester avec => 2

Aide : penser à une boucle infinie et au mot clé break.  

**<H3 STYLE="COLOR:red;">Exercice 5 :</H3>** Ecrire un script qui calcule la racine carrée d’un nombre, avec gestion des exceptions. Utiliser la fonction sqrt() du module math.  

Par exemple : 
``` 
Entrer un nombre : >? go
go n'est pas un nombre valide !
Entrer un nombre : >? -5.26
-5.26 n'est pas un nombre valide !
Entrer un nombre : >? 16
La racine de  16.0 est : 4.0
```

Tester avec :

- "go"

- relancer le programme et tester avec => -5.26

- relancer le programme et tester avec => 16

Remarquez bien qu’on demande le nombre à l’utilisateur *jusqu'à* ce qu’il convienne. 

[Documentation sur les exceptions ](http://docs.python.org/3/tutorial/errors.html#exceptions)
Source :[ Fabrice Sincère ](http://fsincere.free.fr/isn/python/cours_python_ch5.php)-[ Contenu sous licence CC BY-NC-SA 3.0 ](http://creativecommons.org/licenses/by-nc-sa/3.0/fr/)

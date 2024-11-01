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

Une **docstring** est un texte placé juste après l’en-tête d’une fonction en Python. Elle sert à expliquer clairement :

1. **Ce que fait la fonction** ;

2. **Comment l’utiliser** (avec des informations sur les paramètres et le résultat attendu) ;

3. **Les conditions à respecter pour éviter des erreurs**.

C’est une façon de **documenter** le code, c’est-à-dire de rendre les fonctions plus faciles à comprendre pour les autres (et pour soi-même, si on revient sur le code plus tard !).

### **<H3 STYLE="COLOR:GREEN;">1.2. Pourquoi utiliser une docstring ?</h3>**

Quand on écrit une fonction, les autres utilisateurs (ou même nous plus tard) peuvent se demander : 

- « Cette fonction fait quoi ? »

- « Qu’est-ce que je dois donner comme valeurs pour que la fonction fonctionne ? »

- « Qu’est-ce que la fonction va me renvoyer comme résultat ? »

La docstring répond à ces questions directement, **sans avoir à lire le code**. Elle est comme une fiche technique qui aide à comprendre la fonction plus vite.

### **<H3 STYLE="COLOR:GREEN;">1.3. Comment écrire une docstring ?</h3>**

Une docstring se met **entre triples guillemets** `"""` juste après le nom de la fonction. 


**<H3 STYLE="COLOR:red;">Activité n° 1.:</H3>** Exemple de documentation de fonctions que l’on obtient dans l’aide de la fonction 

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0
   >>> factorielle(0)
   1
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n+1):
      resultat = resultat * i
   return resultat
```
### **<H3 STYLE="COLOR:GREEN;">1.4. Comment voir la docstring d’une fonction ?</h3>**

On peut voir la docstring en utilisant la commande **help(nom_de_la_fonction)**. Par exemple :

```python
help(factorielle)
```

Cette commande affichera directement la description de la fonction, les paramètres, la valeur de retour, et les exemples si la docstring est bien écrite.

 
**TESTER l'activité 1 ET help(factorielle)** [ALLER SUR BASTHON](https://console.basthon.fr/)

### **<H3 STYLE="COLOR:GREEN;">1.5. Résumé</h3>**

Réaliser une telle chaîne de documentation permet 

**à l’utilisateur** de la fonction de savoir

- à quoi peut servir la fonction ; 

- comment il peut l’utiliser ; 

- et quelles conditions il doit respecter pour l’utiliser (CU). 

et **au programmeur** de la fonction de préciser 

- le nombre et la nature de ses paramètres ; 

- la relation entre la valeur renvoyée et celle du ou des paramètres ; 

- ses idées avec quelques exemples. 

## **<H2 STYLE="COLOR:BLUE;">2. Les<a name="_page1_x40.00_y350.92"></a> tests</h2>** 

Pour vérifier si un programme ne produit pas d’erreur au cours de son exécution et s’il effectue réellement la tâche que l’on attend de lui, une première méthode consiste à exécuter plusieurs fois ce programme, en lui fournissant des entrées, **appelées tests**, qui servent à **détecter les erreurs éventuelles**.   

### **<H3 STYLE="COLOR:GREEN;">2.1. Les<a name="_page1_x40.00_y523.92"></a> tests simples avec assert</h3>**

#### **<H4 STYLE="COLOR:fuchsia;">2.1.1. Qu’est-ce que `assert` ?</h4>**

L'instruction **`assert`** est une manière rapide de **vérifier qu’un programme fait exactement ce qu’on attend**. Elle permet de tester si une condition est vraie. Si elle est fausse, Python arrête le programme et signale une erreur. En somme, `assert` est une sorte de "gardien" : il vérifie que tout se passe comme prévu.

### **<H4 STYLE="COLOR:fuchsia;">2.1.2. Pourquoi utiliser `assert` ?</h4>**

Lorsqu’on écrit une fonction, on veut souvent vérifier que le résultat est correct pour certaines valeurs. Par exemple :
- Si on écrit une fonction d’addition, on veut être sûr que `addition(2, 3)` renvoie bien `5`.
- `assert` permet de tester rapidement plusieurs cas, pour vérifier qu’il n’y a pas de problème.

### Comment utiliser `assert` ?

`assert` s’écrit sous la forme :
```python
assert condition
```

1. **Condition** : On écrit ce qu’on souhaite vérifier. Par exemple, `assert 2 + 2 == 4` vérifie que 2 + 2 fait bien 4.
2. **Action de `assert`** : Si la condition est vraie, le programme continue comme prévu. Mais si elle est fausse, Python arrête le programme et montre une erreur.

### Exemple simple avec `assert`

Voici un exemple pour illustrer :
```python
def carre(x):
    return x * x

# Test avec assert
assert carre(3) == 9  # Vérifie que le carré de 3 est bien 9
assert carre(0) == 0  # Vérifie que le carré de 0 est bien 0
assert carre(-2) == 4 # Vérifie que le carré de -2 est bien 4
```

Dans cet exemple, `assert` s’assure que le résultat de chaque test est correct :
- **carre(3) == 9** est vrai, donc le programme continue.
- Si on écrivait **assert carre(3) == 8**, Python s’arrêterait, car le carré de 3 n’est pas 8, et il signalerait une erreur.

### Pourquoi est-ce utile ?

`assert` est utile parce qu’il permet de **tester rapidement des fonctions** :
- En testant plusieurs cas d’utilisation, on peut voir si la fonction renvoie les bonnes valeurs.
- En cas d’erreur, `assert` aide à repérer d’où vient le problème (le programme s’arrête là où le test échoue).

### Cas concret avec `division_euclidienne`

Prenons l’exemple de la fonction **`division_euclidienne`** pour tester la division entière et le reste :

```python
def division_euclidienne(a, b):   
    if a >= 0 and b > 0 and type(a) == int and type(b) == int:   
        return a // b, a % b   # Quotient et reste
    else:   
        return -1   # Code d'erreur si les valeurs ne sont pas correctes
```

Et les tests avec `assert` :
```python
if __name__ == '__main__':
    assert division_euclidienne(10, 2) == (5, 0)  # Test valide
    assert division_euclidienne(-10, 7) == -1     # Test d'erreur (négatif)
    assert division_euclidienne(10.3, 4) == -1    # Test d'erreur (nombre décimal)
    assert division_euclidienne(3, 0) == -1       # Test d'erreur (division par zéro)
```

### Que faire si un test échoue ?

Si un **assert échoue**, le programme s’arrête, et tu sais exactement où ça a échoué. Par exemple :
- Si **`assert division_euclidienne(10, 2) == (5, 1)`** échoue, Python montre une erreur, car le reste de `10 divisé par 2` est `0` et non `1`.

L’idée la plus simple à mettre en place est d’utiliser la commande assert pour vérifier que les résultats voulus correspondent à ce que renvoie la fonction désirée.  

En particulier :  

- la division euclidienne de 10 par 2 doit renvoyer un quotient de 5 pour un reste nul ; 
- celles de −10 par 7, de 10 par −7, de 10.3 par 4 ou encore de 11 par 3.5 doivent toutes renvoyer le code −1 « d’erreur »   
- reste le cas particulier du zéro : une division par zéro doit renvoyer −1  

On utilise if ```__name__ == '__main__'```: qui permet de n’exécuter les tests que lorsqu’on  travaille sur ce fichier et pas lorsque ce fichier est appelé par un autre fichier du programme.  



 **<H3 STYLE="COLOR:red;">Activité n° 2.:</H3>**    

```python 
def division_euclidienne(a,b):   
   if a >=0 and b>0 and type(a)==int and type(b) == int:   
      return a%b, a//b   # ici on a inversé le reste et le quotient
   else:   
      return -1   
   
if __name__ == '__main__':   
   assert division_euclidienne(10, 2) == (5, 0)   
   assert division_euclidienne(-10, 7) == -1   
   assert division_euclidienne(10, -7) == -1   
   assert division_euclidienne(10.3, 4) == -1   
   assert division_euclidienne(11, 3.5) == -1   
   assert division_euclidienne(3, 0) == -1   
```  
   
L’inconvénient majeur de cette méthode est que l’on doit traiter **une assertion après l’autre** car le programme s’arrête dès le premier test qui échoue. En cas de réussite, il ne se passe simplement **rien**   
   
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**<H3 STYLE="COLOR:red;">Activité n° 3.:</H3>**    

```python  
def division_euclidienne(a,b):   
   if a >=0 and b>0 and type(a)==int and type(b) == int:   
      return a//b, a%b   
   else:   
      return -1   

if __name__ == '__main__':   
   assert division_euclidienne(10, 2) == (5, 0)   
   assert division_euclidienne(-10, 7) == -1   
   assert division_euclidienne(10, -7) == -1   
   assert division_euclidienne(10.3, 4) == -1   
   assert division_euclidienne(10, 4.3) == -1   
   assert division_euclidienne(3, 0) == -1   
```   
   
**CE SONT LES PLUS UTILISÉS** 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

### **<H3 STYLE="COLOR:GREEN;">2.2. Les<a name="_page2_x40.00_y650.92"></a> tests avec doctest</h3>** 

Les exemples donnés dans les docstrings (chaine de documentation) peuvent être testés à l’aide du module 



**<H3 STYLE="COLOR:red;">Activité n° 4.:</H3>**  

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0
   >>> factorielle(0)
   1
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n+1):
      resultat = resultat * i
   return resultat

import doctest
doctest.testmod()
```
Tester 
[ALLER SUR BASTHON](https://console.basthon.fr/)

La  fonction testmod du module doctest est  allée  chercher  dans  les docstring des  fonctions  du  module actuellement chargé,  tous les exemples (reconnaissables à la présence des triples chevrons >>>   **à mettre un espace après** ), et a vérifié que la fonction documentée satisfait bien ces exemples. Dans le cas présent, une seule fonction dont la documentation contient deux exemples (attempted = 2 ) a été testée, et il n’y a eu aucun échec (failed  = 0 )  



**<H3 STYLE="COLOR:red;">Activité n° 5.:</H3>**on introduit une erreur dans un des exemples du docstring  

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0
   >>> factorielle(0)
   100000000000000
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n+1):
      resultat = resultat * i
   return resultat
import doctest
doctest.testmod()
```
Tester 
[ALLER SUR BASTHON](https://console.basthon.fr/)



**<H3 STYLE="COLOR:red;">Activité n° 6.:</H3>** on peut rendre automatique les tests : 

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
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

if __name__ == '__main__':
   import doctest
   doctest.testmod()
```

Tester

[ALLER SUR BASTHON](https://console.basthon.fr/)

Ici il n’y a aucune erreur, on n’obtient **rien**, ce qui est parfois déconcertant 



**<H3 STYLE="COLOR:red;">Activité n° 7.:</H3>**  avec une erreur   

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0
   >>> factorielle(0)
   100000000000000
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n+1):
      resultat = resultat * i
   return resultat   
   
if __name__ == '__main__':   
   import doctest   
   doctest.testmod()   
```  

Tester [ALLER SUR BASTHON](https://console.basthon.fr/) 

 **<H3 STYLE="COLOR:red;">Activité n° 8.:</H3>**  On rend les doctests bavard même en cas de succès avec le mode verbose   

```python 
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
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

if __name__ == '__main__':
   import doctest
   doctest.testmod(verbose=True)  
```  

Tester [ALLER SUR BASTHON](https://console.basthon.fr/)   

## **<H2 STYLE="COLOR:BLUE;">3. Les<a name="_page5_x40.00_y567.92"></a> préconditions et les postconditions</h2>** 

Les assertions sont utilisées pour vérifier un résultat lorsque le test se fait, **test par test**. Donc un seul test à la fois. 

Mais les assertions peuvent aussi être dans le programme **pour vérifier tous les résultats** 



 **<H3 STYLE="COLOR:red;">Activité n° 9. : Utilisation de l’assertion dans une fonction</H3>**  

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



**<H3 STYLE="COLOR:red;">Activité n° 10. :</H3>**Tester  

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



**<H3 STYLE="COLOR:red;">Activité n° 11. :</H3>**On suppose que l’utilisateur entre une année. Ici il peut fournir une valeur impossible à convertir en entier.  
  
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



 **<H3 STYLE="COLOR:red;">Activité n°12. :</H3>**On peut ainsi intercepter ces erreurs possibles à l’exécution du code  

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

- 20 et 'a'

- 'a' et 3

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.3. Le<a name="_page11_x40.00_y338.92"></a> bloc try/except et les mots clés else et finally</h4>**



**<H3 STYLE="COLOR:red;">Activité n°13. :</H3>**L’instruction else se déroule **s’il n’y a pas d’exceptions** de lever   

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

**<H3 STYLE="COLOR:red;">Activité n°14. :</H3>**L’instruction finally permet d'exécuter du code après un bloc try, **quel que soit le résultat** de l'exécution du bloc. 

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

- 20 et 0

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.4. Avec<a name="_page12_x40.00_y346.92"></a> les assertions</h4>**

L’utilisation de* assert* permet de faire des tests Si le test renvoie True*,* l’exécution se poursuit normalement. Sinon, une exception AssertionError* est levée. 

**<H3 STYLE="COLOR:red;">Activité n°15. :</H3>**Dans le programme testant si une année est bissextile, on pourrait vouloir s’assurer que l’utilisateur ne  saisit pas une année inférieure ou égale à 0 par exemple : 

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

- 'a'

- -1999


???+ question "Faire ce qui est proposé"

    {{ IDE() }}

#### **<H4 STYLE="COLOR:MAGENTA;">5.2.5. Déclencher<a name="_page12_x40.00_y748.92"></a> une exception</h4>**

L’instruction raise permet au programmeur de déclencher une exception spécifique.

**<H3 STYLE="COLOR:red;">Activité n°16. :</H3>**Si l’utilisateur entre une année trop grande par exemple supérieure à 3000, on peut estimer qu’il s’agit d’une erreur 

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

1.Cas des assert : 

- Sa documentation dans le docstring comme dans l’activité 1. Ne pas mettre d’exemples 

- 4 tests en assert (comme dans l’activité 3) : avec 0, avec -1, avec 3.2 et avec ‘a’ 

2.Cas du doctest en mode verbose : 

- Sa documentation dans le docstring comme dans l’activité 1. 

- 4 tests dans le docstring (comme dans l’activité 10) : avec 0, avec -1,  avec 3.2 et avec ‘a’ 

**<H3 STYLE="COLOR:red;">Exercice 2:</H3>** : On considère une fonction somme_carres(x) qui prend en paramètre x (entier strictement positif) et renvoie la somme des x premiers carrés non nuls.  

Ecrire un script de cette fonction avec : 

1.Cas des assert : 

- Sa documentation dans le docstring comme dans l’activité 1. Ne pas mettre d’exemples 

- 3 tests en assert (comme dans l’activité 3) : avec 1, avec 2 et avec 3 

2.Cas du doctest en mode verbose : 

- Sa documentation dans le docstring comme dans l’activité 1.
 
- 3 tests dans le docstring (comme dans l’activité 10) : avec 1, avec 2 et avec 3 

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

- 'salut !'

- 0

- 2

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

- -5.26

- 16

Remarquez bien qu’on demande le nombre à l’utilisateur *jusqu'à* ce qu’il convienne. 

[Documentation sur les exceptions ](http://docs.python.org/3/tutorial/errors.html#exceptions)
Source :[ Fabrice Sincère ](http://fsincere.free.fr/isn/python/cours_python_ch5.php)-[ Contenu sous licence CC BY-NC-SA 3.0 ](http://creativecommons.org/licenses/by-nc-sa/3.0/fr/)

---
author: Elisabeth Le Prettre (LePrettre)
title: 13 Architecture de l’ordinateur
---

**Table des matières**

1. [**Historique de l’informatique**](#_page0_x40.00_y403.92)
2. [**Les différents types de mémoires**](#_page3_x40.00_y539.92)
3. [**Architecture de Von Neumann**](#_page4_x40.00_y536.92)
4. [**Langage assembleur**](#_page8_x40.00_y390.92)
5. [**Simulation CPU**](#_page11_x40.00_y36.92)
6. [**Des booléens aux circuits logiques**](#circuits)
7. [**Exercices sur les circuits**](#exercices_circuits)



## <H2 STYLE="COLOR:BLUE;"> **1. Historique<a name="_page0_x40.00_y403.92"></a> de l’informatique** </H2>

🎥 **Video 1** : [Histoire de l’informatique (Dailymotion)](https://www.dailymotion.com/video/xhleks) 

🎥 **Video 2** : [Évolution des ordinateurs](https://ladigitale.dev/digiview/#/v/669d6e5b4ed67)  


### <H3 STYLE="COLOR:GREEN;"> **1.1. Les<a name="_page0_x40.00_y459.92"></a> machines à programmes externes** </H3>

- **Machines électromécaniques**

L’allemand **Konrad ZUSE** achève le **Z1** en 1938, un ordinateur mécanique utilisant le système binaire, puis le **Z3** en 1941, premier ordinateur entièrement automatique lisant son programme sur une bande perforée. Le Z3 utilisait déjà le calcul en virgule flottante et réalisait 3 à 4 additions par seconde.


**Réplique du Zuse Z3 au Deutsches Museum de Munich.**
![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.002.png)

Peu après, aux États-Unis, **Howard H. AIKEN** construit l’ordinateur électromécanique **MARK I** (1944). Le MARK I pesait environ **5 tonnes** et était composé de plus de **750 000 pièces**.



![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.001.png)
Source : espace-turing.fr

Le **Mark I** lisait ses instructions sur des cartes perforées, exécutait l’instruction courante, puis lisait la suivante.

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.003.png)
Source : Wikipédia

- **Machines électroniques**

L’apparition des **tubes à vide**, bien plus rapides que les relais des machines électromécaniques, marque le début de l’électronique moderne.

Entre 1943 et 1945, les Britanniques **Max NEWMAN** et **Tommy FLOWERS** mettent en service **COLOSSUS**, utilisé pour déchiffrer le code **Lorenz** employé par les Allemands durant la Seconde Guerre mondiale.

Le célèbre **ENIAC**, développé par **John MAUCHLY** et **John ECKERT**, est achevé en novembre 1945 et utilisé pour des calculs balistiques grâce à **18 000 tubes à vide**.


![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.004.png)
Source : Wikipédia

L’ENIAC est le **premier ordinateur entièrement électronique** et peut être reprogrammé pour résoudre divers problèmes de calcul.

### <H3 STYLE="COLOR:GREEN;"> **1.2. Les<a name="_page1_x40.00_y480.92"></a> machines à programmes enregistrés** </H3>

Basées sur les travaux de **MAUCHLY, ECKERT et VON NEUMANN**, ces machines sont les ancêtres des ordinateurs modernes. Dans ce type de machine, **les données et les programmes sont stockés en mémoire**.

Les premières machines de ce type apparaissent dès 1948 avec les ordinateurs britanniques **BABY** et **EDSAC**, suivis par leurs homologues américains **EDVAC** et **UNIVAC**.

Dès les années 1950, les premiers ordinateurs commerciaux apparaissent, dominés par les constructeurs **IBM** (International Business Machines), **DEC** (Digital Equipment Corporation) et **BULL**.


### <H3 STYLE="COLOR:GREEN;"> **1.3. Du<a name="_page1_x40.00_y644.92"></a> micro-ordinateur à la micro-informatique** </H3>
- **Miniaturisation et explosion du marché**

- **Le transistor** (1947) marque la fin des tubes à vide et devient un produit industriel fiable et peu coûteux dès les années 1950.  

- **Le circuit intégré** (1958) miniaturise davantage les composants électroniques.  

- **Le microprocesseur** (**Intel 4004** en 1971) révolutionne l’informatique et ouvre la voie aux ordinateurs personnels.

💻 **Premiers micro-ordinateurs** :  

- **ALTAIR 8800** (1975) : premier ordinateur grand public, sans clavier ni écran.  

- **APPLE II** (1977)  

- **IBM PC** (1981)  

- **COMMODORE 64** (1982)  

- **APPLE MACINTOSH** (1984) : premier ordinateur personnel avec une souris et une interface graphique.


![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.005.png)
ALTAIR 8800

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.007.png)
APLLE II

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.006.png)
IBM PC

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.008.png)
COMMODORE 64

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.009.png)
APPLE MACINTOSH

- **Langages et système d’exploitation**

💾 **Les langages de programmation**  

- **1951** : Premiers compilateurs créés par **Grace HOPPER**.  

- **1956** : **FORTRAN** (John BACKUS).  

- **Années 1960-2000** : **LISP, COBOL, BASIC (1964), C (1972), ADA (1983), C++ (1986), PYTHON (1991), JAVASCRIPT (1995)**.

💻 **Les systèmes d’exploitation**  

- **1960s** : Chaque constructeur crée son propre OS (**OS 360, MVS, UNIX (1970)**).  

- **1984** : **Richard STALLMAN** lance le projet **GNU** et le mouvement du logiciel libre.  

- **1985** : **MS-DOS (Microsoft) domine les micro-ordinateurs**, suivi de **Windows**.  

- **1991** : **GNU/Linux** voit le jour grâce à **Linus TORVALDS**.

Actuellement, les principaux systèmes d’exploitation sont **Windows, macOS et GNU/Linux**.


!!! example "🧠 Exercices dans Capytale => le code vous sera donné par votre enseignant"
    

???+ question "**Activité n°1**"

    Répondre par Vrai ou faux 

    Certaines questions nécessitent une recherche Internet.  

    1️⃣ Blaise Pascal a mis au point le logiciel Turbo Pascal. 

    2️⃣ George Boole était un spécialiste de la logique binaire.  

    3️⃣ Alan Turing a travaillé sur l’intelligence artificielle. 

    4️⃣ Alan Turing a cassé le code Enigma.  

    5️⃣ L’ordinateur ENIAC était aussi petit qu’une boîte à chaussures.  

    6️⃣ John Von Neumann a conçu l’architecture de base des ordinateurs modernes.  

    7️⃣ L’invention du transistor a permis de miniaturiser les ordinateurs.  

    8️⃣ Le premier micro-ordinateur est américain. 

    9️⃣ Le processeur 8086 possède 1 000 000 de transistors.  

    🔟 Gary Kasparov est imbattable aux échecs. 

    1️⃣1️⃣ La loi de Moore est toujours valide en 2020.  



???+ question "**Activité n°2**" 

    Cocher la ou les bonnes réponses. 

    Certaines questions nécessitent une recherche Internet.  

    1️⃣ Le premier algorithme connu remonte... 

    📌 XXe siècle / 📌 XIXe siècle / 📌 Ier siècle / 📌 Bien avant  

    2️⃣ Le mot "algorithme" vient du nom…  

    📌 Al-Khwârizmi / 📌 Grace Hopper / 📌 Steve Jobs / 📌 Ada Lovelace  

    3️⃣ Le premier compilateur a été conçu par… 

    📌 Al-Khwârizmi / 📌 Grace Hopper / 📌 Steve Jobs / 📌 Ada Lovelace  

📌 **Et bien d’autres questions à explorer !**  


## <H2 STYLE="COLOR:BLUE;"> **2. Les<a name="_page3_x40.00_y539.92"></a> différents types de mémoires** </H2>
### <H3 STYLE="COLOR:GREEN;"> **2.1. Organisation<a name="_page3_x40.00_y567.92"></a> de la mémoire** </H3>

Il existe de nombreuses **technologies de mémoire**, qui se distinguent selon plusieurs critères :

- **Durabilité** : mémoire volatile (données perdues à l'arrêt du courant) ou permanente.  

- **Mode d’accès** : accès direct (adressage aléatoire) ou séquentiel.

- **Temps d’accès** : plus une mémoire est rapide, plus elle est chère.  

Les principales catégories de mémoire sont :  

- **Mémoire morte (ROM – Read Only Memory)** : mémoire **non volatile**, utilisée pour stocker des programmes essentiels comme le BIOS (Basic Input Output System). Elle est en lecture seule mais peut être mise à jour (flashage du BIOS).  

- **Mémoire vive (RAM – Random Access Memory)** : mémoire **volatile**, utilisée pour stocker temporairement les instructions et données des programmes en cours d'exécution.  

- **Mémoire de stockage secondaire** : disques durs (HDD, SSD), clés USB, CD-ROM...  

### <H3 STYLE="COLOR:GREEN;"> **2.2. Les<a name="_page4_x40.00_y47.92"></a> registres** </H3>

Un **registre** est un emplacement **mémoire interne** au processeur. Il s’agit de la mémoire **la plus rapide**, mais également **la plus coûteuse**, car son espace est limité.  

🔹 **Rôle des registres** : 

- Stocker des **opérandes** et **résultats intermédiaires** pendant le traitement des instructions.  

- Varier en capacité, nombre et fonctions selon les processeurs. 

- Être directement accessibles via le jeu d’instructions du processeur.  

💡 **La plupart des processeurs modernes ont des registres de 64 bits**.


### <H3 STYLE="COLOR:GREEN;"> **2.3. Mémoires<a name="_page4_x40.00_y175.92"></a> centrales et mémoires caches** </H3>

**Mémoire centrale (RAM)**  

La **mémoire centrale** stocke temporairement les programmes et leurs données pendant leur exécution. Elle est **volatile**, ce qui signifie que les informations sont perdues lorsque l’ordinateur s’éteint.  

🔹 Organisation :  

- Constituée de **cases mémoires** repérées par une **adresse unique**.  

- Accès rapide et en **temps constant**. 

- Types : **SDRAM, DDR, DDR2, DDR3, DDR4, DDR5**.

**Mémoire cache**  

Pour compenser la différence de vitesse entre le **processeur** et la **mémoire centrale**, on utilise une **mémoire cache** intégrée au processeur.  

🔹 Caractéristiques :  

- Stocke les **instructions et données les plus utilisées** pour éviter de les rechercher en RAM.

- Plus rapide que la RAM, mais plus petite et plus chère.

- **Types** :  

  1 **Cache L1** : la plus rapide, située directement dans le cœur du processeur.  

  2 **Cache L2** : plus grande, mais légèrement plus lente.  

  3 **Cache L3** : partagée entre plusieurs cœurs d’un processeur multi-cœur.  


???+ question "**Activité n°3**"

    Quelques interrogations 

    💡 Réfléchissez aux réponses aux questions suivantes :  

    1️⃣ Où sont stockés les programmes dans la mémoire ?  

    2️⃣ Comment l’ordinateur effectue-t-il une addition ?  

    3️⃣ D’où proviennent les données entrées via le clavier ?

    4️⃣ Où vont les informations envoyées vers l’écran ? 

## <H2 STYLE="COLOR:BLUE;"> **3. Architecture<a name="_page4_x40.00_y536.92"></a> de Von Neumann** </H2>

L’**architecture de Von Neumann** (1945) est un **modèle d’ordinateur** où **les instructions et les données partagent la même mémoire**. Ce modèle est toujours utilisé dans les ordinateurs modernes.  



### <H3 STYLE="COLOR:GREEN;"> **3.1. Organisation<a name="_page4_x633.92"></a> générale** </H3>

🔹 **Les trois parties du CPU** : 

- **L’unité arithmétique et logique (UAL ou ALU)** : effectue les **calculs** et les **opérations logiques**.  

- **L’unité de contrôle** : exécute les instructions en coordonnant les autres composants.  

- **La mémoire** : stocke **instructions et données**.  

🔹 **Le bus (système de communication interne)**  

Il permet aux composants de **transporter des données et instructions**.  

Il existe **trois types de bus** :  

1️⃣ **Bus d’adresses** : transporte les adresses mémoire. 

2️⃣ **Bus de données** : transporte les données elles-mêmes. 

3️⃣ **Bus de contrôle** : gère le type d’opération (lecture, écriture…).  

🔹 **Les périphériques d’entrée/sortie**  

Ils permettent à l’ordinateur de communiquer avec l’extérieur (**clavier, écran, imprimante...**).


![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.021.jpeg)

💡 **L’architecture Harvard** est une alternative où les mémoires des programmes et des données sont séparées, permettant un **traitement plus rapide**.

???+ question "**Activité n°4 : Calcul de la mémoire disponible**"  

    1️⃣ **Combien d’adresses mémoire différentes peut-on avoir avec un bus d’adresses de 16 bits ?**  

    2️⃣ **Si chaque case mémoire contient 1 octet, quelle est la capacité maximale de mémoire vive ?**  


### <H3 STYLE="COLOR:GREEN;"> **3.2. Le<a name="_page6_x297.92"></a> CPU** </H3>



Le **processeur** (CPU – Central Processing Unit) est le **cœur de l’ordinateur**.  

🔹 **Caractéristiques** : 

- Manipule des **données binaires** et des **instructions**.  

- Contient des **millions de transistors** miniaturisés.  

- Intégré dans un **boîtier** surmonté d’un **ventilateur**.  





### <H3 STYLE="COLOR:GREEN;"> **3.3. Le rôle de l’horloge CPU**  </H3>

Le **processeur est cadencé** par une **horloge interne**, qui envoie des **impulsions électriques** synchronisant ses opérations.  

📌 **Caractéristiques du CPU** :  

- **Fréquence d’horloge** (en MHz ou GHz).  

- **Nombre d’instructions par seconde**. 

- **Taille des données traitées** (en bits).  

💡 **Un CPU cadencé à 2 GHz exécute 2 milliards d’opérations par seconde**.

???+ question "**Activité n°5**"

    Sur les photos ci-dessous, identifier le processeur. 

    ![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.026.png)
    ![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.027.png)
    ![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.028.png)

### <H3 STYLE="COLOR:GREEN;"> **3.4. Les<a name="_page7_x274.92"></a> limites** </H3>

🔹 **Le principal problème : le goulet d’étranglement**  

- Le processeur est **beaucoup plus rapide** que la mémoire. 

- Le **bus mémoire** ne peut **pas suivre la cadence**.  

- **Solution** : utilisation de **mémoires caches et multiprocesseurs**.  



### <H3 STYLE="COLOR:GREEN;"> **3.5. Évolution<a name="_page7_x423.92"></a> : le multiprocesseur et les mémoires caches** </H3>

🔹 **La loi de Moore** (1965) : 

- 🏆 **Le nombre de transistors double tous les 18 à 24 mois**. 

- 🚀 Augmentation des performances et miniaturisation. 

- ❌ **Depuis 2017, cette loi atteint ses limites physiques.**  

🔹 **Solution moderne** :  

✅ **Multiprocesseurs** et **multi-cœurs** permettent un traitement **parallèle** des données. 

✅ **Mémoire cache plus performante** pour compenser la lenteur de la RAM.  

💡 Aujourd’hui, **l’optimisation mémoire est devenue un enjeu majeur**.



???+ question "**Activité n°6**" 

    Ci-contre, retrouver les interfaces RJ45, VGA, HDMI et USB. 

    ![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.032.jpeg)

## <H2 STYLE="COLOR:BLUE;"> **4. Langage<a name="_page8_x40.00_y390.92"></a> assembleur** </H2>

Le **microprocesseur** ne peut pas interpréter directement des instructions en langage naturel comme :

> _"Additionne le nombre 125 et la valeur située dans le registre R2, range le résultat dans le registre R1"._

Ces instructions doivent être traduites en **code binaire** compréhensible par le processeur :  
```binary
11100010100000100001000001111101
```
Cependant, l'écriture en binaire étant complexe et peu lisible, on utilise des **mnémoniques** sous forme de langage **assembleur**, plus compréhensible pour les programmeurs :  
```assembly
ADD R1, R2, #125
```

Ce code en assembleur signifie :  

- **ADD** : additionne  

- **R1** : registre où stocker le résultat  

- **R2** : registre contenant l'une des valeurs  

- **#125** : valeur immédiate ajoutée à R2  

### <H3 STYLE="COLOR:GREEN;"> **4.1. Exemples d’instructions en assembleur** </H3>

| **Instruction**  | **Description** |
|----------------|---------------|
| `LDR R1, 78`  | Charge la valeur située à l'adresse mémoire **78** dans le registre **R1**. |
| `STR R3, 125` | Stocke la valeur contenue dans le registre **R3** à l'adresse mémoire **125**. |
| `ADD R1, R0, #128` | Additionne **128** avec la valeur du registre **R0** et stocke le résultat dans **R1**. |
| `ADD R0, R1, R2` | Additionne les valeurs des registres **R1** et **R2**, et stocke le résultat dans **R0**. |
| `SUB R1, R0, #128` | Soustrait **128** à la valeur du registre **R0**, et stocke le résultat dans **R1**. |
| `MOV R1, #23` | Stocke la valeur **23** dans le registre **R1**. |
| `MOV R0, R3` | Copie la valeur de **R3** dans **R0**. |
| `B 45` | Change la séquence d'exécution en sautant à l’adresse **45**. |
| `CMP R0, #23` | Compare la valeur de **R0** avec **23**. |
| `CMP R0, #23 BEQ 78` | Si **R0 == 23**, alors saute à l’adresse **78**. |
| `CMP R0, #23 BGT 78` | Si **R0 > 23**, alors saute à l’adresse **78**. |
| `HALT` | Arrête l’exécution du programme. |

???+ question "**Activité n°7**" 

    Expliquer les instructions suivantes 

    📌 **Décrivez les instructions suivantes en langage naturel :** 

    1️⃣ `ADD R0, R1, #42`  

    2️⃣ `LDR R5, 98`  

    3️⃣ `CMP R4, #18`  

    4️⃣ `BGT 77`  

    5️⃣ `STR R0, 15`  

    6️⃣ `B 100`  

### <H3 STYLE="COLOR:GREEN;"> **4.2. Applications** </H3>

???+ question "**Activité n°8**"

    📌 **Écrivez les instructions en assembleur correspondant aux phrases suivantes :**  

    1️⃣ Additionne la valeur stockée dans **R0** et celle stockée dans **R1**, stocke le résultat dans **R5**. 

    2️⃣ Charge la valeur située à l’adresse mémoire **878** dans le registre **R0**.  

    3️⃣ Stocke la valeur du registre **R0** en mémoire à l’adresse **124**.  

    4️⃣ Sauter directement à l’instruction stockée en mémoire **478**.  

    5️⃣ Si **R0 == 42**, sauter à l’adresse **85**.

???+ question "**Activité n°9:**"

    📌 **Comparer le programme suivant en Python et en Assembleur** :

    **Python**  
    ```python
    x = 4
    y = 8
    if x == 10:
        y = 9
    else:
        x = x + 1
    z = 6
    ```

    **Assembleur équivalent**
    ```assembly
    MOV R0, #4
    STR R0, 30
    MOV R0, #8
    STR R0, 75
    LDR R0, 30
    CMP R0, #10
    BNE else
    MOV R0, #9
    STR R0, 75
    B endif
    else:
    LDR R0, 30
    ADD R0, R0, #1
    STR R0, 30
    endif:
    MOV R0, #6
    STR R0, 23
    HALT
    ```
    📌 **Questions** :  

    1️⃣ À quoi sert la ligne `B endif` ?  

    2️⃣ Que représentent les adresses mémoires `23`, `75` et `30` ?  


## <H2 STYLE="COLOR:BLUE;"> **5. Simulation<a name="_page11_x40.00_y36.92"></a> CPU** </H2>

Nous allons utiliser un **simulateur CPU** basé sur l’architecture **Von Neumann**.  

### <H3 STYLE="COLOR:GREEN;"> **5.1. Présentation du simulateur** </H3>

📌 Disponible en ligne : [🔗 Peter Higginson’s CPU Simulator](http://www.peterhigginson.co.uk/AQA/)  

📷 **Interface du simulateur**  

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.050.jpeg)  

🔹 **Zones principales du simulateur** : 

1️⃣ **Mémoire vive (Main Memory)** : Contient les instructions et les données.(à droite)  

2️⃣ **Microprocesseur (CPU)** : Exécute les instructions. (au centre)

3️⃣ **Éditeur d’assembleur (Assembly Language)** : Permet d’écrire du code.  (à gauche)



### <H3 STYLE="COLOR:GREEN;"> **5.2. Configuration de la RAM<a name="_page11_x648.92"></a>** </H3>

Par défaut le contenu des différentes cellules de la mémoire est en base 10 (entier signé), mais d'autres options sont possibles : base 10 (entier non-signé, "unsigned"), base 16 ("hex"), base 2 ("binary"). On accède à ces options à l'aide du bouton "OPTIONS" situé en bas dans la partie gauche du simulateur.

???+ question "**Activité n°10**"  

    1️⃣ Utiliser le bouton **"OPTIONS"** pour afficher la mémoire en **binaire**.  

    2️⃣ Chaque cellule mémoire contient **32 bits**.  

    3️⃣ Vérifier l’adresse mémoire utilisée (entre **000 et 199**). 

    4️⃣ Remettre l’affichage en **base 10**.  (bouton "OPTION"->"signed")



### <H3 STYLE="COLOR:GREEN;"> **5.3. Le<a name="_page12_x73.92"></a> CPU** </H3>

Dans la partie centrale du simulateur, nous allons trouver en allant du haut vers le bas :

- le **bloc "registre"** ("Registers") : nous avons 13 registres (R0 à R12) + 1 registre (PC) qui contient l'adresse mémoire de l'instruction en court d'exécution
- le **bloc "unité de commande"** ("Control Unit") qui contient l'instruction machine en cours d'exécution (au format hexadécimal)
- le **bloc "unité arithmétique et logique"** ("Arithmetic and Logic Unit")

### <H3 STYLE="COLOR:GREEN;"> **5.4. Programmer<a name="_page12_x218.92"></a> en assembleur** </H3>

???+ question "**Activité n°11**"

    1️⃣ Dans l'éditeur **Assembly Language**, saisissez :  
    ```assembly
    MOV R0, #42
    STR R0, 150
    HALT
    ```
    2️⃣ Cliquez sur **Submit**.  

    3️⃣ Vérifiez que :  

    - L’instruction **MOV** est à l’adresse **000**.  

    - L’instruction **STR** est à l’adresse **001**.  

    - L’instruction **HALT** est à l’adresse **002**.  

???+ question "**Activité n°12**" 

    Exécution pas à pas :</H3>
    1️⃣ **Exécutez** le programme en cliquant sur **RUN**.  
    2️⃣ Observez l’animation du CPU.  
    3️⃣ Vérifiez que **l’adresse mémoire 150 contient bien 42**.  
    4️⃣ **Modifier** la vitesse avec **<< et >>**.  

📌 **Remarque** : Pour relancer la simulation, cliquez sur **RESET**.


Une fois la simulation terminée, on constate que la cellule mémoire d'adresse 150, contient bien le nombre 42 (en base 10) et que le registre R0 a bien stocké le nombre 42.


???+ question "**Activité n°13**"

    💡 **Modifier le programme précédent** pour **stocker 54 dans l’adresse mémoire 50** en utilisant **R1**. 

    ✅ **Testez** la modification en exécutant le programme.

???+ question "**Activité n°14**" 

    💡 **Tester le programme suivant** :
    ```assembly
    MOV R0, #4
    STR R0, 30
    MOV R0, #8
    STR R0, 75
    LDR R0, 30
    CMP R0, #10
    BNE else
    MOV R0, #9
    STR R0, 75
    B endif
    else:
    LDR R0, 30
    ADD R0, R0, #1
    STR R0, 30
    endif:
    MOV R0, #6
    STR R0, 23
    HALT
    ```
    ✅ **Analysez** le comportement du programme.

## <H2 STYLE="COLOR:BLUE;"> **6. Des booléens aux circuits logiques<a name="circuits"></a>** </H2>

Au chapitre 04, on a calculé des **tables de vérité** et additionné deux bits avec le XOR et le ET. Dans le processeur, ces calculs sont réalisés **physiquement** par des **circuits logiques** : c'est ainsi que l'**UAL** (unité arithmétique et logique, voir 3.2) effectue additions et comparaisons.

### <H3 STYLE="COLOR:GREEN;"> **6.1. Du transistor à la porte logique** </H3>

💡 Un **transistor** fonctionne comme un **interrupteur** :

- `1` : le courant passe (**état haut**) ;
- `0` : le courant ne passe pas (**état bas**).

En assemblant quelques transistors, on obtient une **porte logique** : un composant qui réalise une opération booléenne sur un ou plusieurs signaux binaires.

🔹 Deux types de circuits logiques :

1. **Circuits combinatoires** : la sortie dépend **uniquement des entrées** (portes, additionneurs, multiplexeurs) ;
2. **Circuits séquentiels** : la sortie dépend des entrées **et des états précédents** (mémoires, registres).

!!! example "Exemple concret"
    Une lampe ne doit s'allumer que si l'interrupteur de sécurité est activé **et** que le bouton de commande est enfoncé : c'est une porte **ET**.

### <H3 STYLE="COLOR:GREEN;"> **6.2. Les portes logiques** </H3>

| Porte | Sortie à 1 quand… | Python | Symbole | Autre symbole |
|---|---|---|---|---|
| **NON** (NOT) | l'entrée vaut 0 | `not a` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.010.png) | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.011.png) |
| **OU** (OR) | au moins une entrée vaut 1 | `a or b` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.012.png) | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.013.png) |
| **ET** (AND) | les deux entrées valent 1 | `a and b` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.014.png) | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.015.png) |
| **OU EXCLUSIF** (XOR) | les entrées sont différentes | `a ^ b` ou `a != b` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.016.png) | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.017.png) |
| **NON ET** (NAND) | pas les deux à 1 | `not (a and b)` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.018.png) | |
| **NON OU** (NOR) | aucune entrée à 1 | `not (a or b)` | ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.019.png) | |

| A | B | ET | OU | XOR | NAND | NOR |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |

💡 Les portes NAND et NOR sont dites **universelles** : avec des portes NAND seulement (ou NOR seulement), on peut construire toutes les autres.

???+ question "**Activité n°15 : un simulateur de circuits en Python**"

    Chaque porte devient une fonction qui renvoie `0` ou `1` ; un circuit est une **composition** de fonctions.

    ```python
    def NON(a):
        return int(not a)

    def ET(a, b):
        return int(a and b)

    def OU(a, b):
        return int(a or b)

    def XOR(a, b):
        return a ^ b

    def circuit(A, B, C):
        """S = (A ET B) OU (NON C)"""
        return OU(ET(A, B), NON(C))

    print("A B C | S")
    for A in (0, 1):
        for B in (0, 1):
            for C in (0, 1):
                print(A, B, C, "|", circuit(A, B, C))
    ```

    1. Prévoir `circuit(1, 0, 0)` et `circuit(1, 1, 1)`, puis vérifier.
    2. Écrire une fonction `NAND(a, b)`, puis `NON_bis(a)` qui n'utilise **que** `NAND` (indice : brancher `a` sur les deux entrées). Vérifier que `NON_bis` et `NON` ont la même table.

    ??? success "Python"
        {{ IDE() }}

    ??? success "Solution"

        **1.** `circuit(1, 0, 0)` = `OU(0, 1)` = **1** ; `circuit(1, 1, 1)` = `OU(1, 0)` = **1**.

        **2.**

        ```python
        def NAND(a, b):
            return NON(ET(a, b))

        def NON_bis(a):
            return NAND(a, a)

        for a in (0, 1):
            print(a, NON(a), NON_bis(a))   # mêmes colonnes : 0 1 1 / 1 0 0
        ```

???+ question "**Activité n°16 : le multiplexeur**"

    La fonction multiplexeur `mux` est définie par : `mux(x, y, z) = (not(x) and y) or (x and z)`.

    1. Compléter sa table de vérité, avec les colonnes intermédiaires `not(x)`, `not(x) and y` et `x and z` (8 lignes).
    2. Que remarque-t-on quand `x = 0` ? quand `x = 1` ?
    3. Trouver l'expression de la fonction `ssi(x, y)` (« si et seulement si »), qui vaut 1 quand `x` et `y` ont la même valeur.

    ??? success "Solution"

        | x | y | z | not(x) | not(x) and y | x and z | mux(x,y,z) |
        |---|---|---|---|---|---|---|
        | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
        | 0 | 0 | 1 | 1 | 0 | 0 | 0 |
        | 0 | 1 | 0 | 1 | 1 | 0 | 1 |
        | 0 | 1 | 1 | 1 | 1 | 0 | 1 |
        | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
        | 1 | 0 | 1 | 0 | 0 | 1 | 1 |
        | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
        | 1 | 1 | 1 | 0 | 0 | 1 | 1 |

        Si **x = 0, mux recopie y** ; si **x = 1, mux recopie z** : x joue le rôle d'un **aiguillage**.

        `ssi(x, y) = (x and y) or (not(x) and not(y))` : c'est le contraire du XOR, `ssi(x, y) = not (x xor y)`.

### <H3 STYLE="COLOR:GREEN;"> **6.3. Simplifier une expression** </H3>

Les règles de l'algèbre de Boole permettent de **simplifier** un circuit (donc d'économiser des portes) :

| Propriété | Avec OU (`+`) | Avec ET (`·`) |
|---|---|---|
| Élément neutre | `a + 0 = a` | `a · 1 = a` |
| Élément absorbant | `a + 1 = 1` | `a · 0 = 0` |
| Idempotence | `a + a = a` | `a · a = a` |
| Complément | `a + a̅ = 1` | `a · a̅ = 0` |
| Distributivité | `a + (b · c) = (a + b) · (a + c)` | `a · (b + c) = a · b + a · c` |

Avec la double négation (`NON (NON a) = a`) et les **lois de De Morgan** (chapitre 04).

💡 Exemple : `A + B + B · C = A + B · (1 + C) = A + B · 1 = A + B`.

### <H3 STYLE="COLOR:GREEN;"> **6.4. Du demi-additionneur à l'UAL** </H3>

- Le **demi-additionneur** additionne deux bits : une porte **XOR** donne la somme `S = A ⊕ B`, une porte **ET** donne la retenue `C = A · B` (C pour *carry*).
- L'**additionneur complet** additionne deux bits **et la retenue** du rang précédent.
- En enchaînant 8 additionneurs complets, on additionne deux octets : c'est le cœur de l'**UAL** du processeur.

## <H2 STYLE="COLOR:BLUE;"> **7. Exercices sur les circuits<a name="exercices_circuits"></a>** </H2>

!!! example "🧠 Exercices dans Capytale => le code vous sera donné par votre enseignant"
    Pour dessiner et tester un circuit : [📜 Fiche méthode Capytale](13h_Fiche_methode_Capytale_circuits.md)

!!! abstract "Exercice n°1 ★"

    On considère le circuit logique suivant.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.022.png)

    1. Réaliser le circuit.
    2. Donner l'expression booléenne de S en fonction des variables A et B.
    3. Compléter la table de vérité ci-dessous.

        ![](Aimg013.png)

    4. Par quel circuit comprenant seulement deux portes peut-on remplacer le circuit étudié ?

!!! abstract "Exercice n°2 ★"

    On considère le circuit logique ci-dessous.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.024.png)

    1. Donner l'expression booléenne de S en fonction des variables A, B et C.
    2. Compléter la table de vérité ci-dessous.

        ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.025.jpeg)

    3. En déduire une formule pour S qui ne dépend que des variables A et B.

!!! abstract "Exercice n°3 ★"

    On considère les circuits logiques ci-dessous.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.026.png)

    1. Donner les expressions booléennes de U et V en fonction des variables A, B et C.
    2. Compléter les tables de vérité ci-dessous.

        ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.028.jpeg)

    3. Les expressions booléennes U et V sont-elles équivalentes ?

!!! abstract "Exercice n°4 ★ (circuit MUX-2)"

    On considère le circuit logique suivant.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.029.png)

    1. Donner l'expression de Out en fonction de C, E1 et E2.
    2. Compléter la table de vérité de ce circuit.

        ![](Aimg014.png)

    Le circuit étudié est appelé multiplexeur à 2 entrées. Selon la valeur de la commande (C), il permet de reproduire en sortie (Out) :

    - le signal E1 si C est à 0 ;
    - le signal E2 si C est à 1.

    **3.** Vérifier ce fonctionnement sur la table de vérité. Quel lien avec la fonction `mux` de l'activité n°16 ?

!!! abstract "Exercice n°5 FACULTATIF ★★★ (circuit MUX-4)"

    On considère un multiplexeur à 4 entrées, dont le circuit est représenté ci-dessous.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.035.jpeg)

    1. Par analyse du circuit, déterminer l'expression booléenne de Out en fonction des entrées E1, E2, E3, E4 et des commandes C0 et C1.
    2. Quelles sont les valeurs des commandes C0 et C1 qui permettent de sélectionner en sortie (Out) :

        - l'entrée E1 ?
        - l'entrée E2 ?
        - l'entrée E3 ?
        - l'entrée E4 ?

!!! abstract "Exercice n°6 ★★ (Half adder)"

    Le circuit étudié, appelé demi-additionneur, permet d'additionner deux bits A et B. Il comporte deux sorties C et S qui représentent deux expressions booléennes.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.037.png)

    1. Donner les expressions booléennes de C et S en fonction de A et B.
    2. Compléter la table de vérité de C et S.

        ![](Aimg015.png)

    3. Quel est le rôle des sorties C et S dans la fonction du circuit ? On pourra comparer avec l'addition binaire `1 + 1 = 10` vue au chapitre 04.

    Le choix de la lettre C vient du fait qu'en anglais, « retenue » se dit « carry ».

!!! abstract "Exercice n°7 FACULTATIF ★★ (Full adder)"

    Le circuit étudié dans cet exercice permet d'additionner deux bits A et B en tenant compte d'une retenue d'entrée Cin. Il produit la somme S et une retenue de sortie Cout.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.053.jpeg)

    1. Réaliser ce circuit et compléter la table de vérité ci-dessous.

        ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.054.jpeg)

    2. Vérifier sur deux lignes de la table que `Cout S` (lu comme un nombre binaire) est bien la somme `Cin + A + B`.

!!! abstract "Exercice n°8 FACULTATIF ★★"

    Soit le circuit ci-dessous :

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.055.png)

    1. Écrivez l'équation de ce circuit.
    2. Établissez la table de vérité de ce circuit.

!!! abstract "Exercice n°9 FACULTATIF ★★★"

    Un pont peut supporter 10 tonnes au maximum. La route menant au pont est strictement interdite aux véhicules de plus de 10 tonnes. À chaque extrémité du pont se trouve une barrière et une bascule pour mesurer le poids (a ou b) des véhicules.

    ![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.056.jpeg)

    Si un seul véhicule attend devant le pont, la barrière devant lui (A ou B) s'ouvre (étape initiale). Sinon :

    - si a + b ≤ 10 tonnes, les barrières A et B s'ouvrent ;
    - si a + b > 10 tonnes, seule la barrière correspondant au véhicule le plus léger s'ouvre ;
    - si a = b, la barrière A s'ouvre en priorité.

    L'autre véhicule attend que le premier ait franchi le pont, puis le protocole d'ouverture des barrières recommence à l'étape initiale.

    Indication : a et b n'étant pas des variables binaires, il convient de créer deux variables binaires x et y et de reformuler l'énoncé du problème.

    Aide : on posera `x = (a + b <= 10)` et `y = (a > b)`.

    1. Écrivez la table de vérité pour l'ouverture des barrières A et B (cas où deux véhicules attendent).
    2. Donnez les équations logiques pour l'ouverture de la barrière A, puis pour l'ouverture de la barrière B.
    3. Dessinez le circuit logique déterminant l'ouverture des barrières.

!!! success "🎞️ Revoir en vidéo et réviser"
    [XOR, NAND, NOR](../04_chapitre_4/04m_xor_nand_nor_video.md) · [📜 Fiche méthode : booléens et circuits](13i_Booleens_circuits_fiche.md)

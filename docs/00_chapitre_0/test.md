P2021 - Les nombres entiers

Ensemble des entiers naturels, ensemble des entiers relatifs
!!! abstract "Définitions"

    * L'ensemble des entiers naturels est formé par les nombres $0, 1, 2, 3,\dots$ On le note $\mathbb{N}$;

    * L'ensemble des entiers relatifs est formé des entiers naturels et de leurs opposés $\dots -3; -2;-1;0;1;2;3\dots$ On le note $\mathbb{Z}$.



Multiples et diviseurs
!!! abstract "Définition"

    Soit $a$ et $b$ deux entiers. On dit que $a$ **est un multiple** de $b$ s'il existe un nombre entier $k$ tel que $a=k \times b$. On dit alors que $b$ **est un diviseur** de a.


!!! success "Propriété"

    Soit $n$ un entier. La somme de deux multiples de $n$ est un multiple de $n$.


???+ example "Démonstration (exigible)"

    Soit les entiers $n$, $k$ et $k'$ et $m$, $m'$ deux multiples de $n$ :

    $\left\{ \begin{array}{l} m = k \times n \\ m'= k' \times n \end{array} \right.$

    $\Leftrightarrow m+m'= k \times n + k' \times n$

    $\Leftrightarrow m+m'= (k+k') \times n$

    On constate que la somme $m+m'$  s'écrit sous la forme $K \times n$, avec $K=k+k'$ ,  elle est donc multiple de $n$.




Nombres pairs et nombres impairs
!!! abstract "Définitions"

    * Un nombre pair est un nombre entier multiple de $2$. Il s'écrit sous la forme $2k$, avec $k$ entier.

    * Un nombre impair est un nombre entier qui n'est pas pair, c'est-à-dire non multiple de $2$. Il s'écrit sous la forme $2k+1$, avec $k$ entier.


!!! success "Propriété"

    Le carré d'un nombre impair est impair.


???+ example "Démonstration (exigible)"

    Soit $n$ un nombre impair qui s'écrit sous la forme $n=2k+1$, avec $k \in \mathbb{Z}$

    $n^2=(2k+1)^2$

    $\Leftrightarrow n^2=(2k)^2 + 4k + 1^2$

    $\Leftrightarrow n^2 = 4k^2+4k+1$

    $\Leftrightarrow n^2=2(2k^2+2k)+1$

    On constate que $n^2$ est de la forme $2K +1$, avec $K=2k^2+2k$, donc $n²$ est un nombre impair.




Nombres premiers
!!! abstract "Définition"
    Un nombre premier est un entier qui possède dans N\mathbb{N}N exactement deux diviseurs : 111 et lui-même.
    Remarques


    000 est divisible par une infinité d'entiers (sauf lui-même), il n'est pas premier;


    111 n'a qu'un seul diviseur, lui-même, il n'est pas premier;


    222 est l'unique nombre premier pair.


!!! success "Propriété"

    Tout entier, supérieur ou égal à $2$ est soit un nombre premier, soit un produit de nombres premiers appelé **décomposition en facteurs premiers**. Cette décomposition est unique.


    Exemple : $360=23×32×5360=2^3 \times 3^2 \times 5360=23×32×5$
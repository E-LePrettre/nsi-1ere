---
author: ELP
title: 07b Le CSS
--- 

**Table des matières** 

1. [La petite histoire du CSS ](#_page0_x40.00_y671.92)
2. [Ou écrit-on le CSS ? ](#_page1_x40.00_y36.92)
3. [Appliquer un style](#_page1_x40.00_y534.92)
4. [Formater du texte](#_page4_x40.00_y36.92)
5. [Ajouter de la couleur et un fond](#_page6_x40.00_y36.92)
6. [Habillage](#_page8_x40.00_y542.92)
7. [Créer des bordures et des ombres](#_page9_x40.00_y302.92)
8. [Les apparences dynamiques](#_page10_x40.00_y621.92)
9. [Les tableaux](#_page11_x40.00_y351.92)
10. [Le modèle des boites](#_page13_x40.00_y36.92)
11. [Le positionnement](#_page15_x40.00_y36.92)
12. [Squelette de base HTML – CSS8](#_page17_x40.00_y239.92)


## <H2 STYLE="COLOR:BLUE;">1. La<a name="_page0_x40.00_y671.92"></a> petite histoire du CSS</H2>

Le **CSS (Cascading Style Sheets)** permet de personnaliser **l’apparence** d’un site web :  

✔ Couleur du texte,  
✔ Police et taille des caractères,  
✔ Bordures et arrière-plan,  
✔ Mise en page (menus, en-tête, pied de page…).  

## 🔍 Pourquoi a-t-on créé le CSS ?  

Au début du Web, **CSS n’existait pas** ! Seul le **HTML** permettait d'afficher du contenu, mais **sans mise en page avancée**.  

💡 **Problème :**  
- HTML mélangeait **contenu** et **mise en forme**, ce qui compliquait les mises à jour.  
- Il fallait **modifier chaque page une par une** pour changer l’apparence d’un site.  

💡 **Solution :**  
➡ **Le CSS est apparu pour séparer la mise en forme (CSS) du contenu (HTML).**  
➡ Résultat : un site **plus facile à gérer et à modifier** !


## <H2 STYLE="COLOR:BLUE;">2. Ou<a name="_page1_x40.00_y36.92"></a> écrit-on le CSS ?</H2>

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.003.png)

On peut écrire du CSS à **trois endroits différents** :  

| Méthode | Explication | Recommandation |
|---------|------------|---------------|
| **Fichier externe (.css)** | Le CSS est écrit dans un fichier **séparé** (`style.css`). | ✅ **Méthode recommandée** (bonne pratique) |
| **Dans l’en-tête (`<head>`)** | Le CSS est ajouté **dans la page HTML**, entre `<style>...</style>`. | ⚠ **Dépannage uniquement** |
| **Directement dans une balise** | Le CSS est ajouté avec **l’attribut `style`** dans une balise HTML. | ❌ **À éviter !** (mauvaise pratique) |

👉 **Nous utiliserons un fichier `style.css`** pour organiser proprement notre code CSS.  
Habituellement, on place ce fichier dans un dossier `css/`, mais dans **Capytale**, il sera à la racine.  



## 🏗 Exemple d’arborescence d’un site web  

```
/mon-site/
│── index.html
│── page2.html
│── page3.html
│── style.css   ← Notre fichier CSS
│── images/
│   ├── image1.jpg
│   ├── image2.jpg
```
ou :

![](6789.png)

**<H3 STYLE="COLOR:red;">Activité n°1.:</H3>** **Dans `index.html`**, ajouter **le lien vers `style.css`** dans la section `<head>` :

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <link rel="stylesheet" href="style.css">
        <title>Logique sur les passoires</title>
    </head>
```
📌 **Explication** :  

- La balise `<link>` relie notre fichier HTML à la feuille de style CSS (`style.css`).  

- Désormais, **toute la mise en forme sera gérée dans ce fichier !**  

✅ **Enregistrer et observer `index.html`**.



![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.006.png)



**<H3 STYLE="COLOR:red;">Activité n°2.:</H3>** 

Ajoutez **la même ligne** dans `page2.html` :  

```html
<link rel="stylesheet" href="style.css">
```

✅ **Enregistrer et observer `page2.html`**.




**<H3 STYLE="COLOR:red;">Activité n°3.:</H3>** Faire un lien également vers le fichier style.css depuis la page3.html. 

Enregistrer et observer les page2.html et page3.html. 

**Pourquoi utiliser un fichier CSS externe ?**  

✔ **Un seul fichier CSS pour tout le site** : 

   - Si vous changez la couleur du texte **dans `style.css`**, **toutes les pages seront mises à jour automatiquement !**  

✔ **Facilité de maintenance** :  

   - Pas besoin de modifier chaque fichier HTML individuellement.  

📌 **Conclusion :**  

Utiliser un **fichier CSS externe** est **la meilleure pratique** pour créer un site bien organisé et facilement modifiable. 🚀
 

## <H2 STYLE="COLOR:BLUE;">3. Appliquer<a name="_page1_x40.00_y534.92"></a> un style</H2> 


Un fichier CSS est composé de **trois éléments clés** :  

| Élément | Rôle |
|---------|------|
| **Sélecteurs (balises)** | Désignent les éléments HTML à modifier (ex : `p`, `h1`, `div`…) |
| **Propriétés CSS** | Définissent l’effet appliqué (ex : `color`, `font-size`) |
| **Valeurs** | Spécifient comment appliquer la propriété (ex : `red`, `16px`) |

 

### <H3 STYLE="COLOR:GREEN;">3.1. Sélectionner<a name="_page2_x40.00_y67.92"></a> une balise</H3>

On peut appliquer un style à **toutes** les balises d’un même type en écrivant simplement le nom de la balise dans le fichier CSS.

### **Exemple :**
```css
p {
    color: blue;
    font-size: 16px;
}
```

📌 Ici, tous les paragraphes `<p>` auront un texte **bleu** et une taille de **16 pixels**.


**<H3 STYLE="COLOR:red;">Activité n°4.:</H3>** Avec la feuille de style modifier toutes les couleurs des mots entre les balises ```<em>``` et ```<strong>```. 

```css
em
{
    color: red;
}
strong
{
    color : rgb(35, 241, 241) ;
}
```
✅ **Enregistrer et observer les changements sur `index.html`**.


**<H3 STYLE="COLOR:red;">Activité n°5.:</H3>** Dans `style.css`, ajoutez :
```css
h1, h2, h3, h4, h5 {
    color: purple;
}
```
✅ **Enregistrer et observer `index.html`**.

📌 **Note :**  

- En listant plusieurs sélecteurs séparés par une **virgule**, on applique un style à plusieurs éléments en même temps.  

### <H3 STYLE="COLOR:GREEN;">3.2. Les<a name="_page2_x40.00_y258.92"></a> commentaires</H3> 

Les **commentaires** permettent d’expliquer du code **sans qu’il soit interprété par le navigateur**.  

📌 **Syntaxe d’un commentaire en CSS :**
```css
/* Ceci est un commentaire */
```

💡 **Bonne pratique :**  

- Utiliser des commentaires pour organiser et clarifier le code CSS.



### <H3 STYLE="COLOR:GREEN;">3.3. Class<a name="_page2_x40.00_y309.92"></a> et id</H3> 

Parfois, **on ne veut pas appliquer un style à toutes les balises d’un même type**, mais seulement à certaines d’entre elles.  

On utilise alors **les classes (`class`)** et **les identifiants (`id`)**.

#### <H4 STYLE="COLOR:MAGENTA;">3.3.1. L’attribut<a name="_page2_x40.00_y406.92"></a> class</H4>

Une **classe** permet d’appliquer un style **à plusieurs éléments**.  

📌 **Syntaxe en HTML :**  
```html
<p class="important">Ce texte est important.</p>
```

📌 **Syntaxe en CSS :**  
```css
.important {
    color: red;
    font-weight: bold;
}
```
➡ Une classe doit toujours être précédée d’un **point (`.`)** en CSS.

**<H3 STYLE="COLOR:red;">Activité n°6.:</H3>** **Dans `index.html`**, encadrer le théorème avec une balise `<p>` en lui attribuant une **classe** 

```html
    <p class ="theoreme"> …………………………………………..</p>
```


**Dans `style.css`**, ajouter :
```css
.theoreme {
    color: red;
    font-style: italic;
}
```

✅ **Enregistrer et observer `index.html`**.




#### <H4 STYLE="COLOR:MAGENTA;">3.3.2. L’attribut<a name="_page2_x40.00_y639.92"></a> id</H4> 

Un **ID** est utilisé **pour un seul élément unique** sur une page.

📌 **Syntaxe en HTML :**  
```html
<h1 id="titre">Mon titre</h1>
```

📌 **Syntaxe en CSS :**  
```css
#titre {
    color: blue;
    text-align: center;
}
```
➡ Un ID doit toujours être précédé d’un **dièse (`#`)** en CSS.

💡 **Différence entre `class` et `id`** :  

- `class` → Peut être utilisé sur **plusieurs éléments**.  

- `id` → Un seul usage **par page**.


### <H3 STYLE="COLOR:GREEN;">3.4. Les<a name="_page3_x40.00_y36.92"></a> balises universelles</H3> 

Parfois, on veut **modifier une partie du texte** sans ajouter de `<p>`.  

Dans ce cas, on utilise les **balises neutres** :

| Balise | Type | Utilisation |
|--------|------|-------------|
| `<span>` | **Inline** | Modifier **quelques mots** dans un texte |
| `<div>` | **Block** | Regrouper un **ensemble d’éléments** |

**<H3 STYLE="COLOR:red;">Activité n°7.:</H3>** 

1 **Dans `index.html`**, modifier le texte du théorème :
```html
<p>La notion de <span class="passoire">passoires</span> est indépendante de la notion de trous.</p>
```

2 **Dans `style.css`**, ajouter :
```css
.passoire {
    font-weight: bold;
    background-color: yellow;
}
```

✅ **Enregistrer et observer `index.html`**.

📌 **Explication :**

- `<span>` **n’ajoute pas de retour à la ligne**.

- Il permet de modifier uniquement le mot **"passoires"**.

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.018.jpeg)


**Exemple : Différence entre `<div>` et `<span>`**  

**Avec `<div>` (bloc)** :
```html
<div class="citation">
    <p>« Un grand pouvoir implique de grandes responsabilités. »</p>
</div>
```
```css
.citation {
    border: 2px solid black;
    padding: 10px;
    background-color: lightgray;
}
```

**Avec `<span>` (inline)** :
```html
<p>Ce mot est <span class="rouge">rouge</span> !</p>
```
```css
.rouge {
    color: red;
    font-weight: bold;
}
```

📌 **À retenir :**

- `<div>` sert à **structurer** la mise en page.

- `<span>` sert à **modifier une partie du texte** sans créer de nouveau bloc.



### <H3 STYLE="COLOR:GREEN;">3.5. Les<a name="_page3_x40.00_y425.92"></a> sélecteurs avancés</H3> 
- ```*``` est un sélecteur universelle il sélectionne toutes les balises sans exception. 
```css
*
{
}
```
 

- une balise dans une autre : par exemple toutes les balises ```<em>``` **situées à l’intérieur** d’une balise ```<h3>```

```css
h3 em
{
}
```
 

- La balise qui suit une autre : par exemple la première balise ```<p>``` **située après** un titre ```<h3>```
```css
h3 + p
{
}
```


- Une balise possédant un attribut : Sélectionne tous les liens ```<a>``` qui possèdent un **attribut** title.
```css
a[title]
{ 
} 
```
Ce style sera sur : 
```html
<a href="http://site.com" title="Infobulle"> 
```
- Etc … pour une liste complète :[ site du W3C ](https://www.w3.org/Style/CSS-selectors-updates/WD-CSS-selectors-20010126.fr.html#selectors)

## <H2 STYLE="COLOR:BLUE;">4. Formater<a name="_page4_x40.00_y36.92"></a> du texte</H2> 
### <H3 STYLE="COLOR:GREEN;">4.1. Taille<a name="_page4_x40.00_y58.92"></a></H3> 

On utilise la propriété font-size* avec deux techniques pour définir la taille : 

- La taille absolue : en pixels, en cm ou en mm 
- La taille relative : en % , ou nom (small, large, xx-large) ou nombre relatif (1em, 1.3em, 0.8em) qui permet de s’adapter à la taille des visiteurs 
```css
balise 
{ 
    font-size: 16px; 
} 
```

**<H3 STYLE="COLOR:red;">Activité n°8.:</H3>** Modifier la feuille de style pour que les paragraphes est une taille de 120% 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.032.jpeg)

### <H3 STYLE="COLOR:GREEN;">4.2. La<a name="_page4_x40.00_y513.92"></a> police</H3> 

C’est la propriété font-family. On peut définir plusieurs polices pour éviter des problèmes de compatibilité chez l’internaute.  
```css
balise 
{ 
    font-family: police1, police2, police3, police4; 
} 
```

Les polices qui fonctionnent sur la plupart des navigateurs : Arial ; Arial Black ; Comic Sans MS ; Courier New ; Georgia ; Impact ; Times New Roman ; Trebuchet MS ; Verdana. 

Il est possible d’utiliser des polices personnalisées que l’internaute téléchargera automatiquement lors de la visite du site. 

**<H3 STYLE="COLOR:red;">Activité n°9.:</H3>** Modifier la feuille de style pour que les paragraphes est une police en Trebuchet MS. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.034.png)

### <H3 STYLE="COLOR:GREEN;">4.3. Italique,<a name="_page5_x40.00_y342.92"></a> gras, souligné</H3> 

- la propriété ```font-style : normal, italic``` 
- la propriété ```font-weight : normal, bold```
- Le soulignement se traite avec ```text-decoration : underline*,* ou none```

### <H3 STYLE="COLOR:GREEN;">4.4. L’alignement<a name="_page5_x40.00_y410.92"></a></H3> 

On utilise la propriété ```text-align : left``` ou ```center``` ou ```right``` ou ```justify```

**<H3 STYLE="COLOR:red;">Activité n°10.:</H3>** Modifier la feuille de style pour que les paragraphes soient justifiés et centré les images (penser à mettre des nom aux balises des images sur la index) 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.036.jpeg)



## <H2 STYLE="COLOR:BLUE;">5. Ajouter<a name="_page6_x40.00_y36.92"></a> de la couleur et un fond</H2> 
### <H3 STYLE="COLOR:GREEN;">5.1. La<a name="_page6_x40.00_y58.92"></a> couleur du texte</H3> 

On utilise la propriété color suivie   

- Du nom de la couleur : white, silver, gray, red, green, blue, fuchsia, purple*…* ![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.037.png)
- De son code hecadécimal : #FF5A28*, …[* https://htmlcolorcodes.com/fr/ ](https://htmlcolorcodes.com/fr/)*ou[ http://www.colorpicker.com/ ](http://www.colorpicker.com/)
- De son code rgb : rgb(240,96,204)*….[ https://htmlcolorcodes.com/fr/ ](https://htmlcolorcodes.com/fr/)*ou[ http://www.colorpicker.com/ ](http://www.colorpicker.com/)

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.038.jpeg)

### <H3 STYLE="COLOR:GREEN;">5.2. Arrière<a name="_page6_x40.00_y498.92"></a> plan</H3> 

La propriété CSS background est une propriété raccourcie qui permet de définir les différentes valeurs des propriétés liées à la gestion des arrière-plans d'un élément (couleur, image, origine, taille, répétition, etc.). 

#### <H4 STYLE="COLOR:MAGENTA;">5.2.1. Couleur<a name="_page6_x40.00_y547.92"></a> de fond</H4>

On utilise la propriété background-color avec les mêmes propriétés que color*.* Il faut mettre cette propriété sur body


**<H3 STYLE="COLOR:red;">Activité n°11.:</H3>** La couleur de fond d'une page est définie comme suit :  
```css
body
{
    background-color: lightblue;
}
```


Modifier la feuille de style pour que la couleur de fond soit #F3E0C5 
```css
body
{
    background-color: #F3E0C5
}
```
 

Modifier la feuille de style pour que la couleur de fond soit rgb(255,0,0) 
```css
body
{
    background-color: rgb(255,0,0)
}
```
 

Il existe aussi un niveau de transparence avec la notation RGBa. Par exemple :  
```css
p
{
    background-color: rgba(255, 0, 0, 0.5); /* Fond rouge à moitié transparent */
}
``` 



#### <H4 STYLE="COLOR:MAGENTA;">5.2.2. Images<a name="_page7_x40.00_y91.92"></a> de fond</H4>

La propriété permettant d'indiquer une image de fond est ```background-image```. Comme valeur, on doit renseigner ```url("nom_de_l_image.png")```

**<H3 STYLE="COLOR:red;">Activité n°12.:</H3>** Choisir une image neutre sur internet que l’on appellera paper.gif et modifier la feuille de style pour y mettre une image de fond sous forme d’url 
```css
body
{
    background-image: url("paper.gif");
```



##### <H4 STYLE="COLOR:MAGENTA;">5.2.2.1. Répétition d’arrière plan</H4>

Par défaut, la background-image propriété répète une image à la fois horizontalement et verticalement. 

Certaines images doivent être répétées uniquement horizontalement ou verticalement, sinon elles auront l'air étrange, comme ceci 

```css
body
{
    background-image: url("paper.gif");
    background-repeat: repeat-x;
}
```



Le ```background-repeat```: répétition du fond. Par défaut, l'image de fond est répétée en mosaïque 

- ```no-repeat```: le fond ne sera pas répété. L'image sera donc unique sur la page. 
- ```repeat-x```: le fond sera répété uniquement sur la première ligne, horizontalement. 
- ```repeat-y```: le fond sera répété uniquement sur la première colonne, verticalement. 
- ```repeat```: le fond sera répété en mosaïque (par défaut). 

##### <H4 STYLE="COLOR:MAGENTA;">5.2.2.2. Position d’arrière plan</H4>

La ```background-position``` propriété est utilisée pour spécifier la position de l'image d'arrière-plan. 
```css
body
{
    background-image: url("paper.gif");
    background-repeat: repeat-x;
    background-position: right top;
}
```


Le ```background-position``` permet d’indiquer la position du fond par rapport au coin supérieur gauche de la page ou les mots clé ```top, bottom, left```… 

##### <H4 STYLE="COLOR:MAGENTA;">5.2.2.3. Fixe ou scroll de l’arrière plan</H4> 

La ```background-attachment``` propriété spécifie si l'image d'arrière-plan doit défiler ou être fixe (ne défile pas avec le reste de la page) 
```css
body
{
    background-image: url("paper.gif");
    background-repeat: repeat-x;
    background-position: right top;
     background-attachment: scroll;
}
```


Le ```background-attachment```: fixer le fond. Deux valeurs sont disponibles :  

- ```fixed```: l'image de fond reste fixe ; 
- ```scroll```: l'image de fond défile avec le texte (par défaut).

##### <H4 STYLE="COLOR:MAGENTA;">5.2.2.4. Propriétés de l’arrière plan abrégée</H4> 

Pour raccourcir le code, il est également possible de spécifier toutes les propriétés du fond dans une seule propriété. C'est ce qu'on appelle une propriété abrégée. 

```css
body {
    background-color: #ffffff;
    background-image: url("img_tree.png");
    background-repeat: no-repeat;
    background-position: right top;
}
```



On peut écrire une propriété abrégée dans une seule déclaration 

```css
body {
    background: #ffffff url("img_tree.png") no-repeat right top;
  }
```



##### <H4 STYLE="COLOR:MAGENTA;">5.2.2.5. Plusieurs images</H4> 

Depuis CSS, il est possible de donner plusieurs images de fond à un élément. Pour cela, il suffit de séparer les déclarations par une virgule, comme ceci : 

```css
body
{
    background: url("soleil.png") fixed no-repeat top right, url("neige.png") fixed;
}
```


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.049.png)

La première image de cette liste sera placée par-dessus les autres. Attention donc, l'ordre de déclaration des images a son importance : si vous inversez le soleil et la neige dans le code CSS précédent, vous ne verrez plus le soleil ! 

## <H2 STYLE="COLOR:BLUE;">6. Habillage<a name="_page8_x40.00_y542.92"></a></H2> 
![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.050.png)

Le CSS permet de faire flotter un élément autour d'un texte grâce à la propriété CSS ```float```. 

- ```left``` : l'élément flottera à gauche. 
- ```right``` : l'élément flottera à droite.
```html
<p>
    <img src="flash.gif" class="imageflottante" alt="Image flottante" />
</p>
```
```css
.imageflottante
{
    float: left;
}
```
![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.054.png)

Pour ne plus faire flotter l'élément, il faut utiliser la propriété clear, qui peut prendre ces trois valeurs : 

- ```left``` : le texte se poursuit en-dessous après un ```float: left```;
- ```right``` : le texte se poursuit en-dessous après un ```float: right```;
- ```both``` : le texte se poursuit en-dessous, que ce soit après un ```float: left```; ou après un ```float: right```;. 
```html
<p><img src="flash.gif" class="imageflottante" alt="Image flottante" /></p>
<p>Texte écrit à côté de l'image.</p>
<p class="dessous">Texte écrit sous l'image.</p>  
```
```css
.imageflottante
{
    float: left;
}
.dessous
{
    clear: both;
}
```  



## <H2 STYLE="COLOR:BLUE;">7. Créer<a name="_page9_x40.00_y302.92"></a> des bordures et des ombres</H2> 
### <H3 STYLE="COLOR:GREEN;">7.1. Bordures<a name="_page9_x40.00_y324.92"></a> standard</H3> 

Pour ```border``` on peut utiliser jusqu'à trois valeurs pour modifier l'apparence de la bordure : 

- **La largeur** : indiquez la largeur de votre bordure. Mettez une valeur en pixels (comme ```2px```). 
- **La couleur** : c'est la couleur de votre bordure. Utilisez, comme on l'a appris, soit un nom de couleur (black,red,…), soit une valeur hexadécimale (```#FF0000```), soit une valeur RGB (```rgb(198, 212, 37)```). 
- **Le type de bordure** : là, vous avez le choix. Votre bordure peut être un simple trait, ou des pointillés, ou encore des tirets, etc. Voici les différentes valeurs disponibles : 
```none```: pas de bordure (par défaut) ; 
 ```solid```: un trait simple ; 
 ```dotted```: pointillés ; 
 ```double```: bordure double ; 
 *etc* 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.057.png)

Ainsi, pour avoir une bordure bleue, en tirets, épaisse de 3 pixels autour de mes titres, je vais écrire : 

```css
h1
{
    border: 3px blue dashed;
}
```

 

Des bordures différentes en fonction du côté : 

- ```border-top```: bordure du haut ; 
- ```border-bottom```: bordure du bas ; 
- ```border-left```: bordure de gauche ; 
- ```border-right```: bordure de droite. 

### <H3 STYLE="COLOR:GREEN;">7.2. Bordures<a name="_page10_x40.00_y115.92"></a> arrondies</H3> 

La propriété ```border-radius``` va nous permettre d'arrondir facilement les angles de n'importe quel élément. Il suffit d'indiquer la taille (« l'importance ») de l'arrondi en pixels, par exemple : ```border-radius : 10px```; 

**<H3 STYLE="COLOR:red;">Activité n°13.:</H3>** Modifier la feuille de style pour que le théorème soit entouré d’une bordure arrondie, d’une couleur, de style de traits et d’épaisseur au choix. Centrer le théorème. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.061.jpeg)

### <H3 STYLE="COLOR:GREEN;">7.3. Les<a name="_page10_x40.00_y299.92"></a> ombres</H3> 

Il est possible de mettre des ombres portés sur : 

- Des boites : la propriété ```box-shadow``` s'applique à tout le bloc et prend quatre valeurs dans l'ordre suivant 

le décalage horizontal de l'ombre ; 
le décalage vertical de l'ombre ; 
L’adoucissement du dégradé ; 
la couleur de l'ombre. 

Par exemple, pour une ombre noire de 6 pixels, sans adoucissement, on écrira :   
```css
p
{
    box-shadow: 6px 6px 0px black;
}
```


- du texte : avec ```text-shadow```  qui a le même fonctionnement 

**<H3 STYLE="COLOR:red;">Activité n°14.:</H3>** Modifier la feuille de style pour que le théorème est une ombre portée sur sa bordure. 
![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.066.jpeg)

## <H2 STYLE="COLOR:BLUE;">8. Les<a name="_page10_x40.00_y621.92"></a> apparences dynamiques</H2> 

En CSS, on peut modifier l'apparence de certaines sections dynamiquement, après le chargement de la page, lorsque certains évènements se produisent. On utilise pour cela les pseudo-formats. 

- ```:hover``` permet de changer l'apparence au survol (par exemple : a:hover pour modifier l'apparence des liens lorsque la souris pointe dessus). 
- ```:active``` applique un style particulier au moment du clic. En pratique, il n'est utilisé que sur les liens.

 
- ```:focus``` applique un style lorsque l'élément est sélectionné. 
- ```:visited``` applique un style à un lien vers une page qui a déjà été vue. 

### <H3 STYLE="COLOR:GREEN;">8.1. Au<a name="_page11_x40.00_y36.92"></a> survol</H3> 

Lorsque la souris survole quelque chose on peut prévoir un style différent. Par exemple : 

```css
a /* Liens par défaut (non survolés) */
{
   text-decoration: none;
   color: red;
   font-style: italic;
}

a:hover /* Apparence au survol des liens */
{
   text-decoration: underline;
   color: green;
}
```



### <H3 STYLE="COLOR:GREEN;">8.2. Au<a name="_page11_x40.00_y195.92"></a> clic</H3> 

On peut par exemple changer la couleur de fond du lien lorsque l'on clique dessus : 
```css
a:active /* Quand le visiteur clique sur le lien */
{
    background-color: #FFCC66;
}
```


### <H3 STYLE="COLOR:GREEN;">8.3. Le<a name="_page11_x40.00_y276.92"></a> lien déjà visité</H3> 

On peut changer cette apparence avec: *visited* (qui signifie « visité »).  
```css
a:visited /* Quand le visiteur a déjà vu la page concernée */
{
    color: #AAA; /* Appliquer une couleur grise */
}
```


## <H2 STYLE="COLOR:BLUE;">9. Les<a name="_page11_x40.00_y351.92"></a> tableaux</H2> 
### <H3 STYLE="COLOR:GREEN;">9.1. Un<a name="_page11_x40.00_y389.92"></a> tableau simple</H3> 

On utilise la balise ```<table></table>```. Puis il faut indiquer le début et la fin de chaque ligne : ```<tr></tr>```. A l’intérieur de chaque ligne, il faut définir toutes les cellules avec ```<td></td>```. 

Par exemple : 
```html
<table>
   <tr>
       <td>Carmen</td>
       <td>33 ans</td>
       <td>Espagne</td>
   </tr>
   <tr>
       <td>Michelle</td>
       <td>26 ans</td>
       <td>États-Unis</td>
   </tr>
</table>
```


Il faut prendre le soin d’indiquer le type de bordure pour les cellules et/ou les lignes dans la feuille de style css. Par exemple : 

```css
table 
{ 
border-collapse: collapse; /* Les bordures du tableau seront collées (plus joli) */ 
} 
td 
{ 
border: 1px solid black; 
}
```



### <H3 STYLE="COLOR:GREEN;">9.2. L’en<a name="_page11_x40.00_y705.92"></a> tête</H3> 

La ligne d'en-tête est très facile à reconnaître pour deux raisons : 

- les cellules sont des ```<th>``` au lieu des ```<td>``` habituels ; 

- c'est la première ligne du tableau 

### <H3 STYLE="COLOR:GREEN;">9.3. Titre<a name="_page12_x40.00_y36.92"></a> du tableau</H3> 

Il est à mettre dans la balise ```  <caption></caption>```  juste après la balise ```<table>```

On peut changer la position du titre avec la propriété CSS ```caption-side``` qui peut prendre deux valeurs : 

- ```top```: le titre sera placé au-dessus du tableau (par défaut) ; 
- ```bottom```: le titre sera placé en dessous du tableau.

### <H3 STYLE="COLOR:GREEN;">9.4. Gros<a name="_page12_x40.00_y120.92"></a> tableau</H3>

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.076.png)

Il existe des balises HTML qui permettent de  définir les trois « zones » du tableau :  

- l'en-tête (en haut) : il se définit avec  les balises ```<thead></thead>```; 
- le corps (au centre) : il se définit avec  les balises ```<tbody></tbody>```;   
- le  pied  du  tableau  (en  bas)  :  il  se  définit  avec  les  balises  ```<tfoot></tfoot>```*.*  

### <H3 STYLE="COLOR:GREEN;">9.5. Fusionner<a name="_page12_x40.00_y268.92"></a></H3>   
- La fusion de colonnes : c'est ce que je viens de faire dans cet exemple. La fusion s'effectue horizontalement. On utilisera l'attribut ```colspan```.
- La fusion de lignes : là, deux lignes seront groupées entre elles. La fusion s'effectuera verticalement. On utilisera l'attribut ```rowspan```.

Par exemple :

```html
<table>
   <tr>
       <th>Titre du film</th>
       <th>Pour enfants ?</th>
       <th>Pour adolescents ?</th>
   </tr>
   <tr>
       <td>Massacre à la tronçonneuse</td>
       <td >Non, trop violent</td>
       <td>Oui</td>
   </tr>
   <tr>
       <td>Les bisounours font du ski</td>
       <td>Oui, adapté</td>
       <td>Pas assez violent...</td>
   </tr>
   <tr>
       <td>Lucky Luke, seul contre tous</td>
       <td colspan="2">Pour toute la famille !</td>
   </tr>
</table>
```


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.078.jpeg)

**<H3 STYLE="COLOR:red;">Activité n°15.:</H3>** Rajouter un tableau résumé à la fin de la index. Modifier la feuille de style pour que le tableau ressemble à l’image ci-dessous. Penser à nommer les balise pour les utiliser en css. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.079.png)![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.080.png)

## <H2 STYLE="COLOR:BLUE;">10. Le<a name="_page13_x40.00_y36.92"></a> modèle des boites</H2>

Dans une mise en page réalisée en CSS, tous les éléments sont considérés comme des boîtes. Chacune de ces boîtes est constituée d’un contenu, d’un espacement intérieur, d’une bordure, et d’une marge externe. 

Voici les  propriétés  CSS  qui  permettent  de  déterminer  les  dimensions, la  couleur,  le style  de chacun  de  ses constituants : 



|**Propriété CSS** |**Ce qui est concerné :** |
| - | - |
|```width``` et ```height``` |largeur et hauteur du contenu (texte, image, etc.) |
|```padding``` |espacement intérieur, entre le contenu et la bordure |
|```border``` |bordure (ou encadrement) |
|```margin``` |marge externe, espace (transparent) entourant le tout |

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.082.png)![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.081.png)

- ```width``` : c'est la largeur du bloc exprimé en pixels (px) ou en pourcentage (%). 
- ```height``` : c'est la hauteur du bloc exprimé en pixels (px) ou en pourcentage (%). 
- ```padding``` : indique la taille de la marge intérieure en pixels (px). 
- ```margin``` : indique la taille de la marge extérieure en pixels (px). 

Un bloc peut avoir des dimensions minimales et maximales : 

- ```min-width``` : largeur minimale ; 
- ```min-height``` : hauteur minimale ; 
- ```max-width``` : largeur maximale ; 
- ```max-height``` : hauteur maximale. 

Les marges extérieures peuvent avoir des valeurs différentes : 

- ```margin-top``` : marge extérieure en haut ; 
- ```margin-bottom``` : marge extérieure en bas ; 
- ```margin-left``` : marge extérieure à gauche ; 
- ```margin-right``` : marge extérieure à droite. 

Idem pour les marges intérieures ! 

Exemple : 
```css
p
{
   width: 350px;
   border: 1px solid black;
   text-align: justify;
   padding: 12px;
   margin: 50px; /* Marge extérieure de 50px */
}
```



![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.088.jpeg)

Remarque : utiliser la propriété ```margin: auto``` pour centrer des blocs. Pour cela, il faut obligatoirement donner une largeur au bloc (avec la propriété ```width```). 

Exemple : 

```css
p
{
    width: 350px; /* On a indiqué une largeur (obligatoire) */
    margin: auto; /* On peut donc demander à ce que le bloc soit centré avec auto */
}
```


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.091.jpeg)

Si vous voulez que le texte ne dépasse pas des limites du bloc, il va falloir utiliser la propriété ```overflow```. Voici les valeurs qu'elle peut accepter : 

- ```visible``` (par défaut) : si le texte dépasse les limites de taille, il reste visible et sort volontairement du bloc. 
- ```hidden``` : si le texte dépasse les limites, il sera tout simplement coupé. On ne pourra pas voir tout le texte. 
- ```scroll``` : le texte sera coupé s'il dépasse les limites. Sauf que cette fois, le navigateur mettra en place des barres de défilement pour qu'on puisse lire l'ensemble du texte. 
- ```auto``` : le navigateur décide de mettre ou non des barres de défilement. 

Remarque : la propriété ```word-wrap: break-word``` permet de forcer la césure des très longs mots (généralement des adresses un peu longues). 

## <H2 STYLE="COLOR:BLUE;">11. Le<a name="_page15_x40.00_y36.92"></a> positionnement</H2> 
### <H3 STYLE="COLOR:GREEN;">11.1. Les<a name="_page15_x40.00_y58.92"></a> positionnements absolu, fixe et relatif</H3> 

La propriété CSS ```position``` permet de positionner avec précision des éléments sur la page. Pour cela, on lui donne une de ces valeurs : 

- ```absolute``` : positionnement absolu ; il permet de placer un élément n'importe où sur la page (en haut à gauche, en bas à droite, tout au centre, etc.). 
- ```fixed``` : positionnement fixe ; identique au positionnement absolu mais, cette fois, l'élément reste toujours visible, même si on descend plus bas dans la page. 
- ```relative``` : positionnement relatif ; ce positionnement permet d'effectuer des « ajustements » : l'élément est décalé par rapport à sa position initiale. 

Si un bloc est positionné en absolu, il faut indiquer au navigateur où le positionner sur la page à l'aide des quatre propriétés CSS : 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.093.png)

- ```left``` : position par rapport à la gauche de la page ; 
- ```right``` : position par rapport à la droite de la page ;
- ```top``` : position par rapport au haut de la page ; 
- ```bottom``` : position par rapport au bas de la page. 

Exemple : 
```css
element
{
    position: absolute;
    right: 0px;
    bottom: 0px;
}
```


Remarque : les éléments positionnés en absolu sont placés par- dessus le reste des éléments de la page ! Par ailleurs, si vous placez deux éléments en absolu vers le même endroit, ils risquent de se chevaucher.  Dans  ce  cas,  utilisez  la propriété ```z-index```  pour indiquer quel élément doit apparaître au-dessus des autres. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.097.png) 

L'élément ayant la valeur de ```z-index``` la plus élevée sera placé par-dessus les autres, comme le montre la figure ci-contre. 

### <H3 STYLE="COLOR:GREEN;">11.2. Le<a name="_page15_x40.00_y697.92"></a> positionnement inline-block</H3> 

En CSS la propriété ```display``` permet de transformer n'importe quel élément de la page d'un type vers un autre et les faire apparaître sous forme de blocs. À ce moment-là, les éléments vont se positionner les uns en-dessous des autres et il devient possible de modifier leurs dimensions ! 

Voici quelques-unes des principales valeurs que peut prendre la propriété ```display``` : 

|**Valeur** |**Exemples** |**Description** |
| - | - | - |
|```inline``` |```<a>, <em>, <span>```…|Eléments d'une ligne. Se placent les uns à côté des autres. |
|```block``` |```<p>, <div>, <section>```… |Eléments en forme de blocs. Se placent les uns en-dessous des autres et peuvent être redimensionnés. |
|```inline-block``` |```<select>, <input>``` |Eléments positionnés les uns à côté des autres (comme les inlines) mais qui peuvent être redimensionnés (comme les blocs). |
|```none``` |```<head>``` |Eléments non affichés. |

Les éléments en ```inline-block``` nous permet d'utiliser la propriété ```vertical-align```. Cette propriété permet de modifier l'alignement vertical des éléments. Voici quelques-unes des valeurs possibles pour cette propriété : 

- ```baseline``` : aligne de la base de l'élément avec celle de l'élément parent (par défaut) ; 
- ```top``` : aligne en haut ; 
- ```middle``` : centre verticalement ;
- ```bottom``` : aligne en bas ; 
- (valeur en px ou %) : aligne à une certaine distance de la ligne de base (```baseline```). 

NB : les éléments ```inline-block``` se positionnent sur une même ligne de base (appelée ```baseline```), en bas. Exemple : nous voulons réaliser la page suivante.  

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.101.jpeg)

Donnons le code HTML correspondant...  
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <link rel="stylesheet" href="style.css" />
        <title>Zozor - Le Site Web</title>
    </head>
    <body>
        <header>
            <h1>Zozor</h1>
            <h2>Carnets de voyage</h2>
        </header>
        
        <nav>
            <ul>
                <li><a href="accueil.html">Accueil</a></li>
                <li><a href="blog.html">Blog</a></li>
                <li><a href="cv.html">CV</a></li>
            </ul>
        </nav>
        
        <section>
            <aside>
                <h1>À propos de l'auteur</h1>
                <p>C'est moi, Zozor ! Je suis né un 23 novembre 2005.</p>
            </aside>
            <article>                
                <h1>Je suis un grand voyageur</h1>
                <p>Bla bla bla bla (texte de l'article)</p>
            </article>
        </section>
        
        <footer>
            <p>Copyright Zozor - Tous droits réservés
            <a href="mailto:zorro@monsite.org">Me contacter !</a></p>
        </footer>
    </body>
</html>
```

...et le code CSS associé. 
```css
nav
{
    display: inline-block;
    width: 150px;
    border: 1px solid black;
    vertical-align: top;
}
section
{
    display: inline-block;    
    border: 1px solid blue;
    vertical-align: top;
}

```
 

 

## <H2 STYLE="COLOR:BLUE;">12. Squelette<a name="_page17_x40.00_y239.92"></a> de base HTML – CSS</H2> 

Le squelette d’une page web possède souvent une structure de base à cinq blocs principaux. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.108.png)

Cette structure de base à cinq blocs principaux convient dans la majorité des cas, car elle permet de fabriquer une grande variété de mises en page.
```html
<!DOCTYPE html>
<html>
<head>
        <title>Titre de la page</title>
        <link rel="stylesheet" href="style.css"/>
</head>
<body>
         <div class="header">En-tête</div>
         <div class="nav">Navigation</div>
         <div class="content">Contenu</div>
         <div class="aside">Contexte</div>
         <div class="footer">Pied de page</div>
</body>
</html>
```
```css
/* Mes styles */

.header {….}

.nav {….}

.content {….}

.aside {….}

.footer {….}

```

Il existe sur le web des collections de modèles de mise en page, à télécharger gratuitement.
 
Exemple : «[ Layout Gala ](http://blog.html.it/layoutgala/)» 
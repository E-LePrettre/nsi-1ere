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

Les **sélecteurs avancés** permettent de **cibler des éléments précis** et d’affiner le style appliqué.

📌 **Sélecteur universel `*`**

Ce sélecteur applique un style à **toutes les balises** d’une page HTML.

```css
* {
    margin: 0;
    padding: 0;
}
```
**Utilisation** : Supprime **les marges et les paddings** par défaut.



📌 **Sélecteur descendant**

Sélectionne une **balise située à l’intérieur** d’une autre.

```css
h3 em {
    color: red;
}
```

**Applique la couleur rouge** uniquement aux `<em>` **situés dans** un `<h3>`.


📌 **Sélecteur adjacent**  

Cible un élément **juste après** un autre.

```css
h3 + p {
    font-weight: bold;
}
```
**Le premier `<p>` après un `<h3>`** sera en **gras**.


📌 **Sélecteur d’attribut**

Cible **les balises ayant un attribut spécifique**.

```css
a[title] {
    text-decoration: underline;
}
```
**Tous les liens `<a>` ayant un attribut `title` seront soulignés**.

✏️ **Consultez la documentation complète**

➡ Pour plus d’exemples, voir : [Sélecteurs CSS W3C](https://www.w3.org/Style/CSS-selectors-updates/WD-CSS-selectors-20010126.fr.html#selectors).



## <H2 STYLE="COLOR:BLUE;">4. Formater<a name="_page4_x40.00_y36.92"></a> du texte</H2>

Le CSS permet de modifier **la taille, la police, l’alignement et la mise en forme** du texte.


### <H3 STYLE="COLOR:GREEN;">4.1. Taille<a name="_page4_x40.00_y58.92"></a></H3> 

La taille du texte est définie avec la propriété `font-size`.  

Il existe **deux types de tailles** :

| Type | Unités | Exemple |
|------|--------|---------|
| **Absolue** | `px`, `cm`, `mm` | `font-size: 16px;` |
| **Relative** | `%`, `em`, `rem`, `small`, `large` | `font-size: 120%;` |

📌 **Recommandation** :  

- **Préférez les tailles relatives** (`%`, `em`, `rem`) pour **s’adapter aux écrans**.


**<H3 STYLE="COLOR:red;">Activité n°8.:</H3>** Dans `style.css`, ajoutez :
```css
p {
    font-size: 120%;
}
```
✅ **Enregistrer et observer `index.html`**.

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.032.jpeg)

### <H3 STYLE="COLOR:GREEN;">4.2. La<a name="_page4_x40.00_y513.92"></a> police</H3> 

La police est définie avec `font-family`.  

Il est possible de spécifier **plusieurs polices**, au cas où la première n’est pas disponible.

```css
p {
    font-family: "Trebuchet MS", Arial, sans-serif;
}
```
📌 **Ordre de préférence** :  

- `"Trebuchet MS"` → Première police souhaitée. 

- `Arial` → Alternative si Trebuchet MS est absente.  

- `sans-serif` → Police générique.


**<H3 STYLE="COLOR:red;">Activité n°9.:</H3>** Modifier la feuille de style pour que les paragraphes est une police en Trebuchet MS. 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.034.png)

✅ **Enregistrer et observer `index.html`**.

### <H3 STYLE="COLOR:GREEN;">4.3. Italique,<a name="_page5_x40.00_y342.92"></a> gras, souligné</H3> 

Les principales propriétés sont :

| Effet | Propriété CSS | Valeurs |
|-------|--------------|---------|
| **Italique** | `font-style` | `normal`, `italic` |
| **Gras** | `font-weight` | `normal`, `bold` |
| **Souligné** | `text-decoration` | `none`, `underline` |

**Exemple :**
```css
p {
    font-style: italic;
    font-weight: bold;
    text-decoration: underline;
}
```
📌 **Recommandation** : Évitez d’abuser du **soulignement**, il est souvent utilisé pour les liens.


### <H3 STYLE="COLOR:GREEN;">4.4. L’alignement<a name="_page5_x40.00_y410.92"></a></H3> 

Le texte peut être **aligné** avec la propriété `text-align` :

| Valeur | Effet |
|--------|-------|
| `left` | Aligné à gauche (par défaut) |
| `center` | Centré |
| `right` | Aligné à droite |
| `justify` | Justifié (alignement des deux côtés) |

**Exemple :**  
```css
p {
    text-align: justify;
}
```

📌 **Les images peuvent aussi être centrées !**  
Avec `display: block;` et `margin: auto;` :
```css
img {
    display: block;
    margin: auto;
}
```
`

**<H3 STYLE="COLOR:red;">Activité n°10.:</H3>** Modifier la feuille de style pour que les paragraphes soient justifiés et centré les images (penser à mettre des nom aux balises des images sur la index) 

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.036.jpeg)

✅ **Enregistrer et observer `index.html`**.

## <H2 STYLE="COLOR:BLUE;">5. Ajouter<a name="_page6_x40.00_y36.92"></a> de la couleur et un fond</H2> 

Le CSS permet **d’améliorer l’apparence** d’une page web en modifiant **la couleur du texte et du fond**.

### <H3 STYLE="COLOR:GREEN;">5.1. La<a name="_page6_x40.00_y58.92"></a> couleur du texte</H3> 

La propriété `color` permet de changer la couleur du texte.  

📌 **Trois façons de définir une couleur :**  

| Méthode | Exemple |
|---------|---------|
| **Nom de couleur** | `color: red;` |
| **Code hexadécimal** | `color: #FF5A28;` |
| **Code RGB** | `color: rgb(240,96,204);` |

💡 **Outils pratiques pour choisir une couleur :**  

🎨 [HTML Color Codes](https://htmlcolorcodes.com/fr/)  

🎨 [Color Picker](http://www.colorpicker.com/)  


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.038.jpeg)

**<H3 STYLE="COLOR:red;">Activité n°11.:</H3>** Ajoutez cette règle dans `style.css` :
```css
body {
    background-color: #F3E0C5;
}
```

📌 **Expérimentez** en essayant ces variantes :  
```css
body {
    background-color: rgb(255, 0, 0); /* Rouge */
}
```
```css
p {
    background-color: rgba(255, 0, 0, 0.5); /* Fond rouge semi-transparent */
}
```

✅ **Enregistrer et observer `index.html`**.

### <H3 STYLE="COLOR:GREEN;">5.2. Arrière<a name="_page6_x40.00_y498.92"></a> plan</H3> 


La propriété `background-image` permet d’ajouter une **image de fond**.

📌 **Syntaxe de base :**
```css
body {
    background-image: url("paper.gif");
}
```






**<H3 STYLE="COLOR:red;">Activité n°12.:</H3>** 
1 Trouvez une **image neutre** et nommez-la `paper.gif`. 

2 Ajoutez-la dans le **même dossier** que votre fichier CSS.  

3 Modifiez `style.css` pour appliquer l’image en fond :
```css
body {
    background-image: url("paper.gif");
}
```

✅ **Enregistrer et observer `index.html`**.



##### <H4 STYLE="COLOR:MAGENTA;">5.2.1. Répétition d’arrière plan</H4>

Par défaut, une image de fond est **répétée** en mosaïque.  

📌 **Contrôler la répétition du fond avec `background-repeat` :**  
```css
background-repeat: no-repeat; /* Aucune répétition */
background-repeat: repeat-x; /* Répétition horizontale */
background-repeat: repeat-y; /* Répétition verticale */
background-repeat: repeat; /* Par défaut, en mosaïque */
```

##### <H4 STYLE="COLOR:MAGENTA;">5.2.2. Position d’arrière plan</H4>

On utilise `background-position` pour **placer l’image** dans la page.

📌 **Exemple :**
```css
background-position: right top; /* En haut à droite */
background-position: center; /* Centré */
```


##### <H4 STYLE="COLOR:MAGENTA;">5.2.3. Fixe ou scroll de l’arrière plan</H4> 


La propriété `background-attachment` permet **de fixer ou faire défiler l’image de fond**.

📌 **Exemple :**
```css
background-attachment: fixed; /* L’image reste fixe */
background-attachment: scroll; /* L’image défile avec la page */
```


##### <H4 STYLE="COLOR:MAGENTA;">5.2.4. Propriétés abrégée de l’arrière plan</H4> 

On peut **regrouper toutes ces propriétés** en une seule ligne :

```css
body {
    background-color: #ffffff;
    background-image: url("img_tree.png");
    background-repeat: no-repeat;
    background-position: right top;
    background-attachment: fixed;
}
```



On peut écrire une propriété abrégée dans une seule déclaration 

```css
body {
    background: #ffffff url("img_tree.png") no-repeat right top fixed;
  }
```

📌 **Ordre des valeurs :** `couleur`, `image`, `répétition`, `position`, `défilement`.

##### <H4 STYLE="COLOR:MAGENTA;">5.2.5. Plusieurs images</H4> 

Depuis CSS3, il est possible **d’empiler plusieurs images de fond** :

```css
body {
    background: url("soleil.png") fixed no-repeat top right,
                url("neige.png") fixed;
}
```

📌 **L’ordre des images est important** : la **première** s’affiche **au-dessus** des autres.




![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.049.png)

La première image de cette liste sera placée par-dessus les autres. Attention donc, l'ordre de déclaration des images a son importance : si vous inversez le soleil et la neige dans le code CSS précédent, vous ne verrez plus le soleil ! 

## <H2 STYLE="COLOR:BLUE;">6. Habillage<a name="_page8_x40.00_y542.92"></a></H2> 

La propriété `float` permet **de positionner une image à gauche ou à droite du texte**.



### <H3 STYLE="COLOR:GREEN;"> **6.1. Flotter un élément à gauche ou à droite</h3>**  

📌 **Exemple :**
```html
<p>
    <img src="flash.gif" class="imageflottante" alt="Image flottante" />
</p>
```
```css
.imageflottante {
    float: left;
    margin-right: 10px;
}
```

➡ L’image sera **alignée à gauche** avec un **espace de 10px à droite**.


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.050.png)

### <H3 STYLE="COLOR:GREEN;"> **6.2. Stopper l’effet float avec `clear`</h3>**  

Si on ne stoppe pas le `float`, **le texte continue à s’enrouler autour de l’image**.  
La propriété `clear` permet **de forcer un retour à la ligne**.

📌 **Exemple :**
```html
<p><img src="flash.gif" class="imageflottante" alt="Image flottante" /></p>
<p>Texte écrit à côté de l'image.</p>
<p class="dessous">Texte écrit sous l'image.</p>  
```
```css
.imageflottante {
    float: left;
}
.dessous {
    clear: both;
}
```

📌 **Explication :**  
- **`clear: left;`** → Le texte **reprend après une image flottant à gauche**.  
- **`clear: right;`** → Le texte **reprend après une image flottant à droite**.  
- **`clear: both;`** → Le texte **reprend après n’importe quelle image flottante**.  


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.054.png)



## <H2 STYLE="COLOR:BLUE;">7. Créer<a name="_page9_x40.00_y302.92"></a> des bordures et des ombres</H2> 

Les bordures et les ombres permettent d’améliorer la mise en forme des éléments en les encadrant ou en leur ajoutant un effet de relief.

### <H3 STYLE="COLOR:GREEN;">7.1. Bordures<a name="_page9_x40.00_y324.92"></a> standard</H3> 

La propriété `border` permet de définir une bordure sur un élément HTML. 

Elle prend **trois paramètres** :

| Paramètre | Description | Exemple |
|-----------|-------------|---------|
| **Largeur** | Épaisseur de la bordure (en `px`, `em`, etc.) | `3px` |
| **Type** | Style de la bordure | `solid`, `dashed`, `dotted`, `double`… |
| **Couleur** | Couleur de la bordure | `red`, `#FF0000`, `rgb(198, 212, 37)` |

📌 **Exemple :**
```css
h1 {
    border: 3px blue dashed;
}
```

➡ **Résultat** : Une **bordure bleue en tirets** de `3px` autour des `<h1>`.



**Bordures spécifiques**  

Il est possible d’appliquer une bordure **uniquement sur un côté** :

| Propriété | Effet |
|-----------|-------|
| `border-top` | Bordure en haut |
| `border-bottom` | Bordure en bas |
| `border-left` | Bordure à gauche |
| `border-right` | Bordure à droite |

📌 **Exemple :**
```css
p {
    border-bottom: 2px solid black;
}
```

➡ **Résultat** : Un **trait noir sous les paragraphes**.




![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.057.png)


### <H3 STYLE="COLOR:GREEN;">7.2. Bordures<a name="_page10_x40.00_y115.92"></a> arrondies</H3> 

La propriété `border-radius` permet d’arrondir les angles d’un élément.

📌 **Exemple :**
```css
div {
    border: 2px solid black;
    border-radius: 10px;
}
```

➡ **Résultat** : Un encadrement **avec des coins arrondis de 10px**.
 

**<H3 STYLE="COLOR:red;">Activité n°13.:</H3>** Ajouter une bordure au théorème**  
Dans `style.css`, ajoutez :
```css
.theoreme {
    border: 4px solid #FF5733; /* Bordure orange */
    border-radius: 15px; /* Coins arrondis */
    text-align: center; /* Centrer le texte */
    padding: 10px; /* Espacement intérieur */
    width: 50%;
    margin: auto; /* Centrer le bloc */
}
```

✅ **Enregistrer et observer `index.html`**.

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.061.jpeg)

### <H3 STYLE="COLOR:GREEN;">7.3. Les<a name="_page10_x40.00_y299.92"></a> ombres</H3> 

Les **ombres** permettent d’ajouter du relief aux éléments.

📌 **Ombre sur un bloc avec `box-shadow`** :
```css
p {
    box-shadow: 6px 6px 0px black;
}
```
📌 **Ombre sur du texte avec `text-shadow`** :
```css
h1 {
    text-shadow: 3px 3px 5px gray;
}
```

➡ **Résultat** : Un **effet d’ombre** qui donne un aspect **en relief**.



**<H3 STYLE="COLOR:red;">Activité n°14.:</H3>** ### ✏️ **Activité n°14 : Ajouter une ombre au théorème**  
Dans `style.css`, ajoutez :
```css
.theoreme {
    box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}
```

✅ **Enregistrer et observer `index.html`**.

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.066.jpeg)

## <H2 STYLE="COLOR:BLUE;">8. Les<a name="_page10_x40.00_y621.92"></a> apparences dynamiques</H2> 


Le CSS permet **de modifier l’apparence des éléments en fonction des interactions de l’utilisateur**.

| Pseudo-classe | Effet |
|--------------|--------|
| `:hover` | Changement au survol de la souris |
| `:active` | Changement au moment du clic |
| `:focus` | Changement quand l’élément est sélectionné |
| `:visited` | Changement sur un lien déjà visité |

### <H3 STYLE="COLOR:GREEN;">8.1. Au<a name="_page11_x40.00_y36.92"></a> survol</H3> 

📌 **Exemple :**
```css
a {
    text-decoration: none;
    color: red;
    font-style: italic;
}

a:hover {
    text-decoration: underline;
    color: green;
}
```
➡ **Résultat** :  
- Les **liens sont rouges** par défaut.  
- Quand on **passe la souris**, ils deviennent **verts et soulignés**.




### <H3 STYLE="COLOR:GREEN;">8.2. Modifier<a name="_page11_x40.00_y195.92"></a> l'apparence d'un clic</H3> 

📌 **Exemple :**
```css
a:active {
    background-color: #FFCC66;
}
```
➡ **Résultat** : Lien **coloré en orange au moment du clic**.

---

## **8.3. Modifier l’apparence d’un lien déjà visité (`:visited`)**  

📌 **Exemple :**
```css
a:visited {
    color: #AAA;
}
```
➡ **Résultat** : **Les liens déjà visités** apparaissent en **gris**.






## <H2 STYLE="COLOR:BLUE;">9. Les<a name="_page11_x40.00_y351.92"></a> tableaux</H2>


Les tableaux en HTML peuvent être améliorés avec CSS.


### <H3 STYLE="COLOR:GREEN;">9.1. Un<a name="_page11_x40.00_y389.92"></a> tableau simple</H3> 

📌 **HTML :**
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

📌 **CSS :**
```css
table {
    border-collapse: collapse;
}

td {
    border: 1px solid black;
    padding: 5px;
}
```




### <H3 STYLE="COLOR:GREEN;">9.2. Ajouter une ligne d’en<a name="_page11_x40.00_y705.92"></a> tête</H3> 

📌 **HTML :**
```html
<tr>
    <th>Nom</th>
    <th>Âge</th>
    <th>Pays</th>
</tr>
```

📌 **CSS :**
```css
th {
    background-color: lightgray;
}
```


### <H3 STYLE="COLOR:GREEN;">9.3. Ajouter un titre<a name="_page12_x40.00_y36.92"></a> du tableau</H3> 

📌 **HTML :**
```html
<table>
   <caption>Informations des utilisateurs</caption>
</table>
```

📌 **CSS :**
```css
caption {
    font-weight: bold;
    caption-side: bottom;
}
```

### <H3 STYLE="COLOR:GREEN;">9.4. Fusionner<a name="_page12_x40.00_y120.92"></a> des cellules</H3>

![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.076.png)

Il existe des balises HTML qui permettent de  définir les trois « zones » du tableau :  

- l'en-tête (en haut) : il se définit avec  les balises ```<thead></thead>```; 
- le corps (au centre) : il se définit avec  les balises ```<tbody></tbody>```;   
- le  pied  du  tableau  (en  bas)  :  il  se  définit  avec  les  balises  ```<tfoot></tfoot>```*.*  

### <H3 STYLE="COLOR:GREEN;">9.5. Fusionner<a name="_page12_x40.00_y268.92"></a></H3>   

📌 **HTML :**
```html
<tr>
    <td colspan="2">Fusion de deux colonnes</td>
</tr>
<tr>
    <td rowspan="2">Fusion de deux lignes</td>
</tr>
```



![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.078.jpeg)

**<H3 STYLE="COLOR:red;">Activité n°15.:</H3>** 

1. **Ajoutez un tableau résumé à la fin de `index.html`**.

2. **Modifiez `style.css` pour obtenir un style similaire à l’exemple ci-dessous.**

📌 **CSS recommandé :**
```css
table {
    width: 80%;
    border-collapse: collapse;
    margin: auto;
}

th, td {
    border: 1px solid black;
    padding: 10px;
    text-align: center;
}

th {
    background-color: #EEE;
}
```

✅ **Enregistrer et observer `index.html`**.



![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.079.png)![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.080.png)

## <H2 STYLE="COLOR:BLUE;">10. Le<a name="_page13_x40.00_y36.92"></a> modèle des boites</H2>

n CSS, **tous les éléments sont des boîtes**.  
Chaque boîte est composée de **quatre zones principales** :

| Propriété CSS | Description |
|--------------|-------------|
| `width` et `height` | Définissent la largeur et la hauteur du contenu |
| `padding` | Définit l’espace intérieur entre le contenu et la bordure |
| `border` | Définit la bordure (épaisseur, style, couleur) |
| `margin` | Définit l’espace extérieur autour de l’élément |

📌 **Exemple :**
```css
p {
    width: 350px;
    border: 1px solid black;
    text-align: justify;
    padding: 12px;
    margin: 50px;
}
```


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.082.png)![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.081.png)

**Centrer un élément avec `margin: auto`**  

📌 **Exemple :**
```css
p {
    width: 350px;
    margin: auto;
}
```
➡ L’élément sera **centré horizontalement**.



**Gérer le dépassement de texte avec `overflow`**  

| Valeur | Effet |
|--------|-------|
| `visible` | Le texte dépasse de la boîte |
| `hidden` | Le texte est coupé s’il dépasse |
| `scroll` | Ajoute une barre de défilement si nécessaire |
| `auto` | Ajoute une barre de défilement uniquement si nécessaire |

📌 **Exemple :**
```css
div {
    width: 200px;
    height: 100px;
    overflow: scroll;
}
```



## <H2 STYLE="COLOR:BLUE;">11. Le<a name="_page15_x40.00_y36.92"></a> positionnement</H2> 

La propriété `position` permet **de placer précisément un élément** dans une page.

### <H3 STYLE="COLOR:GREEN;">11.1. Les<a name="_page15_x40.00_y58.92"></a> positionnements absolu, fixe et relatif</H3> 

| Valeur | Effet |
|--------|-------|
| `absolute` | Positionne l’élément **par rapport au parent** |
| `fixed` | L’élément **reste fixe même lors du défilement** |
| `relative` | Décale l’élément **par rapport à sa position normale** |

📌 **Exemple :**
```css
div {
    position: absolute;
    top: 50px;
    left: 100px;
}
```
➡ L’élément sera placé **50px du haut et 100px de la gauche**.



![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.093.png)

*Gérer la superposition avec `z-index`**  

Si plusieurs éléments se chevauchent, la propriété `z-index` détermine **l’ordre d’affichage**.

📌 **Exemple :**
```css
div {
    position: absolute;
    z-index: 10;
}
```
➡ **Plus la valeur est grande, plus l’élément est au premier plan.**


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.097.png) 

L'élément ayant la valeur de ```z-index``` la plus élevée sera placé par-dessus les autres, comme le montre la figure ci-contre. 

### <H3 STYLE="COLOR:GREEN;">11.2. Le<a name="_page15_x40.00_y697.92"></a> positionnement inline-block</H3> 


La propriété `display` permet de modifier l’affichage d’un élément.

| Valeur | Effet |
|--------|-------|
| `inline` | Les éléments se placent **côte à côte** |
| `block` | Les éléments se placent **les uns en-dessous des autres** |
| `inline-block` | Comme `inline`, mais avec la possibilité de **modifier la taille** |

📌 **Exemple :**
```css
nav {
    display: inline-block;
    width: 150px;
    border: 1px solid black;
    vertical-align: top;
}
```

➡ **Les éléments restent alignés horizontalement, mais peuvent être redimensionnés**.


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

La plupart des sites web suivent une **structure de base** composée de **cinq blocs principaux** :

![](https://i.imgur.com/Ru5GFDX.png)


![](Aspose.Words.d520a3b2-fd79-44d0-beb1-46503fd463ef.108.png)

📌 **HTML :**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Titre de la page</title>
    <link rel="stylesheet" href="style.css">
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

📌 **CSS :**
```css
.header, .nav, .content, .aside, .footer {
    padding: 20px;
    margin: 10px;
    border: 1px solid black;
}
```

➡ **Ce modèle est réutilisable pour structurer tout site web.**


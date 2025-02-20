---
author: ELP
title: 08b Interaction client-serveur - Requête
---


**Table des matières** 

1. [Modèle client/serveur=](#_page0_x40.00_y516.92)
1. [Le protocole HTTP=](#_page1_x40.00_y233.92)
3. [Coder l’envoi d’une requête par le navigateur](#_page3_x40.00_y617.92)
4. [APPLICATION : Création d’une page web dynamique](#_page8_x40.00_y503.92)
5. [Exercices](#_page13_x40.00_y36.92)


## **<H2 STYLE="COLOR:BLUE;">1. Modèle<a name="_page0_x40.00_y516.92"></a> client/serveur**</H2>
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.004.png)

Dans un réseau, les **ordinateurs échangent des données**. L’un agit en **client** en **demandant des ressources**, tandis que l’autre joue le rôle de **serveur**, en **répondant aux requêtes** et en fournissant les ressources demandées.

- **Un client** : application qui **envoie des requêtes**.  
- **Un serveur** : application qui **attend et traite des requêtes**.  
- **Exemple :** Un navigateur (client) demande une page web à un serveur.

💡 **Le Web est devenu dynamique** : Les serveurs ne se contentent plus d’envoyer des fichiers statiques, ils génèrent du code HTML à la volée grâce à des langages comme **PHP, Python, Java**.

**Exemple de génération dynamique de HTML avec PHP**
```php
<?php 
$heure = date("H:i"); 
echo "<h1>Bienvenue sur mon site</h1>";
echo "<p>Il est actuellement $heure</p>";
?>
```
💡 **Si le client se connecte à 18h23, le serveur lui enverra :**
```html
<h1>Bienvenue sur mon site</h1>
<p>Il est actuellement 18h23</p>
```



## **<H2 STYLE="COLOR:BLUE;">2. Le<a name="_page1_x40.00_y233.92"></a> protocole HTTP**</H2>
### **<H3 STYLE="COLOR:GREEN;">2.1. Qu’est<a name="_page1_x40.00_y255.92"></a> ce que c’est et quel est son rôle ?**</H3>

Le **HyperText Transfer Protocol (HTTP)** est utilisé pour **envoyer des requêtes** du client au serveur et recevoir une **réponse** en retour.


### **<H3 STYLE="COLOR:GREEN;">2.2. Les<a name="_page1_x40.00_y417.92"></a> codes de statut HTTP**</H3>

Les réponses HTTP contiennent un **code de statut** indiquant le résultat :

| Code | Signification |
|------|--------------|
| **200** | OK (Succès) |
| **301** | Redirection permanente |
| **404** | Page non trouvée |
| **500** | Erreur interne du serveur |

### **<H3 STYLE="COLOR:GREEN;">2.3. Principe<a name="_page1_x40.00_y564.92"></a> d’une requête**</H3>

Lorsqu’un navigateur envoie une requête à un serveur web, cette requête suit une **structure standardisée**.  

**Composition d’une requête HTTP (client vers serveur) :**  

1. **La méthode employée** (`GET`, `POST`, etc.)  
2. **L’URL de la ressource** (`/index.html`)  
3. **La version du protocole** (`HTTP/1.1`)  
4. **Les en-têtes de requête** (informations supplémentaires sur la requête)  
5. **Le corps de la requête (optionnel)** (données envoyées avec `POST`)  



#### **<H4 STYLE="COLOR:MAGENTA;">2.3.1. Ligne de Requête**</H4>
Elle contient **trois éléments principaux** :  

```
GET /index.html HTTP/1.1
```

🔹 **Méthode HTTP** : `GET` (ou `POST`, `PUT`, `DELETE`, etc.)  
🔹 **Ressource demandée** : `/index.html`  
🔹 **Version du protocole** : `HTTP/1.1`  


#### **<H4 STYLE="COLOR:MAGENTA;">2.3.2. En-têtes de Requête (Headers)**</H4>
Les **en-têtes HTTP** apportent des **informations supplémentaires** sur la requête et le client.  

**Exemple de requête avec en-têtes :**
```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml
```
📌 **Explications** :  
- **Host** → Nom du site demandé (`www.example.com`)  
- **User-Agent** → Type de navigateur utilisé (Chrome, Firefox, Edge…)  
- **Accept** → Types de fichiers acceptés (`text/html`, `image/png`, etc.)  



#### **<H4 STYLE="COLOR:MAGENTA;">2.3.3. Transmission des données avec GET et POST**</H4>

**Cas d’un formulaire HTML**  
Un formulaire HTML envoie **des données** vers le serveur en utilisant **GET** ou **POST**.  

**Exemple de formulaire en GET :**
```html
<form method="GET" action="/login">
    <input type="text" name="username" placeholder="Nom d'utilisateur">
    <input type="password" name="password" placeholder="Mot de passe">
    <button type="submit">Se connecter</button>
</form>
```
➡️ **Avec GET, les données sont visibles dans l’URL** :  
```
https://www.example.com/login?username=dupont&password=azerty
```
🚨 **Problème** : La transmission du mot de passe en clair dans l’URL est **dangereuse**.

**Exemple de formulaire en POST :**
```html
<form method="POST" action="/login">
    <input type="text" name="username" placeholder="Nom d'utilisateur">
    <input type="password" name="password" placeholder="Mot de passe">
    <button type="submit">Se connecter</button>
</form>
```
➡️ **Avec POST, les données sont envoyées dans le corps de la requête** et **n’apparaissent pas dans l’URL**.  



#### **<H4 STYLE="COLOR:MAGENTA;">2.3.4. Différences entre GET et POST**</H4>
| Critère  | **GET**  | **POST**  |
|----------|---------|---------|
| **Visibilité des données** | ✔️ Affichées dans l’URL  | ❌ Cachées (envoyées dans le corps) |
| **Utilisation principale** | Demander une ressource  | Envoyer des données au serveur |
| **Longueur des données** | ⚠️ Limitée par l’URL  | ✅ Illimitée (dépend du serveur) |
| **Sécurité** | ❌ Données visibles (ex : mot de passe) | ✔️ Données masquées |
| **Mémorisation dans l’historique** | ✔️ Oui | ❌ Non |
| **Partage d’URL possible** | ✔️ Oui (`?search=info`) | ❌ Non |
| **Exemples d’utilisation** | Recherche sur un site | Connexion, envoi de formulaire |

📌 **Conclusion :**  
- **GET** est utile pour des recherches (`search=informatique`).  
- **POST** est plus adapté pour **des informations sensibles** (connexion, formulaire…).  

🚀 **Bonnes pratiques** :
- **Toujours utiliser POST pour les mots de passe**.  
- **Préférer GET pour des paramètres non sensibles** (ex : tri d’articles sur un site e-commerce).  

#### **<H4 STYLE="COLOR:MAGENTA;">Exemple de requête GET et POST complètes**</H4>

**GET (visible dans l’URL)**
```
GET /search?q=ordinateur HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
```

➡️ Résultat :  
```
https://www.example.com/search?q=ordinateur
```

**POST (invisible dans l’URL)**
```
POST /login HTTP/1.1
Host: www.example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

username=john&password=secret
```
➡️ **Les données sont transmises dans le corps** et **ne sont pas visibles** dans l’URL.



### **<H3 STYLE="COLOR:GREEN;">2.4. Réponse HTTP du Serveur**</H3>

Après qu'un client envoie une requête HTTP, le serveur lui répond en envoyant **trois éléments** :  

1️⃣ **Un code de statut HTTP**  
2️⃣ **Des en-têtes de réponse**  
3️⃣ **Le corps de la réponse** (le contenu demandé : page HTML, JSON, image...) 

#### **<H4 STYLE="COLOR:MAGENTA;">2.4.1. En-têtes de Réponse**</H4>
Les en-têtes de réponse permettent d’indiquer au client comment interpréter la réponse du serveur.

🔹 **Exemple d’une réponse HTTP :**
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 356
Connection: keep-alive
```

📌 **Explication des éléments :**
- `HTTP/1.1 200 OK` → La requête a réussi et le contenu demandé est retourné.  
- `Content-Type: text/html; charset=UTF-8` → La réponse est une page HTML encodée en UTF-8.  
- `Content-Length: 356` → Indique la taille du contenu en octets.  
- `Connection: keep-alive` → Maintient la connexion ouverte pour d’autres requêtes.  

💡 **Remarque** : Les codes de statut HTTP jouent un rôle crucial :
- **200 OK** : Succès de la requête.
- **404 Not Found** : La ressource demandée n’existe pas.
- **500 Internal Server Error** : Problème côté serveur.


#### **<H4 STYLE="COLOR:MAGENTA;">2.4.2. Corps de la Réponse avec PHP**</H4>

Le corps de la réponse HTTP contient le **contenu réel renvoyé au navigateur**.  
Si une page web est demandée, elle est envoyée sous forme de HTML.

🔹 **Exemple d’une page générée dynamiquement avec PHP :**
```php
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Bienvenue</title>
</head>
<body>
    <?php
    // Récupération des données envoyées via une requête POST
    $name = htmlspecialchars($_POST['name']);
    $city = htmlspecialchars($_POST['city']);
    ?>
    <h1>Bienvenue sur mon site, <?php echo $name; ?> de <?php echo $city; ?> !</h1>
    <p>Nous sommes heureux de vous accueillir.</p>
</body>
</html>
```
📌 **Analyse** :
- Le serveur reçoit les données du formulaire via `$_POST['name']` et `$_POST['city']`.  
- `htmlspecialchars()` empêche les failles XSS en filtrant les caractères spéciaux.  
- Le serveur renvoie une page personnalisée au client.



![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.028.jpeg)

#### **<H4 STYLE="COLOR:MAGENTA;">2.4.3. HTTPS : Sécurisation des échanges**</H4>

🔹 **Différence entre HTTP et HTTPS**  
- **HTTP** : Les données **transitent en clair** sur le réseau.  
- **HTTPS** : Les données sont **chiffrées** grâce au protocole **TLS (Transport Layer Security)**.  

🔹 **Pourquoi HTTPS est important ?**
- ✅ Protège contre **les attaques de type "man-in-the-middle"**.  
- ✅ Sécurise les **informations sensibles** (mots de passe, paiements).  
- ✅ Améliore le **référencement** des sites web (Google favorise les sites HTTPS).  

💡 **Vérification** :  
Si la barre d’adresse affiche 🔒 (cadenas vert), la connexion est sécurisée.  



### **<H3 STYLE="COLOR:GREEN;">2.5. Syntaxe<a name="_page3_x40.00_y314.92"></a> complète des URL**</H3>

📌 **Composition d’une URL complète :**  
```
protocole://nom-de-domaine:port/chemin?paramètre1=valeur1&paramètre2=valeur2#ancre
```
🔹 **Explication** :
- `protocole` → HTTP ou HTTPS.  
- `nom-de-domaine` → Adresse du serveur (`www.example.com`).  
- `port` → Par défaut `80` (HTTP) ou `443` (HTTPS).  
- `chemin` → Page demandée (`/index.html`).  
- `?paramètre1=valeur1` → Données envoyées (utilisé avec GET).  
- `#ancre` → Cible une section spécifique de la page.  

🔹 **Exemple concret :**  
```
https://www.wikipedia.org/wiki/Informatique#Algorithmique
```
💡 **Ici, `#Algorithmique` permet d’accéder directement à la section "Algorithmique" de la page.**




**<H3 STYLE="COLOR:RED;">Activité n°1.**</H3> Passage de paramètre  un serveur 

- Aller sur[ HTTPs://fr.wikipedia.org ](https://fr.wikipedia.org/)
- Dans la zone de recherche taper informatique 
- Noter URL complète obtenue 
- Aller sur[ HTTPs://fr.wikipedia.org/w/index.php?search=informatique.](https://fr.wikipedia.org/w/index.php?search=informatique) Que remarque-t-on ? 
- Aller sur[ HTTPs://fr.wikipedia.org/wiki/Informatique#Algorithmique.](https://fr.wikipedia.org/wiki/Informatique#Algorithmique) Que remarque-t-on ? 

En fait sur la page la portion de code HTML correspondant est : 

```<span… id="Algorithmique">Algorithmique</span>```

## **<H2 STYLE="COLOR:BLUE;">3.  Coder l’envoi d’une requête par le navigateur<a name="_page3_x40.00_y617.92"></a>**</H2>

Les requêtes HTTP peuvent être envoyées de **plusieurs manières** :

1️⃣ **Saisir une URL directement dans le navigateur**  
2️⃣ **Utiliser un formulaire HTML**  
3️⃣ **Écrire une requête via JavaScript**  

### **<H3 STYLE="COLOR:GREEN;">3.1. Exemple<a name="_page4_x40.00_y36.92"></a> d'un formulaire HTML**</H3>

🔹 **Formulaire envoyant une requête GET** :
```html
<form method="GET" action="/search">
    <input type="text" name="query" placeholder="Rechercher">
    <button type="submit">Rechercher</button>
</form>
```
➡️ Résultat :  
```
https://www.example.com/search?query=informatique
```
📌 **Problème** : Les données sont visibles dans l’URL ! ⚠️

---

🔹 **Formulaire envoyant une requête POST** :
```html
<form method="POST" action="/login">
    <input type="text" name="username" placeholder="Nom d'utilisateur">
    <input type="password" name="password" placeholder="Mot de passe">
    <button type="submit">Se connecter</button>
</form>
```
✅ **Les données sont cachées et envoyées dans le corps de la requête.**



**<H3 STYLE="COLOR:RED;">Activité n°2.**</H3>  Ouvrir un bloc-notes. Ajouter le script suivant et vérifier ce qu’on obtient dans le navigateur. Enregistrer le fichier sous `index.html`.

⚠ **ATTENTION** à bien sélectionner **tous les fichiers** lors de l'enregistrement !

![](AZE.png)
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Requête</title>
</head>
<body>
<form method='GET' action='./login'>
    <input name='user' type='text' required>
    <input name='password' type='password' required>
    <button type='submit'>Login</button>
</form>
</body>
</html>
```
Ce formulaire utilise la **méthode GET**, ce qui signifie que :
- Les données saisies (`user` et `password`) seront ajoutées dans l’URL après soumission.
- Exemple d’URL après soumission :
  ```
  https://monsite.com/login?user=dupont&password=azerty
  ```
- ⚠️ **Problème** : Avec `GET`, le mot de passe est visible dans l’URL, ce qui n’est pas sécurisé.



**<H3 STYLE="COLOR:RED;">Activité n°3.****</H3> Remplir ce formulaire et le soumettre fera envoyer une requête **GET** vers l'URL `./login`. Observer la nouvelle URL.

Avec la méthode **GET**, les données du formulaire seront encodées **dans l’URL**.

Si on saisit les valeurs :
- **Nom d'utilisateur** : `Dupont`
- **Mot de passe** : `azerty`

➡ Le navigateur chargera la page avec l'URL suivante :
```
./login?user=dupont&password=azerty
```


- **Problème :** 
  - Les données sont **visibles** dans l'URL, ce qui pose un problème de **sécurité**, notamment pour les mots de passe.



**<H3 STYLE="COLOR:RED;">Activité n°4.****</H3> 
Modifier la page pour pouvoir la soumettre avec une requête **POST**. Remplir ce formulaire et le soumettre fera envoyer une requête **POST**.

Dans ce cas, les données ne seront **pas visibles dans l’URL**, mais envoyées **dans le corps de la requête**.




✅ **Explication :**
- Ici on demande de **modifier la méthode du formulaire** pour utiliser **POST** au lieu de **GET** :
  ```html
  <form method="POST" action="./login">
  ```
- **Différence avec GET :**
  - Avec POST, les données sont **transmises dans le corps de la requête** et **non visibles dans l'URL**.
  - Cela permet de **protéger les informations sensibles** comme les mots de passe.
  - Exemple de requête envoyée par POST :
    ```
    POST /login HTTP/1.1
    Host: monsite.com
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 32

    user=dupont&password=azerty
    ```


### **<H3 STYLE="COLOR:GREEN;">3.2. Différences entre GET et POST**<a name="_page7_x40.00_y370.92"></a> </H3>

| Critère  | **GET**  | **POST**  |
|----------|---------|---------|
| **Visibilité** | ✔️ Données visibles dans l’URL | ❌ Données cachées |
| **Taille des données** | ⚠️ Limitée par l’URL | ✅ Illimitée |
| **Utilisation** | Recherche, navigation | Connexion, formulaires |
| **Sécurité** | ❌ Moins sécurisé (ex : mot de passe visible) | ✔️ Recommandé pour les données sensibles |

💡 **À retenir** : Toujours utiliser **POST** pour les **données confidentielles** !


![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.061.jpeg)





### **<H3 STYLE="COLOR:GREEN;">3.3. Les<a name="_page4_x40.00_y568.92"></a> éléments d’un formulaire HTML**</H3>

Un formulaire HTML est composé de plusieurs éléments permettant de structurer et saisir des données.


![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.047.jpeg)

| **Type**        | **Description** |
|----------------|---------------|
| `<button>`     | Définit un bouton cliquable. |
| `<fieldset>`   | Regroupe les éléments liés dans un formulaire. |
| `<form>`       | Définit le conteneur de formulaire. |
| `<input>`      | Définit un champ de saisie. |
| `<label>`      | Définit une étiquette pour un élément de formulaire. |
| `<legend>`     | Définit l’étiquette d’un groupe de champs. |
| `<option>`     | Définit une option dans une liste déroulante. |
| `<optgroup>`   | Regroupe des options connexes dans une liste. |
| `<select>`     | Définit une liste à choix multiples. |
| `<textarea>`   | Définit une zone de saisie de texte multiligne. |




### **<H3 STYLE="COLOR:GREEN;">3.4. Elément<a name="_page5_x40.00_y275.92"></a> ```<input>``` : quelques exemples**</H3>

Le champ `<input>` est utilisé pour permettre la saisie de texte, mots de passe, et autres valeurs.



![](090.png)

### **<H3 STYLE="COLOR:GREEN;">3.5. Elément<a name="_page5_x40.00_y485.92"></a> ```<select>``` : quelques exemples**</H3>

L'élément `<select>` permet de créer une liste déroulante avec des options de choix.


![](091.png)

### **<H3 STYLE="COLOR:GREEN;">3.6. Elément<a name="_page6_x40.00_y36.92"></a> value dans ```<select>```**</H3>

’attribut `value` d’un `<option>` définit la valeur qui sera envoyée au serveur lorsqu'un choix est fait.

L'attribut value est **facultatif**. S’il n’est pas spécifié, alors **le texte** dans le conteneur **est envoyé à la place** 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.055.png)

### **<H3 STYLE="COLOR:GREEN;">3.8. Les<a name="_page6_x40.00_y300.92"></a> boutons de commande**</H3>

Différents types de boutons permettent d’interagir avec le formulaire :

| **Type**                    | **Description** |
|-----------------------------|----------------|
| `<input type="submit">`     | Envoie les données du formulaire. |
| `<input type="reset">`      | Efface les champs du formulaire. |
| `<input type="button">`     | Bouton personnalisé (nécessite JavaScript). |
| `<input type="image">`      | Bouton sous forme d’image. |
| `<button>`                  | Bouton plus flexible pouvant contenir du texte et des images. |


![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.057.png)

⚠ **Attention à ne pas confondre :**
- `<button>` avec `<input type='button'>`
- `<input type='submit'>` avec `<button type='submit'>`



### **<H3 STYLE="COLOR:GREEN;">3.9. Comment<a name="_page7_x40.00_y36.92"></a> le formulaire interagit avec le serveur ?**</H3> 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.059.jpeg)



### **<H3 STYLE="COLOR:GREEN;">3.10. Les<a name="_page8_x40.00_y290.92"></a> cookies**</H3> 

Il est important pour un site web de pouvoir identifier ces différents clients. Il utilise des **cookies**. C’est une petite quantité de données. Il est composé d’un nom, d’une valeur et optionnellement d’une date d’expiration. Le nom, la valeur et la durée de vie sont choisie par le serveur.  

Lorsqu’un serveur veut déposer un cookie particulier chez un client, il l’envoie comme un entête de réponse HTTP.  

**Exemple d'Entête de Réponse HTTP avec Cookie**

```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Set-Cookie: username=JohnDoe; Expires=Wed, 21 Jul 2024 07:28:00 GMT; Path=/; Domain=example.com; Secure; HttpOnly
```


**Ligne de Statut** :

   - `HTTP/1.1 200 OK` : Indique que la requête a été traitée avec succès et que le serveur renvoie une réponse correcte.

**En-têtes de Réponse** :

   - `Content-Type: text/html; charset=UTF-8` : Spécifie le type de contenu de la réponse. Ici, il s'agit de HTML encodé en UTF-8.
   
**Set-Cookie** :

   - `Set-Cookie: username=JohnDoe` : Crée un cookie nommé `username` avec la valeur `JohnDoe`.

   - `Expires=Wed, 21 Jul 2024 07:28:00 GMT` : Date et heure d'expiration du cookie. Passée cette date, le cookie sera supprimé par le navigateur.

   - `Path=/` : Le cookie est disponible pour toutes les URL du domaine.

   - `Domain=example.com` : Le domaine pour lequel le cookie est valide. Le cookie sera envoyé pour toutes les requêtes à `example.com` et ses sous-domaines.

   - `Secure` : Indique que le cookie doit être envoyé uniquement via des connexions sécurisées (HTTPS).

   - `HttpOnly` : Indique que le cookie n'est accessible que par le serveur et ne peut pas être manipulé par le JavaScript côté client, ce qui aide à protéger contre les attaques XSS.

**Utilisation Typique**

Lorsqu'un client (navigateur web) reçoit cette réponse du serveur, il stocke le cookie conformément aux directives spécifiées. Par exemple :

**Connexion sécurisée** :

   - Le cookie ne sera envoyé au serveur que lors de requêtes via HTTPS (grâce au flag `Secure`).

**Accès au cookie** :

   - Le cookie est accessible pour toutes les pages du domaine `example.com` (grâce au flag `Path=/` et `Domain=example.com`).

**Durée de vie** :

   - Le cookie expirera et sera supprimé automatiquement après le 21 juillet 2024 (grâce au flag `Expires`).

**Protection contre XSS** :

   - Le cookie n'est pas accessible via JavaScript, ce qui le protège contre certaines attaques XSS (grâce au flag `HttpOnly`).

**<H3 STYLE="COLOR:RED;">Activité n°5****</H3>: faire les exercices

## **<H2 STYLE="COLOR:BLUE;">4. APPLICATION<a name="_page8_x40.00_y503.92"></a> : Création d’une page web dynamique**</H2>

 
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.067.png)

### **<H3 STYLE="COLOR:GREEN;">4.1. Mise<a name="_page8_x40.00_y565.92"></a> en place d’un serveur Apache Wamp**</H3>  

Telecharger un serveur Wamp (choisissez le exe) : UwAmp Wamp Server - Apache MySQL PHP [https://www.uwamp.com/fr/](https://www.uwamp.com/fr/)

Normalement il s’installe dans C:\UwAmp

**<H3 STYLE="COLOR:RED;">Activité n°6****</H3> Demarrer le serveur Wamp




### **<H3 STYLE="COLOR:GREEN;">4.2. Formulaire<a name="_page9_x40.00_y154.92"></a> d’une page Web version php**</H3>
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.072.png)

PHP est un langage de programmation qui s'intègre dans vos pages  HTML. Le sigle PHP est un acronyme récursif pour : PHP **Hypertext  Preprocessor** ! Il permet la **génération automatisée** (Preprocessor)  de vos pages Web (Hypertext). Celles-ci peuvent ainsi **s'adapter à la  demande ou suivant certaines conditions**. C'est pour cela que l'on  parle de pages **web dynamiques.**   

Cas très simple où le serveur va renvoyer au client une simple page HTML statique. Le serveur Web Apache a été configuré pour qu'il envoie vers le client une page HTML située dans un répertoire nommé "www", ce répertoire "www" devant se trouver dans votre répertoire C:\UwAmp



**<H3 STYLE="COLOR:RED;">Activité n°7.****</H3> Créer avec le bloc note, un fichier où on aura copier :

```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Utilisation d'Apache</title>
    </head>
    <body>
        <p>Le serveur Apache fonctionne parfaitement</p>
    </body>
</html>
```
Enregistrer le dans le répertoire C:\UwAmp\www  sous le nom "index.html". **ATTENTION** à bien sélectionner tous les fichiers.
![](AZE.png)


**<H3 STYLE="COLOR:RED;">Activité n°8.****</H3> Ouvrir votre navigateur Web et taper dans la barre d'adresse **"localhost"**. On devrait voir la page Web s'afficher. 

Avec le "localhost", on indique au navigateur que le serveur Web se trouve sur le même ordinateur que lui (on parle de machine locale). Dans un cas normal, la barre d'adresse devrait être renseignée avec l'adresse du serveur Web. 

Pour l'instant, le site est **statique** : la page reste identique, quelles que soient les actions des visiteurs. Pour avoir un **site dynamique**, nous allons **exécuter, côté serveur, un programme qui va créer de toute pièce une page HTML**, cette page HTML sera ensuite envoyée au client par l'intermédiaire du serveur Web. Il existe différents langages de programmation qui permettent de générer des pages HTML à la volée **: Python, Java, Ruby...** Dans notre cas, nous allons utiliser le **PHP.**  

Le PHP est un langage très utilisé même si dans le monde professionnel Java, Python, Ruby,... sont préférés au PHP.  

Il est très important de bien comprendre les processus mis en œuvre : 

- **le client (le navigateur Web) envoie** une requête HTTP vers un serveur Web 
- en fonction de la requête reçue **le serveur "fabrique" une page HTML** grâce à l'exécution d'un programme écrit en PHP (ou en Python, Java...) 
- **le serveur Web envoie la page nouvellement créée au** client 
- une fois reçue, **la page HTML est affichée dans le navigateur** Web 



**<H3 STYLE="COLOR:RED;">Activité n°9. ****</H3> Après avoir supprimé le fichier "index.html" préalablement créé dans le répertoire "www" **ET** le fichier "index.php", Créer avec le bloc note, un fichier où on aura copier : toujours dans le répertoire "www". 
```php
<?php
date_default_timezone_set('Europe/Paris'); // Définir le fuseau horaire à Paris
$heure = date("H:i");
echo '<h1>Bienvenue sur mon site</h1>
      <p>Il est '.$heure.'</p>';
?>
```
Enregistrer le dans le répertoire C:\UwAmp\www  sous le nom "index.php". **ATTENTION** à bien sélectionner tous les fichiers.


**<H3 STYLE="COLOR:RED;">Activité n°10.****</H3> Ouvrir votre navigateur Web et taper dans la barre d'adresse **"localhost"**. 

On doit avoir une page HTML qui donne l'heure, si on **actualise** la page, **l'heure évolue**. On a donc bien une page dynamique : le serveur PHP crée la page Web au moment où elle est demandée. À chaque fois que la page est actualisée, la page HTML est générée de nouveau. 

L’extension ".html" a été remplacée par ".php". Au moment de la requête, le programme contenu dans ce fichier a été exécuté et la page HTML a été générée. Dans les 2 cas, le fichier se nomme "index", car par défaut, le serveur prend en compte un fichier nommé "index" ("index.php" ou "index.html" selon les cas).  

**Comment ça marche ?** 

- "```$heure = date("H:i");```", "```$heure```" est une variable (en **PHP les variables commencent** par **un "**$**"**), cette variable "contient" une chaîne de caractères qui correspond à l'heure courante 

- **l'instruction "**```echo```**" permet d'afficher la chaîne de caractères** **qui suit l'instruction**. 

Dans  notre  cas,  la  chaîne  de  caractères  est  "```<h1>Bienvenue  sur  mon  site</h1>  <p>Il  est '.$heure.'</p>```" ce qui correspond à du HTML à l'exception de "$heure" qui permet d'afficher le contenu de la variable "```$heure```".  

La page Web générée contiendra le code HTML et le contenu de la variable "$heure".  

**Le point "**.**" est, en PHP, l'opérateur de concaténation** (alors que par exemple en Python, l'opérateur de concaténation est le "+")  

Si un client effectue une requête à 18h23, le serveur enverra au client le code HTML ci-dessous : 
```html
<h1>Bienvenue sur mon site</h1> 
<p>Il est 18h23</p> 
```
**<H3 STYLE="COLOR:RED;">Activité n°11.****</H3> Après avoir supprimé le fichier "index.php" préalablement créé dans le répertoire "www", Créer avec le bloc note, un fichier où on aura copier : toujours dans le répertoire "www". 

```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="trait_form.php" method="post">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```
Enregistrer le dans le répertoire C:\UwAmp\www  sous le nom "index.html". ATTENTION à bien sélectionner tous les fichiers.

**<H3 STYLE="COLOR:RED;">Activité n°12.****</H3> : Créer avec le bloc note, un fichier où on aura copier : toujours dans le répertoire "www".  
```php
<?php
    $n=$_POST['nom'];
    $p=$_POST['prenom'];
    echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>";
?>
```
Enregistrer le dans le répertoire C:\UwAmp\www  sous le nom " trait_form.php  ". ATTENTION à bien sélectionner tous les fichiers.

**<H3 STYLE="COLOR:RED;">Activité n°13.****</H3> : Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, remplir le formulaire proposé et valider en cliquant sur le bouton "Envoyer"

**Comment ça marche ?** 

- **Dans la page en HTML** :   

Dans la balise ```<form>``` du code HTML, il y a 2 attributs : « action » et « method ».  

- L’attribut ```action="trait_form.php"```  indique que le client enverra une requête http vers le serveur en cas de click sur le bouton « envoyer ». Pour répondre à cette requête du client, le serveur devra exécuter le programme PHP contenu dans le fichier « trait_form.php ».  

- La ```method="post"``` indique que la méthode utilisée pour effectuer cette requête http est une méthode « POST » . 

Au niveau des deux balises « input » permettant de saisir le nom et le prénom, on voit l’attribut « name »   

- **Dans la page en PHP** :  
- la ligne ```$n=$\_POST['nom'];``` permet d’attribuer à la variable $n la chaine de caractères qui a été saisie par l’utilisateur dans le formulaire : balise input ayant l’attribut name="nom". Le nom de ```$_POST['nom']``` est directement lié au nom de l’attribut ```name="nom"```.
- Le principe est le même pour la variable $p : le ```prenom``` de ```$_POST['prenom']``` est directement lié au prenom de l’attribut ```name="prenom"```.
Un ```$_POST['toto']```  contiendra  la  chaine  de  caractère  saisie  par  l’utilisateur  dans  le  champ correspondant à une balise input possédant un attribut ```name="toto"```. 

- ```echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>"```  contient l’instruction echo déjà vu précédemment 

Un clic sur le bouton "Envoyer" **déclenche une requête HTTP** vers le serveur et que les informations saisies dans le formulaire sont envoyées vers le serveur (puisqu'il est possible de récupérer ces informations au niveau du code PHP : une fois de plus, le code **PHP est uniquement exécuté du côté serveur**).  

Ces informations transitent entre le client et le serveur selon méthode utilisée par la requête HTTP. Dans l'exemple ci-dessus, la méthode utilisée est la méthode "POST" ("```method="post```"). 



**<H3 STYLE="COLOR:RED;">Activité n°14.****</H3> Modifier les fichiers "index.html" et "trait_form.php" comme suit : 
Pour index.html
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="trait_form.php" method="get">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```


Pour trait_form.php 
```php
<?php
    $n=$_GET['nom'];
    $p=$_GET['prenom'];
    echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>";
?>
```



**<H3 STYLE="COLOR:RED;">Activité n°15.****</H3> Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, Saisir le prénom et le nom puis valider en cliquant sur le bouton "Envoyer". **Observer attentivement la barre d'adresse du navigateur. 

Cette  fois-ci,  les  informations  du  formulaire  sont  transmises  au  serveur  par  l'intermédiaire  de  l'url  : ```localhost/trait_form.php?nom=tartempion&prenom=tartiflette```

Dans le cas de l'utilisation d'une méthode "POST" les données issues d'un formulaire sont envoyées au serveur **sans être directement visibles**, alors que dans le cas de l'utilisation d'une méthode "GET", les données **sont visibles** (et accessibles) puisqu'elles sont envoyées par l'intermédiaire de l'url. 

Les données envoyées par l'intermédiaire d'une méthode "GET" peuvent être modifiées directement dans l'url. 

**<H3 STYLE="COLOR:RED;">Activité n°16.****</H3> Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, Saisir le prénom et le nom puis valider en cliquant sur le bouton "Envoyer". Modifier l'url : "```localhost/trait_form.php?nom=Martin&prenom=Jean-Pierre```", validez votre modification en appuyant sur la touche "Entrée". 

Normalement la page a bien été modifiée : "Bonjour Jean-Pierre Martin, j'espère que vous allez bien." 

Même si dans notre cas cette opération de modification d'URL est inoffensive, il faut bien se douter que dans des situations plus complexes, une telle modification pourrait entrainer des conséquences plus problématiques (piratage). **Il faut donc éviter d'utiliser la méthode "**GET**" pour transmettre les données issues d'un formulaire vers un serveur.** 

Il est important de bien comprendre que la méthode "POST" **n'offre pas non plus une sécurité absolue** puisque toute personne ayant un bagage technique minimum sera capable de lire les données transmises à l'aide de la méthode "POST" en analysant la requête HTTP, même si ces données ne sont pas directement visibles dans l'URL. Seule l'utilisation du **protocole sécurisé HTTPS** garantit un transfert sécurisé des données entre le client et le serveur (les données sont chiffrées et donc illisibles pour une personne ne possédant pas la clé de déchiffrement). 

**<H3 STYLE="COLOR:RED;">Activité n°17****</H3> Fermer le serveur Wamp

Si le PHP vous passionne :  

- Introduction.[ http://www.phpdebutant.org/article118.php ](http://www.phpdebutant.org/article118.php)
- Afficher une phrase ou une image.[ http://www.phpdebutant.org/article14.php ](http://www.phpdebutant.org/article14.php) 
- Afficher la date et l'heure.[ http://www.phpdebutant.org/article53.php ](http://www.phpdebutant.org/article53.php) 
- PHP dans du code HTML.[ http://www.phpdebutant.org/article54.php ](http://www.phpdebutant.org/article54.php) 
- La concaténation.[ http://www.phpdebutant.org/article55.php ](http://www.phpdebutant.org/article55.php) 
- Récupérer les valeurs d'un formulaire.[ http://www.phpdebutant.org/article56.php ](http://www.phpdebutant.org/article56.php) 
- Les structures de contrôle.[ http://www.phpdebutant.org/article57.php ](http://www.phpdebutant.org/article57.php) 
- Ecrire et lire dans un fichier texte.[ http://www.phpdebutant.org/article58.php ](http://www.phpdebutant.org/article58.php) 
- Les fonctions utilisateurs.[ http://www.phpdebutant.org/article59.php ](http://www.phpdebutant.org/article59.php) 
- Les variables d'environnement.[ http://www.phpdebutant.org/article60.php ](http://www.phpdebutant.org/article60.php) 
- Quelques fonctions utiles.[ http://www.phpdebutant.org/article61.php ](http://www.phpdebutant.org/article61.php) 
- Les sessions.[ http://www.phpdebutant.org/article69.php ](http://www.phpdebutant.org/article69.php) 

Editeurs PHP en ligne : 

- [http://phpfiddle.org/ ](http://phpfiddle.org/) 
- [https://www.runphponline.com/ ](https://www.runphponline.com/) ![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.008.png)



## **<H2 STYLE="COLOR:BLUE;">5. Exercices<a name="_page13_x40.00_y36.92"></a>**</H2> 


**<H3 STYLE="COLOR:RED;">Exercice n°1 :****</H3> Réaliser le visuel du formulaire suivant :

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.129.jpeg)

Pour cela : 

- vous utilisez les balises input et select,  
- vous préciserez le type lors de l'utilisation d'une balise input, 
- vous préciserez le name dans chacun des cas (attribut name utilisé plus tard pour retrouver la valeur d'un élément d'un formulaire).
- vous proposerez deux types de carte bancaire possibles : 'Visa' et 'Bleue' (carte par défaut). 
- Attention ! Sans Javascript, votre bouton 'Valider le paiement' sera sans effet.

**<H3 STYLE="COLOR:RED;">Exercice n°2 :****</H3> Expliquer ce que fait ce code. 
```html
<form>
<p> Choix d'une nationalité :</p>
    <select id="choix" name="lang" onchange="selection()">
        <option value="ras">Choisir sa nationalité</option>
        <option value="fr">Français</option>
        <option value="zh">Chinois</option>
        <option value="it">Italien</option>
    </select>
<p> Vous avez choisi comme nationalité :<span id="nat">  </span>

 </p>
</form>
```


**Pour aller plus loin (avec du JS) : <H3 STYLE="COLOR:RED;">Exercice n°3 :**</H3>** 

Pour l'exercice on a besoin de trois instructions (déjà vues) : 

- **getElementById('id')** est une méthode qui récupère l'objet de la page identifié par 'id'. 

document.getElementById('id') récupère l'objet de la page en cours identifié par 'id'.

- **selectedIndex** est une méthode qui renvoie la valeur l'option choisie par une liste déroulante ; plus généralement, cette méthode indique le rang à partir de 0 de l'élément de la liste qui a été sélectionnée par l'utilisateur.

selecteur.selectedIndex renvoie l'indice du choix fait par l'utilisateur de la liste déroulante nommée 'selecteur'. 

- **innerHTML** est une méthode qui permet de récupérer tout le contenu HTML d'un élément d'une page html.

document.getElementById('ici').innerHTML intégre du contenu html à l'emplacement de la page identifié par l'id nommé 'ici'. 

voilà le script d'une fonction écrite en javascript :
```JS
function selection() {
        const selecteur = document.getElementById('choix');
        const monChoix = selecteur[selecteur.selectedIndex];
        console.log(monChoix.value +' '+ monChoix.text);
        document.getElementById('nat').innerHTML = monChoix.text;
    }
```


1. Intégrer au code de l'exercice 2 ci-dessus ce script, soit directement, soit avec un lien vers un fichier javascript. 
1. Relancer le code ainsi augmenté de l'exercice 2. Que remarquez-vous ? 
1. Commenter chaque ligne de cette fonction écrite en JavaScript. 

Utiliser la console de votre navigateur afin de voir l'effet d'une des lignes. 

**Pour aller plus loin (avec du JS) : <H3 STYLE="COLOR:RED;">Exercice n°4 :**</H3>**  

Ecrire un formulaire qui demande votre âge et qui indique dans la même page si vous êtes majeur ou mineur. 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.136.png) ![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.137.jpeg)

**Pour aller plus loin (avec du JS) : <H3 STYLE="COLOR:RED;">Exercice n°5 :**</H3>**  

On donne le code suivant : 
```html
<form>
    <fieldset>
        <legend>Veuillez sélectionner vos spécialités l'année prochaine :
        </legend>
        <div>
            <input type="checkbox" id="nsi" name="interest" value="nsi">
            <label for="nsi">NSI</label>
        </div>
        <div>
            <input type="checkbox" id="ma" name="interest" value="ma">
            <label for="ma">Maths</label>
        </div>
        <div>
            <input type="checkbox" id="svt" name="interest" value="svt">
            <label for="svt">SVT</label>
        </div>
    </fieldset>
</form>
```


En vous inspirant de l'exercice précédent, faire un formulaire qui demande quelles spécialités vous allez conserver l'année prochaine 

Vous ferez une question pour la première 

La réponse sera affichée dans la page HTML. 

Si la réponse contient NSI, la page HTML doit afficher : "Bravo, bon choix !". 
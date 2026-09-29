---
author: Elisabeth Le Prettre (LePrettre)
title: 12 📜 Fiche Méthode - Traitement des données en tables
---



# Traitement des données en tables

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 17"
    Fiche **compacte** pour **refaire seul les activités** : **CSV** / **JSON**,
    importation, **recherche**, **filtrage**, **tri**, visualisation et **fusion** de tables.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les formats CSV / JSON et la structure d'une table ;
- **lire** un fichier avec `csv.reader` / `csv.DictReader` ;
- **expliquer** liste de listes vs liste de dictionnaires ;
- **programmer** : recherche, filtrage, tri, visualisation, fusion.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Donnée tabulaire** | Données organisées en **table**. |
| **Table** | Ensemble d'enregistrements. |
| **Descripteur** | Nom d'une **colonne** (attribut). |
| **Enregistrement** | Une **ligne** (un objet). |
| **Valeur** | Contenu d'une case. |
| **CSV** | Texte tabulaire à **séparateurs**. |
| **JSON** | Données **structurées** (clés-valeurs). |
| **Séparateur** | Caractère séparant les valeurs (`,` `;`). |
| **Encodage** | Codage des caractères (`utf-8`). |
| **Liste de listes** | Table indexée par **position**. |
| **Liste de dictionnaires** | Table indexée par **descripteur**. |
| **Clé** | Descripteur d'un dictionnaire. |
| **Filtre** | Sélection selon un **critère**. |
| **Critère de tri** | Donnée servant à ordonner. |
| **Doublon** | Valeur répétée. |
| **Fusion** | Combiner deux tables. |
| **Colonne commune** | Descripteur partagé (clé de fusion). |

---

## 3. CSV vs JSON

| | **CSV** | **JSON** |
|---|---|---|
| Organisation | tableau (lignes / colonnes) | structure imbriquée |
| Séparateur | `,` ou `;` | accolades, crochets |
| Types | tout en **chaînes** | nombres, listes, objets |
| Lisibilité | tableur | hiérarchique |
| Usage | données plates | échange de données |

---

## 4. Lire un CSV avec `csv.reader`

```python
import csv
with open("albums.csv", encoding="utf-8") as f:
    lecteur = csv.reader(f, delimiter=",")
    table = []
    for ligne in lecteur:
        table.append(ligne)
```

- chaque **ligne** est une **liste** ; les **valeurs** sont des **chaînes** ;
- `with` ferme le fichier automatiquement.

---

## 5. Lire avec `csv.DictReader`

```python
import csv
with open("albums.csv", encoding="utf-8") as f:
    lecteur = csv.DictReader(f, delimiter=",")
    table = []
    for ligne in lecteur:
        table.append(ligne)
# accès : ligne["titre"]
```

- la **1ʳᵉ ligne** sert de **clés** ; on obtient une **liste de dictionnaires** ;
- accès par **descripteur** (`ligne["titre"]`) au lieu d'un indice (`ligne[0]`).

---

## 6. Choisir la représentation

| Représentation | Avantage | Limite | Usage |
|---|---|---|---|
| **Ligne affichée** | rapide | non manipulable | aperçu |
| **Liste de listes** | compacte | accès par **indice** (peu lisible) | petites tables |
| **Liste de dictionnaires** | accès par **nom** (clair) | un peu plus lourde | traitement courant |

---

## 7. Rechercher une donnée

```python
def rechercher(table, descripteur, valeur):
    for enr in table:
        if enr[descripteur] == valeur:
            return enr
    return None          # absence
```

---

## 8. Filtrer une table

!!! tip "Étapes"
    1. créer une **liste vide** ;
    2. **parcourir** les enregistrements ;
    3. **tester** une ou plusieurs conditions ;
    4. **ajouter** les lignes correspondantes ;
    5. **retourner** la liste.

```python
def filtrer(table):
    resultat = []
    for enr in table:
        if int(enr["annee"]) > 2000 and enr["style"] == "rock":
            resultat.append(enr)
    return resultat
```

*Critères possibles : année, style, nombre de fans, intervalle.*

---

## 9. Comparer correctement

!!! warning "Réflexes"
    - **convertir** : `int(enr["annee"])`, `float(...)` (les valeurs CSV sont des chaînes) ;
    - **ignorer la casse** : `enr["style"].lower() == "rock"` ;
    - vérifier les **chaînes vides** (`if enr["x"] != ""`) ;
    - traiter les **conversions impossibles** ;
    - **`set()`** pour enlever les **doublons**.

---

## 10. Trier une table

```python
def cle(enr):
    return int(enr["fans"])          # critère converti

trie = sorted(table, key=cle, reverse=True)   # décroissant
```

!!! note "`sorted()` vs `.sort()`"
    - **`sorted(table, key=cle)`** : renvoie une **nouvelle** liste ;
    - **`table.sort(key=cle)`** : **modifie** la liste existante.

---

## 11. Filtrer puis trier

!!! tip "Méthode"
    1. **filtrer** d'abord les enregistrements ;
    2. **trier** le résultat ;
    3. **sélectionner** les informations à afficher ;
    4. **vérifier** le nombre de résultats.

```python
selection = filtrer(table)
selection = sorted(selection, key=cle, reverse=True)
```

---

## 12. Visualiser

```python
import matplotlib.pyplot as plt
X = [int(enr["annee"]) for enr in table]
Y = [int(enr["fans"]) for enr in table]
plt.plot(X, Y)
plt.xlabel("Année")
plt.ylabel("Fans")
plt.title("Évolution")
plt.show()
```

- construire **X** et **Y**, **convertir** les valeurs, nommer les **axes**, titrer,
  éventuellement **plusieurs séries**, puis `plt.show()`.

---

## 13. Fusionner deux tables

!!! tip "Étapes"
    1. repérer le **descripteur commun** ;
    2. trouver sa **valeur** dans la 1ʳᵉ table ;
    3. la **rechercher** dans la 2ᵉ ;
    4. **rassembler** les données ;
    5. **gérer** l'absence de correspondance.

```python
def fusionner(table1, table2, commun):
    resultat = []
    for a in table1:
        for b in table2:
            if a[commun] == b[commun]:
                fusion = dict(a)
                fusion.update(b)
                resultat.append(fusion)
    return resultat
```

*Exemples : `CountryCode`, `Capital` / `ID`, numéro de client.*

---

## 14. Ajouter un descripteur

```python
for enr in table:
    correspondance = rechercher(autre_table, "id", enr["id"])
    if correspondance is not None:
        enr["pays"] = correspondance["pays"]
    else:
        enr["pays"] = ""          # valeur vide si absence
```

---

## 15. `pandas` (application)

```python
import pandas as pd
df = pd.read_csv("data.csv")                       # charger
df.loc[df["annee"] > 2000]                          # filtrer (lignes)
df["titre"]                                         # une colonne
df[(df["annee"] > 2000) & (df["fans"] > 1000)]      # conditions combinées
df["fans"].mean()                                   # calcul
df.sort_values("fans", ascending=False)             # trier
df.merge(autre, on="id")                            # fusionner
```

- combiner des conditions avec **`&`** / **`|`** et des **parenthèses** ;
- **`NaN`** = valeur **manquante**.

---

## 16. Écrire un CSV (projet qualité de l'air)

```python
import csv
with open("sortie.csv", "w", newline="", encoding="utf-8") as f:
    ecrivain = csv.writer(f)
    ecrivain.writerow(["ville", "valeur"])   # en-tête
    for ligne in donnees_filtrees:
        ecrivain.writerow(ligne)
```

- mode **`"w"`** avec **`newline=""`** ; `csv.writer` ; `writerow()` ; conserver l'**en-tête** ;
  **filtrer** les lignes ; `with` ferme le fichier.

---

## 17. Lecture de code

!!! tip "Comment retrouver…"
    - le **fichier** et l'**encodage** (`open`) ;
    - le **séparateur** (`delimiter`) ;
    - la **structure produite** (liste de listes / de dictionnaires) ;
    - les **clés** (`DictReader`) ;
    - le **filtre** (la condition) ;
    - la **conversion** (`int`, `float`) ;
    - le **critère de tri** (`key=cle`) et le **sens** (`reverse`) ;
    - la **valeur retournée**.

---

## 18. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Importation**
    | Ligne CSV | Liste obtenue | Dictionnaire obtenu |
    |---|---|---|

    **Filtrage**
    | Enregistrement | Condition | Test | Ajout ? |
    |---|---|---|---|

    **Conversion**
    | Valeur initiale | Conversion | Valeur numérique |
    |---|---|---|

    **Tri**
    | Enregistrement | Clé de tri | Rang |
    |---|---|---|

    **Fusion**
    | Table 1 | Clé commune | Table 2 | Données fusionnées |
    |---|---|---|---|

---

## 19. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Mauvais **nom / emplacement** | vérifier le chemin du fichier |
| Mauvais **encodage** | préciser `encoding="utf-8"` |
| Mauvais **séparateur** | adapter `delimiter` (`,` ou `;`) |
| Oubli de **fermer** le fichier | utiliser `with` |
| Confusion **liste / dictionnaire** | indice vs clé |
| Faute dans un **nom de clé** | respecter l'en-tête (casse) |
| Comparer **nombre / chaîne** | convertir avec `int` / `float` |
| **Tri alphabétique** de nombres | convertir dans la clé |
| Confusion **`sorted` / `.sort`** | nouvelle liste vs modification |
| **Oubli de `key`** | tri sur la mauvaise donnée |
| Mauvais sens de **`reverse`** | `True` = décroissant |
| Problème de **majuscules** | `.lower()` |
| **Doublons** non supprimés | `set()` |
| **Absence de correspondance** (fusion) | prévoir le cas vide |
| Oubli des **parenthèses** avec `&` / `|` | parenthéser chaque condition |

---

## 20. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Qu'est-ce qu'un descripteur ?"
    Le **nom d'une colonne** (attribut).

??? question "2. (N1) Qu'est-ce qu'un enregistrement ?"
    Une **ligne** de la table (un objet).

??? question "3. (N2) Différence entre liste de listes et liste de dictionnaires ?"
    Accès par **indice** vs accès par **descripteur**.

??? question "4. (N2) Qu'est-ce qu'une colonne commune ?"
    Un descripteur **partagé** servant à **fusionner**.

??? question "5. (N1) Qu'est-ce qu'un doublon ?"
    Une **valeur répétée**.

### CSV / JSON

??? question "6. (N1) Dans un CSV, de quel type sont les valeurs lues ?"
    Des **chaînes**.

??? question "7. (N2) Quel séparateur courant pour un CSV ?"
    La **virgule** (ou le point-virgule).

??? question "8. (N2) Que fait `DictReader` de la première ligne ?"
    Il l'utilise comme **clés**.

??? question "9. (N3) Quand préférer JSON à CSV ?"
    Pour des données **structurées / imbriquées**.

??? question "10. (N2) Pourquoi préciser l'encodage ?"
    Pour lire correctement les **caractères accentués**.

### Lecture de code

??? question "11. (N1) Que vaut `ligne[0]` dans une liste de listes ?"
    La **première valeur** de la ligne.

??? question "12. (N2) Que vaut `ligne[\"titre\"]` ?"
    La valeur du descripteur **titre**.

??? question "13. (N2) Que renvoie `csv.reader` à chaque tour ?"
    Une **liste** (la ligne).

??? question "14. (N3) Que fait `int(enr[\"annee\"])` ?"
    **Convertit** l'année (chaîne) en entier.

??? question "15. (N2) Que fait `with open(...)` ?"
    Ouvre le fichier et le **ferme** automatiquement.

### Recherche et filtre

??? question "16. (N1) Que renvoie une recherche infructueuse ?"
    `None` (absence).

??? question "17. (N2) Écrire la condition « année > 2000 »."
    `int(enr[\"annee\"]) > 2000`.

??? question "18. (N2) Filtrer le style « rock » sans tenir compte de la casse."
    `enr[\"style\"].lower() == \"rock\"`.

??? question "19. (N3) Filtrer un intervalle d'années (1990–2000)."
    `1990 <= int(enr[\"annee\"]) <= 2000`.

??? question "20. (N2) Comment éviter une erreur sur une case vide ?"
    Tester `if enr[\"x\"] != \"\"` avant la conversion.

### Tri

??? question "21. (N1) Que renvoie `sorted(table, key=cle)` ?"
    Une **nouvelle** liste triée.

??? question "22. (N2) Trier par fans décroissant."
    `sorted(table, key=cle, reverse=True)`.

??? question "23. (N2) Différence entre `sorted` et `.sort` ?"
    `sorted` crée une liste ; `.sort` **modifie** la liste.

??? question "24. (N3) Pourquoi convertir dans la fonction clé ?"
    Sinon le tri est **alphabétique** (faux pour des nombres).

??? question "25. (N3) Écrire une fonction clé sur l'année."
    ```python
    def cle(enr):
        return int(enr[\"annee\"])
    ```

### Fusion

??? question "26. (N1) Quel élément relie deux tables ?"
    La **colonne commune**.

??? question "27. (N2) Que faire si aucune correspondance n'existe ?"
    Prévoir une **valeur vide** (ou ignorer la ligne).

??? question "28. (N2) Quelle clé commune pour pays / capitales ?"
    `CountryCode` (ou `ID`).

??? question "29. (N3) Comment fusionner clients et commandes ?"
    Via le **numéro de client** commun.

??? question "30. (N3) En pandas, quelle méthode fusionne ?"
    `.merge(autre, on=\"id\")`.

### Correction d'erreurs

??? question "31. (N1) `int` oublié avant une comparaison d'année : conséquence ?"
    Comparaison de **chaînes** (résultat faux).

??? question "32. (N2) Mauvais `delimiter` : conséquence ?"
    Les colonnes sont **mal découpées**.

??? question "33. (N2) `.sort()` utilisé comme `sorted()` : erreur ?"
    `.sort()` renvoie `None` : utiliser `sorted` si on veut une liste.

??? question "34. (N3) `df[df[\"a\"]>1 & df[\"b\"]<2]` : erreur ?"
    Manque les **parenthèses** : `(df[\"a\"]>1) & (df[\"b\"]<2)`.

??? question "35. (N2) Doublons non retirés : correction ?"
    Utiliser `set()`.

### Programmation

??? question "36. (N1) Ouvrir `data.csv` en lecture (utf-8)."
    `open(\"data.csv\", encoding=\"utf-8\")`.

??? question "37. (N2) Stocker toutes les lignes d'un `reader`."
    `for ligne in lecteur: table.append(ligne)`.

??? question "38. (N2) Accéder au titre d'un enregistrement (DictReader)."
    `enr[\"titre\"]`.

??? question "39. (N3) Écrire une en-tête dans un CSV."
    `ecrivain.writerow([\"ville\", \"valeur\"])`.

??? question "40. (N4) Filtrer puis trier par fans décroissant."
    ```python
    sel = filtrer(table)
    sel = sorted(sel, key=cle, reverse=True)
    ```

---

## 21. Exercices flash corrigés

??? question "Reconnaître descripteur et enregistrement"
    Descripteur = **colonne** ; enregistrement = **ligne**.

??? question "Choisir un séparateur pour un fichier `a;b;c`"
    `delimiter=\";\"`.

??? question "Compléter `csv.____(f)` pour une liste de dictionnaires"
    `DictReader`.

??? question "Accéder à la valeur `annee` d'un enregistrement"
    `enr[\"annee\"]`.

??? question "Convertir `\"2003\"` en nombre"
    `int(\"2003\")`.

??? question "Écrire une condition de filtre « fans > 1000 »"
    `int(enr[\"fans\"]) > 1000`.

??? question "Ignorer la casse pour comparer un style"
    `enr[\"style\"].lower() == \"rock\"`.

??? question "Écrire une fonction clé sur les fans"
    `def cle(enr): return int(enr[\"fans\"])`.

??? question "Choisir `sorted` ou `.sort` pour garder l'original"
    `sorted`.

??? question "Trier en décroissant"
    `sorted(table, key=cle, reverse=True)`.

??? question "Retrouver une colonne commune pays / villes"
    `CountryCode` (ou `ID`).

??? question "Compléter une fusion simple sur `id`"
    `if a[\"id\"] == b[\"id\"]: …`.

---

## À retenir absolument

!!! success "Importation"
    - **CSV** : valeurs en **chaînes**, **séparateur** (`,`/`;`), **encodage** `utf-8` ;
    - **`csv.reader`** → liste de **listes** (indices) ;
    - **`csv.DictReader`** → liste de **dictionnaires** (`enr[\"clé\"]`).

!!! note "Traitements"
    - **convertir** les types avant de comparer (`int`, `float`) ; `.lower()` pour la casse ;
    - **filtrer** : liste vide + condition + `append` ;
    - **trier** : `sorted(table, key=cle, reverse=…)` ;
      **`sorted`** crée une liste, **`.sort`** modifie ;
    - **fusionner** par **descripteur commun**.

!!! quote "Visualisation & écriture"
    - **matplotlib** : construire X/Y, `plt.plot`, axes, titre, `plt.show()` ;
    - **écrire** : `csv.writer` + `writerow` (en-tête conservé, `newline=\"\"`).
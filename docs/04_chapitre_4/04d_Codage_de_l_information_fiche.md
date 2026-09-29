---
author: Elisabeth Le Prettre (LePrettre)
title: 04 📜 Fiche Méthode - Codage
---
# Codage de l'information

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 4"
Fiche compacte mais complète pour refaire seul les exercices : bases de
numération, entiers signés (complément à 2), réels (IEEE 754), caractères
(ASCII / Unicode) et images (RVB). Les points marqués « Approfondissement »
ne sont pas indispensables.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** : bit, octet, bases (2, 10, 16), complément à 2, ASCII/Unicode, RVB ;
- **comprendre** : pourquoi l'ordinateur travaille en binaire ;
- **convertir** : base 10 ↔ base 2 ↔ base 16, et les fractions ;
- **calculer** : additions et multiplications binaires, complément à 2 ;
- **expliquer** : un code couleur, une image binaire, un format d'image ;
- **programmer** : conversions avec `bin`, `hex`, `int`, `format`, `ord`, `chr`.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Bit** | Chiffre binaire (`0` ou `1`). |
| **Octet** | Groupe de **8 bits**. |
| **Mot** | Groupe de bits traité d'un bloc (selon la machine). |
| **Unité de stockage** | ko, Mo, Go… (multiples de l'octet). |
| **Base** | Nombre de chiffres utilisés (2, 10, 16). |
| **Bit de poids fort** | Bit le **plus à gauche** (poids le plus élevé). |
| **Complément à 2** | Codage des entiers **négatifs**. |
| **Nombre flottant** | Représentation d'un **réel** (signe, exposant, mantisse). |
| **Signe** | Bit indiquant positif (`0`) ou négatif (`1`). |
| **Exposant** | Puissance de 2 (biaisée en IEEE 754). |
| **Mantisse** | Chiffres significatifs du nombre. |
| **ASCII** | Code des caractères sur 7 bits. |
| **Unicode** | Jeu universel de caractères. |
| **UTF-8** | Encodage d'Unicode (taille variable). |
| **Pixel** | Plus petit point d'une image. |
| **Résolution** | Nombre de pixels (largeur × hauteur). |
| **RVB** | Couleur définie par Rouge, Vert, Bleu (0–255). |
| **Compression** | Réduction de la taille d'un fichier. |

---

## 3. Fiches méthodes

??? note "Convertir base 10 → base b (divisions successives)"
    - **Étapes :** diviser par `b`, noter les **restes**, recommencer ; **lire les
      restes de bas en haut**.
    - **Exemple :** `13 → binaire` : 13/2=6 **r1**, 6/2=3 **r0**, 3/2=1 **r1**, 1/2=0 **r1**
      → `1101`.
    - **Erreur :** lire les restes dans le **mauvais sens**.

??? note "Convertir base b → base 10 (puissances)"
    - **Étapes :** multiplier chaque chiffre par `b` puissance sa **position**, additionner.
    - **Exemple :** `1101₂ = 1·8 + 1·4 + 0·2 + 1·1 = 13`.

??? note "Convertir décimal ↔ binaire"
    - **→ binaire :** divisions par 2 ; **→ décimal :** puissances de 2.
    - **Exemple :** `25 = 11001₂` (16 + 8 + 1).

??? note "Convertir binaire ↔ hexadécimal (groupes de 4 bits)"
    - **Étapes :** regrouper les bits **par 4** (depuis la droite), convertir chaque groupe.
    - **Exemple :** `11010110₂ → 1101 | 0110 → D6₁₆` ; et `A3₁₆ → 1010 0011`.
    - **Erreur :** mauvais **regroupement** (oublier de compléter à 4 bits).

??? note "Convertir décimal ↔ hexadécimal"
    - **→ hexa :** divisions par 16 ; **→ décimal :** puissances de 16.
    - **Exemple :** `214 = D6₁₆` (214/16 = 13 reste 6, et 13 = D).

??? note "Additionner en binaire"
    - **Règle :** `1+1 = 10` (0 + **retenue** 1).
    - **Exemple :** `1011 + 0110 = 10001` (11 + 6 = 17).
    - **Erreur :** oublier la **retenue**.

??? note "Multiplier en binaire (approfondissement)"
    - Comme à la main : décaler et additionner.
    - **Exemple :** `101 × 11 = 1111` (5 × 3 = 15).

??? note "Additionner en hexadécimal"
    - **Exemple :** `1A + 2B = 45₁₆` : `A+B = 15₁₆` (écrire 5, retenue 1), `1+2+1 = 4`.

??? note "Compléter un binaire sur 8 bits"
    - Ajouter des **zéros à gauche**.
    - **Exemple :** `101 → 00000101`.

??? note "Coder un entier négatif en complément à 2"
    - **Étapes :** écrire `|n|` sur 8 bits → **inverser** tous les bits → **ajouter 1**.
    - **Exemple :** `-5` : `00000101` → `11111010` → **+1** → `11111011`.

??? note "Décoder un complément à 2"
    - **Bit de signe** `1` → négatif. **Inverser** + **ajouter 1** pour la valeur absolue.
    - **Exemple :** `11111011` → inverser `00000100` → +1 `00000101` = 5 → **−5**.

??? note "Additionner des entiers signés"
    - Additionner les codes sur 8 bits, **ignorer le dépassement** au-delà de 8 bits.
    - **Exemple :** `5 + (−3)` : `00000101 + 11111101 = (1)00000010` → `00000010` = **2**.

??? note "Convertir un réel binaire en décimal"
    - **Étapes :** puissances **positives** à gauche, **négatives** à droite de la virgule.
    - **Exemple :** `101.101₂ = 4 + 1 + 0.5 + 0.125 = 5.625`.

??? note "Convertir la partie fractionnaire décimale en binaire"
    - **Étapes :** multiplier par 2, noter la **partie entière** (0 ou 1), recommencer
      avec la partie fractionnaire.
    - **Exemple :** `0.625` : ×2 = **1**.25 → ×2 = **0**.5 → ×2 = **1**.0 → `0.101`.
    - **Erreur :** une fraction peut donner une suite **infinie** (précision limitée).

??? note "Construire une représentation IEEE 754 (approfondissement)"
    - **Étapes :** signe → écrire en binaire → **normaliser** `1,… × 2^e` → exposant
      **biaisé** (`e + 127`) → mantisse (après la virgule).
    - **Exemple :** `5.625 = 101.101₂ = 1.01101 × 2²` → signe `0`, exposant
      `2 + 127 = 129 = 10000001`, mantisse `01101…` :
      `0 10000001 01101000000000000000000`.
    - **À adapter :** suivre la **convention de l'énoncé** (taille, biais).

??? note "Passer d'un code ASCII au caractère (et inversement)"
    - `chr(code)` → caractère ; `ord(caractère)` → code.
    - **Exemple :** `ord('A') = 65`, `chr(97) = 'a'`.

??? note "Interpréter une image binaire 8×8"
    - Chaque **ligne** = 1 **octet** ; un bit `1` = pixel **noir**, `0` = **blanc** (selon convention).
    - **Exemple :** `00111100` → 2 blancs, 4 noirs, 2 blancs.

??? note "Interpréter une couleur RVB"
    - Trois valeurs **0–255** : Rouge, Vert, Bleu.
    - **Exemples :** `(255, 0, 0)` = rouge (`#FF0000`) ; `(255, 255, 255)` = blanc ;
      `(0, 0, 0)` = noir.

??? note "Comparer BMP, JPEG, PNG, GIF"
    | Format | Compression | Particularité |
    |---|---|---|
    | **BMP** | aucune (ou faible) | fichiers **lourds** |
    | **JPEG** | **avec pertes** | photos |
    | **PNG** | **sans perte** | transparence |
    | **GIF** | sans perte | 256 couleurs, **animations** |

---

## 4. Python

| Fonction | Rôle | Exemple |
|---|---|---|
| `bin(n)` | décimal → binaire (préfixe `0b`) | `bin(13)` → `'0b1101'` |
| `hex(n)` | décimal → hexa (préfixe `0x`) | `hex(214)` → `'0xd6'` |
| `int(ch, base)` | chaîne (base) → décimal | `int('1101', 2)` → `13` |
| `format(n, '08b')` | binaire sur 8 bits | `format(5, '08b')` → `'00000101'` |
| `0b…` / `0x…` | littéral binaire / hexa | `0b1101 = 13`, `0xD6 = 214` |
| `ord(c)` | caractère → code | `ord('A')` → `65` |
| `chr(n)` | code → caractère | `chr(65)` → `'A'` |
| `split(',')` | découper une chaîne | `"255,0,0".split(',')` → `['255','0','0']` |

!!! note "Fonctions des sources"
    | Fonction | Objectif (param → retour) |
    |---|---|
    | `complement_a_2(n, bits)` | code l'entier négatif `n` en complément à 2 → chaîne binaire |
    | `binaire_vers_decimal(b)` | chaîne binaire → entier décimal |
    | `dec2bin(n)` | décimal positif → chaîne binaire |
    | `dec2bin_negatif(n, bits)` | décimal négatif → complément à 2 |
    | `conversion(...)` | conversion d'une base vers une autre |
    | `decimal(...)` | partie / nombre → valeur décimale |
    | `entiere(...)` | extrait / convertit la **partie entière** |
    | `bin2float(...)` | binaire → **flottant** (approfondissement) |

    *Pour chacune : penser aux **tests** (cas ordinaire, valeur nulle, négative, limite)
    et aux **cas incorrects** (mauvaise base, bits insuffisants).*

---

## 5. Lecture et compréhension de code

!!! tip "Méthode"
    - **prévoir un résultat** (suivre le calcul pas à pas) ;
    - **suivre quotient et reste** dans une conversion par divisions ;
    - **suivre une boucle** de conversion (variable accumulée) ;
    - **expliquer une condition** (bit de signe, reste nul…) ;
    - **compléter un code à trous** (init, mise à jour, retour) ;
    - **vérifier les types** (`str` binaire vs `int`) ;
    - **repérer une erreur** (mauvaise base, sens des restes) ;
    - **tester des cas limites** (0, valeur négative, dépassement 8 bits).

---

## 6. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Divisions successives** (ex. `13 → binaire`)
    | Nombre | Quotient | Reste |
    |---|---|---|
    | 13 | 6 | 1 |
    | 6 | 3 | 0 |
    | 3 | 1 | 1 |
    | 1 | 0 | 1 |

    **Décomposition en puissances**
    | Chiffre | Puissance | Contribution |
    |---|---|---|
    | 1 | 2³ = 8 | 8 |

    **Addition binaire**
    | Position | Bits | Retenue | Résultat |
    |---|---|---|---|
    | 0 | 1 + 1 | 1 | 0 |

    **Complément à 2**
    | Étape | Valeur |
    |---|---|
    | `|n|` sur 8 bits | 00000101 |
    | inversion | 11111010 |
    | + 1 | 11111011 |

    **Partie fractionnaire**
    | Avant ×2 | Produit | Bit obtenu | Nouvelle fraction |
    |---|---|---|---|
    | 0.625 | 1.25 | 1 | 0.25 |

    **IEEE 754**
    | Signe | Binaire | Normalisé | Exposant biaisé | Mantisse |
    |---|---|---|---|---|
    | 0 | 101.101 | 1.01101 × 2² | 129 | 01101… |

    **Image 8×8**
    | Ligne | Octet | Pixels |
    |---|---|---|
    | 1 | 00111100 | ⬜⬜⬛⬛⬛⬛⬜⬜ |

---

## 7. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| **Mauvaise base** | vérifier les **chiffres autorisés** (binaire : 0–1 ; hexa : 0–F) |
| **Restes lus à l'envers** | lire **de bas en haut** |
| **Oubli des zéros à gauche** | compléter à 8 bits (ou à 4 pour l'hexa) |
| **Chiffre / valeur confondus** | en hexa, `A = 10`, `F = 15` |
| **Mauvais regroupement par 4** | grouper **depuis la droite** |
| **Erreur de retenue** | reporter `1+1 = 10` |
| **Dépassement sur 8 bits** | ignorer le bit au-delà du 8ᵉ |
| **Oubli d'inverser / d'ajouter 1** | complément à 2 = inverser **puis** +1 |
| **Mauvaise lecture du bit de signe** | bit de poids fort `1` → négatif |
| **Partie entière / fractionnaire** | divisions (entière) vs multiplications (fraction) |
| **Oubli des puissances négatives** | après la virgule : `2⁻¹`, `2⁻²`… |
| **Précision « infinie »** | certaines fractions sont **approchées** |
| **Exposant biaisé** | ajouter le **biais** (127) |
| **ASCII / Unicode / UTF-8 confondus** | ASCII ⊂ Unicode ; UTF-8 = encodage |
| **Résolution / compression** | nombre de pixels ≠ réduction de taille |
| **Mauvaise valeur RVB** | chaque composante **0–255** |

---

## 8. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Combien de bits dans un octet ?"
    **8 bits**.

??? question "2. (N1) Qu'est-ce que le bit de poids fort ?"
    Le bit le **plus à gauche** (poids le plus élevé).

??? question "3. (N2) Différence entre ASCII et Unicode ?"
    ASCII code peu de caractères (7 bits) ; Unicode est **universel** ; UTF-8 en est un **encodage**.

??? question "4. (N1) Que représentent les trois nombres d'un code RVB ?"
    Les intensités de **Rouge**, **Vert**, **Bleu** (0–255).

??? question "5. (N2) À quoi sert le complément à 2 ?"
    À coder les entiers **négatifs** en binaire.

### Compréhension

??? question "6. (N2) Pourquoi lit-on les restes de bas en haut ?"
    Le **dernier** reste est le bit de **poids fort** (calculé en dernier).

??? question "7. (N2) Pourquoi une fraction décimale peut-elle être approchée en binaire ?"
    Sa conversion peut être **infinie** : on la **tronque**, d'où une approximation.

??? question "8. (N2) Pourquoi regroupe-t-on les bits par 4 pour l'hexadécimal ?"
    Parce que 4 bits codent exactement un chiffre hexa (`0000`–`1111` = `0`–`F`).

??? question "9. (N3) Comment reconnaît-on un nombre négatif en complément à 2 ?"
    Son **bit de poids fort** vaut `1`.

??? question "10. (N2) Résolution et compression désignent-elles la même chose ?"
    Non : la **résolution** = nombre de pixels ; la **compression** = réduction de taille.

### Conversion

??? question "11. (N1) Convertir `1010₂` en décimal."
    `8 + 0 + 2 + 0 = 10`.

??? question "12. (N1) Convertir `25` en binaire."
    `11001` (16 + 8 + 1).

??? question "13. (N2) Convertir `D6₁₆` en décimal."
    `13 × 16 + 6 = 214`.

??? question "14. (N2) Coder `−5` en complément à 2 sur 8 bits."
    `00000101` → inverser `11111010` → +1 → `11111011`.

??? question "15. (N3) Convertir `0.75` en binaire."
    ×2 = **1**.5 → ×2 = **1**.0 → `0.11`.

### Lecture de code

??? question "16. (N1) Que renvoie `bin(13)` ?"
    `'0b1101'`.

??? question "17. (N1) Que renvoie `int('1101', 2)` ?"
    `13`.

??? question "18. (N1) Que renvoie `format(5, '08b')` ?"
    `'00000101'`.

??? question "19. (N2) Que renvoie `ord('A')` et `chr(97)` ?"
    `65` et `'a'`.

??? question "20. (N2) Que renvoie `\"255,0,0\".split(',')` ?"
    `['255', '0', '0']`.

### Méthode

??? question "21. (N1) Comment convertir un décimal en hexadécimal ?"
    Par **divisions successives par 16**, restes lus de bas en haut.

??? question "22. (N2) Comment additionner `1011 + 0110` ?"
    En reportant les retenues : résultat `10001` (17).

??? question "23. (N3) Comment décoder `11111011` (8 bits signés) ?"
    Bit de signe `1` → inverser (`00000100`) +1 (`00000101` = 5) → **−5**.

??? question "24. (N2) Comment passer de binaire à hexadécimal ?"
    Regrouper par **4 bits** depuis la droite et convertir chaque groupe.

??? question "25. (N3) Comment écrire `5.625` en binaire ?"
    Partie entière `101`, partie fractionnaire `0.625 → 0.101` → `101.101`.

### Correction d'erreurs

??? question "26. (N1) `1010₂` lu comme `0101` : quelle erreur ?"
    Restes / bits lus **à l'envers**.

??? question "27. (N2) `A + 9 = 19₁₆` est-il correct ?"
    Non : `A = 10`, `10 + 9 = 19` en décimal = `13₁₆`.

??? question "28. (N2) `-3` codé `10000011` : erreur ?"
    Ce n'est pas du complément à 2 : `-3 = 11111101`.

??? question "29. (N1) `sqrt`… non, `hex(255)` attendu `0xff` mais on écrit `255` : pourquoi ?"
    Oubli de la fonction : `hex(255)` renvoie `'0xff'`, pas `255`.

??? question "30. (N3) Couleur `(300, 0, 0)` : erreur ?"
    `300 > 255` : chaque composante RVB doit rester **entre 0 et 255**.

### Programmation / code à compléter

??? question "31. (N1) Compléter : `int('FF', __)` pour obtenir 255."
    `int('FF', 16)`.

??? question "32. (N2) Écrire une expression donnant le code de `'Z'`."
    `ord('Z')` (vaut 90).

??? question "33. (N2) Compléter `format(n, '____')` pour 8 bits."
    `format(n, '08b')`.

??? question "34. (N3) Décoder une ligne d'image `11100000` (1 = noir)."
    3 pixels **noirs** puis 5 **blancs**.

??? question "35. (N4) Convertir `(255, 255, 0)` en hexa et nommer la couleur."
    `#FFFF00` → **jaune** (rouge + vert au maximum).

---

## 9. Exercices flash corrigés

??? question "Reconnaître une base : `1F` est en base… ?"
    Base **16** (présence du chiffre `F`).

??? question "Compléter une table de puissances de 2 (jusqu'à 2⁴)"
    `1, 2, 4, 8, 16`.

??? question "Trouver quotient et reste : 13 ÷ 2"
    Quotient `6`, reste `1`.

??? question "Convertir un petit nombre : `6` en binaire"
    `110`.

??? question "Compléter un groupe de 4 bits : `11 → ____`"
    `0011`.

??? question "Addition : `0011 + 0001`"
    `0100`.

??? question "Coder un négatif : `−1` sur 8 bits"
    `11111111`.

??? question "Décoder un signé : `10000000` (8 bits)"
    Bit de signe `1` → inverser `01111111` +1 `10000000` = 128 → **−128**.

??? question "Convertir une fraction : `0.5` en binaire"
    `0.1`.

??? question "Compléter un IEEE 754 : signe d'un nombre positif"
    Bit de signe `0`.

??? question "Utiliser `ord` / `chr` : code de `'a'`"
    `ord('a') = 97`.

??? question "Décoder une couleur : `(0, 0, 255)`"
    **Bleu** (`#0000FF`).

??? question "Décoder une ligne d'image : `00011000` (1 = noir)"
    3 blancs, 2 noirs, 3 blancs (motif centré).

---

## 10. À retenir absolument

!!! success "Bases & conversions"
    - **chiffres autorisés** : binaire `0–1`, hexa `0–F` ;
    - **base → décimal** : multiplier par les **puissances** de la base ;
    - **décimal → base** : **divisions successives**, restes **de bas en haut** ;
    - **binaire ↔ hexa** : **groupes de 4 bits** ;
    - **addition** : reporter les **retenues** (`1+1 = 10`).

!!! note "Entiers signés & réels"
    - **complément à 2** : `|n|` → **inverser** → **+1** ; bit de signe `1` = négatif ;
    - **fraction décimale → binaire** : **multiplications par 2**, lire les parties entières ;
    - **IEEE 754** : **signe · exposant biaisé · mantisse** *(approfondissement)*.

!!! note "Caractères & images"
    - **ASCII ⊂ Unicode** ; **UTF-8** = encodage d'Unicode ;
    - **pixel** = point d'image ; **RVB** = trois composantes **0–255** ;
    - **résolution** (nb de pixels) ≠ **compression** (réduction de taille).
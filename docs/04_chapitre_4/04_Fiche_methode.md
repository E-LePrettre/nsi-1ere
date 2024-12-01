---
author: ELP
title: 04 Fiche Méthode
---

## **Fiche méthode : Conversion entre les bases**

### **1. Conversion de la base 10 vers une base \( b \)**

#### **Étapes :**
1. **Choisir la base de destination (\( b \)) :**
   - Exemples : \( b = 2 \) (binaire), \( b = 16 \) (hexadécimal), \( b = 5 \) ou \( b = 7 \) etc.

2. **Diviser le nombre en base 10 par \( b \) :**
   - Divisez le nombre entier par \( b \) et notez le **reste** (c'est le chiffre dans la base \( b \)).

3. **Répéter la division :**
   - Prenez le **quotient** obtenu et divisez-le à nouveau par \( b \).
   - Continuez jusqu’à ce que le quotient soit égal à 0.

4. **Lire le résultat :**
   - Les restes, lus de **bas en haut**, donnent le nombre dans la base \( b \).

---

#### **Exemples :**

1. **Conversion de \( 45_{10} \) en base \( 2 \) (binaire) :**
   - \( 45 \div 2 = 22 \), reste \( 1 \)
   - \( 22 \div 2 = 11 \), reste \( 0 \)
   - \( 11 \div 2 = 5 \), reste \( 1 \)
   - \( 5 \div 2 = 2 \), reste \( 1 \)
   - \( 2 \div 2 = 1 \), reste \( 0 \)
   - \( 1 \div 2 = 0 \), reste \( 1 \)

   **Résultat :** \( 45_{10} = 101101_2 \)

2. **Conversion de \( 254_{10} \) en base \( 16 \) (hexadécimal) :**
   - \( 254 \div 16 = 15 \), reste \( 14 \) (\( E \) en hexadécimal)
   - \( 15 \div 16 = 0 \), reste \( 15 \) (\( F \) en hexadécimal)

   **Résultat :** \( 254_{10} = FE_{16} \)

3. **Conversion de \( 78_{10} \) en base \( 5 \) :**
   - \( 78 \div 5 = 15 \), reste \( 3 \)
   - \( 15 \div 5 = 3 \), reste \( 0 \)
   - \( 3 \div 5 = 0 \), reste \( 3 \)

   **Résultat :** \( 78_{10} = 303_5 \)

---

### **2. Conversion d’une base \( b \) vers la base 10**

#### **Méthode avec tableau :**
1. **Dessiner un tableau avec les puissances de la base \( b \) :**
   - Chaque colonne correspond à une puissance de la base \( b \), en commençant par \( b^0 \) (de droite à gauche).

2. **Écrire les chiffres du nombre dans le tableau :**
   - Placez chaque chiffre (en base \( b \)) dans une colonne.

3. **Calculer les contributions de chaque chiffre :**
   - Multipliez chaque chiffre par la puissance correspondante de \( b \).

4. **Additionner les résultats :**
   - La somme des contributions donne le nombre en base 10.

---

#### **Exemples :**

1. **Conversion de \( 101101_2 \) en base \( 10 \) :**

| Puissances de \( 2 \) | \( 2^5 \) | \( 2^4 \) | \( 2^3 \) | \( 2^2 \) | \( 2^1 \) | \( 2^0 \) |
|-----------------------|-----------|-----------|-----------|-----------|-----------|-----------|
| Chiffres             | \( 1 \)   | \( 0 \)   | \( 1 \)   | \( 1 \)   | \( 0 \)   | \( 1 \)   |
| Contributions        | \( 32 \)  | \( 0 \)   | \( 8 \)   | \( 4 \)   | \( 0 \)   | \( 1 \)   |

**Résultat :** \( 32 + 0 + 8 + 4 + 0 + 1 = 45_{10} \)

2. **Conversion de \( FE_{16} \) en base \( 10 \) :**

| Puissances de \( 16 \) | \( 16^1 \) | \( 16^0 \) |
|------------------------|------------|------------|
| Chiffres              | \( F (15) \) | \( E (14) \) |
| Contributions         | \( 15 \cdot 16 = 240 \) | \( 14 \cdot 1 = 14 \) |

**Résultat :** \( 240 + 14 = 254_{10} \)

3. **Conversion de \( 303_5 \) en base \( 10 \) :**

| Puissances de \( 5 \) | \( 5^2 \) | \( 5^1 \) | \( 5^0 \) |
|-----------------------|-----------|-----------|-----------|
| Chiffres             | \( 3 \)   | \( 0 \)   | \( 3 \)   |
| Contributions        | \( 3 \cdot 25 = 75 \) | \( 0 \cdot 5 = 0 \) | \( 3 \cdot 1 = 3 \) |

**Résultat :** \( 75 + 0 + 3 = 78_{10} \)

---

### **3. Conversion binaire <=> hexadécimal**

#### **Règle pratique :**
- **Groupes de 4 bits** : Chaque chiffre hexadécimal correspond à **4 bits** en binaire.
- Conversion directe entre les deux bases sans passer par la base 10.

---

#### **Exemples :**

1. **Conversion de \( 101101_2 \) en hexadécimal :**
   - Groupes de 4 bits (ajouter des zéros à gauche si nécessaire) : \( 101101 \rightarrow 0010\ 1101 \).
   - Convertir chaque groupe : \( 0010 = 2 \), \( 1101 = D \).

   **Résultat :** \( 101101_2 = 2D_{16} \)

2. **Conversion de \( 3E_{16} \) en binaire :**
   - Convertir chaque chiffre hexadécimal en 4 bits :
     - \( 3 = 0011 \), \( E = 1110 \).

   **Résultat :** \( 3E_{16} = 00111110_2 \)

---



### **4. Addition en binaire**

#### **Règles :**
1. **Addition chiffre par chiffre de droite à gauche :**
   - \( 0 + 0 = 0 \)
   - \( 0 + 1 = 1 \)
   - \( 1 + 0 = 1 \)
   - \( 1 + 1 = 10 \) (soit \( 0 \) et une retenue de \( 1 \))
   - \( 1 + 1 + 1 = 11 \) (soit \( 1 \) et une retenue de \( 1 \))

2. **Appliquer les retenues :**
   - Ajouter la retenue au chiffre suivant.

---

#### **Exemple 1 : \( 1011_2 + 1101_2 \)**
1. Écrire les nombres alignés sur la droite :
   ```
         1011
      +  1101
   ```

2. Additionner colonne par colonne, en appliquant les règles :
   - \( 1 + 1 = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 1 + 0 + 1 (\text{retenue}) = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 0 + 1 + 1 (\text{retenue}) = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 1 + 1 + 1 (\text{retenue}) = 11 \), on écrit \( 1 \) et on retient \( 1 \).
   - On place la retenue restante \( 1 \) à gauche.

   **Résultat :** \( 1011_2 + 1101_2 = 11000_2 \)

---

#### **Exemple 2 : \( 11101_2 + 1011_2 \)**
1. Écrire les nombres alignés sur la droite :
   ```
          11101
      +   01011
   ```

2. Effectuer l’addition (avec retenues) :
   - \( 1 + 1 = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 0 + 1 + 1 (\text{retenue}) = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 1 + 0 + 1 (\text{retenue}) = 10 \), on écrit \( 0 \) et on retient \( 1 \).
   - \( 1 + 1 + 1 (\text{retenue}) = 11 \), on écrit \( 1 \) et on retient \( 1 \).
   - \( 1 + 0 + 1 (\text{retenue}) = 10 \), on écrit \( 0 \) et on retient \( 1 \).

   **Résultat :** \( 11101_2 + 1011_2 = 100000_2 \)

---

### **5. Addition en hexadécimal**

#### **Règles :**
1. Additionner chiffre par chiffre de droite à gauche :
   - Si la somme est inférieure à \( 16 \), écrivez directement le résultat.
   - Si la somme est \( \geq 16 \), convertissez-la en hexadécimal et placez une retenue.

2. Utiliser les correspondances hexadécimales pour les chiffres \( A = 10 \), \( B = 11 \), etc.

3. Ajouter les retenues comme en base 10.

---

#### **Exemple 1 : \( 1F_{16} + E_{16} \)**
1. Écrire les nombres alignés :
   ```
         1F
      +   E
   ```

2. Additionner les chiffres de droite à gauche :
   - \( F (15) + E (14) = 29 \), soit \( 1D \) (retenue \( 1 \), écrire \( D \)).
   - \( 1 + 1 (\text{retenue}) = 2 \).

   **Résultat :** \( 1F_{16} + E_{16} = 2D_{16} \)

---

#### **Exemple 2 : \( 3B_{16} + 27_{16} \)**
1. Écrire les nombres alignés :
   ```
          3B
      +   27
   ```

2. Additionner les chiffres de droite à gauche :
   - \( B (11) + 7 = 18 \), soit \( 12 \) en hexadécimal (retenue \( 1 \), écrire \( 2 \)).
   - \( 3 + 2 + 1 (\text{retenue}) = 6 \).

   **Résultat :** \( 3B_{16} + 27_{16} = 62_{16} \)

---





### **6. Représentation des nombres binaires signés**



- **Bit de poids fort (MSB)** :
  - \( 0 \) → Nombre **positif**.
  - \( 1 \) → Nombre **négatif** (en complément à 2).
- Pour un nombre signé sur 8 bits, la plage des valeurs est : \[  -128 \text{ à } 127  \]
  - Exemple :
    - \( 01111111_2 = 127 \) (plus grand nombre positif),
    - \( 10000000_2 = -128 \) (plus petit nombre négatif).

---

### **7. Conversion de binaire signé vers décimal**

#### **Étapes :**
1. Vérifiez le **bit de poids fort** :
   - Si le **bit de poids fort** est \( 0 \), le nombre est positif. Convertissez directement en base 10.
   - Si le **bit de poids fort** est \( 1 \), le nombre est négatif :
     - Complément à 1 : Inversez tous les bits.
     - Complément à 2 : Ajoutez \( 1 \).
     - Convertissez en décimal et ajoutez le signe \( - \).

---

#### **Exemples :**

1. **\( 00000101_2 \) :**
   - MSB = \( 0 \) → nombre positif.
   - \( 00000101_2 = 5_{10} \).

2. **\( 11111011_2 \) :**
   - MSB = \( 1 \) → nombre négatif.
   - Complément à 1 : \( 11111011 \rightarrow 00000100 \).
   - Ajouter \( 1 \) : \( 00000100 + 1 = 00000101 \).
   - Résultat : \( -5_{10} \).

3. **\( 10000001_2 \) :**
   - MSB = \( 1 \) → nombre négatif.
   - Complément à 1 : \( 10000001 \rightarrow 01111110 \).
   - Ajouter \( 1 \) : \( 01111110 + 1 = 01111111 \).
   - \( 01111111_2 = 127_{10} \).
   - Résultat : \( -127_{10} \).

4. **\( 01111111_2 \) :**
   - MSB = \( 0 \) → nombre positif.
   - \( 01111111_2 = 127_{10} \).

---

### **8. Conversion de décimal vers binaire signé**

#### **Étapes :**
1. Si le nombre est **positif**, convertissez directement en binaire avec \( n \) bits.
2. Si le nombre est **négatif** :
   - Prenez la **valeur absolue** et convertissez-la en binaire sur \( n \) bits.
   - Complément à 1 : Inversez tous les bits.
   - Complément à 2 : Ajoutez \( 1 \).

---

#### **Exemples  :**

1. **\( 5_{10} \) :**
   - \( 5 \) en binaire : \( 00000101 \).
   - Résultat : \( 00000101_2 \).

2. **\(-5_{10}\) :**
   - Valeur absolue : \( 5 \) en binaire → \( 00000101 \).
   - Complément à 1 : \( 00000101 \rightarrow 11111010 \).
   - Ajouter \( 1 \) : \( 11111010 + 1 = 11111011 \).
   - Résultat : \( 11111011_2 \).

3. **\(-127_{10}\) :**
   - Valeur absolue : \( 127 \) en binaire → \( 01111111 \).
   - Complément à 1 : \( 01111111 \rightarrow 10000000 \).
   - Ajouter \( 1 \) : \( 10000000 + 1 = 10000001 \).
   - Résultat : \( 10000001_2 \).

4. **\(-128_{10}\) :**
   - Valeur absolue : \( 128 \) dépasse la plage possible. Sur 8 bits, le plus petit négatif est \( -128 \), soit directement \( 10000000_2 \).

---



### **9. Méthode alternative pour calculer le complément à 2 utilisée en programmation**

**Étapes pour appliquer cette méthode :**
1. **Calculez \( 2^n \) (la valeur correspondant à la plage maximale pour \( n \) bits)**.
2. **Soustrayez la valeur absolue du nombre négatif (\( |N| \))**.
3. **Convertissez le résultat en binaire**.
4. **Ajoutez le bit de signe \( 1 \)** à gauche pour indiquer un nombre négatif.

---

#### **Exemple : Calculer \(-88_{10}\) en binaire signé sur 8 bits**

1. **Calculez \( 2^8 = 256 \).**
2. Soustrayez \( |88| \) :
   \[
   256 - 88 = 168
   \]
3. Convertissez \( 168 \) en binaire sur 8 bits :
   \[
   168_{10} = 10101000_2
   \]
4. Ajoutez le bit de signe \( 1 \) pour indiquer que le nombre est négatif :
   \[
   \text{Résultat : } 10101000_2
   \]

---


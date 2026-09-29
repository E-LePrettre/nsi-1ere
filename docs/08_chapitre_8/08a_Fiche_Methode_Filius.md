---
author: Elisabeth Le Prettre (LePrettre)
title: 08a FICHE MÉTHODE — FILIUS
---

# FICHE MÉTHODE — FILIUS

[**Fiche Filius en pdf**](https://eleprettre.forge.apps.education.fr/nsi-1ere/08_chapitre_8/08a_Fiche_Methode_Filius.pdf)

*Où cliquer pour faire quoi ?*

---

## 1. Les deux modes de Filius

Filius a **deux modes** qu'on alterne en permanence. Toute la barre d'outils change selon le mode actif.

| 🔨 Mode CONCEPTION | ▶️ Mode SIMULATION |
|---|---|
| Clic sur l'icône **marteau 🔨** | Clic sur le **triangle vert ▶️** |
| On y **construit** le réseau : | On y **teste** le réseau : |
| • Placer les équipements | • Installer des applications |
| • Les câbler | • Lancer des commandes |
| • Configurer les IP | • Observer les échanges |
| **On ne peut PAS** lancer de commandes ni installer d'applications. | **On ne peut PAS** ajouter ni modifier d'équipements. |

---

## 2. Construire le réseau (mode conception 🔨)

### Ajouter un équipement

| Je veux… | Je fais… |
|---|---|
| **Ajouter un ordinateur** | Barre d'outils → clic sur l'icône Ordinateur portable (ou de bureau) → clic sur le plan de travail pour le poser. |
| **Ajouter un switch** | Barre d'outils → icône Switch → clic sur le plan. |
| **Ajouter un routeur** | Barre d'outils → icône Routeur → clic sur le plan. |
| **Ajouter un serveur** | Barre d'outils → icône Serveur (tour) → clic sur le plan. |
| **Déplacer un équipement** | Sélectionner l'équipement → maintenir clic gauche → glisser. |
| **Supprimer un équipement** | Clic sur l'équipement → touche Suppr (ou clic droit → Supprimer). |

### Câbler deux équipements

| Je veux… | Je fais… |
|---|---|
| **Relier deux équipements** | Barre d'outils → clic sur l'icône **Câble** (fil). Puis : clic sur le **1er équipement** → clic sur le **2e équipement**. Un trait vert apparaît = c'est connecté. |
| **Supprimer un câble** | Clic droit sur le câble → Supprimer. |

!!! warning "Attention"
    Le switch ne se câble jamais directement à un autre switch (dans les activités du cours). Les ordinateurs se branchent au switch, le switch se branche au routeur.

### Configurer un équipement

| Je veux… | Je fais… |
|---|---|
| **Ouvrir la configuration** | **Double-clic** sur l'équipement. La fenêtre de paramétrage s'ouvre. |
| **Donner un nom** | Champ « Nom » en haut de la fenêtre → taper le nom voulu. |
| **Configurer l'adresse IP** | Champ « Adresse IP » → taper l'adresse (ex. : 192.168.1.10). |
| **Configurer le masque** | Champ « Masque de sous-réseau » → en général laisser 255.255.255.0. |
| **Configurer la passerelle** | Champ « Passerelle » → taper l'IP du routeur. Ex. : 192.168.1.1 pour le réseau 192.168.1.x |
| **Configurer le serveur DNS** | Champ « Serveur DNS » → taper l'IP du serveur DNS. |

!!! tip "Astuce"
    Le switch n'a rien à configurer : il fonctionne tout seul dès qu'il est câblé.

### Configurer un routeur

Le routeur est spécial : il a **une interface réseau par câble branché**. Chaque interface a sa propre adresse IP.

| Je veux… | Je fais… |
|---|---|
| **Ouvrir la config du routeur** | **Double-clic** sur le routeur. |
| **Configurer une interface** | Chaque ligne correspond à un câble branché. Cliquer sur la ligne → remplir l'**adresse IP** et le **masque**. Ex. : interface 1 = 192.168.1.1, interface 2 = 192.168.2.1 |

!!! warning "Attention"
    Il faut d'abord câbler le routeur pour que ses interfaces apparaissent. Branchez les câbles d'abord, configurez ensuite.

---

## 3. Tester le réseau (mode simulation ▶️)

### Installer une application

| Je veux… | Je fais… |
|---|---|
| **Ouvrir un équipement** | **Double-clic** sur l'ordinateur ou le serveur. Une fenêtre s'ouvre avec deux onglets : **Bureau** et **Installation de logiciel**. |
| **Installer une application** | Onglet **Installation de logiciel** → cocher l'application voulue → clic sur **Appliquer les modifications**. |
| **Lancer une application** | Onglet **Bureau** → **double-clic** sur l'icône de l'application. |

!!! warning "Attention"
    Si l'application n'apparaît pas sur le Bureau, vérifiez que vous avez bien cliqué sur « Appliquer les modifications » dans l'onglet Installation.

### Lancer une commande réseau

Il faut d'abord installer **Ligne de commande** sur le poste (voir ci-dessus).

| Je veux… | Je fais… |
|---|---|
| **Tester la connexion** | Dans Ligne de commande, taper : `ping 192.168.1.11` (remplacer par l'IP voulue) |
| **Voir ma config réseau** | Taper : `ipconfig` — Affiche l'IP, le masque et la MAC. |
| **Voir le chemin vers une machine** | Taper : `traceroute [IP]` — Affiche tous les routeurs traversés. |
| **Résoudre un nom de domaine** | Taper : `host [nom]` — Ex. : `host www.serverwebdensi.fr` |

### Observer les données échangées

| Je veux… | Je fais… |
|---|---|
| **Voir ce qui transite** | **Clic droit** sur un équipement → **Afficher les données échangées**. Un tableau s'ouvre avec les trames envoyées et reçues (adresses MAC, IP, ports, contenu). |

---

## 4. Utiliser les serveurs

### Serveur générique (envoi de messages)

| Côté serveur | Côté client |
|---|---|
| 1. Installer **Serveur générique** | 1. Installer **Client générique** |
| 2. Ouvrir l'appli | 2. Ouvrir l'appli |
| 3. Port : **55555** | 3. IP : celle du serveur |
| 4. Clic **Démarrer** | 4. Port : **55555** |
| | 5. Clic **Connecter** |
| | 6. Taper un message → **Envoyer** |

### Serveur web (héberger un site)

| Je veux… | Je fais… |
|---|---|
| **Installer le serveur web** | Sur le serveur : installer **Serveur web** + **Éditeur de texte**. |
| **Modifier la page web** | Ouvrir l'**Éditeur de texte** → ouvrir le fichier **/root/webserver/index.html** → modifier le HTML → Enregistrer. |
| **Importer vos fichiers HTML** | Installer **Explorateur de fichiers** sur le serveur. Naviguer dans **/root/webserver/** → Importer vos fichiers (clic droit → Importer). |
| **Démarrer le serveur web** | Ouvrir l'appli **Serveur web** → clic **Démarrer**. |
| **Accéder au site depuis un client** | Sur un autre poste : installer **Navigateur web**. Taper dans la barre d'adresse : **http://[IP du serveur]** — Ex. : `http://192.168.1.12` |

### Serveur DNS (noms de domaine)

| Je veux… | Je fais… |
|---|---|
| **Installer le serveur DNS** | Sur le serveur DNS : installer **Serveur DNS**. |
| **Ajouter un enregistrement** | Ouvrir l'appli **Serveur DNS** → Champ **Nom de domaine** : taper le nom (ex. : `www.serverwebdensi.fr`) → Champ **Adresse IP** : taper l'IP du serveur web → Clic **Ajouter** → puis **Démarrer**. |
| **Utiliser le DNS depuis un client** | Vérifier que l'IP du serveur DNS est renseignée dans la config de **chaque** poste (champ « Serveur DNS » en mode conception). Puis dans le navigateur : `http://www.serverwebdensi.fr` |

---

## 5. Dépannage rapide

### « Mon ping ne fonctionne pas »

- [ ] Vérifiez que les câbles sont verts (pas rouges).
- [ ] Vérifiez les adresses IP : les machines du même réseau doivent avoir les mêmes 3 premiers octets (ex. : 192.168.1.x).
- [ ] Vérifiez le masque de sous-réseau : il doit être identique partout (255.255.255.0).
- [ ] Si les machines sont sur des réseaux différents : vérifiez la passerelle sur chaque poste.
- [ ] Vérifiez les interfaces du routeur : chaque interface doit avoir une IP dans le bon sous-réseau.

### « Je ne trouve pas où cliquer »

| Symptôme | Cause probable |
|---|---|
| Je ne peux pas ajouter d'équipement | Vous êtes en mode simulation. Cliquez sur le marteau 🔨. |
| Je ne peux pas installer d'application | Vous êtes en mode conception. Cliquez sur le triangle ▶️. |
| L'appli n'apparaît pas sur le Bureau | Cliquez sur « Appliquer les modifications » dans l'onglet Installation. |
| Le routeur n'a pas d'interface | Branchez d'abord les câbles au routeur, les interfaces apparaîtront. |
| Le navigateur n'affiche rien | Le serveur web est-il démarré ? L'URL commence-t-elle par http:// ? |
| Le DNS ne marche pas | L'IP du serveur DNS est-elle renseignée sur tous les postes (en mode conception) ? |
| Les câbles sont rouges | Conflit de ports. Débranchez et rebranchez le câble. |

---

## 6. Mémo : les gestes essentiels

???+ note "À retenir"

    **Double-clic sur un équipement**

    - → Mode conception : ouvre la **configuration** (IP, masque, passerelle)
    - → Mode simulation : ouvre le **Bureau** (applications)

    **Clic droit sur un équipement**

    - → Mode simulation : **Afficher les données échangées**

    **Barre d'outils**

    - → **Marteau 🔨** = passer en mode conception
    - → **Triangle ▶️** = passer en mode simulation
    - → **Icône fil** = outil câble (relier deux équipements)

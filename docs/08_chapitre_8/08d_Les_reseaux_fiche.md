---
author: Elisabeth Le Prettre (LePrettre)
title: 08b 📜 Fiche Méthode - Les réseaux
---

# Les réseaux

!!! abstract "Fiche méthode & révision — Première NSI · Chapitre 13"
    Fiche **compacte** pour **refaire seul les exercices et simulations** : adressage
    IP, équipements, couches TCP/IP, protocoles (TCP/UDP, ARP, DNS), **Filius** et
    dépannage.

---

## 1. Objectifs

À la fin du chapitre, vous devez savoir :

- **connaître** les équipements, les couches et les protocoles ;
- **expliquer** encapsulation, routage, résolution DNS, handshake TCP ;
- **calculer** adresse réseau, broadcast, plage d'hôtes ;
- **lire** une trame (Wireshark) ;
- **configurer**, **tester** et **dépanner** un réseau sous **Filius**.

---

## 2. Définitions essentielles

| Terme | Définition |
|---|---|
| **Réseau** | Ensemble de machines reliées. |
| **Protocole** | Règles d'échange. |
| **Client / serveur** | Demande / fournit un service. |
| **Switch** | Relie un réseau **local** (utilise les **MAC**). |
| **Routeur** | Relie des réseaux **différents** (utilise les **IP**). |
| **Box** | Routeur + switch + accès Internet. |
| **Port** | Numéro identifiant un service / une connexion. |
| **Segment / paquet / trame** | Unités des couches Transport / Internet / Accès. |
| **IPv4 / IPv6** | Adresses logiques (32 bits / 128 bits). |
| **NetID / HostID** | Partie **réseau** / partie **machine** d'une IP. |
| **Masque** | Sépare NetID et HostID. |
| **Adresse réseau / broadcast** | Première / dernière adresse d'un réseau. |
| **IP publique / privée** | Routable sur Internet / interne. |
| **NAT** | Traduit privé ↔ public. |
| **Adresse MAC** | Adresse physique de la carte réseau. |
| **ARP** | Trouve la **MAC** à partir d'une **IP**. |
| **Table CAM** | Table MAC ↔ port d'un switch. |
| **Passerelle** | Sortie vers les autres réseaux. |
| **DNS** | Traduit un **nom** en **IP**. |
| **URL** | Adresse d'une ressource web. |
| **Encapsulation / décapsulation** | Ajout / retrait des en-têtes. |
| **TCP / UDP** | Transport **fiable** / **rapide**. |
| **ACK / bit alterné** | Accusé de réception / fiabilité simple. |

---

## 3. Équipements et rôles

| Équipement | Couche | Fonction | Adresses | Situation |
|---|---|---|---|---|
| **Ordinateur** | toutes | client / serveur | IP + MAC | poste utilisateur |
| **Serveur** | Application | fournit un service | IP + MAC | web, DNS… |
| **Switch** | Accès réseau | relie un réseau local | **MAC** | LAN |
| **Routeur** | Internet | relie des réseaux | **IP** | entre réseaux |
| **Box** | Internet/Accès | routeur + switch + accès | IP pub/priv | domicile |
| **Serveur DNS** | Application | nom → IP | IP | résolution |

---

## 4. Couches TCP/IP

| Couche | Protocoles | Unité |
|---|---|---|
| **Application** | HTTP, HTTPS, FTP, DNS | **donnée** |
| **Transport** | TCP, UDP | **segment** |
| **Internet** | IP | **paquet** |
| **Accès réseau** | Ethernet, Wi-Fi | **trame** |

---

## 5. Fiches méthodes

??? note "Séparer NetID et HostID"
    Le **masque** indique les bits du **NetID** (à 1) ; le reste est le **HostID**.

??? note "Convertir un préfixe en masque"
    | Préfixe | Masque |
    |---|---|
    | `/8` | `255.0.0.0` |
    | `/16` | `255.255.0.0` |
    | `/21` | `255.255.248.0` |
    | `/24` | `255.255.255.0` |

??? note "Calculer l'adresse réseau (AND)"
    `réseau = IP AND masque`.
    *Ex. : `192.168.1.10 /24` → `192.168.1.0`.*

??? note "Calculer l'adresse de broadcast"
    Mettre tous les bits **HostID à 1**.
    *Ex. : `192.168.1.10 /24` → `192.168.1.255`.*

??? note "Calculer le nombre d'adresses et de machines"
    `2^h` adresses (`h` = bits hôte) ; `2^h − 2` machines.
    *Ex. : `/24` → `256` adresses, `254` machines.*

??? note "Vérifier si deux IP sont dans le même réseau"
    Comparer leurs **adresses réseau** : identiques → même réseau.
    *Ex. : `192.168.1.10/24` et `192.168.1.200/24` → même (`192.168.1.0`).*

??? note "Choisir la passerelle d'un poste"
    C'est l'**IP du routeur** **dans le réseau** du poste (même NetID).

??? note "Distinguer IP publique et privée"
    **Privées** : `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16` ; **publiques** : le reste.

??? note "Expliquer le rôle du NAT"
    Il **traduit** les IP **privées** en IP **publique** (et inversement) pour sortir sur Internet.

??? note "Retrouver la MAC d'une IP (ARP)"
    Le poste envoie une requête **ARP** « qui a cette IP ? » ; la machine répond avec sa **MAC**.

??? note "Expliquer le fonctionnement d'un switch"
    Il apprend les **MAC** (table **CAM**) et envoie chaque trame **vers le bon port**.

??? note "Suivre l'encapsulation / décapsulation"
    À l'envoi, chaque couche **ajoute** un en-tête (donnée → segment → paquet → trame) ;
    à la réception, chaque couche le **retire**.

??? note "Suivre un paquet passant par un routeur"
    L'**IP** source/destination reste, mais les **MAC** changent à chaque saut.

??? note "Expliquer une résolution DNS"
    Le client interroge le **serveur DNS** avec un **nom** ; il reçoit l'**IP** correspondante.

??? note "Lire une URL"
    `https://www.exemple.fr:443/page` → protocole · domaine · port · chemin.

??? note "Suivre SYN / SYN-ACK / ACK"
    Ouverture TCP : client `SYN` → serveur `SYN-ACK` → client `ACK`.

??? note "Perte, retransmission, doublon (bit alterné)"
    Chaque envoi porte un drapeau **0/1** ; sans **ACK** avant le **timeout**, on **retransmet** ;
    le drapeau permet de repérer un **doublon**.

??? note "Comparer TCP et UDP"
    **TCP** : fiable (séquence, ACK, retransmission) ; **UDP** : rapide, sans garantie.

??? note "Choisir une commande réseau"
    Voir le **tableau des commandes** (§10) selon l'objectif.

??? note "Lire une capture de trame"
    Repérer MAC, IP, protocole, ports, `Seq`/`Ack` (voir §9).

??? note "Analyser une menace et choisir une protection"
    Voir le **tableau menaces / protections** (§11).

---

## 6. Filius

!!! tip "Manipulations clés"
    - **conception** (construire le réseau) vs **simulation** (le faire fonctionner) ;
    - **ajouter et câbler** les équipements ;
    - **configurer** IP, **masque**, **passerelle**, **DNS** de chaque poste ;
    - **configurer les interfaces** d'un routeur (une IP par réseau) ;
    - **installer** : ligne de commande, serveur/client générique, **serveur web**,
      **navigateur**, **serveur DNS** ;
    - **lancer** : `ping`, `ipconfig`, `traceroute`, `host` ;
    - **afficher** les données échangées ;
    - **héberger** un site dans `/root/webserver/` ;
    - **créer** une correspondance **nom ↔ IP** dans le serveur DNS.

---

## 7. Méthode de dépannage Filius

!!! tip "9 étapes"
    1. vérifier le **mode actif** (conception / simulation) ;
    2. vérifier les **câbles** ;
    3. contrôler **IP et masque** ;
    4. vérifier que les postes d'un même réseau partagent le **NetID** ;
    5. contrôler la **passerelle** pour joindre un autre réseau ;
    6. vérifier les **interfaces du routeur** ;
    7. contrôler l'**adresse DNS** ;
    8. vérifier que les **services** sont installés et **démarrés** ;
    9. tester **progressivement** : `ping`, puis `host`, puis navigateur.

---

## 8. Tableaux de suivi

!!! example "Modèles de tableaux"
    **Adressage**
    | IP | Masque | Réseau | Broadcast | Plage d'hôtes |
    |---|---|---|---|---|

    **Encapsulation**
    | Couche | En-tête ajouté | Unité |
    |---|---|---|

    **Handshake TCP**
    | Étape | Drapeau | Séquence | ACK |
    |---|---|---|---|

    **Trajet d'un paquet**
    | Équipement traversé | IP source/dest | MAC source/dest |
    |---|---|---|

    **Commandes**
    | Commande | Objectif | Résultat attendu |
    |---|---|---|

    **Dépannage**
    | Symptôme | Cause probable | Correction |
    |---|---|---|

---

## 9. Lecture de trame

!!! tip "Comment retrouver…"
    - **MAC source / destination** : en-tête de la couche **Accès** ;
    - **IP source / destination** : en-tête **IP** ;
    - **protocole de transport** : TCP ou UDP ;
    - **ports** : ports source et destination ;
    - **service associé** : d'après le port (80 = HTTP, 443 = HTTPS, 53 = DNS) ;
    - **`Seq` / `Ack`** : numéros de séquence et d'accusé (TCP) ;
    - **sens de la communication** : qui est source, qui est destination.

---

## 10. Commandes réseau

| Commande | Rôle |
|---|---|
| `hostname` | nom de la machine |
| `ipconfig` / `ifconfig` | configuration IP (Windows / Linux) |
| `ipconfig /all` | configuration **détaillée** |
| `ipconfig /flushdns` | **vide** le cache DNS |
| `ipconfig /displaydns` | **affiche** le cache DNS |
| `ping` | teste l'accessibilité d'une machine |
| `tracert` / `traceroute` | affiche les **routeurs** traversés |
| `netstat` | connexions et ports ouverts |
| `arp -a` | table **ARP** (IP ↔ MAC) |
| `ip neigh` | voisins (équivalent ARP, Linux) |
| `host` | **résolution DNS** d'un nom |

---

## 11. Menaces et protections

| Menace | Description | Protection | Rôle |
|---|---|---|---|
| **Phishing** | hameçonnage | **chiffrement / vigilance** | éviter le vol d'identifiants |
| **DDoS** | saturation d'un service | **pare-feu / proxy** | filtrer le trafic |
| **MITM** | interception | **HTTPS / TLS, VPN** | chiffrer la liaison |
| **IP spoofing** | usurpation d'IP | **pare-feu** | bloquer les paquets suspects |

| Protection | Rôle |
|---|---|
| **Pare-feu** | filtre les connexions |
| **Proxy** | intermédiaire filtrant |
| **VPN** | tunnel chiffré |
| **Chiffrement** | rend les données illisibles |
| **HTTPS / TLS** | sécurise le web |

---

## 12. Erreurs fréquentes

| Erreur | Cause / correction |
|---|---|
| Confondre **IP** et **MAC** | IP logique / MAC physique |
| Confondre **segment / paquet / trame** | Transport / Internet / Accès |
| Confondre **switch** et **routeur** | MAC (local) / IP (entre réseaux) |
| Confondre **réseau** et **broadcast** | première / dernière adresse |
| Confondre **routeur** et **passerelle** | la passerelle est l'**IP du routeur** côté réseau |
| Confondre **port serveur / temporaire** | service fixe / port client variable |
| Confondre **TCP / UDP** | fiable / rapide |
| Confondre **HTTP / HTTPS** | non chiffré / chiffré |
| Confondre **DNS / URL** | service de résolution / adresse |
| Confondre **MAC finale / MAC passerelle** | dans un autre réseau, on vise la MAC de la **passerelle** |
| **Oublier le DNS** | pas de résolution de nom |
| Deux réseaux **même NetID** | conflit : NetID distincts |
| **Passerelle hors du réseau** | doit avoir le **même NetID** |
| **Service non démarré** (Filius) | installer **et** lancer le service |
| **Mauvais mode Filius** | passer en **simulation** pour tester |

---

## 13. Questions-réponses corrigées

### Vocabulaire

??? question "1. (N1) Quelle adresse utilise un switch ?"
    L'adresse **MAC**.

??? question "2. (N1) À quoi sert un serveur DNS ?"
    À traduire un **nom** en **adresse IP**.

??? question "3. (N2) Différence entre switch et routeur ?"
    Le **switch** relie un réseau local (MAC) ; le **routeur** relie des réseaux (IP).

??? question "4. (N2) Que fait ARP ?"
    Il trouve la **MAC** correspondant à une **IP**.

??? question "5. (N1) Qu'est-ce qu'une passerelle ?"
    La **sortie** d'un réseau vers les autres (IP du routeur).

### Adressage

??? question "6. (N1) Convertir `/24` en masque."
    `255.255.255.0`.

??? question "7. (N2) Réseau et broadcast de `192.168.1.10/24` ?"
    Réseau `192.168.1.0` ; broadcast `192.168.1.255`.

??? question "8. (N2) Combien de machines dans un `/24` ?"
    `2^8 − 2 = 254`.

??? question "9. (N3) `10.0.0.5/24` et `10.0.1.5/24` : même réseau ?"
    Non : réseaux `10.0.0.0` et `10.0.1.0`.

??? question "10. (N2) `192.168.0.4` est-elle publique ou privée ?"
    **Privée** (`192.168.0.0/16`).

### Protocoles

??? question "11. (N1) Quel protocole est fiable, TCP ou UDP ?"
    **TCP**.

??? question "12. (N2) Quels ports pour HTTP et HTTPS ?"
    `80` et `443`.

??? question "13. (N2) Quelle est la suite du handshake TCP ?"
    `SYN` → `SYN-ACK` → `ACK`.

??? question "14. (N3) Que fait le bit alterné en cas de perte ?"
    Sans **ACK** avant le timeout, le segment est **retransmis**.

??? question "15. (N2) Quel protocole de transport pour le streaming rapide ?"
    **UDP**.

### Encapsulation

??? question "16. (N1) Quelle unité à la couche Transport ?"
    Le **segment**.

??? question "17. (N2) Dans quel ordre les unités à l'envoi ?"
    donnée → segment → paquet → trame.

??? question "18. (N2) Que fait chaque couche à l'envoi ?"
    Elle **ajoute** son en-tête (encapsulation).

??? question "19. (N3) Que change un routeur dans un paquet ?"
    Les **MAC** (source/destination) ; les **IP** restent.

??? question "20. (N2) Que fait la décapsulation ?"
    Elle **retire** les en-têtes à la réception.

### Lecture de trame

??? question "21. (N1) Où lit-on les adresses MAC ?"
    Dans l'en-tête de la couche **Accès**.

??? question "22. (N2) Port 53 : quel service ?"
    **DNS**.

??? question "23. (N2) Que donnent `Seq` et `Ack` ?"
    Les numéros de **séquence** et d'**accusé** (TCP).

??? question "24. (N3) Comment connaître le sens d'une communication ?"
    Repérer **qui est source** et **qui est destination**.

??? question "25. (N2) Port 443 : quel service ?"
    **HTTPS**.

### Filius

??? question "26. (N1) Quel mode pour tester un réseau ?"
    Le mode **simulation**.

??? question "27. (N2) Où héberge-t-on un site web dans Filius ?"
    Dans `/root/webserver/`.

??? question "28. (N2) Quelle commande teste l'accessibilité d'un poste ?"
    `ping`.

??? question "29. (N3) Que configure-t-on pour qu'un poste joigne un autre réseau ?"
    Une **passerelle** (IP du routeur du réseau).

??? question "30. (N3) Que crée-t-on dans le serveur DNS ?"
    Une correspondance **nom ↔ IP**.

### Dépannage

??? question "31. (N1) Premier réflexe si un ping échoue ?"
    Vérifier **câbles** et **IP/masque**.

??? question "32. (N2) Deux postes ne se voient pas dans le même réseau : cause ?"
    NetID différents (mauvais masque / IP).

??? question "33. (N2) Le nom ne se résout pas : cause ?"
    DNS mal configuré ou **service non démarré**.

??? question "34. (N3) `ping` par IP marche mais `host` échoue : cause ?"
    Problème **DNS** (le réseau fonctionne, pas la résolution de nom).

??? question "35. (N3) Un autre réseau est injoignable : cause probable ?"
    **Passerelle** absente / incorrecte, ou interface routeur mal configurée.

### Correction d'erreurs

??? question "36. (N1) Annoncer une MAC comme adresse logique : erreur ?"
    La MAC est **physique** ; l'IP est **logique**.

??? question "37. (N2) Passerelle `10.0.0.1` pour un poste `192.168.1.5/24` : erreur ?"
    La passerelle doit avoir le **même NetID** que le poste.

??? question "38. (N2) Deux réseaux avec le même NetID : erreur ?"
    Conflit : leur attribuer des NetID **distincts**.

??? question "39. (N3) HTTP utilisé pour un mot de passe : erreur ?"
    Non chiffré : utiliser **HTTPS**.

??? question "40. (N2) Service web installé mais site inaccessible : erreur ?"
    Le service n'est pas **démarré**.

---

## 14. Exercices flash corrigés

??? question "Reconnaître l'équipement reliant deux réseaux"
    Un **routeur**.

??? question "Réseau et broadcast de `172.16.5.1/24`"
    Réseau `172.16.5.0` ; broadcast `172.16.5.255`.

??? question "Faut-il un routeur entre `192.168.1.x` et `192.168.2.x` ?"
    **Oui** (NetID différents).

??? question "Choisir la passerelle d'un poste `10.0.0.20/24`"
    Une IP du routeur en `10.0.0.x` (ex. `10.0.0.1`).

??? question "Retrouver le port de HTTPS"
    `443`.

??? question "Ordonner les couches TCP/IP (haut → bas)"
    Application → Transport → Internet → Accès réseau.

??? question "Compléter le handshake : `SYN`, ____, `ACK`"
    `SYN-ACK`.

??? question "Choisir une commande pour voir les routeurs traversés"
    `traceroute` (ou `tracert`).

??? question "Lire une ligne Wireshark : port destination 53"
    Service **DNS**.

??? question "Configurer un poste Filius (champs essentiels)"
    IP, **masque**, **passerelle**, **DNS**.

??? question "Diagnostiquer un ping impossible vers un autre réseau"
    Vérifier la **passerelle** et les **interfaces du routeur**.

---

## À retenir absolument

!!! success "Adressage"
    - **réseau** = `IP AND masque` ; **broadcast** = bits hôte à 1 ;
    - `2^h` adresses, `2^h − 2` machines ;
    - **privées** : `10.x`, `172.16-31.x`, `192.168.x` ; **NAT** privé ↔ public.

!!! note "Équipements & protocoles"
    - **switch** = MAC (local) ; **routeur** = IP (entre réseaux) ; **passerelle** = IP du routeur ;
    - **ARP** : IP → MAC ; **DNS** : nom → IP ;
    - **couches** : Application (donnée) → Transport (segment) → Internet (paquet) → Accès (trame) ;
    - **encapsulation** : chaque couche ajoute son en-tête ;
    - **TCP** fiable (`SYN`/`SYN-ACK`/`ACK`, bit alterné) ; **UDP** rapide.

!!! quote "Dépannage Filius"
    mode simulation → câbles → IP/masque → NetID partagé → passerelle → interfaces
    routeur → DNS → services **démarrés** → tester `ping`, `host`, navigateur.
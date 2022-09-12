---
id: g1aii4whycjogz7h281kiuh
title: Robotique Mobile et Navigation
desc: ''
updated: 1662996046053
created: 1662982234199
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par M. Thaix

---

> Notes du 2022/09/12 - Start

# Chap I - Introduction

![](/assets/images/RMN.CM.Slide38.20220912-01.png)

- video sur des compétitions pour concevoir des voitures autonomes pour l'armée (2005 premier succes)

## Modalités du cours

![](/assets/images/RMN.CM.Slide38.20220912-02.png)

## Définitions

![](/assets/images/RMN.CM.Slide38.20220912-03.png)

**Def:**
- **Robotique Mobile** = déplacement d'un **engin mobile** dans un environnement **connu/inconnu** et/ou **exact/imprecis** pour exécuter une tâche
- Qui dit mouvement dit interaction => programmé des opérations
- Boucle continu: Perception --> Décision --> Action --> Perception ...

- comme chez les humains, on peut nécessiter d'avoir des comportements sur plusieurs niveaux selon si l'on veut une reaction rapide ou bien prendre le temps de faire un choix (e.g. main sur une plaque chaude => reaction 'instantanée')

## Généralités

### Déplacement

![](/assets/images/RMN.CM.Slide38.20220912-04.png)

- mouvement => connaître le placement !
- Calcul de trajectoire nécessaire
- aspects décisionnels: evenement asynchrone

### Intérêts

![](/assets/images/RMN.CM.Slide38.20220912-05.png)

### Domaines applicatifs

![](/assets/images/RMN.CM.Slide38.20220912-06.png)

- voiture autonome: easymile
- de nos jours de plus en plus les filoguidés intègre un certain degré d'autonomie

### Constituants

![](/assets/images/RMN.CM.Slide38.20220912-07.png)

Important: Communication !
- Ce système doit garantir qu'en cas de rupture des communications il existe des décisions pré-programmés pour prévenir des accidents potentiels

Locomotion:
- interaction entre le robot et le sol (pts de contact, stabilité statique/dynamique)
- vitesse => roue d'office (oui avec pattes peuvent etre rapide mais la consommation energetique est enorme)

## Robots à roues

### Types de roues

![](/assets/images/RMN.CM.Slide38.20220912-08.png)

- omniwheel (suédoise): sur ligne droite trop de deviation => nécessite une tres bonne connaissance de l'environnement

### Arrangements

![](/assets/images/RMN.CM.Slide38.20220912-09.png)

![](/assets/images/RMN.CM.Slide38.20220912-10.png)

# Chap II - Modèle cinématique de RM à roues

![](/assets/images/RMN.CM.Slide38.20220912-11.png)

- Modèle Cinématique = correspondance entre vitesse du robot et vitesse des roues
- Modèle Dynamique = correspondance entre couple des moteurs au niveau des roues et l'accélération du robot

Hypothèse:
- Robot monocorps
- Contact ponctuel sur sol plat (pas besoin de simulation sur sol sableux, ...)
- Roues indéformables et rayon constant
- Roulement **sans** glissement

## Differential-Drive (unicycle)

![](/assets/images/RMN.CM.Slide38.20220912-12.png)

- placement possible en 2D avec le triplet $(x,y,\theta)$
- ceci ne permet pas de connaitre la configuration exacte des roues (savoir combien de tour la roue a effectué) [ignoré ici]

> forme fétiche en industrie le cercle car si rotation pas de collision 

## Roulement sans glissement

$$
\dot x + r\dot q = 0
$$

$$
J_1 T \dot X = J_2 \dot q = 0
$$

![](/assets/images/RMN.CM.Slide38.20220912-13.png)

## Contrainte de roulement

![](/assets/images/RMN.CM.Slide38.20220912-14.png)

## Contrainte non holonome

### Definition
![](/assets/images/RMN.CM.Slide38.20220912-15.png)

- contrainte non holonome = ne peut pas s'ecrire $f(x_1, \dots, x_n,t) = 0$

- bras à manche => 6 parametres
- mais les pts de depart des manche sont fixe => 4 contraintes
- donc système à deux parametres et 4 contraintes

### Exemple

![](/assets/images/RMN.CM.Slide38.20220912-16.png)

> **Crochet de Lie** = ecart entre deux vecteurs (faire un movement puis faire le mouvement inverse correspondant ne ramene pas au meme vecteur, l'ecart correspond au crochet de lie)

## Modèle cinématique pour RM de Type  Unicycle

![](/assets/images/RMN.CM.Slide38.20220912-17.png)

> À corriger !!!

![](/assets/images/RMN.CM.Slide38.20220912-18


$$
\dot x_c - r \, cos(\theta) \, \dot q_1 + l \, cos(\theta)\dot\theta = 0\\
\dot y_c - r \, cos(\theta) \, \dot q_2 + l \, sin(\theta)\dot\theta = 0\\
l \, sin(\theta) \, cos(\theta) \, \dot q_1 - l \, sin(\theta) \, cos(\theta) \, \dot q_1 = 0\\

$$

$$
\dot x_c = cos(\theta) \, v_c\\
\dot y_c = sin(\theta) \, v_c\\
\dot \theta = \omega = \dfrac{r}{\; 2\,l \;} (\dot q_1 - \dot q_2)
$$

avec $v_c = cos(\theta) \, \dfrac{\; r(\dot q_1 + \dot q_2) \;}{2}$

> À corriger !!!


## Modèle cinématique pour RM de Type voiture

### Problématique

![](/assets/images/RMN.CM.Slide38.20220912-19.png)

Si le point $C$ est positionné sur l'axe des roues alors on peut simplifier le problème avec une matrice inversible

### Equations Trois Roues

![](/assets/images/RMN.CM.Slide38.20220912-20.png)

semi remorque:
- le chauffeur ne controle que le guidant $\omega$ et l'acceleration $v_c$ (frein/gaz) mais il y aura des paramètres supplémentaires $(\theta,\phi,\beta)$
- et ainsi de suite

## Exemple vélo

![](/assets/images/RMN.CM.Exemple.Velo.png)

- Si la traction se faisait sur la roue avant il faudrait simplement remplacer $v_C$ par $v_A$


> Notes du 2022/09/12 - End

---

> Notes du 2022/09/12 - Start



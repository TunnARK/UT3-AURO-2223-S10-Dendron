
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut et P. Ribot

---

> Notes du 2023/01/05 - Start



![](assets/images/PSH.Slide1.Presentation-01.png)

# Sommaire

![](assets/images/PSH.Slide1.Presentation-02.png)

# 1) Introduction

## Objectifs

![](assets/images/PSH.Slide1.Presentation-03.png)

Système Hybride = Systeme mélangeant du formalisme STC et SED

Probleme de theories et de simulations.

## Modalités

![](assets/images/PSH.Slide1.Presentation-04.png)


# 2) Modélisation STC

## Modélisation formelle

![](assets/images/PSH.Slide1.Presentation-05.png)

STC = Systeme Temps Continu

entrees/sorties
etats
equation evolution
equation de sortie

## Hypothèses en TC

![](assets/images/PSH.Slide1.Presentation-06.png)
![](assets/images/PSH.Slide1.Presentation-07.png)

# 3) Modélisation de SED

## Caractéristiques des SED

![](assets/images/PSH.Slide1.Presentation-08.png)

SED = Syst. Evenement Discret


## Concept d'évènement

![](assets/images/PSH.Slide1.Presentation-09.png)

attention evenement est tj instantanee
exogene = exterieur
endogene = interieur

obsvble = mesurable
nonobsvble = blackpox carte dont on connait le fonctionne mais ne mesure pas

## Exemple syst. discret

### Entrepôt

![](assets/images/PSH.Slide1.Presentation-10.png)

### Réservoir d'eau

![](assets/images/PSH.Slide1.Presentation-11.png)


Problematique du choix du niveau d'abstraction

Maquette Bac Eaux tres dynamique mais peut aussi etre represente par un modele discret avec le bon niveau d'absatraction
Capteur binaire donc $2^4$ etats

**Mealy** tout est evenement (tout sur les transitions) front montant sans !!! front descendant avec !!!
Moore sorties sont des niveaux (donc ne se trouve pas sur les transitions) [similaire au reseau de petri]

si plusieurs valeurs possible alors on cree plusieurs etat discret pour faire l'abstraction de la dynamique

### Exemple syst discretisable: Air Conditionné

![](assets/images/PSH.Slide1.Presentation-12.png)

## Modélisation formelle d'un SED

![](assets/images/PSH.Slide1.Presentation-13.png)

## Modélisation par abstraction

![](assets/images/PSH.Slide1.Presentation-14.png)

# 4) Exemples

## SED

### Trains

![](assets/images/PSH.Slide1.Presentation-15.png)

### Bras manipulateur

![](assets/images/PSH.Slide1.Presentation-16.png)

## Automatique

### Rebond de balle

#### Principe fondamental

![](assets/images/PSH.Slide1.Presentation-17.png)

En lair mode 1

$\ddot x  = -g$ les etats $z = [x , \dot x]$ le systeme modelise est alors

$$
\dot z_1 = z_2\\
\dot z_2 = -g
$$

Au sol mode 2

$$
m\ddot x = -mg + F_{rsol} + F_{rebont}\\
\ddot x = - \lambda \dot x
$$

$$
\dot z_1 = 0\\
\dot z_2 = - \lambda \dot x
$$

#### Modélisation des modes

![](assets/images/PSH.Slide1.Presentation-18.png)
![](assets/images/PSH.Slide1.Presentation-19.png)

En lair
$$
\mathcal{C} = \{z\in\mathbb{R}^2 \;|\; z_1>0 \;\text{or}\; (z_1 = 0 \;\text{and}\; z_2>0)\}
$$

Au sol
$$
\mathcal{D} = \{z\in\mathbb{R}^2|z_1 = 0 \;\text{and}\; z_2\leq0\}
$$

Phenomene de ré-initialisation
$$
z_1^{+} = 0\\
z_2^{+} = - \lambda z_2
$$


1er modele
![](assets/images/PSH.BB20230105-1.png)


**phenomene de zenon** quand la CI est z_1=z_2=0

mais vu que le mode sol est instantanee on peut le voir comme une action d'ou le 2eme modele

### Les lucioles

![](assets/images/PSH.Slide1.Presentation-20.png)
![](assets/images/PSH.Slide1.Presentation-21.png)

meme si un flash est un evenement ici on realise un modele globale qui lui considere l'horloge = 1 comme evenement (alors que localement la luciole considere le flash comme evenement)

![](assets/images/PSH.BB20230105-2.png)
![](assets/images/PSH.BB20230105-3.png)
![](assets/images/PSH.BB20230105-4.png)
![](assets/images/PSH.Slide1.Presentation-22.png)

si les lucioles se fatigue a chaque flash il faut adapter le modele

une option c'est de changer l'evolution $\dot \tau = a_i$ via une action conditionne sur $a_i$ (on change les parametres d'un meme modele au final)

autre option est de changer de modele qui lui cree un nouvel etat pour chaque changement d'evolution

cette derniere modelisation apporte l'advantage de garder trace de l'evolution des changements et donc pouvoir etudier le syst. d'un point de vue usage

### Le bloqueur d'ordre zéro

![](assets/images/PSH.Slide1.Presentation-23.png)

Pour l'automatique discrete, le bloqueur d'ordre zero fonctionne sur la theorie des SED

Ici ce modele est a temps continu du coup on s'affranchit l'approximation causer par une discretisation

![](assets/images/PSH.BB20230105-5.png)
![](assets/images/PSH.BB20230105-6.png)
![](assets/images/PSH.BB20230105-7.png)

# 5) Conclusion

> Keywords pour la recherche bibliographique: hybrid automata ; hybrid dynamical system

> termes à retenir

![](assets/images/PSH.Slide1.Presentation-24.png)

# 6) Bibliographie

![](assets/images/PSH.Slide1.Presentation-25.png)




> Notes du 2023/01/05 - End

---
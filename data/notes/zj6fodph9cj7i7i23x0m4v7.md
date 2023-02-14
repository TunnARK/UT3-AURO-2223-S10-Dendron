
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat et M. Thaix

---

> Notes RKA du 2023/01/31 - Start




![](/assets/images/B3.RIA.CM.AssVis-1.png)

En robotique, on applique un entre deux de l'automatique et de la commande trop simpliste.

Parfois une commande purement autom ne pourra pas être mise à jour en temps réelle car trop complexe. Ou encore la commande est trop sensible.

Mais on ne veut pas non-plus introduire trop de simplicité.

# I- Introduction

## Problématique: Approche Classique vs Approche Réf. Capteur

![](/assets/images/B3.RIA.CM.AssVis-2.png)

## Définition

L'**Asservissement Visuel** ou la commande référencée vision consiste à contrôler un robot à partir des infos renvoyées par une ou plusieurs caméras embarquées ou déportées.

## Application

- Robotique mobile (agricole, sous-marine, drones, ...)
- Robotique humanoïde
- Robotique industrielle, médicale, mirco-robotique, ...

## Structure de commande (historique)

Premier travaux 3D environ 1972 avec des temps de calculs qui prenait plus de 5sec. Pour le 2D c'etait 1984 aussi avec des performances faibles.

![](/assets/images/B3.RIA.CM.AssVis-3.png)

De nos jours on a abondonné l'idée de vouloir découplé position et image.

Donc on a essayé la piste de la jacobienne ou du 2D et demi, et en ce moment c'est le photogramétrique et en environnement non contrôlée.

### PBVS: Position-Based Visual Servoing (3D)

On raisonne sur la situation reconstruite avec la caméra.

Advantage:
- maîtrise des trajectoirs du bras

Incinvénient:
- reconstruction prend du temps
- reconstruction oblige à passer sur des modèles donc perte de robustesse (mais de nos jours les caméras 3D sont plus précise)

### IBVS: Image-Based Visual Servoing (2D)

On raisonne dans l'image et donc sur les indices visuels.

Advantage:
- plus de précision

Inconvénient:
- plus difficile de gérer les singularités et autres puisqu'on est pas conscient de la structure

# II- Focus sur l'IBVS

> Les explications données ici seront en caméras embarquées.

![](/assets/images/B3.RIA.CM.AssVis-4.png)


## II-1. Étape 1

L'étape 1 consiste à mettre en relation l'effet des mouvements sur l'image.

### II-1.1) Modélisation Caméra

> Keywords:
- modèle sténopé ;
- projection perspective ;
- focal ;
- centre optique ;
- coordonnées métriques

![](/assets/images/B3.RIA.CM.AssVis-5.png)
![](/assets/images/B3.RIA.CM.BB20230131-01.png)

### II-1.2) Modélisation Intéraction

> Keywords:
- $s$ indices visuels
- $r$ situation caméra

![](/assets/images/B3.RIA.CM.AssVis-6.png)
![](/assets/images/B3.RIA.CM.BB20230131-02.png)
![](/assets/images/B3.RIA.CM.BB20230131-03.png)
![](/assets/images/B3.RIA.CM.BB20230131-04.png)
![](/assets/images/B3.RIA.CM.BB20230131-05.png)

$M$ peut se voir comme une matrice de conversion.

### II-1.3) Modélisation Robot

![](/assets/images/B3.RIA.CM.AssVis-7.png)
![](/assets/images/B3.RIA.CM.BB20230131-06.png)
![](/assets/images/B3.RIA.CM.BB20230131-07.png)
![](/assets/images/B3.RIA.CM.BB20230131-08.png)

## II-2. Étape 2

### Détermination de la commande

![](/assets/images/B3.RIA.CM.AssVis-8.png)

La tâche est définie par l'image de référence (c.à.d. la valeur des indices visuels quand la caméra est à la situation finale $s^*$).

Donc la tâche est réalisée si $s=s^*\;$.

On peut alors définir une erreur dans l'image: $e = s - s^*$ dans le but de faire converger cette erreur à 0.

En robotique, la commande en vitesse est donnée par $u(t) = \dot q(t)\;$.

**Question:** Comment trouver $\dot q(t)$ tel que $e(t) \rightarrow 0\;$ ?

Ceci est équivalent à chercher $\dot q$ tel que $e = e_0\;e^{-\lambda t}\;$  avec $\;\lambda>0\;$.

![](/assets/images/B3.RIA.CM.BB20230131-09.png)
![](/assets/images/B3.RIA.CM.BB20230131-10.png)
![](/assets/images/B3.RIA.CM.BB20230131-11.png)




> Notes RKA du 2023/01/31 - End

---
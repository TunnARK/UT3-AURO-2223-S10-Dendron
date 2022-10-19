---
id: 0lfigiu2hovpehlxl2j0ce1
title: Chap 5 - SLAM - Simultaneous Localization and Mapping
desc: ''
updated: 1666170197477
created: 1663595387176
---

> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par M. Thaix

Support de cours:
- [RMN.CM.SLAM.Poly.pdf](https://homepages.laas.fr/danes/UPS/M2AURO/slamauro.pdf)

> Notation:
- \# = nombre
- landmark = amer (syn. repère)

---




> Notes du 2022/09/19 - Start


# I- Introduction

![](/assets/images/RMN.CM.SLAM.Poly20220919-01.png)

Faire naviguer un robot dans un environnment inconnu en se localisant dans une carte mise à jour régulièrement.

Une autre approche serait de ne pas modéliser tous les environnments mais plustôt utiliser des primitives perceptuelles.

On sait pas si l'être humain utilise une localisation ou bien la méthode des primitives perceptuelles.


Problème probaliste :
- inférence pour caracterise la position du robot et la carte de l'environnment de facon iterative
- filtre de kalman

Autre méthode pour faire du SLAM c'est d'utiliser des graphes de factor (dans ce cas il n'y a plus besoin des notions de probabilité).

# Notions fondamentales

## Features of the problem

![](/assets/images/RMN.CM.SLAM.Poly20220919-02.png)

- Robot equipped with :
    - control inputs
    - odometry
    - self motion
- Aim :  incremental/recursive map building and localization

## Pose Graph

![](/assets/images/RMN.CM.SLAM.Poly20220919-03.png)

- Pose = Position + Configuration du robot
- Pose Graph = Collection de position et configuration
- Graphe de ces poses pour faire des mesures relatives des poses afin d'incorporer des contraintes de fermeture de loop
    - fermeture de boucle = être capable de se rappeler qu'une pose est déjà connu

## Mapping

![](/assets/images/RMN.CM.SLAM.Poly20220919-04.png)

RMN.CM.SLAM.ListesCarte

- Dense metric map = carte de primitive geometrique
- Dyson a mit une camera 360 sur un aspirateur autonome pour reperer les coins des polygones dans l'environnment
- Amers = primitive perceptuelle pour se localiser dans un environnment (des points de repère)

## Localization

Position et du configuration du robot déduites des amers

## SLAM

Sans savoir la pose ni la carte, resoudre la localisation et la cartographie de l'environnement en estimant des vecteurs etats avec des filtres de Bayes (EKF/UKF particle filter).

Ceci dans le but d'optimiser la trajectoire du robot

# II- Survol des manipulations d'incertitudes dans un contexte probabiliste

## Probabilité

![](/assets/images/RMN.CM.SLAM.Poly20220923-p2.png)

### Variables aléatoires

- $x = X(\omega)\;$ : $\;X$ se réalise en $x$
    - Si une variable est en grand alors il s'agit d'une variable aléatoire
    - Si la variable est petite alors il s'agit de la réalisation de la variable aléatoire assoicée
- $P_X(x)$ fonction de répartition

- $p_X(x)$ fonction de distribution (correspond à la dérivée de la fonction de répartition)

![](/assets/images/RMN.CM.SLAM.BB20221017-01.jpg)
> - en bleu fonction de répartition en rouge la distribution
> - densité uniforme dans l'exemple car pour un interval de meme 'taille' on a la meme aire du rectangle comme proba

- $P_X(x) = \int_{I} p_X(\xi)d\xi \quad \longleftarrow$ attention intégrale multivariable

### Gaussienne

- Gaussienne d'une variable aléatoire scalaire : $X \thicksim \mathcal{N}(\overline{x}, \sigma^2)$
- Gaussienne vectoriel : $X \thicksim \mathcal{N}(\overline{x}, P)$

![](/assets/images/RMN.CM.SLAM.BB20220919-1.png)

### Interval/Ellipse de confiance

- Intervalle de confiance : $I_{\alpha} = \left]\overline{x} - \alpha\sigma ; \overline{x} + \alpha\sigma \right[$ tel que $\mathbb{P}(X\in I_{\alpha}) = p_{\alpha}$
- Ellipse de confiance : $\epsilon_{\alpha}$
- Thm de limite centrale : "a random vector which is the sum of a large number of independant random excitations is Gaussian"

### Espérance & Covariance

![](/assets/images/RMN.CM.SLAM.Poly20220923-p3-02.png)

- covariance = distribution de x p.r.à sa moyenne

![](/assets/images/RMN.CM.SLAM.BB20220919-2.png)
![](/assets/images/RMN.CM.SLAM.BB20220919-3.png)


### Joint vs Marginal Distribution

![](/assets/images/RMN.CM.SLAM.Poly20220923-p3-03.png)
![](/assets/images/RMN.CM.SLAM.BB20220919-4.png)
![](/assets/images/RMN.CM.SLAM.BB20220919-5.png)
![](/assets/images/RMN.CM.SLAM.BB20221017-03.jpg)

Exemple de variables dépendantes mais non corrélées:

- [Simple examples of uncorrelated but not independent $X$
and $Y$](https://stats.stackexchange.com/questions/85363/simple-examples-of-uncorrelated-but-not-independent-x-and-y)

![](/assets/images/RMN.CM.SLAM.BB20221017-02.jpg)

Important:
$$
m_{X|Z} = m_X + P_{XZ}P_{ZZ}^{-1}\big(z-m_z\big)\\[0.2cm]
P_{X|Z} = P_{XX} - P_{XZ}P_{ZZ}^{-1}P_{ZX}
$$
- si $P_{XZ}$ et $P_{ZX}$ sont nulles alors $X$ et $Z$ sont mutuellement indépendant et on obtient bien sur que $m_{X|Z}=m_X$ tout comme $P_{X|Z}=P_XX$
- En outre, si $P_{ZZ} = \infty$ alors Z peut etre sur tous l'espace avec la meme probabilité et comme on divise par $P_{ZZ}$ on en déduit que $Z$ n'apporte rien d'utile à la mesure (ce qui fait du sens)

## Estimation de Bayes

> ATTENTION : sur un evenement on ne peut pas connaitre la valeur de $X-\hat X$ mais on connait tres bien sa distribution

- Minimal Mean Sqaure Error (MMSE) = estimation de l'esperance de $X-\hat X$ celle-ci représente la distance quadratic minimale la plus proche de la valeur réelle
- Maximum a Posteriori (MAP)

> En SLAM on utilise bcp le MAP

!!!

### Cas Statique

- Loi a priori nécessite un modèle d'observation donné
- Problématique de nb de mesures prà la dimension du $x$ pour pouvoir résoudre le système
- On décrit statistiquement le vrai paramètre à estimer
    - comme dans l'exemple dé à couleurs changeantes
    - lorsqu'on estime que sous une couleur qui cache la numéro il y a tant de chance d'avoir un certain numéro et pas un autre alors ceci est la loi posterieure
    - cad on estime $x$ (le numéro) à travers la mesure $z$ (la couleur)
![](/assets/images/RMN.CM.SLAM.BB20221019-01.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-02.png)
- en générale déterministe (sans hasard)
- Une fois la loi posterieur trouvée, il faut savoir passer à un estimé (càd trouver une fonction paramétré en $z$ qui retourne $\^x$)
![](/assets/images/RMN.CM.SLAM.BB20221019-03.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-04.png)


#### Exemple 10 mesures
- 10 tirs lasers
- fabriquant dit que chaque mesure donne une mesure vrai plus ou moins qlqs centimètres dans $x\%$ des cas
- attention ces 10 mesures doivent être conjointement indépendante
    - si on croit qu'elles ne sont pas conjointement indépendante alors qu'elles le sont alors ce sera un modèle optimiste
        - ce pb est a faire attention quand on partage des estimations entre robot qui prennent des mesures indépendamment mais fusion leurs estimation régulièrement
    - on evalue la différence statisque des moyennes de $X$ et $\^X$ mais aussi la densité de composant de $\^X$ (soit si les points sont dispercé ou regroupé) ceci à travers le calcul de la covariance de l'estimateur

#### Généralité

![](/assets/images/RMN.CM.SLAM.BB20221019-05.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-06.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-07.png)

> Pic de la loi a posteriori est à la fois $X_{MAP}$ et $X_{MBSE}$

#### Cas $m_z \geq m_x$

![](/assets/images/RMN.CM.SLAM.BB20221019-08.png)

> Rem: Faire le lien avec les **moindres carrés recursifs**

![](/assets/images/RMN.CM.SLAM.BB20221019-09.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-10.png)

> **Matrice d'information**: inverse des matrices de covariances
> **MLE**: Maximum Likelyhood Estimate (pic de vraissemblance)
$$
\^x_{MLE} = \arg_{z} \min_{x} P_{Z|X}(z|x)
$$

### Cas Dynamique

![](/assets/images/RMN.CM.SLAM.BB20221019-11.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-12.png)

> **Attention**:
en orange ce n'est pas du "conjointement indépendant" mais du "**conditionnellement indépendant**" lié à du **Bruit Blanc** (cf. Conditionning ci-dessous)
![[Projet.Kalman.VideoLecture11#conditionning]]

![](/assets/images/RMN.CM.SLAM.BB20221019-13.png)
![](/assets/images/RMN.CM.SLAM.BB20221019-14.png)

> Rem: on travaille ici que sur la marginale et non la jointe

> Prediction = Time Update $\longrightarrow$ 2 equations

> Filtrage = Measurement Update $\longrightarrow$ 3 equations

> Sur matlab, bien ordonner les colonnes sur un instant 


## Exemple Dé à couleurs changeantes

!!!



> Notes du 2022/09/19 - End

---

> Notes du 2022/09/21 - Start






## Linear Gaussian Case

... if Z =....

![](/assets/images/RMN.CM.SLAM.BB20220921-1.png)
![](/assets/images/RMN.CM.SLAM.BB20220921-2.png)

## Dynamic Case

...

# III- Landmarked-based SLAM

## Variables

...

> ATTENTION:
- $r_k$ ne vit pas dans un espace euclidien mais dans l'espace $\mathbb{S}^3$ (cf [[la définition d'une variété dans le sens de la "Category Theory"|CategoryTheory.Def.Category]])
- Exemple une carte de la terre (en 2D) ne sera exacte que localement puisque globalement il existe deux points (i.e. aux pôles) qui auront une latitude unique mais une infinité de longitude 

## Models

...

> **Rem:** 
- $f$ dépend de la géométrie du robot, des modèles geom./ciném. choisis, ...
- On va supposer que les amers sont fixes sinon celles-ci ne le sont pas alors nous n'allons pas les traiter comme des amers mais autrement 
- bruit blanc = bruit n'influence les probilités des evenements ???

## Workflow

- Front-end = collection des amers/data
- Back-end = calcul des estimations

...

# IV- Probabistic SLAM

- En Full SLAM soit avec $p(r_{0:k}\,,\;m|z_{0:k}\,;\;u_{0:k-1})$, on s'interesser à toutes les positions du robot de 0 à k sur toutes les trajectoires possibles
- Alors qu'en Online SLAM soit $p(r_{k}\,,\;m_k|z_{0:k}\,;\;u_{0:k-1})$

## IV-1) EFK Solution

Notation:
- $x_{k+1|k}$ se lit la variable $x$ à l'instant $k+1$ sachant les mesures à l'instant $k$

- Time update = Prediction $\^x_{k+1|k}$ et $\^P_{k+1|k}$

Figure

- Les ellipses représentées ici incorporent les mesures en plus des incertitudes liées à l'odométrie donc ces ellipses sont plus petit que celles vues lorsqu'on a parlé d'erreurs cumulées
- Il suffit de visiter un seul amer pour collasper drastiquement tous les amers (en effet chaques amers sont relatifs l'un à l'autre)
- Une fois que la precision des amers augmente d'office les ellipses représentant la position collapsent aussi

### Illustration


> **Def: ATAN**
- si $x>0 \quad atan2(y,x)=arctan(\frac{y}{x})$
- si $x<0 \quad atan2(y,x)=arctan(\frac{y}{x}) \pm \pi$
![](/assets/images/RMN.CM.SLAM.BB20220921-3.png)

#### Static control input and measurement output variables

![](/assets/images/RMN.CM.SLAM.Poly20220919-001.png)

![](/assets/images/RMN.CM.SLAM.BB20220921-4.png)



- bleu = 2eme membre du bearing
- rouge = 3eme membre du bearing

![](/assets/images/RMN.CM.SLAM.BB20220921-5.png)
![](/assets/images/RMN.CM.SLAM.BB20220921-6.png)
![](/assets/images/RMN.CM.SLAM.BB20220921-7.png)





> Notes du 2022/09/21 - End

---

> Notes du 2022/09/23 - Start





#### Prior Dynamics

![](/assets/images/RMN.CM.SLAM.Poly20220923-01.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-01.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-02.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-03.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-04.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-05.png)

![](/assets/images/RMN.CM.SLAM.Poly20220923-02.png)
> Corriger $\mathcal{g}_{\mathcal{R}}$ par $\mathcal{f}_{\mathcal{R}}$

#### Observation Model

![](/assets/images/RMN.CM.SLAM.Poly20220923-03.png)
![](/assets/images/RMN.CM.SLAM.BB20220923-06.png)

On cherche la première composante de $z_{k,j}$ :
![](/assets/images/RMN.CM.SLAM.BB20220923-07.png)

Puis sa deuxième composante :
![](/assets/images/RMN.CM.SLAM.BB20220923-08.png)

Mais on pouvait aussi voir le problème de la manière suivante en considérant le point $b$ comme suit :
![](/assets/images/RMN.CM.SLAM.BB20220923-09.png)

Ainsi la deuxième composante peut aussi s'écrire $atan2(b,a)$

#### SLAM initialization

![](/assets/images/RMN.CM.SLAM.Poly20220923-04.png)

#### SLAM Time Update

![](/assets/images/RMN.CM.SLAM.Poly20220923-05.png)

#### SLAM Measurement

![](/assets/images/RMN.CM.SLAM.Poly20220923-06.png)

#### Unseen Landmarks

![](/assets/images/RMN.CM.SLAM.Poly20220923-07.png)

#### Data association

Attention à l'association des données :
- Il peut arriver que le robot ne remarque pas que deux mesures d'amer représentent un même amer (et donc il peut y avoir des complications pour la fusion des mesures)
- De même, il peut arriver que les mesures ne soient pas indicées correctement p.r. aux indices des amers

![](/assets/images/RMN.CM.SLAM.Poly20220923-08.png)

## IV-2) Particle Filter Solution

![](/assets/images/RMN.CM.SLAM.Poly20220923-09.png)
> 2 Algo: `FastSLAM 1.0` et `FastSLAM 2.0`

### Réseau Bayésien

![](/assets/images/RMN.CM.SLAM.BB20220923-10.png)

On peut implimenter de l'automatique en définissant des etats et en considérant que l'on fait de l'observation (de la reconstruction d'états)

Localiser le robot c'est faire un tirage des hypothèses des trajectoires du robot associé à un poids mis à jour régulièrement (on ne considère pas les mesures $m$)
$$
p(x) = \sum w_i \delta(\dots)
$$

# V- Optimization SLAM

## Factor Graph Approach

![](/assets/images/RMN.CM.SLAM.Poly20220923-10.png)
![](/assets/images/RMN.CM.SLAM.Poly20220923-11.png)

Les inconnus $X$ sont représentés par des cercles et les mesures par des rectangles
![](/assets/images/RMN.CM.SLAM.Poly20220923-Graph01.png)
L'orientation des flèches vers les mesures reflète que ces mesures sont uniquement dépendantes de leurs parents

Ici, chaque point correspond à un facteur du produit (d'où le nom "Factor Graph")
![](/assets/images/RMN.CM.SLAM.Poly20220923-Graph02.png)

## Statement

![](/assets/images/RMN.CM.SLAM.Poly20220923-12.png)

## Sparse Optimization

![](/assets/images/RMN.CM.SLAM.Poly20220923-13.png)




> Notes du 2022/09/23 - End

---


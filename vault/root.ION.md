---
id: brwx5egxx9wy1how2r6eao1
title: ION - Introduction à l'Optimisation Numérique
desc: ''
updated: 1661858665667
created: 1661846475154
---

# Notes 2022/08/30

![](/assets/images/ION.CoursSlide1.png)

- TP sur Python !!! cf. palteforme **fun mooc**
- ROS utilise C++/Python

## Partie 1 - Concepts et ouitls de base pour l'optimisation

#### Pb Général :
**Minimiser une fonction sous contrainte(s)**

- Reveint à chercher le (ou les) minimum local (global)

![](/assets/images/ION.Cours.PbGeneral.png)

#### Objectif :

![](/assets/images/ION.Cours.Objectif.png)

- seulement minimiser car maximiser revient à minimiser -f

### 1.1 Modélisation mathématique

![](/assets/images/ION.CoursSlide7.png)

#### Tableau Terminologie

![](/assets/images/ION.CoursSlide8.TableauConceptsOpti.png)

- méthode du gradient pour la 4D

### 1.2 Application

![](/assets/images/ION.CoursSlide9.ApplicationsExemple.png)

#### Exemple 1 :

Nape de laser qui nous fournit des points

Chercher à modéliser Y = A X + B

resoudre y_i -ax_i -b = 0 à minimiser en fonction de a et b (les inconnus)

$$
min \sum_{i=1}^{n} (y_i -ax_i -b)
$$

pb d'optimisation sans contraintes

#### Exemple 2 : Construction Hangar

Volume $1500 m^3$ soit LxlxH = 1500

largeur = 2 x hauteur

cout N_1 / m^2 pour le mur

cout N_2 / m^2 pour le plafond

cout N_3 / m^2 pour le sol

Du coup:

$$
min \big( N_1 (2yz+2xz) + N_2 (xy) + N_3 (xy) \big)
$$

s.c. xyz=1500 et y=2z

Pb NLSC non linéaire sous contraintes

#### Exemple 3 : Entrepot Pb de logistique

n dépots et m points de ventes

cout transport C_{ij}

stocks depots X_i

niveau demande D_j

CdC flou car on ne sait si l'objectif est de vider tous les entrepots ou de vendre un maximum ou meme minimiser les couts

ces objectifs sont necessaire pour modéliser cad pour savoir si l'on va utliser une inégalité ou égalité et quelle serait sa structure

Les variables que l'on controle ici sont Xi et x_{ij} le nombre de marchandise transportée de i à j

$c_{ij} \cdot x_{ij} + ...$ 

$$
min_{x_{ij}} \sum_{i=1}^{n} \sum_{j=1}^{m} \Big( c_{ij} \cdot x_{ij} \Big)
$$

s.c. : 
- $X_i = \sum_{j=1}^{m} x_{ij}$
  - (cad vider les depots) -> donc n contraintes d'égalités
  - ou bien $\frac{X_i}{2} \leq \sum_{j=1}^{m} x_{ij} \leq X_i$ ou autre selon le CdC

- $D_j = \sum_{i=1}^{n} x_{ij}$
  - objectif ici : satisfaire la demande

Ici Pb est de type PL linéaire se résoud même avec des systèmes très grands


Exemple 1 => Bloc 1
Exemple 2,3 => Bloc 2

### 1.3 Rappels et Compléments

![](/assets/images/ION.CoursSlide10.Rappels.png)

- Dérivation de fonction scalaire

- Dérivation de fonction vectoriel -> définit un plan tangent

- Gradient de f
  - vector correspondant à la projection du vecteur perpendiculaire au plan tangent au point $x_0$
  - se trouve être perpendiculaire à la courbe de niveau

- Matrice Hessienne (symmétrique)

- les outils d'optimisation se base souvent sur le gradient (avec ordre 1 ou 2) ou la hessienne

- Attention dans le cas de fonction NL le gradient peut ne pas suffir pour minimiser

![](/assets/images/ION.CoursSlide11.DeriveeDirectionnelle.png)

- Dérivée directionnelle :

  ...

- Direction en descente :

  direction _d_ de descente si $d^t \cdot \grad f(x)$ 

- Theorem :

  ...

- Du coup le gradient nous permet de connaitre la directin menant à une minimisation c'est pourquoi bcp d'algorithm utilise le Gradient

#### Exemple : Fonction Quadratique

![](/assets/images/ION.CoursSlide12.FctQuadratic.png)

- Définition: Fonction Quadratique

  - dans ces cas le gradient est connu ! c'est $Qx+G$ du coup 'facile' à minimiser

### 1.4 Vitesse de Convergence d'un algorithme

![](/assets/images/ION.CoursSlide13.VistesseConvergence.png)

- Pq plus pratique d'avoir une convergence quadratique ?

  - supposant l'erreur vaut $10^{-3}$ alors à la prochaine itération elle sera de $10^{-5}$ puis de $10^{-9}$
  - du coup si solution la convergence de l'erreur est plus rapide dans un algo quadratique

### 1.5 Minimum

![](/assets/images/ION.CoursSlide14.Minimum.png)

- en NL les algo ne fonctionnent qu'en local (pas de global à moins d'avoir une chance) [sauf pour les focntions quadratiques ou linéaires]

- si min global nécessaire alors il faut appliquer l'algo sur plusieurs points initiaux

  - pb sur des milliers de min locaux il faut encore plus de point initiaux
    - d'où l'utilisation d'algo génétique
    - ou méthode montécalor (rajoute de l'aléatoire donc accpete que la fonction croisse pour esperer qu'elle descende plus loin)

![](/assets/images/ION.CoursSlide15.ExistenceMin.png)

- focntion coercive si sa limite tend vers l'infinie

### 1.6 Convexité

![](/assets/images/ION.CoursSlide16.Convexite.png)

- fonction convexe 
  - => tout min local est global et unique
  - si matrice hessienne est définie (semi-définie) positive pour tout x alors f est strict. convexe (convexe)

### 1.7 Optimisation d'une fonction d'une variable réelle

![](/assets/images/ION.CoursSlide17.MethodeDichotomie.png)

- f fonction unimodale si :
  - f admet un min unique $x*$ dans $I$
  - f strict. décroissante sur $[a,x*[$ et strict croissante sur $[x*,b[$

- unimodale = fct convexe en dimension 1 (seule la contrainte du strict. s'ajoute à la déf d'une fct convexe)

- méthode dichotomie

![](/assets/images/ION.CoursSlide18.MethodeSectionDoree.png)

- plus éfficace que la méthode de dichotomie car utilise le nombre d'or pour la division dichotomique

![](/assets/images/ION.CoursSlide19.MethodeRecherche.png)

- méthode numérique itérative

### 1.8 Méthode de résolution

![](/assets/images/ION.CoursSlide20.MethodeResolution.png)

- méhtode de _line search_

  - choisir une direction
  - détermine de combien y aller

- méthode de confiance _trust region_

  - approxime autour d'un voisinage

    -> donne la région de confiance

  - puis on cherche la direction de descente dans cette région

- principalement on utilisera la _line search_

![](/assets/images/ION.CoursSlide21.PbHypothenuse.png)

100m de plage

50m de nage

vitesse course 18km/h = 5m/s

vitesse nage 10km/h = (1/0,36)m/s

bombe explose dans 35sec

distance plage courue d_P
distance nage

$$
d_N = \sqrt{(100-d_P)^2+50^2}
$$

minimiser
$$
d_N \cdot \dfrac{1}{v_N} + d_P \cdot \dfrac{1}{v_P} \leq 35
$$

ici temps minimum est 34,96s avec x = 66,59m

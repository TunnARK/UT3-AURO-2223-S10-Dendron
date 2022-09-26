---
id: yojgfew3rfjxo114lk7q9re
title: Introduction à l'Optimisation Numérique
desc: ''
updated: 1664185672582
created: 1662932489444
nav_exclude: true
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par M. Thaix

Support de cours:

- [OE.CM.Slide.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.CM.Slide.pdf)

- [OE.NotesGEA.CM.20220830.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.NotesGEA.CM.20220830.pdf)

- [OE.NotesGEA.CM.20220907.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.NotesGEA.CM.20220907.pdf)

- [OE.NotesGEA.CM.20220908.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.NotesGEA.CM.20220908.pdf)

- [OE.NotesGEA.CM.20220915.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.NotesGEA.CM.20220915.pdf)

- [OE.NotesGEA.CM.20220919.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.NotesGEA.CM.20220919.pdf)



---

> Notes du 2022/08/30 - Start




# Partie 1 - Concepts et ouitls de base pour l'optimisation

![](/assets/images/OE.CoursSlide1.png)


### Pb Général :
**Minimiser une fonction sous contrainte(s)**

- Reveint à chercher le (ou les) minimum local (global)

![](/assets/images/OE.Cours.PbGeneral.png)

### Objectif :

![](/assets/images/OE.Cours.Objectif.png)

- seulement minimiser car maximiser revient à minimiser -f

## 1.1 Modélisation mathématique

![](/assets/images/OE.CoursSlide7.png)

### Tableau Terminologie

![](/assets/images/OE.CoursSlide8.TableauConceptsOpti.png)

- méthode du gradient pour la 4D

## 1.2 Application

![](/assets/images/OE.CoursSlide9.ApplicationsExemple.png)

### Exemple 1 :

Nape de laser qui nous fournit des points

Chercher à modéliser Y = A X + B

resoudre y_i -ax_i -b = 0 à minimiser en fonction de a et b (les inconnus)

$$
min \sum_{i=1}^{n} (y_i -ax_i -b)
$$

pb d'optimisation sans contraintes

### Exemple 2 : Construction Hangar

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

### Exemple 3 : Entrepot Pb de logistique

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

## 1.3 Rappels et Compléments

![](/assets/images/OE.CoursSlide10.Rappels.png)

- Dérivation de fonction scalaire

- Dérivation de fonction vectoriel -> définit un plan tangent

- Gradient de f
  - vector correspondant à la projection du vecteur perpendiculaire au plan tangent au point $x_0$
  - se trouve être perpendiculaire à la courbe de niveau

- Matrice Hessienne (symmétrique)

- les outils d'optimisation se base souvent sur le gradient (avec ordre 1 ou 2) ou la hessienne

- Attention dans le cas de fonction NL le gradient peut ne pas suffir pour minimiser

![](/assets/images/OE.CoursSlide11.DeriveeDirectionnelle.png)

- Dérivée directionnelle :

  ...

- Direction en descente :

  direction _d_ de descente si $\quad d^t \cdot \nabla f(x) < 0$ 

- Theorem :

  ...

- Du coup le gradient nous permet de connaitre la directin menant à une minimisation c'est pourquoi bcp d'algorithm utilise le Gradient

### Exemple : Fonction Quadratique

![](/assets/images/OE.CoursSlide12.FctQuadratic.png)

- Définition: Fonction Quadratique

  - dans ces cas le gradient est connu ! c'est $Qx+G$ du coup 'facile' à minimiser

## 1.4 Vitesse de Convergence d'un algorithme

![](/assets/images/OE.CoursSlide13.VistesseConvergence.png)

- Pq plus pratique d'avoir une convergence quadratique ?

  - supposant l'erreur vaut $10^{-3}$ alors à la prochaine itération elle sera de $10^{-5}$ puis de $10^{-9}$
  - du coup si solution la convergence de l'erreur est plus rapide dans un algo quadratique

## 1.5 Minimum

![](/assets/images/OE.CoursSlide14.Minimum.png)

- en NL les algo ne fonctionnent qu'en local (pas de global à moins d'avoir une chance) [sauf pour les focntions quadratiques ou linéaires]

- si min global nécessaire alors il faut appliquer l'algo sur plusieurs points initiaux

  - pb sur des milliers de min locaux il faut encore plus de point initiaux
    - d'où l'utilisation d'algo génétique
    - ou méthode montécalor (rajoute de l'aléatoire donc accpete que la fonction croisse pour esperer qu'elle descende plus loin)

![](/assets/images/OE.CoursSlide15.ExistenceMin.png)

- focntion coercive si sa limite tend vers l'infinie

## 1.6 Convexité

![](/assets/images/OE.CoursSlide16.Convexite.png)

- fonction convexe 
  - => tout min local est global et unique
  - si matrice hessienne est définie (semi-définie) positive pour tout x alors f est strict. convexe (convexe)

## 1.7 Optimisation d'une fonction d'une variable réelle

![](/assets/images/OE.CoursSlide17.MethodeDichotomie.png)

- f fonction unimodale si :
  - f admet un min unique $x*$ dans $I$
  - f strict. décroissante sur $[a,x*[$ et strict croissante sur $[x*,b[$

- unimodale = fct convexe en dimension 1 (seule la contrainte du strict. s'ajoute à la déf d'une fct convexe)

- méthode dichotomie

![](/assets/images/OE.CoursSlide18.MethodeSectionDoree.png)

- plus éfficace que la méthode de dichotomie car utilise le nombre d'or pour la division dichotomique

![](/assets/images/OE.CoursSlide19.MethodeRecherche.png)

- méthode numérique itérative

## 1.8 Méthode de résolution

![](/assets/images/OE.CoursSlide20.MethodeResolution.png)

- méhtode de _line search_

  - choisir une direction
  - détermine de combien y aller

- méthode de confiance _trust region_

  - approxime autour d'un voisinage

    -> donne la région de confiance

  - puis on cherche la direction de descente dans cette région

- principalement on utilisera la _line search_

![](/assets/images/OE.CoursSlide21.PbHypothenuse.png)

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





> Notes du 2022/08/30 - End

---

> Notes du 2022/09/07 - Start




# Part 2 - Optimisation sans contrainte

![](/assets/images/OE.Slide-22.png)

## A) Conditions

![](/assets/images/OE.Slide-23.png)

Thm: CN1 - Condition nécessaire d'optimatilité du 1er odre

$x^*$ min local ...

![](/assets/images/OE.Slide-24.png)

![](/assets/images/OE.Slide-25.png)

Cas particulier
matrice hessienne avec vp + et - alors ni def + ni def -

![](/assets/images/OE.Slide-26.png)

![](/assets/images/OE.Slide-27.png)

![](/assets/images/OE.Slide-28.png)

Thm: Condition suffisante d'optimalité gloabe

La matrice $Q$ (trouvé lors du calcul de la hessienne) contient l'information.

![](/assets/images/OE.Slide-29.png)

Exemple 1:

![](/assets/images/OE.Slide-29-Ex1.png)

Exemple 2:

![](/assets/images/OE.Slide-29-Ex2.png)

![](/assets/images/OE.Slide-30.png)

Exemple 3:

![](/assets/images/OE.Slide-30-Ex3.png)![](/assets/images/OE.Slide-30-Ex3bis.png)

> **Attention:** les algos nous donne un point critiques or ce point n'est qu'un candidat !


Exemple 4 :

![](/assets/images/OE.Slide-31.png)

![](/assets/images/OE.Slide-31-Ex4-01.png)
![](/assets/images/OE.Slide-31-Ex4-02.png)

> **Méthode:** VERIFIER si la hessienne est bien symmétrique !

> Toute matrice de la forme $\begin{bmatrix}a & b\\ b & 0\end{bmatrix}$ aura toujours des valeurs propres de signes opposés quelque soit les signes de $a$ et $b$ !


## B) Méthodes
![](/assets/images/OE.Slide-32.png)

### Méthode de recherche linéaire
![](/assets/images/OE.Slide-33.png)

Def - Direction de descente

### Algo général
![](/assets/images/OE.Slide-34.png)

> Attention: Travailler avec des erreurs relatives et non pas absolus !

### Thm du gradient
![](/assets/images/OE.Slide-35.png)

### Méthode du gradient
![](/assets/images/OE.Slide-36.png)

#### $\alpha$ bien calibré
![](/assets/images/OE.Slide-37.png)

#### $\alpha$ trop grand
![](/assets/images/OE.Slide-38.png)

#### $\alpha$ trop petit
![](/assets/images/OE.Slide-39.png)

#### $\alpha$ variable
![](/assets/images/OE.Slide-40.png)

#### $\alpha$ optimal
![](/assets/images/OE.Slide-41.png)

Exemple:

![](/assets/images/OE.Slide-41-Ex.png)
![](/assets/images/OE.Slide-41-Exbis.png)

- On calcule le gradient de $f$
- On détermine le pas suivant $\quad x_{k+1} = x_k - \alpha_k \nabla f(x_k)$
- On évalue alors $f$ en $x_{k+1}$
- Il faut alors trouver $\alpha$ en calculant $\quad \partial_{\alpha_k}f(x_{k+1}) = 0$

![](/assets/images/OE.Slide-42.png)

#### Remarque
![](/assets/images/OE.Slide-43.png)

![](/assets/images/OE.BlackBoard.RemAlphaOptimal.png)

### Conditionnment
![](/assets/images/OE.Slide-44.png)

On cherche à avoir un nombre de conditionnement égal à 1.

Or quand on inverse une matrice on obtient un det qui est proche de 0 ce qui rend la matrice mal conditionnée.

Donc on va devoir faire un préconditionnement en otpimisant par un changement de variable pour éviter d'optimiser sur $f$.

#### Exemple
![](/assets/images/OE.Slide-45.png)

#### Pas sur la longueur
![](/assets/images/OE.Slide-46.png)

> Première condition de Wolfe-Armijo (pas trop grand ?)

> Seconde condition de Wofle (pas trop petit ?)

En général, les boites à outils implémente ces critères.

#### Exemple
![](/assets/images/OE.Slide-47.png)

### Convergence globale
![](/assets/images/OE.Slide-48.png)

> Thm de Zoutendijk: convergence globale des algos de descente et pas de wolfe

Pb du thm: il est très difficile de prouver la condition du thm pour le moment.

Les boites à outils sont des algos automatiques qui vérifient des conditions spécifiques.

### Exemple: Méthode du Gradient
![](/assets/images/OE.Slide-49.png)

![](/assets/images/OE.Slide-49-Ex.png)

![](/assets/images/OE.Slide-50.png)

> Selon le point de départ on tombera sur un des points critiques, donc il faut lancer le programme sur plusieurs points.

### Problématiques Quadratiques
![](/assets/images/OE.Slide-51.png)

### Gradient conjugué
> **Attention:** cette méthode n'est à utiliser qu'avec des fonctions quadratiques !

![](/assets/images/OE.Slide-52.png)

![](/assets/images/OE.Slide-53.png)

![](/assets/images/OE.Slide-54.png)

![](/assets/images/OE.Slide-55.png)





> Notes du 2022/09/07 - End

---

> Notes du 2022/09/08 - Start





### Méthode de Newton

![](/assets/images/OE.Slide-56.png)

- En multidim on fait le dev limitee en fct du gradient

![](/assets/images/OE.Slide-57.png)

Def:

- Direction de Newton:
  $$
  d_k = -\Big(\nabla^2 f(x_k)\Big)^{-1}\nabla f(x_k)
  $$

![](/assets/images/OE.Slide-58.png)

![](/assets/images/OE.Slide58-Exo.png)


- Ici nous avons convergé en une seule itération avec cette méthode

![](/assets/images/OE.Slide-59.png)

Pb: cette méthode nécéssite de calculer la hessienne et de l'imverse -> pour éviter cela on utilise la **méthode de quasi-newton**

> En commande optimale on va utiliser des matrices **sparces** [matrices creuses] (contenant des blocs sur la diag et des zéros ailleurs).

### Méthode de quasi-Newton

#### Approximation des dérivées
![](/assets/images/OE.Slide-60.png)

- Utilise une approximation de la dérivée

Def:

- **Equation sécante**
  $$
  d_{k-1} = x_k - x_{k-1}
  $$
- **Matrice Jacobienne** de $f:\mathbb{R}^n \to \mathbb{R}^m$
  $$
  J\big(f(x)\big) = 
  \begin{bmatrix}
  \big( \nabla f_1(x) \big)^T\\
  \vdots\\
  \big( \nabla f_m(x) \big)^T\\
  \end{bmatrix} 
  $$

#### Idée de Broyden

![](/assets/images/OE.Slide-61.png)

- **Idée de Broyden**: minimiser le nombre d'itération en utilisation l'itération précédente pour ne pas tous calculer à nouveau
- Pb: cette idée fonctione pour chercher le zéro d'une fonction mais pas pour le zéro d'un gradient car cette idée ne garantit pas du tout que $A_k$ reste symmétrique

#### Broyden-Fletcher-Goldfarb-Shanno (BFGS)

![](/assets/images/OE.Slide-62.png)

### Moindres Carrés

![](/assets/images/OE.Slide-63.png)

![](/assets/images/OE.Slide-64.png)

**Prop:**
$$
\nabla f(x) = J^T(x) \cdot r(x)
$$
$$
\nabla^2 f(x) = J^T(x) \cdot J(x) + \sum_{j=1}^m r_j(x) \cdot \nabla^2 r_j(x)
$$

Rappel:
- On cherche à trouver les zéros du gradient pour connaître les points critiques
- Puis on cherche à calculer la hessienne
- Dans le cas des moindres carrées, on a la chance que notre fonction peut s'écrire comme une somme de carrés car cela nous permet de connaître le gradient et la hessienne via la jacobienne

#### Moindres Carrés Linéaires

![](/assets/images/OE.Slide-65.png)

#### Exercice: Cercle

![](/assets/images/OE.Slide-66.png)

1. Écrire l'équation du cercle $(a,b,R)$
2. Définir le résidu
3. Écrire le problème à minimiser
4. Structurer ce problème de sorte de le rendre linéaire en faisant le bon choix de paramètres

![](/assets/images/OE.Slide66-Exo.png)

#### Moindres Carrés Pondérés

![](/assets/images/OE.Slide-67.png)

### Moindres Carrés Non-Linéaires

#### Méthode de Gauss-Newton

![](/assets/images/OE.Slide-68.png)

- Idée: considérer négligeable la somme résiduelle dans le calcul de la hessienne dans la méthode de Newton

**Prop:**
$$
\nabla f(x) = J^T(x) \cdot r(x)
$$
$$
\nabla^2 f(x) = J^T(x) \cdot J(x)
$$
On suppose  $\sum_{j=1}^m r_j(x) \cdot \nabla^2 r_j(x) = 0$

#### Advantages/Inconvénient

![](/assets/images/OE.Slide-69.png)

#### Exercice: Gauss-Newton

![](/assets/images/OE.Slide69-Exo.png)




> Notes du 2022/09/08 - End

---

> Notes du 2022/09/15 - Start




#### Complément

![](/assets/images/OE.Slide-70.png)

Méthode de Gauss-Newton utile car nous evite de calculer les dérivées secondes mais certains algos (i.e. Levenberg-Marquardt) posent probleme avec cette methode (comme en Pereception 3D)



Ceci est dû que le probleme est mal posé (l'approximation de Gauss-Newton n'est pas valable gobalement) du coup on va essayer de **régulariser** ce problème (c.à.d. rajouter des contraintes aux CIs pour minimiser l'erreur d'approximation).

Cela implique de faire un choix du coup l'optimisation est **délicate*.*

#### Methode de Tikhonov

$$
\min \frac{1}{2} ||Ax - b||^2 + \frac{\epsilon^2}{2}||F(x)||^2 \quad \text{avec la contrainte} \quad F(x)=0
$$

#### Methode de Levenberg-Marquardt

**Idée:** similaire à Newton mais sur un voisinage de $x$ avec une contrainte de voisinage dépendant à une **région de confiance**

$$
\min \frac{1}{2} ||
$$

![](/assets/images/OE.Slide-71.png)

3 situations:
- solution dans la région de confiance:
  - Contrainte inactive
  - $\lambda = 0$
  - on se retrouve avec Gauss-Newton
- solution sur le bord de la région de confiance
  - la matrice définie positive
  !!!

![](/assets/images/OE.Slide-72.png)

# Part 3 - Optinimisation non linéaire avec contraintes

![](/assets/images/OE.Slide-73.png)

## A) Conditions théoriques

points admissibles: points respectent toutes les contraintes

contraintes actives: $g_j(x)\leq0$
  - active si $g_(x^*)=0$
  - inactive si $g_(x^*)<0$

![](/assets/images/OE.Slide-74.png)

### Cone des directions & Contraintes linéairement indépendante (LICQ)

![](/assets/images/OE.Slide-75.png)


> $f(x)$ pour la fonctione étudié

> $g(x)$ pour les contraintes d'inégalités

> $h(x)$ pour les contraintes d'égalités

### Optimisation avec contrainte égalité

**Fonction lagrangienne** $L$

$$
L(x,\lambda) = f(x) + \lambda^t \, h(x)
$$

![](/assets/images/OE.Slide-76.png)

**Pourquoi rajouter le $\lambda$ ?**

On souhaite minimiser le $x$ sous la contrainte que $x$ appartiennent à une surface $S_1$.

$$
\min_{x\in S_1} ||x|| = \min f(x)
$$

Supposons que la surface est représentable par une contrainte d'égalité $h_1(x)$. On peut alors calculer son gradient.

On va utiliser le gradient de $h$ pour contraindre la minimisation de $f$ d'où l'intéret du $\lambda$ vu qu'on va chercher à resoudre :

$$
\nabla f \pm \lambda \nabla h = 0
$$

<!-- OE.Slide76-Nota -->


#### Thm KKT (Condition Necessaire Karush-Kuhn-Tucker)

> pas une condition d'ordre 1

![](/assets/images/OE.Slide-77.png)

![](/assets/images/OE.Slide-78.png)

#### Exemple

![](/assets/images/OE.Slide-79.png)

![](/assets/images/OE.Slide79-Ex-01.png)
![](/assets/images/OE.Slide79-Ex-02.png)
![](/assets/images/OE.Slide79-Ex-03.png)
![](/assets/images/OE.Slide79-Ex-04.png)
![](/assets/images/OE.Slide79-Ex-05.png)

<!-- 
OE.Slide79-Ex01

OE.Slide79-Ex02

!!!

OE.Slide79-GEA01

OE.Slide79-GEA01
-->

#### Illustration de la direction admissible

OE.Slide79-DirecAdmissible01

OE.Slide79-DirecAdmissible02

#### Exemple Bonus

![](/assets/images/OE.Slide-80.png)

> Solution Lundi

#### Advantages de KKT

> Resolution d'equations lineaires

![](/assets/images/OE.Slide-81.png)

> ATTENTION: sur un probleme réel $A$ n'est jamais carré !


### Optimisation avec contrainte égalité et inégalité

![](/assets/images/OE.Slide-82.png)

#### Thm KKT Conditions Necessaires

![](/assets/images/OE.Slide-83.png)

> Attention: Ici $y\neq0$

#### Thm KKT Conditions Suffisantes

![](/assets/images/OE.Slide-84.png)

#### Exemple

![](/assets/images/OE.Slide-85.png)

![](/assets/images/OE.Slide-86.png)



> Notes du 2022/09/15 - End

---

> Notes du 2022/09/19 - Start




## B) Méthodes et algorithmes

![](/assets/images/OE.Slide-87.png)

> Problème très difficile !

### Méthode du gradient projeté

![](/assets/images/OE.Slide-88.png)

![](/assets/images/OE.Slide-89.png)

> La projection résoud un problème d'optimisation

### Lagrangien augmenté

![](/assets/images/OE.Slide-90.png)

Idée: on resoud une probleme d'optimisation sans contrainte en espérant qu'à force toutes les contraintes sont respectées

On appele aussi cette technique une régularisation

> Peut aussi s'appliquer aux contraintes d'inégalité

![](/assets/images/OE.Slide-91.png)

> Lagrangien augmenté =  on inclue les contraintes dans le lagrangien

> On ne connait pas $\lambda$ et $c$ (plus difficile de faire converger $\lambda$ vers $\lambda^*$)

![](/assets/images/OE.Slide-92.png)

> Attention: $\tau>1$ dans $c_{k+1} = \tau \, c_k$

> Au final l'optimisation avec contraintes se ramène aux contraintes sans contraintes




> Notes du 2022/09/19 - End

---

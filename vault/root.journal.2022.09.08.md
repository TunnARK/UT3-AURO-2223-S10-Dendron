---
id: khtoumzyqzrdh52xdq7mcc7
title: '2022-09-08'
desc: ''
updated: 1662938731135
created: 1662615930573
traitIds:
  - journalNote
published: false
---

# OE - 07H45/09H45

#### Méthode de Newton

![](/assets/images/OE.Slide-56

- En multidim on fait le dev limitee en fct du gradient

![](/assets/images/OE.Slide-57

Def:

- Direction de Newton:
  $$
  d_k = -\Big(\nabla^2 f(x_k)\Big)^{-1}\nabla f(x_k)
  $$

![](/assets/images/OE.Slide-58

OE.ExoSlide58

- Ici nous avons convergé en une seule itération avec cette méthode

![](/assets/images/OE.Slide-59

Pb: cette méthode nécéssite de calculer la hessienne et de l'imverse -> pour éviter cela on utilise la **méthode de quasi-newton**

> En commande optimale on va utiliser des matrices **sparces** [matrices creuses] (contenant des blocs sur la diag et des zéros ailleurs).

#### Méthode de quasi-Newton

##### Approximation des dérivées
![](/assets/images/OE.Slide-60

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

##### Idée de Broyden

![](/assets/images/OE.Slide-61

- **Idée de Broyden**: minimiser le nombre d'itération en utilisation l'itération précédente pour ne pas tous calculer à nouveau
- Pb: cette idée fonctione pour chercher le zéro d'une fonction mais pas pour le zéro d'un gradient car cette idée ne garantit pas du tout que $A_k$ reste symmétrique

##### Broyden-Fletcher-Goldfarb-Shanno (BFGS)

![](/assets/images/OE.Slide-62

#### Moindres Carrés

![](/assets/images/OE.Slide-63

![](/assets/images/OE.Slide-64

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

##### Moindres Carrés Linéaires

![](/assets/images/OE.Slide-65

##### Exercice: Cercle

![](/assets/images/OE.Slide-66

1. Écrire l'équation du cercle $(a,b,R)$
2. Définir le résidu
3. Écrire le problème à minimiser
4. Structurer ce problème de sorte de le rendre linéaire en faisant le bon choix de paramètres

OE.ExoCercle

##### Moindres Carrés Pondérés

![](/assets/images/OE.Slide-67

#### Moindres Carrés Non-Linéaires

##### Méthode de Gauss-Newton

![](/assets/images/OE.Slide-68

- Idée: considérer négligeable la somme résiduelle dans le calcul de la hessienne dans la méthode de Newton

**Prop:**
$$
\nabla f(x) = J^T(x) \cdot r(x)
$$
$$
\nabla^2 f(x) = J^T(x) \cdot J(x)
$$
On suppose  $\sum_{j=1}^m r_j(x) \cdot \nabla^2 r_j(x) = 0$

##### Advantages/Inconvénient

![](/assets/images/OE.Slide-69

##### Exercice: Gauss-Newton

OE.ExoGaussNewton

# VI TD1 - 10H00/12H00

### I.3) Matrices de Passage Homogènes

#### Question 3.1:

![](/assets/images/VIRCRV.TD1.Question31.png)

Il s'agit de la composition d'une translation et d'une rotation.

Il nous faut donc une matrice de passage homogène.

$$
T_{01} =
\begin{bmatrix}
    R_{01} & {P_{01}}_{(0)}\\
    \mathcal{O}_{1\times 3} & 1
\end{bmatrix}
$$

avec 
$$
{P_{01}}_{(O)} = \overrightarrow{O_0O_1}_{(O)} =
\begin{pmatrix}
    a\\
    b\\
    c\\
\end{pmatrix}
$$

...

**Conclusion:** Rotation autour de $\overrightarrow{z}_0$ d'angle $\theta$

#### Question 3.2:

![](/assets/images/VIRCRV.TD1.Question32.png)

BM à 6 liaisons donc $\mathcal{R}_6$ est le repère lié à l'OT

VIRCRV.TD1.Question32.RepereO6

VIRCRV.TD1.Question32.RepereO7

Ici on s'interesse à $\;\overrightarrow{O_0O_7}_{(O)}$ soit la position de $O_7$ dans $\mathcal{R}_0$.

Pour calculer $\;\overrightarrow{O_0O_7}_{(O)}$,  on a besoin de $T_{06}$


- relation intrinsèque 
  $$
  \overrightarrow{O_0O_7} = \overrightarrow{O_0O_6} + \overrightarrow{O_6O_7}
  $$
  - position interne de l'outils
- relation extrinsèque
  $$
  \overrightarrow{O_0O_7}_{(O)} = \overrightarrow{O_0O_6}_{(O)} + \overrightarrow{O_6O_7}_{(O)}
  $$
  - postion outils dans l'environmmnet

$$
\overrightarrow{O_0O_7}_{(O)} = \overrightarrow{O_0O_6}_{(O)} + \overrightarrow{O_6O_7}_{(O)}
...  
$$

**Autre solution:**

$$
\begin{pmatrix}
    \overrightarrow{O_0O_7}_{(O)}\\
    1\\
\end{pmatrix}
= T_{06}
\begin{pmatrix}
    \overrightarrow{O_6O_7}_{(O)}\\
    1\\
\end{pmatrix}
= 
\begin{pmatrix}
    0 & 1 & 0 & 0\\
    0 & 0 & 1 & L\\
    1 & 0 & 0 & H\\
    0 & 0 & 0 & 1\\
\end{pmatrix}
\begin{pmatrix}
    d_1\\
    0\\
    d_2\\
    1
\end{pmatrix}
=
\begin{pmatrix}
    0\\
    d_2+L\\
    d_1+H\\
    1
\end{pmatrix}
$$

**Conclusion:** Situation de l'OT
$$
x = 
\begin{pmatrix}
    x_P\\
    x_R\\
\end{pmatrix}
\quad\text{avec}\quad
x_P = 
\begin{pmatrix}
    0\\
    d_2+L\\
    d_1+H
\end{pmatrix}
\quad\text{et}\quad
x_R = 
\begin{pmatrix}
    {\overrightarrow{x_6}}_{(0)}\\
    {\overrightarrow{z_6}}_{(0)}\\
\end{pmatrix}
=
\begin{pmatrix}
    0\\
    0\\
    1\\
    0\\
    1\\
    0
\end{pmatrix}
$$

cosinus directeurs partiels souvent choisit avec x et z


---


# VI - CM BM

## Modélisation des BM

VIRCRV.BM.Slide01

### I- Problématique

**Pb:**
- Faire un lien entre l'espace opérationnel et l'espace des configurations pour obtenir les modèles
- Il existe différents types de modèles

VIRCRV.BM.BlackBoard.MGMC

**But:** Survol de ces modèles et une première méthode de calcul

### II- Modèle Géométrique (MG)

> **ATTENTION:** Le temps n'intervient pas dans ce modèle (**"modèle photo" pas de mouvement !**) donc, pour faire bouger le BM, ce modèle est nécessaire mais pas suffisant.

#### II-1) MGD

VIRCRV.BM.Slide02

On cherche à trouver $x = 
\begin{pmatrix}
    x_P\\
    x_R\\
\end{pmatrix}$ en fct de $q$.

> Le **vecteur de configuration** $q$ est connu !

Les $q_i$ sont aussi appelées les **coordonnées généralisées** ou **articulaires**.

On travaille en 2 étapes:
1. **Matrice de Passage Homogème:** Calculer de $T_{0n}$ en fct de $q$
2. **Repr. de la Situation:** De $\;T_{0n}\;$, on déduit $\;\overrightarrow{O_0O_{n+1}}_{(O)}\;$ puis on fait un choix de coord. opéra. $x$ que l' on calcule

VIRCRV.BM.Slide04

##### Etape 1

- Entrer le calcul direct de $\;T_{0n}\;$ est trop compliqué (sauf sur un BM "simple")

- Idée:
  1. Positionner un repère $\mathcal{R}_i$ sur chaque corps $C_i$
  2. Calculer les matrices de passage homogènes $T_{i-1,i}(q_i)$
  >  $T_{i-1,i}(q_i)$ ne dépend que de $q_i$ seul
  3. Déduire $\;T_{0n}(q) = \prod_{i=1}^n \; T_{i-1,i}(q_i)$

- **Rem:**
  - Positionnement des repères $\mathcal{R}_i$ sur les corps $C_i$ 
    - Positionnement au hasard
      - $T_{i-1,i}$ spécifique donc pas d'automatisation possible du calcul
      - bon pour BM avec peu de liaisons
    - Respecter une convention
      - Expression générique de $T_{i-1,i}$ donc automatisation du calcul possible
      - Très bien adapté aux BM industriels

VIRCRV.BM.Slide06

##### Etape 2

VIRCRV.BM.Slide07

#### II-2) MGI

VIRCRV.BM.Slide08

On connaît les coord. oper. $x$ et on cherche la configuration $q$ (ou LES configurations).

Par essence, MGI est plus compliqué que MGD car pour une même coord. oper. $x$ on peut (souvent) trouver plusieurs config possibles.

##### Méthode de calcul

1. De $x$, on calcule $T_{0n}$ de ce calcul on définit un ${T_{0n}}^*$ qui est connu
  $$
  {T_{0n}}^* = 
  \begin{bmatrix}
    t_{11} & t_{12} & t_{13} & t_{14}\\
    t_{21} & t_{22} & t_{23} & t_{24}\\
    t_{31} & t_{32} & t_{33} & t_{34}\\
    0 & 0 & 0 & 1
  \end{bmatrix}
  $$
2. Calculer le MGD pour trouver $T_{0n}(q)$
3. Identifier $T_{0n}(q)$ à ${T_{0n}}^*$ et trouver $q$ tel que
  $$
  {T_{0n}}(q) = {T_{0n}}^*
  $$

### III- Modèle Cinèmatique

**Attention:**
- Temps intervient donc mouvement possible
- On néglige les effets dynamiques (inerties frottements,...)
- MC passage des vitesses généralisées/articulaires $\dot q$ vers les vitesses oper. $\dot x$ via MCD et inversement via MCI

#### III-1) Modèle Cinématique Direct (MCD)


Situation particulière 
$$
x =
\begin{pmatrix}
    x_P\\
    x_R\\
\end{pmatrix}
=
\begin{pmatrix}
    x_1\\
    \vdots\\
    x_m\\
\end{pmatrix}
=
\begin{pmatrix}
    f_1(q_1,\dots,q_n)\\
    \vdots\\
    f_m(q_1,\dots,q_n)\\
\end{pmatrix}
\longleftarrow \; \text{MCD}
$$

On dérive le MCD pour trouver $\dot x$ avec la **matrice jacobienne du BM** $J$:

$$
\dot x = 
\begin{pmatrix}
    \partial_{q_1} f_1 & \dots & \partial_{q_n} f_1 \\
    \vdots & \ddots & \vdots\\
    \partial_{q_1} f_m & \dots & \partial_{q_n} f_m\\
\end{pmatrix}
\begin{pmatrix}
    \dot q_1\\
    \vdots\\
    \dot q_m\\
\end{pmatrix}
$$

> **ATTENTION:** **$J$ dépend de $q$** et $J$ n'est **pas forcément carré** !

VIRCRV.BM.Slide09

#### III-2) MGI

On connaît $\dot x$ et on cherche $\dot q$

> On ne dérive jamais le MGI !

On tire avantage de l'équation du MCD : $\quad \dot x = J(q)\;\dot q\quad$
  - bonus simple résolution algébrique
  - seul pb est lié à $J$ étant dépendant de $q$
    - ceci nous amène parfois à des $J$ non inversible 
    - c'est le cas lorsque le degré de liberté diminue
  - mais on peut aussi avoir de la redondance
    - permet de réaliser pls taches (robot humanoide: equilibre, attrape objet, ...)

> À l'ingénieur de bien poser l'équation pour répondre aux besoins

> Prendre une bouteille peut se faire le bras tendue tous le long du deplacement ou seulement a la fin ! 
> Selon la taille de $J$, on obtient 3 cas
  - $m=n$ donc $\; \dot q = {J(q)}^{-1}\;\dot x\quad$
  - $m>n$ alors il nous faut utiliser les moindres carrés
  - $m<n$ donc il y a une infinité de solution
    - c'est dans ce cas que la notion de redandonce peut etre utilisé pour faire des choix de comportement
    - $\dot q = {J(q)}^{+}\;\dot x + (...)g$
    - le premier terme correspond à notre but puis s'ajoute à cela une infinité de config possible où $g$ s'identifie souvent à un gradient représentant différents critères de performances (optimisation énergétique, spatiales, ...)



---



# CR FG 13H30/15H30

Cas réalisation minimale:

Pour obtenir une réalisation minimale, il faut étudier le rang des matrices résidus.

Soit, $\;\rho_i = rang(N_i)\;$ alors il existe $\;C_i\in\mathbb{R}^{p\times\rho_i}\;$ et $\;B_i\in\mathbb{R}^{\rho_i\times m}\;$ tel que $\;N_i=B_i\,C_i\;$

Finalement,
$$
y(s) = \sum_{i=1}^{n}\dfrac{\;C_i\,B_i\;}{s-p_i}\,u(s)
$$

Ainsi, on pose $\;x_i(s) = \dfrac{B_i}{s-p_i}u(s) \;\in\mathbb{R}^{\rho_i}$

On en déduit le système suivant avec $1\leq i \leq n$:

$$
\dot x_i(t) = p_ix_i(t) + B_i u(t)
$$
$$
y(t) = \sum_{i=1}^{n}C_ix_i(t) + D
$$

Dont le nombre d'états est égal à la somme des $\rho_i$ .

CR.FG.Cours0908.systemeABCD

> EXAMEN: $D\neq0$ alors il faut faire la div eucli de la frac ratio

**Thm:** Cette représentation est **minimale** !

> **Repr. minimale** = nb minimale d'etats qui sont cmble et obsble 

## Réalisation sous forme compagne de commande par bloc

**Exemple:** 
$$
G(s) = \dfrac{s+3}{\;s^2+4s+8\;}
$$

**Rem:** Forme Compagne de Commande
- Dans la forme comp. de cmmde, on peut lire facilement le poly. caractéristique
- Dans la forme comp. de cmmde, on sépare clairement le numérateur de la FT donc ça part dans C
- Très liée aux variables du plan de phase donc aux dérivées de la chaine d'intégrateur
- La difficulté est dans le numérateur donc récrire l'équation avec une variable intermédiaire $v(s)$

1. Transformer $y(s)$ avec la variable intermédiaire $v(s)$
2. Définir un plan de phase sur $v(s)$ en posant $\;x_1(t) = v(t)\;$ et $\;x_2(t) = \dot v(t)\;$

CR.FG.Cours0908.FormeCompABCDGS

> Dès qu'on arrive au plan de phase, il n'est plus nécessaire de se preoccuper du rang car d'office tous ces etats sont forcément comble et obsble

> Méthode de ? = Minimiser le nb de + et x 

#### Cas général

Considérant $\;G(s)\in\mathbb{R}^{p\times m}\;$ et $\;G(s) = \dfrac{1}{\;d(s)\;}N(s)\;$, donc
$$
y(s) = \dfrac{1}{\;d(s)\;}N(s)\;u(s)
$$

On va essayer de réaliser une forme compagne de commande pour chaque $u(s)$.

On pose 
$\;N(s) = 
\begin{bmatrix}
  N_1(s) & \dots & N_m(s)
\end{bmatrix}\in\mathbb{R}^{p\times m}\;$ et donc $\;y(s) = \sum_{i=1}^{m}y_i(s)\;$ avec
$$
y_i(s) = \dfrac{1}{\;d(s)\;}N_i(s)\;u_i(s)
$$

> Forcément cmble car pour chaque entrée on crée un form comp cmde SISO

Soit $\;d(s) = s^n+a_{n-1}s^{n-1}+\dots+a_o\;$ et on pose $\;v_i(s) = \frac{1}{d(s)}u_i(s)\;$.

On choisit 
$$
\left\{
  \begin{array}{rcl}
    x_{1i}(t) & = & v_i(t) \\
    x_{2i}(t) & = & \dot v_i(t) \\
    &\vdots&\\
    x_{ni}(t) & = & v_i^{(n-1)}(t) \\
\end{array}\right.
$$

$$
\dot X_i(t) = AX_i(t) + BU_i(t)
$$

$$
A=
\begin{bmatrix}
  0 & 1 & & \\
  & \ddots & \ddots & \\
  & & 0 & 1\\
  -a_0 & -a_1 & \dots & -a_{n-1}
\end{bmatrix}
\quad\text{et}\quad
B=
\begin{bmatrix}
  0\\
  \vdots\\
  0\\
  1
\end{bmatrix}
$$

Or $\quad y(s) = N_i(s)v_i(s)\quad$ donc on pose $\quad N_i(s) = \sum_{j=1}^{n}N_{ji}\;s^{j-1}$

Du coup, $\quad y(t) = \sum_{j=1}^{n}N_{ji}\;x_{ji}(t)\quad$ et
$\quad B=
\begin{bmatrix}
  N_{1i} & \dots & N_{ni}
\end{bmatrix}$

On répète l'opération pour les $m$ entrées et on somme les contributions des états sur les sorties.

Finalement, on obtient $n\times m$ états **commandables**.

CR.FG.Cours0908.BlocDeFormCompCmde

**Exemple:** MISO 
$$
H(s) =
\begin{bmatrix}
  \dfrac{1}{\;s\;} & \dfrac{1}{\;s(s+2)\;} & \dfrac{1}{\;(s+1)(s+3)\;}
\end{bmatrix}
$$
Q1) Appliquer la méthode de Gilbert à $H(s)$

1. Mettre sous la forme de smith
2. Faire la decomposition matricielle en elmnts simple
3. Poser $x_i(s) = N_i(s)u(s)$
4. Remplir le système 


Q2) Appliquer la forme de compagne de commande à $H(s)$


# COOSATR - 15H45/17H45

> git a été developpe pour le noyau linux

# Lien utile
- [Bac à Sable pour apprendre Git](https://learngitbranching.js.org/)

# Code Management

![](/assets/images/COOSTAR.SlideCodeMgmt.01.png)

- [Lien vers les slides](https://homepages.laas.fr/matthieu/talks/git.pdf)

![](/assets/images/COOSTAR.SlideCodeMgmt.02.png)

## Agenda
![](/assets/images/COOSTAR.SlideCodeMgmt.03.png)

## Introduction
![](/assets/images/COOSTAR.SlideCodeMgmt.04.png)

![](/assets/images/COOSTAR.SlideCodeMgmt.05.png)

### Version Control Concepts
![](/assets/images/COOSTAR.SlideCodeMgmt.06.png)

- un commit = un freeze de l'état d'un dossier
  - prend la version parent
  - regarde ce qui est nouveau
  - en fait un hash
  - lors de la creation avec `git init` on cree un revision parente ici A puis chaque commit donne l'etat B puis C
  

![](/assets/images/COOSTAR.SlideCodeMgmt.07.png)

- possibilité de revenir sur un parent et faire une nouvelle branche
- historiquement la branche principale en Forge était appelé `master` puis elle a été corrigé à `main`
- dans projet on essais d'éviter de créer trop de branches

### Handling branches

![](/assets/images/COOSTAR.SlideCodeMgmt.08.png)

### Working in teams

![](/assets/images/COOSTAR.SlideCodeMgmt.09.png)

### Centralized model

![](/assets/images/COOSTAR.SlideCodeMgmt.10.png)

### Distributed model

![](/assets/images/COOSTAR.SlideCodeMgmt.11.png)

- Advantage plus besoin d'etre directement connecter au serveur (donc transfert de fichier plus rapide)

## Git Concepts

![](/assets/images/COOSTAR.SlideCodeMgmt.12.png)

**Def:** Repository / diff or patch / commit (verb and noun) / branch / tag 

![](/assets/images/COOSTAR.SlideCodeMgmt.13.png)

- tag reste à jamais sur un commit alors que la branch change à chaque commit
  - interface tig
    - `[]` branches du pc local (en bold pour la branch current)
    - `{}` branches sur le serveur

**Def:** Working Tree / Index / Blob

![](/assets/images/COOSTAR.SlideCodeMgmt.14.png)

### Git Interfaces

![](/assets/images/COOSTAR.SlideCodeMgmt.15.png)

Autre interface: `git gui`

### Git Forges

![](/assets/images/COOSTAR.SlideCodeMgmt.16.png)

### Initial Setup

![](/assets/images/COOSTAR.SlideCodeMgmt.17.png)

- `--global` configuration appliquée sur le pc
- set favorite editor: `git config --global --add core.editor emacs -nw`
- configuration stockée dans `~/.gitconfig`

## Individual Developper

![](/assets/images/COOSTAR.SlideCodeMgmt.18.png)

### Creating repository

![](/assets/images/COOSTAR.SlideCodeMgmt.19.png)

### Adding files

![](/assets/images/COOSTAR.SlideCodeMgmt.20.png)

### Querying Status

![](/assets/images/COOSTAR.SlideCodeMgmt.21.png)

> Pour montrer le status du dossier

### Committing changes

![](/assets/images/COOSTAR.SlideCodeMgmt.22.png)

- `git commit -a` réalise un `add` et puis `commit` en une seule ligne
- `-m` pour attacher un message au commit

### Git Index

![](/assets/images/COOSTAR.SlideCodeMgmt.23.png)

### Commits

![](/assets/images/COOSTAR.SlideCodeMgmt.24.png)

- digital signature
  - permet de comparer un clone en l'identifier avec une cle

### Interactive add

![](/assets/images/COOSTAR.SlideCodeMgmt.25.png)

- `-i` permet de visualiser quels fichiers selectionner pour le commit

### Looking Back

![](/assets/images/COOSTAR.SlideCodeMgmt.26.png)

- `index 6bd8f3c..c0ee9ab 100644` indique qu'on compare commit 6bd8f3c avec c0ee9ab et donne l'attribut de c0ee9ab avec 100644 pour indiquer si les permissions sont read/write/exe

### Examining Changes

![](/assets/images/COOSTAR.SlideCodeMgmt.27.png)

### Marking a version

![](/assets/images/COOSTAR.SlideCodeMgmt.28.png)

### Fixing mistakes

![](/assets/images/COOSTAR.SlideCodeMgmt.29.png)

## Using Branches

![](/assets/images/COOSTAR.SlideCodeMgmt.30.png)

### Branches

![](/assets/images/COOSTAR.SlideCodeMgmt.31.png)

### Switching branches

![](/assets/images/COOSTAR.SlideCodeMgmt.32.png)

### Listing available branches

![](/assets/images/COOSTAR.SlideCodeMgmt.33.png)

### Merging changes from another branche

![](/assets/images/COOSTAR.SlideCodeMgmt.34.png)

- fast forward vs normal merge
- software meld montre bien le principe des "3 way merge"

### Handling conflicts

![](/assets/images/COOSTAR.SlideCodeMgmt.35.png)

### Tools to help with merge

![](/assets/images/COOSTAR.SlideCodeMgmt.36.png)

### Picking individual changes

![](/assets/images/COOSTAR.SlideCodeMgmt.37.png)

- cherry-pick

### Replaying changes from a branch

![](/assets/images/COOSTAR.SlideCodeMgmt.38.png)

### Rebase

![](/assets/images/COOSTAR.SlideCodeMgmt.39.png)

### Interactive Rebase

![](/assets/images/COOSTAR.SlideCodeMgmt.40.png)

> DON'T USE after pushing ! Why ?

## Working together

![](/assets/images/COOSTAR.SlideCodeMgmt.41.png)

### Copying a repository

![](/assets/images/COOSTAR.SlideCodeMgmt.42.png)

### Remote repository

![](/assets/images/COOSTAR.SlideCodeMgmt.43.png)

> La remote s'appelle par défaut `origin`

### Updating from a repository

![](/assets/images/COOSTAR.SlideCodeMgmt.44.png)

### Remote branches

![](/assets/images/COOSTAR.SlideCodeMgmt.45.png)

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

---
id: 79qv6ar44g8507aebvkrrbu
title: Chap 3 - Modélisation des Bras Manipulateurs
desc: ''
updated: 1662980221790
created: 1662937716192
nav_order: 30
---


> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par V. Cadenat

Support de cours:
- ...

---


> Notes du 2022/09/08 - Start

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





> Notes du 2022/09/08 - End

---

> Notes du 2022/09/? - Start


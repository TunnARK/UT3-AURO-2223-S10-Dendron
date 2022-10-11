---
id: c8w59wkp2hs6zpwhjthixb2
title: Chap 2 - Outils Fondamentaux
desc: ''
updated: 1665498202663
created: 1662929802355
nav_order: 20
---

> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat

Support de cours:
- [VIRCRV.NotesRKA.SlideOutilsFondam.20220901.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/VIRCRV.NotesRKA.SlideOutilsFondam.20220901.pdf)
- [VIRCRV.NotesGEA.20220901.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/VIRCRV.NotesGEA.20220901.pdf)

---

> Notes Cours 09/01 - Start

![](/assets/images/VIRCRV.SlideOutilsFondam.01.png)

## I- Représentation de la situation de l'OT

![](/assets/images/VIRCRV.SlideOutilsFondam.02.png)

**Rappel:**
  - **Configuration** = Positiion de la SM donc $q = \begin{pmatrix} q_1 \\ ... \\ q_n 
\end{pmatrix}
$
  - **Situation** de l'OT =
    - **Position** de l'OT par rapport à $\mathcal{R}_0$ ; et
      - **Position** de l'OT = Position d'un point de référence de l'OT $O_{n+1}$ p.r.à $\mathcal{R}_0$
    - **Orientation** de l'OT par rapport à $\mathcal{R}_0$.
      - Définie par $x = \begin{pmatrix} x_P \\ x_R\end{pmatrix}$
      - **Orientation** de l'OT = Orientation du repère $\mathcal{R}_n$ lié à l'OT p.r.à $\mathcal{R}_0$
    - donc **Situation OT = Position de $\;\mathcal{O}_{n+1}\;$ + Orientation de $\;\mathcal{R}_n\;$ p.r.à $\;\mathcal{R}_0$** 

**Question:** Quelle représentation mathématique ?

![](/assets/images/VIRCRV.SlideOutilsFondam.03.png)


### I-1) Représentation de la position

**Problématique:** Quels paramètres utiliser pour représenter la position de $\;\mathcal{O}_{n+1}\;$ p.r.à $\;\mathcal{R}_0$* ?

- Premier choix (naturel) = Coord. Cartésiennes
  - **Coord. Opérationnelles de position :** $\quad x_P = \begin{pmatrix} x\\ y\\ z\end{pmatrix} = \overrightarrow{\mathcal{O}_0\mathcal{O}_{n+1}}_{(0)}$
  - ceci pour 90% des cas car permet de représenter n'importe quelle position
  - mais dans certains cas il est plus intéressant d'utiliser d'autres répères comme les coord. sphériques

![](/assets/images/VIRCRV.SlideOutilsFondam.04.png)

#### Cart. --> Cylindriques

VIRCRV.SlideOutilsFondam.CalcCartCyl

- Au lieu d'utiliser arc tangente qui rend un angle entre -pi/2 et pi/2 les roboticiens préfèrent utiliser arc tangent 2 noté $\quad atan2(Y,X) \in\; ]-\pi,\pi[$

- **Singularité de réprésentation** = infinité de réprésentations possibles
  - exemple (cas particulier):
    
    $X=Y=0$ implique $\rho=0$ et $\theta$ indéfini donc on a une singularité de représentation

    On ne peut pas définir la position de manière unique

![](/assets/images/VIRCRV.SlideOutilsFondam.05.png)

### I-2) Représentation de l'orientation

![](/assets/images/VIRCRV.SlideOutilsFondam.06.png)

**Question:** Quels paramètre utiliser pour représenter l'orientation de $\;\mathcal{R}_{n}\;$ p.r.à $\;\mathcal{R}_0$*

**Objectif:** Définir $x_R$

**Rem:**
  - Il faut au moins 3 param. pour définir l'orientation
  - Plus on a de param. moins on risque d'avoir de singularité

#### I-2.1) Une première paramétrisation : Cosinus directeurs

Cette paramétrisation nous donne les **cosinus directeurs**.

- **Cosinus directeurs directes** : $\quad x_R = \begin{pmatrix} {\overrightarrow{x}_n}_{(0)}\\ {\overrightarrow{y}_n}_{(0)}\\ {\overrightarrow{z}_n}_{(0)}\end{pmatrix}$
  - donc nous avons ici **9 paramètres**

- **Cosinus directeurs partiels** : $\quad x_R = \begin{pmatrix} {\overrightarrow{x}_n}_{(0)}\\  {\overrightarrow{z}_n}_{(0)}\end{pmatrix}$ avec ${\overrightarrow{y}_n}_{(0)} = {\overrightarrow{z}_n}_{(0)} \wedge {\overrightarrow{x}_n}_{(0)}$
  - donc seulement **6 paramètres**

**Rem:** ${\overrightarrow{x}_n}_{(0)}$, ${\overrightarrow{y}_n}_{(0)}$ et ${\overrightarrow{z}_n}_{(0)}$ permettent de définir la **matrie de rotation** :
$$
\quad R_{o,n} = \begin{bmatrix}\cdot&\cdot&\cdot\\\cdot&\cdot&\cdot\\\cdot&\cdot&\cdot\\\end{bmatrix} = \begin{pmatrix} {\overrightarrow{x}_n}_{(0)} & {\overrightarrow{y}_n}_{(0)} &  {\overrightarrow{z}_n}_{(0)} \end{pmatrix}
$$

**Exemple:**

VIRCRV.SlideOutilsFondam.ExempleMatRotation

#### I-2.2) Autres paramétrisations

![](/assets/images/VIRCRV.SlideOutilsFondam.07.png)

##### Overview

- **Représentation 3 angles**:
  - **Advantages**: 3 angles donc 3 paramètres du coup repr. minimales
  - **Inconvéniant** il existera des singularité de repr.

- **Représentation non minimales avec 4 param.**:
  - **Advantages**: Pas de singularité et peu de param.
  - **Inconvéniant** Pas toujours très visuel

##### Représenation à 3 angles

![](/assets/images/VIRCRV.SlideOutilsFondam.08.png)

-  **Angle de Bryant** (ou de Cadrant)

  ![](/assets/images/VIRCRV.SlideOutilsFondam.09.png)

  ![](/assets/images/VIRCRV.SlideOutilsFondam.10.png)

  ![](/assets/images/VIRCRV.SlideOutilsFondam.11.png)

-  **Angle d'Euler**

  ![](/assets/images/VIRCRV.SlideOutilsFondam.12.png)

  ![](/assets/images/VIRCRV.SlideOutilsFondam.13.png)

**Exemple:**

VIRCRV.SlideOutilsFondam.ExempleRepr3angles

- Vérifier si $r_{13} \neq \pm 1$ pour savoir si on a une singularité
- si pas de sing. alors utiliser les formules

##### Représenation à 4 param.

![](/assets/images/VIRCRV.SlideOutilsFondam.14.png)

Pb complètement différent vu qu'on cherche à définir la rotation éffectuée par son **axe** et son **angle**

- Pour l'axe, on va définir une **droite** à l'aide de son **vecteur directeur unitaire** $\overrightarrow{u}$

- Pour l'angle, on utilise son **angle de rotation** $\theta$

**N.B.:**

- On donne les composantes de $\overrightarrow{u}$ dans $\mathcal{R}_0$ : $\quad {\overrightarrow{u}}_{(0)} = \begin{pmatrix} {\overrightarrow{u}_x}\\  {\overrightarrow{u}_y}\\ {\overrightarrow{u}_z}\\ \end{pmatrix}$

- Ceci donne les **coord. opérationnel d'orientation** : $\quad x_{R} = \begin{pmatrix} \theta\\{\overrightarrow{u}_x}\\  {\overrightarrow{u}_y}\\ {\overrightarrow{u}_z}\\ \end{pmatrix}$

![](/assets/images/VIRCRV.SlideOutilsFondam.15.png)

##### Les Quaternions

![](/assets/images/VIRCRV.SlideOutilsFondam.16.png)

- $\eta$ lié à l'angle de rotation $\theta$
- ${\overrightarrow{\epsilon}}_{(0)}$ lié à l'axe de rotation de $\overrightarrow{u}$

> Les Quarternions sont très utilisés car ils permettent de garder de meilleurs optimisations malgré que cette repr. soit moins visuelle.

**Exemple:**

VIRCRV.SlideOutilsFondam.ExempleQuaternions

#### I-2.3) Bilan

![](/assets/images/VIRCRV.SlideOutilsFondam.17.png)

![](/assets/images/VIRCRV.SlideOutilsFondam.18.png)

![](/assets/images/VIRCRV.SlideOutilsFondam.19.png)

![](/assets/images/VIRCRV.SlideOutilsFondam.20.png)



> Notes Cours 09/01 - End

---

> Notes Cours 09/07 - Start



## II- Matrices de transformation

**But** Acquérir la deuxième compétence -> changement de repère

![](/assets/images/VIRCRV.SlideOutilsFondam.21.png)

Cas général: $\mathcal{R}(O,{\overrightarrow{x}},{\overrightarrow{y}},{\overrightarrow{z}})_{fixe} \longrightarrow \mathcal{R}'(O,{\overrightarrow{x}},{\overrightarrow{y}},{\overrightarrow{z}})_{mobile}$

2 cas:
  - $\mathcal{R}'$ effectue seulement une rotation p.r.à $\mathcal{R}$
  - $\mathcal{R}'$ effectue une translation et une rotation p.r.à $\mathcal{R}$

### II-1) Rotation seule

On est dans le cas où:
  - seules la direction des axes ${\overrightarrow{x'}},{\overrightarrow{y'}},{\overrightarrow{z'}}$ change
  - $O = O'$

La rotation effectuée est caractérisée par la matrice de rotation
$$
R =
\begin{matrix}
\times & \times & \times & \leftarrow{\overrightarrow{x}}_{(\mathcal{R}')}\\
\times & \times & \times & \leftarrow{\overrightarrow{y}}_{(\mathcal{R}')}\\
\times & \times & \times & \leftarrow{\overrightarrow{z}}_{(\mathcal{R}')}\\
{\overrightarrow{x'}}_{(\mathcal{R})} & {\overrightarrow{y'}}_{(\mathcal{R})} & {\overrightarrow{z'}}_{(\mathcal{R})}\\ 
\end{matrix}
$$

La matrice de rotation est aussi une matrice de passage entre $\mathcal{R}$ et $\mathcal{R}$'.

VIRCRV.SlideOutilsFondam.RMatPassage

**Prop:** $$R^{-1} = R^T$$

$R$ est une matrice orthonormale: 
  - Tips: du coup une façon de vérifier qu'il n'y est pas d'erreur c'est de vérifier que la matrice est bien orthonormale

Def:
  - Une matrice est _**orthonormée**_ si **toutes les colonnes et toutes les lignes ont une norme 1** ET **le produit scalaire des cols 2 à 2 est nulle**

**Composition des rotations**

VIRCRV.SlideOutilsFondam.CompositionRotation

### II-2) Rotation + Translation

![](/assets/images/VIRCRV.SlideOutilsFondam.22.png)

On est dans le cas où:
  - la direction des axes ${\overrightarrow{x'}},{\overrightarrow{y'}},{\overrightarrow{z'}}$ change
  - $O \neq O'$

On rend compte ici de la rotation avec $R$ et de la translation avec ${\overrightarrow{OO'}}_{(\mathcal{R})}$

Localisation de $M$

VIRCRV.GEAOutilsFondam.LocalisationM

**Bilan**
- si rotation seule: $R$
    $$
        {\overrightarrow{OM}}_{(\mathcal{R})} = R \;\cdot\;{\overrightarrow{OM}}_{(\mathcal{R'})}
    $$
- si rotation seule: $R\;$ et $\;{\overrightarrow{OO'}}_{(\mathcal{R})}$
$$
    {\overrightarrow{OM}}_{(\mathcal{R})} = R \;\cdot\;{\overrightarrow{O'M}}_{(\mathcal{R'})} + {\overrightarrow{OO'}}_{(\mathcal{R'})}
$$ 

![](/assets/images/VIRCRV.SlideOutilsFondam.23.png)

**Def:**
- **Matrice de passage homogène**
    $$
    T = 
    \begin{bmatrix}
        \mathcal{R} & P_{(\mathcal{R})}\\
        \mathcal{O}_{1 \times 3} & 1\\
    \end{bmatrix}
    $$
- Matrice carrée pour garantir son inversabilité afin qu'elle puisse faire preuve de matrice de passage.
- Du coup on ne peux plus utiliser les **composantes classiques**, il faut utiliser alors les **composantes homogènes**.

VIRCRV.GEAOutilsFondam.ComposantesHomogenes

![](/assets/images/VIRCRV.SlideOutilsFondam.24.png)


> **ATTENTION:** Pas de rotation $\Longrightarrow \quad R = \begin{bmatrix}1&0&0\\0&1&0\\0&0&1\\\end{bmatrix}$ 

#### Propriétés de $T$

- $T$ **inversible**
    $$
    T = 
    \begin{bmatrix}
        \mathcal{R} & P_{(\mathcal{R})}\\
        \mathcal{O}_{1 \times 3} & 1\\
    \end{bmatrix}
    \Longrightarrow
    T^{-1} = 
    \begin{bmatrix}
        \mathcal{R}^T & -\mathcal{R}^T \, P_{(\mathcal{R})}\\
        \mathcal{O}_{1 \times 3} & 1\\
    \end{bmatrix}
    $$
- **Composition de translations**
    VIRCRV.GEAOutilsFondam.CompositionTranslations



> Notes Cours 09/07 - End

---




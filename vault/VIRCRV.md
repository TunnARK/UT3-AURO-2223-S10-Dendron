---
id: 3nx1o8j8h3vbt6lu2fqlpq3
title: VIRCRV - Vision Industrielle
desc: ''
updated: 1662058517467
created: 1662025359124
---

# Notes de Cours

> **À Retenir:**
  - Indice Mobilité
  - Configuration
  - Situation
  - Degré de liberté

## Chap 1 - Introduction à la robotique

![](/assets/images/VIRCRV.SlideIntro.01.png)

### Bref survol de la planète robotique

![](/assets/images/VIRCRV.SlideIntro.02.png)

- _robota_ mot tchèque pour "travail forcé"

- remplacer l'opérateur de main pour les tâches pénibles, impossibles ou dangeureuses

Dates clés:
- 1947 premier manipulateur télé-opéré
- 1954 premier robot programmable (séquence de commande avec bras manipulateur sans retour sur l'environnement)
- 1961 premier bras manipulateur sur chaîne d'assemblage (i.e. General Motors)

> Différence entre automate et robot car les automates eux peuvent remonter jusqu'à l'antiquité

![](/assets/images/VIRCRV.SlideIntro.03.png)

Définition: Robot

  - sytème mécanique _articulé_ ou _doué de mouvement_ capable d'effectuer _automatiquement_ cetaines tâches

  - structures mécaniques adaptées à la tâche à réaliser 

  - le mouvement fait la spéificité du robot
    - interaction avec l'environment
    - ce n'est pas un ordinateur
  
  - on peut décomposer un robot par :
    - structure mécanique
    - capteurs
    - pc

![](/assets/images/VIRCRV.SlideIntro.04.png)

- tâches nécessitant bcp de dextérité le robot n'arrive pas à égaler les humains du coup l'industrie du futur veut se tourner vers de la robotique collaborative appelé  (i.e. RACE)

- manipulation
  - problématique résolu par le robot
  - implique un environnement connu est maitrise

![](/assets/images/VIRCRV.SlideIntro.05.png)

- navigation 
  - problématique résolu par le robot
  - implique un environnment non contrôlé non maîtrisé


![](/assets/images/VIRCRV.SlideIntro.06.png)

- robotique de service sans interaction humaine
  - thématique très récente


![](/assets/images/VIRCRV.SlideIntro.07.png)

- robotique de service avec interaction humaine

- robotique de service sans interaction humaine

![](/assets/images/VIRCRV.SlideIntro.08.png)

- 3 niveaux d'utilité
  - agir dans le monde réel
  - s'adapter à son environment
  - collaborer avec l'homme/l'environnement


- Principe: Boucle sans fin
  - Perception: voir via des capteurs embarqués/déportés (e.g. proprioceptifs/extéroceptifs)
    - **capteur proprioceptif** reseigne le robot sur lui-même
    - **capteur extéroceptif** reseigne le robot sur l'environnement
    - **embarqués** = sur le robot
    - **déportés** = sur l'environnement
    - traitement de données
  - Décision
    - déterminer le mouvement à réaliser
    - Automatique
  - Action
    - réalise le mouvement souhaité
    - IA our SED

- traitement de donné se fait dans la perception mais les frontières sont flous

### Focus sur la robotique industrielle

#### SM à chaîne simple

![](/assets/images/VIRCRV.SlideIntro.09.png)

Deux parties sur un robot:
- OT: **organe terminal** ou effecteur
  - réalise la tâche

- SM: Structure mécanique
  - positionne l'OT
  - il en existe 3
    - **Robot manipulateur à chaine simple**
      - corps et liaison
      > **Liaison**: mets en mouvement un **corps** par rapport à un autre
      - antécédent et succésseur

#### SM à chaîne arborescente

![](/assets/images/VIRCRV.SlideIntro.10.png)

#### SM à chaîne complexe

![](/assets/images/VIRCRV.SlideIntro.11.png)

- ici chaine fermée alors que les précedentes étaient ouvertes

#### Liaisons rotoïdes et prismatiques

![](/assets/images/VIRCRV.SlideIntro.12.png)

- cylindre: rotation
- prisme: translation

- robot souvent nommé selon sa séquence de liaison en P et R

#### Exemple de différentes séquences de liaisons

![](/assets/images/VIRCRV.SlideIntro.13.png)

#### Notions de Bases sur BM Fixe

![](/assets/images/VIRCRV.SlideIntro.14.png)

![](/assets/images/VIRCRV.SlideIntro.15.png)

- $C_i$: corps illustré en oval
- $L_i$: liaison illustré en cercle
- $BM$: Bras Manipulateur
- **indice de mobilité** ($M$): nombre de liaison
- **Configuration**: position de la SM
  - définit par un **vecteur de configuration** $q = \begin{pmatrix} q_1 \\ ... \\ q_n 
\end{pmatrix}
$
  - $q_i$ angle de rotation si $L_i=R$ sinon allongement si $L_i=P$
  - $q$: **coordonnée générale** lisée ou **coordonnée articulaire**

- **Position**: situation + ortientation de l'OT
- $R_0$: Repère de base qui est fixe
- $x = \begin{pmatrix} x_P \\ x_R\end{pmatrix}$ **coordonnées opérationnelles** avec $x_P$ la coord. de position et $x_R$ la coord. d'orientation

- **Degré de liberté** (DDL): 
  - peut être confondu par l'indice de mobilité
  - ici il faut le comprendre comment le degré de liberté de l'OT

![](/assets/images/VIRCRV.SlideIntro.16.png)

- DDL: Nb de mouvement permis par l'OT
  - dans une configuration donnée (**DDL Local $d$**)
  - pour toutes les configurations possibles (**DDL Global $D$**)
- Robot gauche: $(M,d,D) = (2,2,2)$
- Robot droite: $(M,d,D) = (2,1,1)$ (robot **redondant**)

![](/assets/images/VIRCRV.SlideIntro.17.png)

- Robot gauche: $(M,d,D) = (3,3,3)$
- Robot droite: $(M,d,D) = (3,2,3)$ (**config. singulière**)
- ici on regarde deux configurations différentes sur le même robot

### Problématique

![](/assets/images/VIRCRV.SlideIntro.18.png)

- L'opérateur définit la tâche dans l'espace opérationnel (en terme de situation par rapport à l'OT)

- BM se déplace avec la SM
  - donc réfléchit en terme de configuration (dans l'espace articulaire)

> Il faut donc un pont/changement de base entre l'espace opérationnel et l'espace articulaire

- On doit donc faire le lien entre $(q,\dot q, \ddot q)$ et $(x,\dot x,\ddot x)$
- On parle alors de 3 modèles:
  - $q$ --> $x$ modèle géométrique (MG)
  - $\dot q$ --> $\dot x$ modèle cinématique (MC)
  - $\ddot q$ --> $\ddot x$ modèle d'accélération (MA)
  - MGD: Modele Geo Directe quand on va de $q$ vers $x$
  - MGI: Modele Geo Inverse quand on va de $x$ vers $q$
  - Idem pour les autres modèles


![](/assets/images/VIRCRV.SlideIntro.19.png)

- ACT: Actionneur -> toute la partie automatique
- ROB: strucuture mécanique

> La robotique en général nécessite trois comptétences:
1. Déterminer/représenter la situation (e.g. le $X_{but}
2. Gérer les changements de repère
3. Gérer les changements de modèle


## Chap 2 - Outils Fondamentaux

![](/assets/images/VIRCRV.SlideOutilsFondam.01.png)

### I- Représentation de la situation de l'OT

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


#### I-1) Représentation de la position

**Problématique:** Quels paramètres utiliser pour représenter la position de $\;\mathcal{O}_{n+1}\;$ p.r.à $\;\mathcal{R}_0$* ?

- Premier choix (naturel) = Coord. Cartésiennes
  - **Coord. Opérationnelles de position :** $\quad x_P = \begin{pmatrix} x\\ y\\ z\end{pmatrix} = \overrightarrow{\mathcal{O}_0\mathcal{O}_{n+1}}_{(0)}$
  - ceci pour 90% des cas car permet de représenter n'importe quelle position
  - mais dans certains cas il est plus intéressant d'utiliser d'autres répères comme les coord. sphériques

![](/assets/images/VIRCRV.SlideOutilsFondam.04.png)

##### Cart. --> Cylindriques

VIRCRV.SlideOutilsFondam.CalcCartCyl

- Au lieu d'utiliser arc tangente qui rend un angle entre -pi/2 et pi/2 les roboticiens préfèrent utiliser arc tangent 2 noté $\quad atan2(Y,X) \in\; ]-\pi,\pi[$

- **Singularité de réprésentation** = infinité de réprésentations possibles
  - exemple (cas particulier):
    
    $X=Y=0$ implique $\rho=0$ et $\theta$ indéfini donc on a une singularité de représentation

    On ne peut pas définir la position de manière unique

![](/assets/images/VIRCRV.SlideOutilsFondam.05.png)

#### I-2) Représentation de l'orientation

![](/assets/images/VIRCRV.SlideOutilsFondam.06.png)

**Question:** Quels paramètre utiliser pour représenter l'orientation de $\;\mathcal{R}_{n}\;$ p.r.à $\;\mathcal{R}_0$*

**Objectif:** Définir $x_R$

**Rem:**
  - Il faut au moins 3 param. pour définir l'orientation
  - Plus on a de param. moins on risque d'avoir de singularité

##### I-2.1) Une première paramétrisation : Cosinus directeurs

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

##### I-2.2) Autres paramétrisations

![](/assets/images/VIRCRV.SlideOutilsFondam.07.png)

###### Overview

- **Représentation 3 angles**:
  - **Advantages**: 3 angles donc 3 paramètres du coup repr. minimales
  - **Inconvéniant** il existera des singularité de repr.

- **Représentation non minimales avec 4 param.**:
  - **Advantages**: Pas de singularité et peu de param.
  - **Inconvéniant** Pas toujours très visuel

###### Représenation à 3 angles

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

###### Représenation à 4 param.

![](/assets/images/VIRCRV.SlideOutilsFondam.14.png)

Pb complètement différent vu qu'on cherche à définir la rotation éffectuée par son **axe** et son **angle**

- Pour l'axe, on va définir une **droite** à l'aide de son **vecteur directeur unitaire** $\overrightarrow{u}$

- Pour l'angle, on utilise son **angle de rotation** $\theta$

**N.B.:**

- On donne les composantes de $\overrightarrow{u}$ dans $\mathcal{R}_0$ : $\quad {\overrightarrow{u}}_{(0)} = \begin{pmatrix} {\overrightarrow{u}_x}\\  {\overrightarrow{u}_y}\\ {\overrightarrow{u}_z}\\ \end{pmatrix}$

- Ceci donne les **coord. opérationnel d'orientation** : $\quad x_{R} = \begin{pmatrix} \theta\\{\overrightarrow{u}_x}\\  {\overrightarrow{u}_y}\\ {\overrightarrow{u}_z}\\ \end{pmatrix}$

![](/assets/images/VIRCRV.SlideOutilsFondam.15.png)

###### Les Quaternions

![](/assets/images/VIRCRV.SlideOutilsFondam.16.png)

- $\eta$ lié à l'angle de rotation $\theta$
- ${\overrightarrow{\epsilon}}_{(0)}$ lié à l'axe de rotation de $\overrightarrow{u}$

> Les Quarternions sont très utilisés car ils permettent de garder de meilleurs optimisations malgré que cette repr. soit moins visuelle.

**Exemple:**

VIRCRV.SlideOutilsFondam.ExempleQuaternions

##### I-2.3) Bilan

![](/assets/images/VIRCRV.SlideOutilsFondam.17.png)

![](/assets/images/VIRCRV.SlideOutilsFondam.18.png)

![](/assets/images/VIRCRV.SlideOutilsFondam.19.png)

---
id: d595je6hknlukejasdtry1g
title: '2022-09-01'
desc: ''
updated: 1662059303585
created: 1662032369198
traitIds:
  - journalNote
published: false
---

# COOSATR 13H30/15H30

## Exemple Forges

Forges = type de logiciel de gestion de version et de projet.

Ici on va utiliser GitHub.

### Créer un projet GitHub

- Créer un compte github.com
- Configurer une clé crypto pour communiquer avec GitHub depuis le terminal
- Create "New Repository"
- Choisir l'owner
  - peut etre une personne (compte perso)
  - mais peut aussi etre une organisation (compte pro)
- Choisir un nom pour le projet
  - éviter les noms communs car il sera plus difficile à trouver
  - ne mettre que des minuscule pour ne pas compliquer le site URL
- Rajouter une description
- Choisir si le projet sera privée ou public
- Rajouter un README
- Ignorer le gitignore pour maintenant
- Pour le choix de licence, toute creation a droit a une licence toujours mieux de le faire ici on va choisir BSD 2 clause
- Lancer le projet

Le projet contiendra automatiquement un fichier license et un readme.

### Commit

- Visiter le lien https://github.com/nim65s/conception-orientee-objet

- Cliquer sur commits

- Lorsqu'on veut ajouter un fichier dans le projet on réalise un commit qui contient un titre et une description pour expliquer quest-ce qui est ajouté/modifié au projet

### Include/SRC

La structure du git sera expliqué plus tard.

### Adder

?

## Include

`#include file.hpp`

dis au compilateur d'inclure le contenu de la librairie `file.hpp`

Ce fichier commence avec un `#ifndef` pour dire au compuilateur que si cette librairie n'a pas déjà été crée alors il l'a définie sinon il ne l'inclut pas car elle a déjà était inclut précédemment.

## CMake

- Créer un fichier `CMakeList.txt`
- On choisit la version de CMake (à décider avant de créer le projet selon ses besoins)
  - `cmake_minimum_required(VERSION 3.18)`
  - ici on prend une version récente pour voir les nouvelles fonctionnalités


- Puis on déclare un projet CMake pour faire la bijection avec le projet Git
  - ```
project(
  Conception-Orientee-Objet
  VERSION 0.1.0 \\ semantic versionning
  DESCRIPTION "example project for a class"
  HOMEPAGE_URL "https://github.com/nim65s/conception-orientee-objet"
  LANGUAGES CXX
  )
  ```

- Il faut ensuite indiquer la librairie
  - choisir si la lib est static (.a ou .o sur win) ou dynamic (.so)
    - static on a tout sur le fichier exécutable
    - dynamic va seulement faire des liens entre lib et exe donc il ne faudra pas à chaque fois recréer un exe
  - ici on considère du dynamic ici donc on va rajouter `SHARED`
  - ```
  add_library(
    example-adder SHARED include/conception-orientee-objet/example-adder.hpp
                       src/example-adder.cpp
    )
  ```


- Finalement il faut indiquer au projet CMake la target 

  - ```
  target_include_directories(
    example-adder PUBLIC $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
    )
  ```

Maintenant on peut exécuter CMake avec la commande `cmake -S . -B build`
  - elle va verifier que le projet a les bonnes versions ainsi que les bons compilateurs et les bonnes dépendances
  - `-S .` informe CMake le path vers la source
  - `-B build` créer un dossier build contenant les fichier temporaire sur les versions, compilateurs et dépendances que cmake à trouver

- On lance ensuite la commande `cmake --build build`
  - ceci va créer la lib dynamic `libexample-adder.so`


## Executable

- On crée un fichier main `adder.cpp`
- ici on choisit d'utiliser `return EXIT_FAILURE;` `return EXIT_SUCCESS;` (donné de base par la lib cpp standard) au lieu de faire un `return 0;`

- `argc` paramètre
- `argv` _arg vemus_

- si maintenant on lance `./adder 8 8` le compilateur va faire des liens dynamic entre la lib et l'exécutable

- `ldd` va lancer un exécutable et vérifier ce que cette exe a besoin pour se lancer

## PUSH/PULL

- PUSH va synchroniser les modifs faite dans dossier local

- PULL va récuperer les modifs faites par le collaborateur et donc synchroniser les nouveautés sur GitHub en les installant sur mon local

- Commit correspond à unité de changment

## Test

- Ctest définie une option `BUILD_TESTING`
- On crée un main test pour y faire des `assert`

- `assert(coo::add())` on indique a assert de chercher la fct add du **namespace** coo
- un namespace est un dossier contenant les listes des fct

- En recompilant le dossier build les tests vont etre verifier (si on obtient aucune erreur alors penser un forcer un test false pour verifier que les test ont bien été réalisé)

- On parle de test unitaire car le test va assertifié une partie (une unité) du programme (ou bien fonction par fonction ou classe par classe)


## Module Python

- On ajoute au `CMakeLists.txt` un build interface pour python
  - ici on choisit de faire des bindings python avec `boost`
    - Boost est une librairie Python contenant les dernières fctionnalités pas encore intégré sur le stable
  - ici on garde boost mais plus tard on passera sur pybind11

- `Boost` c'est le projet CMake
- `boost` lui est un nom de fichier (souvent en minuscule)

- `BOOST_PYTHON_MODULE` Macro CPP souvent en maj

> Un jour CPP n'aura plus d'include ou de marco (qui viennent du C et que l'on cherche à supprimer)

- ici on a code python binaire donc exe que sur un pc avec une architecture précise



# VIRCRV - 15H45/17H45



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

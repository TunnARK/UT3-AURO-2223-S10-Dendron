---
id: uht0x4uyk77p9lqlg2uh8ja
title: '2022-09-07'
desc: ''
updated: 1662551926647
created: 1662529826478
traitIds:
  - journalNote
publishing: private
---

# OE - 07H45/09H45

## Part 2 - Optimisation sans contrainte

![](/assets/images/OE.Slide22.png)

### A) Conditions

![](/assets/images/OE.Slide23.png)

Thm: CN1 - Condition nécessaire d'optimatilité du 1er odre

$x^*$ min local ...

![](/assets/images/OE.Slide24.png)

![](/assets/images/OE.Slide25.png)

Cas particulier
matrice hessienne avec vp + et - alors ni def + ni def -

![](/assets/images/OE.Slide26.png)

![](/assets/images/OE.Slide27.png)

![](/assets/images/OE.Slide28.png)

Thm: Condition suffisante d'optimalité gloabe

La matrice $Q$ (trouvé lors du calcul de la hessienne) contient l'information.

![](/assets/images/OE.Slide29.png)

Exemple 1:

OE.

Exemple 2:

OE.

![](/assets/images/OE.Slide30.png)

Exemple 3:

OE.

> **Attention:** les algos nous donne un point critiques or ce point n'est qu'un candidat !


Exemple 4 :

OE.

> **Méthode:** VERIFIER si la hessienne est bien symmétrique !

> Toute matrice de la forme $\begin{bmatrix}a & b\\ b & 0\end{bmatrix}$ aura toujours des valeurs propres de signes opposés quelque soit les signes de $a$ et $b$ !

![](/assets/images/OE.Slide31.png)

### B) Méthodes
![](/assets/images/OE.Slide32.png)

#### Méthode de recherche linéaire
![](/assets/images/OE.Slide33.png)

Def - Direction de descente

#### Algo général
![](/assets/images/OE.Slide34.png)

> Attention: Travailler avec des erreurs relatives et non pas absolus !

#### Thm du gradient
![](/assets/images/OE.Slide35.png)

#### Méthode du gradient
![](/assets/images/OE.Slide36.png)

##### $\alpha$ bien calibré
![](/assets/images/OE.Slide37.png)

##### $\alpha$ trop grand
![](/assets/images/OE.Slide38.png)

##### $\alpha$ trop petit
![](/assets/images/OE.Slide39.png)

##### $\alpha$ variable
![](/assets/images/OE.Slide40.png)

##### $\alpha$ optimal
![](/assets/images/OE.Slide41.png)

Exemple:

OE.

- On calcule le gradient de $f$
- On détermine le pas suivant $\quad x_{k+1} = x_k - \alpha_k \nabla f(x_k)$
- On évalue alors $f$ en $x_{k+1}$
- Il faut alors trouver $\alpha$ en calculant $\quad \partial_{\alpha_k}f(x_{k+1}) = 0$

![](/assets/images/OE.Slide42.png)

##### Remarque
![](/assets/images/OE.Slide43.png)

![](/assets/images/OE.BlackBoard.RemAlphaOptimal.png)

#### Conditionnment
![](/assets/images/OE.Slide44.png)

On cherche à avoir un nombre de conditionnement égal à 1.

Or quand on inverse une matrice on obtient un det qui est proche de 0 ce qui rend la matrice mal conditionnée.

Donc on va devoir faire un préconditionnement en otpimisant par un changement de variable pour éviter d'optimiser sur $f$.

##### Exemple
![](/assets/images/OE.Slide45.png)

##### Pas sur la longueur
![](/assets/images/OE.Slide46.png)

> Première condition de Wolfe-Armijo (pas trop grand ?)

> Seconde condition de Wofle (pas trop petit ?)

En général, les boites à outils implémente ces critères.

##### Exemple
![](/assets/images/OE.Slide47.png)

#### Convergence globale
![](/assets/images/OE.Slide48.png)

> Thm de Zoutendijk: convergence globale des algos de descente et pas de wolfe

Pb du thm: il est très difficile de prouver la condition du thm pour le moment.

Les boites à outils sont des algos automatiques qui vérifient des conditions spécifiques.

#### Exemple: Méthode du Gradient
![](/assets/images/OE.Slide49.png)

OE.

![](/assets/images/OE.Slide50.png)

> Selon le point de départ on tombera sur un des points critiques, donc il faut lancer le programme sur plusieurs points.

#### Problématiques Quadratiques
![](/assets/images/OE.Slide51.png)

#### Gradient conjugué
> **Attention:** cette méthode n'est à utiliser qu'avec des fonctions quadratiques !

![](/assets/images/OE.Slide52.png)

![](/assets/images/OE.Slide53.png)

![](/assets/images/OE.Slide54.png)

![](/assets/images/OE.Slide55.png)

---


# COOSATR - 10H00/12H00

![](/assets/images/COOSATR.SlideOutils.01.png)

![](/assets/images/COOSATR.SlideOutils.02.png)

![](/assets/images/COOSATR.SlideOutils.03.png)

## VOUS
![](/assets/images/COOSATR.SlideOutils.04.png)

### Ergonomie
![](/assets/images/COOSATR.SlideOutils.05.png)

### Clavier
![](/assets/images/COOSATR.SlideOutils.06.png)

## Style
![](/assets/images/COOSATR.SlideOutils.07.png)

### Code lisible
![](/assets/images/COOSATR.SlideOutils.08.png)

### PEP8
![](/assets/images/COOSATR.SlideOutils.09.png)

### Black
![](/assets/images/COOSATR.SlideOutils.10.png)

### clang-format
![](/assets/images/COOSATR.SlideOutils.11.png)

## Analyse Statique
![](/assets/images/COOSATR.SlideOutils.12.png)

### MyPy Motivation
![](/assets/images/COOSATR.SlideOutils.13.png)

Pb print add des chaines de caracteres donc (3,4) donnera 34 au lieu de 7

### MyPy
![](/assets/images/COOSATR.SlideOutils.14.png)

### pyupgrade
![](/assets/images/COOSATR.SlideOutils.15.png)

## Méta
![](/assets/images/COOSATR.SlideOutils.16.png)

### IDE
![](/assets/images/COOSATR.SlideOutils.17.png)

### Pre-Commit
![](/assets/images/COOSATR.SlideOutils.18.png)

> Il faut faire un fichier "config" yaml

#### Utilisation
![](/assets/images/COOSATR.SlideOutils.19.png)

S'il y a un probleme de formattage le software retournera 0.

#### CI
![](/assets/images/COOSATR.SlideOutils.20.png)

> Utile pour des projets où d'autres collaborateur n'utilise pas precommit

## GitHub Project (suite)


### Commit: "CMake: minimal project"

> [lein vers le commit "CMake: minimal project"](https://github.com/nim65s/conception-orientee-objet/commit/f5de5b63f91cbd9e50193c0accfe246d49bd961a)

- semantic versioning
  - majeur
  - mineur
  - patch

- on incremente le num majeur pour indique de grosse modification comme changer le type d'une variable

- on reste en version 0 tant que le projet n'est pas stable

- certains mette l'annee au lieu de 0 dans le majeur

### Commit: "add an executable"

> [lein vers le commit "add an executable"](https://github.com/nim65s/conception-orientee-objet/commit/36d4162c43d634aae59ab36457cc9b46d9eecd44)

le code faite la somme et retourne le resultat

il verifie aussi si on lui donne 2 param avec:
```
std::cerr << "This program needs 2 integers\n";
  return EXIT_FAILURE;
```

### Commit: "add a test"

> [lein vers le commit "add a test"](https://github.com/nim65s/conception-orientee-objet/commit/b433b44d7b2ada9a538944dda4dd144b683ce928)

- le fichier CMakeLists.txt est construit de façon modulaire
  - dans le root on indique au CMakeLists.txt les sousfichiers CMakeLists.txt
      ```
      if(BUILD_TESTING)
        add_subdirectory(tests)
      endif()
      ```
  - on peut aussi avoir un CMakeLists pour src et ainsi de suite

> Lien utile: [ccpreference.com](ccpreference.com)

### Commit: "add python module"

> [lein vers le commit "add python module"](https://github.com/nim65s/conception-orientee-objet/commit/2f4cd4a786e2ce7e2e242fce5dba685e06496fd1)

- on indique a python comment compiler du cpp by linking la lib ainsi
  ```
  python_add_library(conception_orientee_objet MODULE WITH_SOABI
                     conception_orientee_objet.cpp)
target_link_libraries(conception_orientee_objet PUBLIC example-adder
                                                         Boost::python)
  ```

### Commit: "add python wrapper function"

> [lein vers le commit "add python wrapper function"](https://github.com/nim65s/conception-orientee-objet/commit/9522846c446151b9d87cf583b3b269425e4de479)

- attention 3 methodes quand on fait des import
    - fichier `adder.py`
    - lib `adder.[...].so`
    - dossier `adder/__init__.py`

- ici on a importer un dossier
  ```
  from .binary_module import add as binary_add
  ```

- cette fct va s'assurer d'adapter les params au type de la fct add pour que meme si on lui donne des params en `string` il les convertisse en `int`

- `ipython` lance un terminal python
  - on y test la fct add avec les param `3` et `"-4"` et avec le wrapper on a plus l'erreur de compatibilite de type et add retourne `-1`
  - on peut aussi demander à `ipython` de donner des indications sur la fct en remplaçant les params par `?`

- on utilise le mot `wrapper` pour indiquer qu'on encapsule des fonctionnalités supplémentaires sur la fct principal
  - c'est comme rajouter des _features_ à un système

### Commit: "add python unittests "

> [lein vers le commit "add python unittests "](https://github.com/nim65s/conception-orientee-objet/commit/41ce3e0fbdf70dad0d81e3d598d94b0996202573)

- on ajoute un fichier test pour vérifier si la fonction retourne les bons résultats

- l'execution de `test_add.py` retourne 0 si aucune erreur n'est trouver dans la liste de test et retourne 1 si un des tests de la liste n'est pas vérifié

### Commit: "let CTest run python unittests"

> [lein vers le commit "let CTest run python unittests"](https://github.com/nim65s/conception-orientee-objet/commit/e155b740f31e0d9ad48f22d3c2b2dc4b68799825)

- on rajoute un fichier qui va executer tous les tests unitaires

- du coup il faut faire attention à comment on va importer les fichiers/dossiers

- se rappeler que les imports se font sur 3 méthodes

- pour bien indiquer où chercher les fichiers/dossiers à importer on donne au compilateur un `PYTHONPATH` (une liste de paths)
  ```
  set_tests_properties(test-python PROPERTIES ENVIRONMENT
                                              PYTHONPATH=${CMAKE_BINARY_DIR})
  ```

### Commit: "add doctest examples and checks"

> [lein vers le commit "add doctest examples and checks"](https://github.com/nim65s/conception-orientee-objet/commit/998c571a2785550406ab29efa74b9fa48a2b0d9e)

- on donne un paragraphe contenant les tests à vérifier

- advantage: on peut faire d'une pierre 2 coups car on donne la documentation dans les listes tests et ainsi la doc est utile pour l'utilisateur et la machine (plus besoin d'avoir une doc que pour les utilisateurs et une liste d'appel de fcts pour les tests)

- une ligne `...` sera comprise par doctest comme ignorer un bloc de ligne sur le résultat du terminal

### Commit: "setup pre-commit"

> [lein vers le commit "setup pre-commit"](https://github.com/nim65s/conception-orientee-objet/commit/85bda769d361aaf3aa450698f8d8bb194461403d)

- il est conseillé de rajouter les outils au départ d'un projet meme si ici cela a été rajouté pour rendre le cours plus fluide

### Commit: "setup github actions"

> [lein vers le commit "setup github actions"](https://github.com/nim65s/conception-orientee-objet/commit/e54277a90fe8996c676cb38d6b6e27e511a1c20a)

- on fait le push et pre-commit.ci va s'occuper de faire les tests pre-commit pour nous avons de publier

- pour ce faire on ecrit un fichier `yaml` pour executer des GitHub Actions
  - premier job fait le build pour voir que tout fonctionne en faisant un `checkout` puis plusieurs executions:
  ```
    build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: install Ubuntu dependencies
      run: sudo apt install libboost-python-dev python-is-python3 python3-pip

    - name: install PyPI dependencies
      run: pip install -U pip && pip install -U cmake

    - name: configure the project
      run: cmake -B build -S .

    - name: build the project
      run: cmake --build build

    - uses: actions/upload-artifact@v3
      with:
        name: build
        path: build
  ```
  - intégration continue: important de run ces actions sur plusieurs OS (ici on a fait les actions pour Ubuntu seulement)
  - on rajoute une liste d'actions pour les tests
    ```
      test:
    runs-on: ubuntu-latest
    needs: "build"
    steps:
    - uses: actions/checkout@v3

    - name: install Ubuntu dependencies
      run: sudo apt install libboost-python-dev python-is-python3 python3-pip

    - name: install PyPI dependencies
      run: pip install -U pip && pip install -U cmake

    - uses: actions/download-artifact@v3
      with:
        name: build
        path: build

    - run: ls build
    - run: ls build/tests
    - run: ls build/conception_orientee_objet

    - name: test the project
      run: cmake --build build -t test
      env:
        CTEST_OUTPUT_ON_FAILURE: "ON"
    ```
  - Attention: par défaut CTEST n'indique pas d'indice sur les tests failed donc il faut lui demander en paramétrant le suivant sur ON 
  
    ```CTEST_OUTPUT_ON_FAILURE: "ON"```


### Commit: "Boost::python → pybind11 "

> [lein vers le commit "Boost::python → pybind11 "](https://github.com/nim65s/conception-orientee-objet/commit/d21be5053db17a34c6eef44faac814a9922f7fe6)

puisque la lib pythonboost n'est pas facilement installable on decide d'utiliser une autre lib pybind11 du coup on implémente tous les changements nécessaires


### Commit: "CI: upgrade python"

> [lein vers le commit "CI: upgrade python"](https://github.com/nim65s/conception-orientee-objet/commit/ffb2a8c5f7947de3cc9ff6645c060e6f5af75f72)

Un changement à ne pas oublier c'est d'adapter les actions

### Templates

il est possible d'utiliser un répertoire comme template pour créer des projets contenant déjà du contenu

  

### Extra: ET Logique
- `&`: et logique
- `and`: equivalant du `&&` en C



---




# VIRCRV - 13H30/15H30

## Chap 2

### II- Matrices de transformation

**But** Acquérir la deuxième compétence -> changement de repère

![](/assets/images/VIRCRV.SlideOutilsFondam.21.png)

Cas général: $\mathcal{R}(O,{\overrightarrow{x}},{\overrightarrow{y}},{\overrightarrow{z}})_{fixe} \longrightarrow \mathcal{R}'(O,{\overrightarrow{x}},{\overrightarrow{y}},{\overrightarrow{z}})_{mobile}$

2 cas:
  - $\mathcal{R}'$ effectue seulement une rotation p.r.à $\mathcal{R}$
  - $\mathcal{R}'$ effectue une translation et une rotation p.r.à $\mathcal{R}$

#### II-1) Rotation seule

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

#### II-2) Rotation + Translation

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

##### Propriétés de $T$

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


# TD1

![](/assets/images/VIRCRV.TD1.Slide.01.png)

## Partie I: Outils Mathématiques


### I.1) Les trois rotations

![](/assets/images/VIRCRV.TD1.Slide.02.png)

- Vue 2D:
    - Cercle avec point $\Longrightarrow$ vecteur pointe vers le lecteur
    - Cercel avec croix $\Longrightarrow$ vecteur s'en va du lecteur

![](/assets/images/VIRCRV.TD1.Slide.03.png)

![](/assets/images/VIRCRV.TD1.Slide.04.png)


#### Question 1.1:

![](/assets/images/VIRCRV.TD1.Question1.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    1 & 0 & 0\\
    0 & cos\theta & -sin\theta\\
    0 & sin\theta & cos\theta
\end{bmatrix}
$$


#### Question 1.2:

![](/assets/images/VIRCRV.TD1.Question2.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    cos\theta & 0 & sin\theta\\
    0 & 1 & 0\\
    -sin\theta & 0 & cos\theta
\end{bmatrix}
$$

#### Question 1.3:

![](/assets/images/VIRCRV.TD1.Question3.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    cos\theta & -sin\theta & 0\\
    sin\theta & cos\theta & 0\\
    0 & 0 & 1
\end{bmatrix}
$$

#### Question 1.4:

![](/assets/images/VIRCRV.TD1.Question4.png)

Réponse:
- 1er matrice est une rotation autour de $\overrightarrow{y}$ avec un angle de $\theta=\dfrac{\pi}{3}$
    $$
    R_{01} =
    \begin{bmatrix}
        0.5 & 0 & 0.87\\
        0 & 1 & 0\\
        -0.87 & 0 & 0.5
    \end{bmatrix}
    $$
- 2ème matrice est une rotation autour de $\overrightarrow{z}$ avec un angle de $\theta=\dfrac{\pi}{2}$
    $$
    R_{01} =
    \begin{bmatrix}
        0 & -1 & 0\\
        1 & 0 & 0\\
        0 & 0 & 1
    \end{bmatrix}
    $$
- 3ème matrice est une rotation autour de $\overrightarrow{x}$ avec un angle de $\theta=\dfrac{3\pi}{2}$
    $$
    R_{01} =
    \begin{bmatrix}
        1 & 0 & 0\\
        0 & 0 & 1\\
        0 & -1 & 0
    \end{bmatrix}
    $$

### I.2) Composition des rotations et changements de base


#### Question 2.1:

![](/assets/images/VIRCRV.TD1.Question21.png)

**Réponse:**

**a)**

VIRCRV.TD1.Question21a.NotesGEA

**b)**
$$
R_{01} =
\begin{bmatrix}
    0 & 0 & -1\\
    0 & 1 & 0\\
    1 & 0 & 0
\end{bmatrix}
$$

$$
R_{12} =
\begin{bmatrix}
    1 & 0 & 0\\
    0 & 0 & -1\\
    0 & 1 & 0
\end{bmatrix}
$$

**c)**

$$
R_{02} = R_{01} \times R_{12} =
\begin{bmatrix}
    0 & -1 & 0\\
    0 & 0 & -1\\
    1 & 0 & 0
\end{bmatrix}
$$

> **Attention:** $R_{02}$ n'a pas d'identification possible avec une des 3 matrices de rotation classiques !

**d)**

$$
\overrightarrow{v}_{(0)} = 
\begin{pmatrix}
    0 \\
    1 \\
    2
\end{pmatrix}
\Longrightarrow
\overrightarrow{v}_{(0)} = R_{01} \;\overrightarrow{v}_{(1)}

$$
...


![](/assets/images/VIRCRV.TD1.Slide.05.png)


# CR FG - 15H45/17H45

###### Notion d'ordre/zéros/pôles pour une fonction de transfert

Considérons une fonction de transfert $F(s)\in \mathbb{R}^{p\times m}$.

Soit $\psi(s) = ppcm(den(F_{ij}(s)))$.

Ainsi, $F(s) = \dfrac{N(s)}{\psi(s)}$ où $N(s)$ est une matrice polynomiale en $s$.

CR.FG.Cours0907.ExemplePPCM

Def: Forme de Smith

Il existe $\overline{u}$ et $\overline{v}$ deux matrices unimodulaires (c.à.d. matrices polynomiales carrées ayant inverse polynomiale sans det=0) telles que 

$$
\overline{u}(s) N(s) \overline{v}(s) = diag(\alpha_1(s),...,\alpha_r(s),0 \dots 0)
$$

où $r=rang(N(s))$ et $\alpha_i$ sont des polynomes invariants tels que

$$
\alpha_i(s) = \dfrac{\Delta_i(s)}{\Delta_{i-1}(s)}
$$

avec $\Delta_0(s)=1$ et $\Delta_i(s)=pgcd\Big(\text{mineurs de la sous matrice de taille } i\times i \text{ de }N(s)\Big)$

> Mineur = determinant sous-matrice

> Def (matricielle) du **rang**: la taille du mineur le plus grand ayant un determinant non identiquement nul

Def: Forme de Smith-MacMiller

$$
F_{SM}(s) = \overline{u}(s)\;F(s)\;\overline{v}(s) = \dfrac{1}{\psi(s)} \; \overline{u}(s)\;N(s)\;\overline{v}(s)
$$

Les modes du système sont les racines de $\psi_i(s)$.

Les zéros de transmission sont les racines de $\epsilon_i(s)$.

Le polynome caractéristique s'écrit $\psi_1(s) \dots \psi_r(s)$.

**Rappel:**

- Les zéros servent à bloquer les pertubations et en mutlivariable on a plus de zéros

- Il existe trois classes de zéros ceux d'entrées/sorties/transmissions.

- Ceux d'entrées et de sorties bloquent tous modes en approchent.

- Ceux de transmissions bloquent des fréquences spécifiques entre les transferts entre une entrée et une sortie.

- Les zéros invariants sont une sous classes des zéros de transmissions.

**Exemple:** (type examen) (conseils tj commencer par calculer le nombre d'entrée et de sorties)

CR.FG.Cours0907.ExempleFormeSmithMacMillerRang

1. Calculer le ppcm 
2. Calculer le rang

    > Attention: on cherche si le polynome est toujours nul ! On ne recherche pas ici le rang peut ê au moins 1
    les racines.

    > Le polynome identiquement nul doit avoir tous ces coefficients nuls.

    > Le rang d'une matrice non carrée ne peut pas ê plus grand que le min de sa taille.

3. Calculer les delta

    > Ne jamais déveloper $N(s)$

    CR.FG.Cours0907.ExempleFormeSmithMacMillerDelta

4. Calculer $F_{SM}(s)$

    $$
    F_{SM}(s) =
    \begin{bmatrix}
    \dfrac{1}{s(s+1)(s+2)} & 0\\
    0 & \dfrac{1}{s(s+2)}\\
    0 & 0
    \end{bmatrix}
    $$

5. Calculer son polynome caractéristique

    $P=s^2(s+2)^2(s+1)$

6. Calculer les poles et les zéros

    pôles $= \{0,0,-2,-2,-1\}$

    zéros $= \empty$


**Rem:**
- Sur cette exemple, on pourrait penser que l'espace d'état nécessite 6 états (mais on a que 2 états sont ni comble ni obsble) or la forme de smith nous permet de savoir qu'il existe un espace d'état à seulement 4 états tous comble et obsble.
- Cependant il est très difficile de trouver ces états.
- C'est plus facile de trouver des etats comble mais non obsble de meme que des etats non comble mais obsble. Avoir les deux est bcp plus durs.
- Pb le système est influence par u et v or ce n'est pas autorise en espace d'etat vu qu'il ne sont pas constant or nous ne connaissons pas leurs derivees (donc leur comportements) ?


### II- Réalisation sous forme d'E.E.

**Exemple 1** 

$$
G(s) = \dfrac{1}{(s+1)(s+2)}
$$

1. Faire la décomposition en élément simple

2. Exprimer $y(s)=G(s)\;u(s)$

3. Faire un changement de variable

4. Écrire le système E.E.

CR.FG.Cours0907.ExempleRealisation

#### II-1) La forme modale (forme de Guilbert)

> On est sûr d'avoir comble et obsble avec cette forme.

On considère $F(s)$ et $\psi(s) = ppcm(den(F_{ij}(s)))$.

**Hyp:** $\psi(s)$ admet des **racines simples** $\quad \psi(s) = \prod_{i=1}^{n}(s-p_i)$ 

Donc $F(s) = \dfrac{1}{\psi(s)}\;N(s) = \dfrac{N(s)}{\;\prod_{i=1}^{n}(s-p_i)\;}$

La décomposition en éléments simples 
$$
F(s) = \sum_{i=1}^{n}\dfrac{N_i}{\;s-p_i\;}
$$
où $N_i = lim_{s\rightarrow p_i} (s+p_i)\;F(s)$

**Exemple 2:**

CR.FG.Cours0907.ExempleFormeModale

1. Calculer le ppcm

2. Factoriser avec le ppcm

3. Faire la décomposition en elmts simples de chaque composant de la matrice

4. Décomposer en cherchant la quantité

Donc

$$
y(s)
= \sum_{i=1}^{n}\dfrac{N_i}{\;s-p_i\;}\;u(s)
= \sum_{i=1}^{n}X_i(s)
$$

avec $N_i(s)\in\mathbb{R}^{p\times m}$ et **ATTENTION** $X_i(s)\in\mathbb{R}^p$

Du coup,

$$
\dot X_i(t) = p_i\;X_i(t) + N_i\;u(t)
$$

$$
...
$$

> ATTENTION: On vient d'utiliser trop d'états car les N_i ne sont pas forcément de rang plein !
---
id: 5vk3d7xzn1sjrtqtr1zf29e
title: Exemple - Repo GitHub
desc: ''
updated: 1662934744349
created: 1662934112118
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par G. Saurel

Support de cours:
- [COOSTART.NotesGEA.20220901.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/COOSTART.NotesGEA.20220901.pdf)
- [Lien vers le Repo GitHub](https://github.com/nim65s/conception-orientee-objet)

---

> Notes du 2022/09/01 - Start

## GitHub

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

## Adder

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



> Notes du 2022/09/01 - End

---

> Notes du 2022/09/07 - Start




## Commit: "CMake: minimal project"

> [lein vers le commit "CMake: minimal project"](https://github.com/nim65s/conception-orientee-objet/commit/f5de5b63f91cbd9e50193c0accfe246d49bd961a)

- semantic versioning
  - majeur
  - mineur
  - patch

- on incremente le num majeur pour indique de grosse modification comme changer le type d'une variable

- on reste en version 0 tant que le projet n'est pas stable

- certains mette l'annee au lieu de 0 dans le majeur

## Commit: "add an executable"

> [lein vers le commit "add an executable"](https://github.com/nim65s/conception-orientee-objet/commit/36d4162c43d634aae59ab36457cc9b46d9eecd44)

le code faite la somme et retourne le resultat

il verifie aussi si on lui donne 2 param avec:
```
std::cerr << "This program needs 2 integers\n";
  return EXIT_FAILURE;
```

## Commit: "add a test"

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

## Commit: "add python module"

> [lein vers le commit "add python module"](https://github.com/nim65s/conception-orientee-objet/commit/2f4cd4a786e2ce7e2e242fce5dba685e06496fd1)

- on indique a python comment compiler du cpp by linking la lib ainsi
  ```
  python_add_library(conception_orientee_objet MODULE WITH_SOABI
                     conception_orientee_objet.cpp)
target_link_libraries(conception_orientee_objet PUBLIC example-adder
                                                         Boost::python)
  ```

## Commit: "add python wrapper function"

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

## Commit: "add python unittests "

> [lein vers le commit "add python unittests "](https://github.com/nim65s/conception-orientee-objet/commit/41ce3e0fbdf70dad0d81e3d598d94b0996202573)

- on ajoute un fichier test pour vérifier si la fonction retourne les bons résultats

- l'execution de `test_add.py` retourne 0 si aucune erreur n'est trouver dans la liste de test et retourne 1 si un des tests de la liste n'est pas vérifié

## Commit: "let CTest run python unittests"

> [lein vers le commit "let CTest run python unittests"](https://github.com/nim65s/conception-orientee-objet/commit/e155b740f31e0d9ad48f22d3c2b2dc4b68799825)

- on rajoute un fichier qui va executer tous les tests unitaires

- du coup il faut faire attention à comment on va importer les fichiers/dossiers

- se rappeler que les imports se font sur 3 méthodes

- pour bien indiquer où chercher les fichiers/dossiers à importer on donne au compilateur un `PYTHONPATH` (une liste de paths)
  ```
  set_tests_properties(test-python PROPERTIES ENVIRONMENT
                                              PYTHONPATH=${CMAKE_BINARY_DIR})
  ```

## Commit: "add doctest examples and checks"

> [lein vers le commit "add doctest examples and checks"](https://github.com/nim65s/conception-orientee-objet/commit/998c571a2785550406ab29efa74b9fa48a2b0d9e)

- on donne un paragraphe contenant les tests à vérifier

- advantage: on peut faire d'une pierre 2 coups car on donne la documentation dans les listes tests et ainsi la doc est utile pour l'utilisateur et la machine (plus besoin d'avoir une doc que pour les utilisateurs et une liste d'appel de fcts pour les tests)

- une ligne `...` sera comprise par doctest comme ignorer un bloc de ligne sur le résultat du terminal

## Commit: "setup pre-commit"

> [lein vers le commit "setup pre-commit"](https://github.com/nim65s/conception-orientee-objet/commit/85bda769d361aaf3aa450698f8d8bb194461403d)

- il est conseillé de rajouter les outils au départ d'un projet meme si ici cela a été rajouté pour rendre le cours plus fluide

## Commit: "setup github actions"

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


## Commit: "Boost::python → pybind11 "

> [lein vers le commit "Boost::python → pybind11 "](https://github.com/nim65s/conception-orientee-objet/commit/d21be5053db17a34c6eef44faac814a9922f7fe6)

puisque la lib pythonboost n'est pas facilement installable on decide d'utiliser une autre lib pybind11 du coup on implémente tous les changements nécessaires


## Commit: "CI: upgrade python"

> [lein vers le commit "CI: upgrade python"](https://github.com/nim65s/conception-orientee-objet/commit/ffb2a8c5f7947de3cc9ff6645c060e6f5af75f72)

Un changement à ne pas oublier c'est d'adapter les actions

## Templates

il est possible d'utiliser un répertoire comme template pour créer des projets contenant déjà du contenu

  

## Extra: ET Logique
- `&`: et logique
- `and`: equivalant du `&&` en C



> Notes du 2022/09/07 - End

---



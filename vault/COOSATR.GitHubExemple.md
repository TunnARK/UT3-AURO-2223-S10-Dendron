---
id: 5vk3d7xzn1sjrtqtr1zf29e
title: Exemple - Repo GitHub
desc: ''
updated: 1663146784942
created: 1662934112118
---

> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par G. Saurel

Support de cours:
- [COOSTART.NotesGEA.20220901.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/COOSTART.NotesGEA.20220901.pdf)
- [Lien vers le Repo GitHub](https://github.com/nim65s/conception-orientee-objet)

---

> Notes du 2022/09/01 - Start

# Introduction

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

???

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

# Explication Commits

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

> [lien vers le commit "CMake: minimal project"](https://github.com/nim65s/conception-orientee-objet/commit/f5de5b63f91cbd9e50193c0accfe246d49bd961a)

- semantic versioning
  - majeur
  - mineur
  - patch

- on incremente le num majeur pour indique de grosse modification comme changer le type d'une variable

- on reste en version 0 tant que le projet n'est pas stable

- certains mette l'annee au lieu de 0 dans le majeur

## Commit: "add an executable"

> [lien vers le commit "add an executable"](https://github.com/nim65s/conception-orientee-objet/commit/36d4162c43d634aae59ab36457cc9b46d9eecd44)

le code faite la somme et retourne le resultat

il verifie aussi si on lui donne 2 param avec:
```
std::cerr << "This program needs 2 integers\n";
  return EXIT_FAILURE;
```

## Commit: "add a test"

> [lien vers le commit "add a test"](https://github.com/nim65s/conception-orientee-objet/commit/b433b44d7b2ada9a538944dda4dd144b683ce928)

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

> [lien vers le commit "add python module"](https://github.com/nim65s/conception-orientee-objet/commit/2f4cd4a786e2ce7e2e242fce5dba685e06496fd1)

- on indique a python comment compiler du cpp by linking la lib ainsi
```
python_add_library(conception_orientee_objet MODULE WITH_SOABI
                    conception_orientee_objet.cpp)
target_link_libraries(conception_orientee_objet PUBLIC example-adder
                                                        Boost::python)
```

## Commit: "add python wrapper function"

> [lien vers le commit "add python wrapper function"](https://github.com/nim65s/conception-orientee-objet/commit/9522846c446151b9d87cf583b3b269425e4de479)

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

> [lien vers le commit "add python unittests "](https://github.com/nim65s/conception-orientee-objet/commit/41ce3e0fbdf70dad0d81e3d598d94b0996202573)

- on ajoute un fichier test pour vérifier si la fonction retourne les bons résultats

- l'execution de `test_add.py` retourne 0 si aucune erreur n'est trouver dans la liste de test et retourne 1 si un des tests de la liste n'est pas vérifié

## Commit: "let CTest run python unittests"

> [lien vers le commit "let CTest run python unittests"](https://github.com/nim65s/conception-orientee-objet/commit/e155b740f31e0d9ad48f22d3c2b2dc4b68799825)

- on rajoute un fichier qui va executer tous les tests unitaires

- du coup il faut faire attention à comment on va importer les fichiers/dossiers

- se rappeler que les imports se font sur 3 méthodes

- pour bien indiquer où chercher les fichiers/dossiers à importer on donne au compilateur un `PYTHONPATH` (une liste de paths)
  ```
  set_tests_properties(test-python PROPERTIES ENVIRONMENT
                                              PYTHONPATH=${CMAKE_BINARY_DIR})
  ```

## Commit: "add doctest examples and checks"

> [lien vers le commit "add doctest examples and checks"](https://github.com/nim65s/conception-orientee-objet/commit/998c571a2785550406ab29efa74b9fa48a2b0d9e)

- on donne un paragraphe contenant les tests à vérifier

- advantage: on peut faire d'une pierre 2 coups car on donne la documentation dans les listes tests et ainsi la doc est utile pour l'utilisateur et la machine (plus besoin d'avoir une doc que pour les utilisateurs et une liste d'appel de fcts pour les tests)

- une ligne `...` sera comprise par doctest comme ignorer un bloc de ligne sur le résultat du terminal

## Commit: "setup pre-commit"

> [lien vers le commit "setup pre-commit"](https://github.com/nim65s/conception-orientee-objet/commit/85bda769d361aaf3aa450698f8d8bb194461403d)

- il est conseillé de rajouter les outils au départ d'un projet meme si ici cela a été rajouté pour rendre le cours plus fluide

## Commit: "setup github actions"

> [lien vers le commit "setup github actions"](https://github.com/nim65s/conception-orientee-objet/commit/e54277a90fe8996c676cb38d6b6e27e511a1c20a)

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

> [lien vers le commit "Boost::python → pybind11 "](https://github.com/nim65s/conception-orientee-objet/commit/d21be5053db17a34c6eef44faac814a9922f7fe6)

puisque la lib pythonboost n'est pas facilement installable on decide d'utiliser une autre lib pybind11 du coup on implémente tous les changements nécessaires


## Commit: "CI: upgrade python"

> [lien vers le commit "CI: upgrade python"](https://github.com/nim65s/conception-orientee-objet/commit/ffb2a8c5f7947de3cc9ff6645c060e6f5af75f72)

Un changement à ne pas oublier c'est d'adapter les actions

## Templates

il est possible d'utiliser un répertoire comme template pour créer des projets contenant déjà du contenu

  

## Extra: ET Logique
- `&`: et logique
- `and`: equivalant du `&&` en C



> Notes du 2022/09/07 - End

---

> Notes du 2022/09/14 - Start




# Deployement

## Structure et Gestion des dossiers

### Contexte

COOSATR.GitHubExemple.PicTree

### Bonne pratique

Attention:
- éviter de tous mettre dans le root `\`
- git est hierarchique du coup on va plutot utiliser des préfixes `$PREFIX`
- 3 prefix par défaut: `\` `\usr\` ou `\usr\local\`
- pb par securite pas tout le monde ne peut ecrire directe dans ces prefix => on prefere travailler sur `\tmp\` un dossier temporaire git n'est present que sur la RAM et s'efface quand on eteint l'ordi

par convention on prefere mettre les binaires dans un dossier `\bin\` et les librairies dans un dossier `\lib\`

### How to

`export PATH=/tmp/install/bin:$PATH` rajoute le path `/tmp/install/bin` dans la liste de tous les path (ici en debut de liste)

## Utiliser CMake pour lancer le deployment

### Commit: " install targets & files "

> [lien vers le commit " install targets & files "](https://github.com/nim65s/conception-orientee-objet/commit/7e670ce3b115695668dcd23cb15cd575a654f569)

```CMake
install(TARGETS example-adder adder)
install(FILES include/conception-orientee-objet/example-adder.hpp
        DESTINATION include/conception-orientee-objet)
```

- lancer `cmake --install build` retournera une erreur car il va vouloir installer le build dans `/usr/local/` or ce dossier necessite les droits admin pour y modifier le contenu
- pour eviter de casser son ordi on va faire l'install dans `/tmp/` comme preciser ci-dessus
- du coup on lance la commande `cmake -B buil -S. -DCMAKE_INSTALL_PREFIX=${{ github.workspace }}/install`


## Packaging

- mettre un dossier dans un zip ou tar pour partager ce dossier à d'autres coequipier
- on peut par exemple creer ainsi des packet binaire `deb`

## CMake Export

> Comment permettre à d'autres d'utiliser mon projet

C'est la pierre angulaire de cmake car il automatise la routine de gestion des depandonces

### Commit: "install exports "

> [lien vers le commit "install exports "](https://github.com/nim65s/conception-orientee-objet/commit/3f5152ec477b11e6984c05cfd147d696b29bdfa4)

- Dans cmakelist principal on rajoute ces lignes pour indiquer où chercher mes header
  ```CMake
  example-adder PUBLIC $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
                        $<INSTALL_INTERFACE:include>)
  ```
- puis on rajoute les bons exports aux autres fichiers

- install ce fait sur un des 9 dossiers conventionnels de cmake (le plus connu etant `/lib/cmake/`)
  ```CMake
  install(
    EXPORT Conception-Orientee-ObjetTargets
    NAMESPACE Conception-Orientee-Objet::
    DESTINATION lib/cmake/Conception-Orientee-Objet)

  include(CMakePackageConfigHelpers)
  configure_package_config_file(
    Config.cmake.in Conception-Orientee-ObjetConfig.cmake
    INSTALL_DESTINATION lib/cmake/Conception-Orientee-Objet)
  write_basic_package_version_file(Conception-Orientee-ObjetConfigVersion.cmake
                                  COMPATIBILITY AnyNewerVersion)

  install(FILES "${CMAKE_BINARY_DIR}/Conception-Orientee-ObjetConfig.cmake"
                "${CMAKE_BINARY_DIR}/Conception-Orientee-ObjetConfigVersion.cmake"
          DESTINATION lib/cmake/Conception-Orientee-Objet)
  ```

- `...target-release.cmake` compile en essayant d'optimiser le code (par defaut set at -03)
  - optimisation -01 bof -02 bien
  -03 et plus commence optimiser au point de ne plus rendre des resultats si exact

### Commit: "CMake: set PROJECT_NAME"

> [lien vers le commit "CMake: set PROJECT_NAME"](https://github.com/nim65s/conception-orientee-objet/commit/0426aa11ad7823d5adcb44c0a67fd2fcf1189e4f)

Dans ce commit on a simplifier les noms de variable pour eviter de s'y perdre avec le "-" et "_" ou les majuscules et minuscule en utilisant la syntax `${...}` pour remplacer une chaine de `char` comme sur `bash`.

### Commit: "test packaging "

> [lien vers le commit "test packaging "](https://github.com/nim65s/conception-orientee-objet/commit/78256ef172ce96a23a0a4849a465b1fa8ac76c6e)

- on rajoute un code pour faire les multiplications et on test le code
- donc on va vouloir faire un build dans ce dossier multiplier
- mais la commande cmake ne fonctionnera pas car il ne trouvera pas les fichiers .cmake
- du coup on va rajouter le path vers les .cmake dans la variable `CMAKE_PREFIX_PATH`
  - similaire a `sys.path` de chez python ou encore `PTYHON_PATH`
  - pour cela on fait `export CMAKE_PREFIX_PATH = /tmp/install`
- on relance le build puis compiler et lancer les tests




### Commit: "ci: test packaging "

> [lien vers le commit "ci: test packaging "](https://github.com/nim65s/conception-orientee-objet/commit/7f63ead9eaf19036e4320d25618ef312a9fe6046)

l'idée est d'automatiser les tests
  
On rajoute le job `packaging`:
```YML
  packaging:
    runs-on: ubuntu-latest
    needs: "build"
    steps:
    - uses: actions/checkout@v3
    - uses: actions/download-artifact@v3
      with:
        name: build
        path: build

    - name: install the project
      run: cmake --install build

    - name: test packaging
      run: cmake -B test-packaging -S tests/multiply
      env:
        CMAKE_PREFIX_PATH: "${{ github.workspace }}/install"

    - name: build subproject
      run: cmake --build test-packaging
```

Ceci va creer une action

> un fichier ML est un standard avec langage markup qui organise des donnees variables


### Commit: "set RPATH"

> [lien vers le commit "set RPATH"](https://github.com/nim65s/conception-orientee-objet/commit/e0d1188d0c249845ed94f065a29a007617886a86)

Lorsqu'une erreur est cause parce que l'interpreteur ne trouve pas la lib alros mettre à jour la variable `LD_LIBRARY_PATH = /tmp/install/lib`.

Ces noms de variables sont important pour que des users puissent lancer le projet et adapter ces variables a leur context.

Mais apres avoir bcp de projet sur l'ordi on peut commencer a s'y perdre on va chercher a optimiser ces noms de variables avec `RPATH`

Pour cela on rajoute dans le cmakelist principal cette ligne
```
set_target_properties(adder PROPERTIES INSTALL_RPATH "$ORIGIN/../lib")
```
où `$Origin`

`/tmp/install/bin/../lib/` == `/tmp/install/lib/` 

## Commande pour modifier le PATH

- `exprt $PATH=Path1:Path2:${PATH}` où par exemple PATH etait egal avant l'expor à `Path3:Path4:Path5`
  - du coup `echo $PATH` retournera : `Path1:Path2:Path3:Path4:Path5`

- `objdump -x /tmp/install/bin/adder`
  - pour explorer du code binaire
  - indique des informations utiles liée à cette executable comme la lib, l'architecture, ...

> Notes du 2022/09/14 - End

---

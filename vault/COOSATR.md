---
id: xwu3g3jpcxdipzc4fdm0kvh
title: COOSATR
desc: ''
updated: 1662056237543
created: 1662024458834
---

# Notes 2022/08/31 - Intro

![](/assets/images/COOSATR.SlideIntro.01.png)

![](/assets/images/COOSATR.SlideIntro.02.png)

![](/assets/images/COOSATR.SlideIntro.03.png)

![](/assets/images/COOSATR.SlideIntro.04.png)

## Présentation

- responsable technique
  - C++ plus optimale
  - Python très facile pour prototyper

- ne develope pas mais aide les developeurs (doctorant) à les implémenter et les diffuser s'assure de la bonne documentation

- code en amateur du rust

![](/assets/images/COOSATR.SlideIntro.05.png)

![](/assets/images/COOSATR.SlideIntro.06.png)

## Sondage

![](/assets/images/COOSATR.SlideIntro.07.png)

![](/assets/images/COOSATR.SlideIntro.08.png)

- formattage automatique (ne pas perdre de temps sur du format tabulation espace et ce concentré sur le contenu)

- test unitaire

- Intégration continue implémente des analyse statique, les test unitaires et le formattage automatiquement
  - ceci afin que le code soit constructif et transmissible au reste du groupe

## Modalités du Cours

![](/assets/images/COOSATR.SlideIntro.09.png)


- ROS: ?
  - en robotique algo de controle doit agir en temps réel

# Notes 2022/08/31 - COO 101

![](/assets/images/COOSATR.SlideCours101.01.png)

![](/assets/images/COOSATR.SlideCours101.02.png)

![](/assets/images/COOSATR.SlideCours101.03.png)

## Hello World

![](/assets/images/COOSATR.SlideCours101.04.png)

### Hello World: C++
![](/assets/images/COOSATR.SlideCours101.05.png)

```
#include <iostream>
auto main() -> int {
std::cout << "hello\n";
return 0;
}
```

- a.out:
  - fichier binaire directement compréhensible par l'ordinateur
- ```g++ hello.cpp && ./a.out```
  - ecriture shell -> langague unix
  - commande de compilation
  - puis excecute le fichier a.out

- `true && echo "Hello"` -> affiche
- `false && echo "Hello"` -> n'affiche pas



### Hello World: Python
![](/assets/images/COOSATR.SlideCours101.06.png)

```
#!/usr/bin/env python

if __name__ == "__main__":
print("hello")
```

- `#!` shybang indique à l'OS le type de fichier
  - comportement différent selon l'OS

```
chmod +x hello.py && ./hello.py
```

### Data Types

![](/assets/images/COOSATR.SlideCours101.07.png)

- compilateur choisit pour nous le type

- `auto ga{3}; // int`
  - prends 4 places dans la mémoire


- `auto bu{3.14}; // double`
  - prends 8 places dans la mémoire


- `auto to{"tau"};` devient automatiquement `const auto *const zo{"tau"}; // const char *const`
  - magnière compliquée de corriger l'input 
  - `const` empêche toute modification de la variable (sinon retourne variable en lecture seule donc pas d'affectation)


- `std::string meu{"pi"};`
  - manière plus propre/optimale pour créer un string


- **Attention**: ne pas optimiser avant d'avoir un programme lisible


- concepts similaire en Python

```
ga: int = 3
bu: float = 3.14
zo: str = "pi"
```

> Python et C++ sont des langages **fortement typés** (ecriture restrictive)


## Counter Flow

![](/assets/images/COOSATR.SlideCours101.08.png)

### Functions

![](/assets/images/COOSATR.SlideCours101.09.png)



`auto add(int first, int second) -> int {`
  - auto pour choisir le type de la fonction
  - add nom de la fct
  - deux parametres
  - retourne un int

`return first + second;`
  - réalise la somme

`}`

> L'execution est linéaire mais le compilateur lui regarde le code par unité de compilation (de façon plus globale que linéaire)

### Conditions: C++

![](/assets/images/COOSATR.SlideCours101.10.png)

### Conditions: Python

![](/assets/images/COOSATR.SlideCours101.11.png)

### Loops: While

![](/assets/images/COOSATR.SlideCours101.12.png)

#### C++

```
auto user_input{0};
while (user_input != 42) {
std::cout << "guess: ";
std::cin >> user_input;
}
```

TODO: Rajouter un indice chaud/froid à l'utilisateur

#### Python

```
user_input: int = 0
while user_input != 42:
user_input = int(input("guess: "))
```

- `int(input(...))` sur python il faut lui indiquer le type

#### Walrus

```
while (user_input := int(input("guess: "))) != 42:
print("it's not", user_input)
```

- `:=` symbol/technique _walrus_

> Contrairement au C++, Python "_impose_" une manière de coder selon que cela soit plus convenable pour la communauté donc Walrus n'est pas recommandé puisqu'il est plus difficile à lire


### Loops: Break C++

![](/assets/images/COOSATR.SlideCours101.13.png)

### Loops: Break Python

![](/assets/images/COOSATR.SlideCours101.14.png)

### Loops: for/break C++

![](/assets/images/COOSATR.SlideCours101.15.png)

> pas obliger d'avoir un break dans une boucle for

### Loops: for/break Python

![](/assets/images/COOSATR.SlideCours101.16.png)

### Loops: continue

![](/assets/images/COOSATR.SlideCours101.17.png)

> `continue` fait retourner au début de la boucle et ne s'applique que sur la boucle la plus proche

> CPU ne sait pas faire de boucle mais fait des **saut conditionnel**

### Loops: containers

![](/assets/images/COOSATR.SlideCours101.18.png)

- sur C++ peu de types primitifs le reste c'est des objets

- sur python il n'y a que des objets

- containers est un type d'objet (i.e. de type vecteur)

#### C++

`using Colors = std::vector<std::string>;`

`Colors colors{"orange", "blue", "pink"};`
  - ici on ne peut pas utiliser `auto`

`for (const auto &color: colors) {`
  - ici le compilateur propose de rajouter `&` à colors
  - on définit une variable `color` comme indice

`std::cout << color << "\n";`

`}`

#### Python

```
colors = ["orange", "blue", "pink"]
for color in colors:
print(color)
```
> plus facile qu'en C++

## Objects

![](/assets/images/COOSATR.SlideCours101.19.png)

### C++

![](/assets/images/COOSATR.SlideCours101.20.png)

```
class Robot {
  public:
    auto work() { battery -= 5; }
    \\ methode pour changer le niveau de la batterie
    auto get_battery() const -> int { return battery; }
    \\ methode pour donner la valeur de la batterie a d autre partie du code
    \\ methode avec effet de bord constant elle ne modifie pas le contenu de la classe
  protected:
    int battery{100}; \\ initialise la batterie a 100
};

auto main() -> int {
  auto robot = Robot{};
  std::cout << robot.get_battery() << "%remaining\n";
  robot.work();
  std::cout << robot.get_battery() << "%remaining\n";
  return 0;
}
```

- L'objet "correspond" à la variable et la méthode "correspond" à la fonction

- On ne peut pas faire une méthode charge avec une entete contenant `const` puisqu'on veut modifier la valeur d'un attribut de la classe mais const nous en empêche.

  exemple: `auto charge(int new_value) const -> {battery +=1:}` ce code retournera une erreur

### Python

![](/assets/images/COOSATR.SlideCours101.21.png)

```
class Robot:
  battery = 100

  def work(self):
    self.battery -= 5
  def get_battery(self) -> int:
    return self.battery

if __name__ == "__main__":
  robot = Robot()
  print(robot.get_battery(), "% remaining")
  robot.work()
  print(robot.get_battery(), "% remaining")
```

- Sur Python il n'existe pas de type `const` du coup l'utilisateur peut toujours modifier donc sur python il n'y a pas de protection des variables

- `robot = Robot()` instancie une variable robot de type Robot

### Inheritance: C++

![](/assets/images/COOSATR.SlideCours101.22.png)

```
class LeggedRobot : public Robot {
  public:
    auto walk() { battery -= 10; }
};

auto main() -> int {
  auto robot = LeggedRobot{};
  std::cout << robot.get_battery() << "% remaining\n";
  robot.work();
  robot.walk();
  std::cout << robot.get_battery() << "% remaining\n";
  return 0;
}
```

### Inheritance: Python

![](/assets/images/COOSATR.SlideCours101.23.png)

```
class LeggedRobot(Robot):
  def walk(self):
    self.battery -= 10

if __name__ == "__main__":
  robot = LeggedRobot()
  print(robot.get_battery(), "% remaining")
  robot.work()
  robot.walk()
  print(robot.get_battery(), "% remaining")
```




# Notes 2022/09/01 - Exemple Forges



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
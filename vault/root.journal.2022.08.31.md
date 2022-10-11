---
id: 58t7nh4l2dls68ut4nct9ah
title: '2022-08-31'
desc: ''
updated: 1662025978115
created: 1661933499552
traitIds:
  - journalNote
published: false
---


# COOSATR - 10H00/12H00 - Intro

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

# COOSATR - 10H00/12H00 - COO 101

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


# VICRV - 13H30/15H30

> À Retenir:
  - Indice Mobilité
  - Configuration
  - Situation
  - Degré de liberté

## Introduction à la robotique

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


# CR - 15H45/17H45

> Sur le planning: CR avec CLA indique alors Commande Linéaire Avancé

1 TP noté avec GOUAISBAUT

## Commande linéaire avancée

### Objectif

Étudier des systèmes MIMO (Multi Input Multi Output)

Décomposée en deux parties:
  - Performances et robustesses
  - Systèmes nominaux + modèles/réalisation commande

- Système **réalisable** si (considérant un input output) peut-on déterminer un système d'espace d'état

- souvent dans l'industrie les modèles sont déterminer par des physiciens et donc possède bcp de fonctions de transfert ce qui rend la command plus compliquée

### I- Modélisation des Systèmes MIMO

#### 1) Rappel sur les Systèmes MIMO

> Hyp: Les modèles considérés sont **linéaires**

Les différents types de modèle :
- fréquentiel vs temporelle 
  - classement selon la technique d'analyse voulu par après
- Entrée/Sortie
  - fonctions de transferts
  - EDOs
- Espace d'État

CR.Cours0831.DiagModeles

- EDO
  - Transformé de Laplace $\mathcal{L}$ oublie les CIs
- G(p) (fct transfert)

- EE
  - difficile d'y entrer car création de variable ce qui est appelé la **réalisation**
    - se fait à travers de la **forme modale** (Decomp. en éléments simple) ou la **forme de compagne** (approches polynomiales)
  - facile de passer de EE à G ou EDO via la transformé de laplace

#### 2) Les modèles MIMO

##### 2.1) Les modèles E/S

###### Les modèles temporels

Ils représentent des EDOs couplés entre les différentes entrées et sorites d'un système.

Considérant $m$ entrées, $p$ sorites, le modèle EDO s'écrit

CR.Cours0831.Eq1

**Rem:**
- Le système est causal donc $s \geq r$
  - **Causalité** les effets ne peuvent pas précéder les causes
  - si $s=r$ alors système directe (strict. causal)
- il y a autant d'EDO que de sorties donc p EDO pour p sorties
  - si plus d'EDO que de sorties alors on contraint trop le système qui peuvent passer de contraintes dynamiques à des contraintes algébriques (potentiellement)
  - contraintes dynamiques = equations que les variables doivent respectées qui sont propres au système ($x_1= ax_2+b$)
  - contraintes algébriques = fixer des variables ($x_1 = x_3 = 0$)

- si pas assez d'EDO que de sorties alors l'unicité des solutions n'est pas assurée


On introduit l'opérateur différentiel: $D = \dfrac{d}{dt}$
  - donc si on écrit $D^k$ on comprend la composition D avec lui meme k fois

Ceci pour concaténer le modèle précédent dans un **modèle compact**

CR.Cours0831.Eq2

On obtient un **modèle temporel E/S** :

$$
L(D) \cdot y(t) = M(D) \cdot u(t)
$$

Exemple:
CR.Cours0831.Ex1

- $M(D)$ ne fait que combiner les entrées
- $L(D)$ contient la dynamique du système
- Méthode de résolution d'une EDO
  - primo on se pose la question de l'ordre
    - ceci nous permet de connaitre le nombre de CIs nécessaire à la résolution du systeme

Rem: Comment déterminer l'ordre grâce à $L(D)$
- Si $L(D)$ est tri. inf./sup. et les degrés de D sur les colonnes sont croissant alors 


pivot de gaus forme algo de la forme Lu

Lemme:
CR.Cours0831.Lemme1

Théorème:
CR.Cours0831.Thm1

Donc on pourrait avoir des situations où le degré est diminuer par le $det$ ce qui nous permettrez d'avoir besoin de moins de CIs.

Exemple:
CR.Cours0831.Ex2

- On a besoin que d'une CI sur l'une des deux entrées

###### Les modèles fréquentiels

Les modèles fréquentiels utilisent la transformée de laplace (partant par exemple d'EDO).

Dans le cas monovariable, le modèle s'écrit: $F(s) = \dfrac{Y(s)}{\;U(s)\;}$

Dans le cas multivariable, le modèle s'écrit: $Y(s) = F(s) \cdot U(s)$ avec $Y(s) \in \mathbb{C}^p[s]$ et $U(s) \in \mathbb{C}^m[s]$ donc $F(s) \in \mathbb{C}^{p\times m}[s]$

Exemple:
$$
F(s) = \begin{bmatrix} \frac{1}{s+1}&\frac{1}{s}\\ \frac{1}{s+2}&\frac{1}{(s+1)(s+2)}\\ \end{bmatrix}
$$

Du coup, 

CR.Cours0831.

Mtnt que peut-on faire avec cette matrice F, on va chercher à :
- définir l'ordre du modèle
- définir les pôles
  - important pour analyser la stabilité
  - savoir bloquer les pertubations via les zéros
    - mais attention si on factorise $F(s)$ on risque de créer des zéros artificiels et donc on peut changer la dynamique du système
  - si mtnt on ajoute au Num et au Den un poly on se retrouve par imposer une nouvelle CI fictive qui sera ou pas observable

####### Définitions (Ordre/Zéro/Pôles) d'une FT

- si la matrice $F(s)$ est sous forme diagonale alors on peut facilement déterminer l'ordre/zero/pole
- donc on va diagonaliser les matrices
- MAIS comment diagonaliser des matrices non carrées ?!! => utiliser la forme SMITH
























PAS DE COURS DE MICHEL TAIX D'OPTIMISATION


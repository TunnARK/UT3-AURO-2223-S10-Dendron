---
id: cndd09tc515h7gb5n6ye6rt
title: BackUp
desc: ''
updated: 1665483611878
created: 1662377831805
published: false
---

# CR DP 13H30/15h30

## Bornée une incertitude

### Equation vers Figure

![](/assets/images/CR.DP.CM.BlackBoard.20220905-01.Rappel.png)

On veut créer un objet incertain qui qppqrtient dans un interval: $A(\delta) \in \mathbb{R}^{n \times n}$

On commence avec un scalaire $a \in \mathbb{R}^{1 \times 1}$$

![](/assets/images/CR.DP.CM.BlackBoard.20220905-02.IncertitudeScalaire.png)


- combinaison linéaire convexe
- convexe car $\zeta\geq0$ 


On vient d'exprimer comment visualier un scalaire incertain dans un interval


Maintenant on veut faire de même pour des matrices

![](/assets/images/CR.DP.CM.BlackBoard.20220905-03.png)

![](/assets/images/CR.DP.CM.BlackBoard.20220905-04.png)


- $0 \leq \vartheta_i \leq 1$

On représente une forme geom qui graphiquement donne

![](/assets/images/CR.DP.CM.BlackBoard.20220905-05.png)

### Figure vers Equation

Maintenant essayons de faire l'inverse et d'écrire une representation geom du triangle suivant :

![](/assets/images/CR.DP.CM.BlackBoard.20220905-06.png)

- $Co\{s_1,...,s_n\}$ : **ensemble convexe des sommets** $s_1,...,s_n$

## Identification d'espace incertain

On réalise des mesures et après un certain nombres, on étudie toutes les combinaisons linéaires convexes de ces points pour trouver la combinaison qui englobe tous les points.

Pb: très couteux en calcul (surtout pour des dims grandes)


interval dim 1

polygone dim 2

polyhedre dim 3

Polytope dim gene

![](/assets/images/CR.DP.CM.BlackBoard.20220905-07.png)

### Exemple 


Considérant le système suivant :
![](/assets/images/CR.DP.CM.BlackBoard.20220905-08

Avec :
- **coef d'amortissement :** $1/2 \leq \zeta \leq 3/2$ 
- **pulsation naturelle :** $3 \leq \omega_n \leq 7$

On obtient la figure suivante :
![](/assets/images/CR.DP.CM.BlackBoard.20220905-09.png)

Or on constate qu'il ne s'agisse pas d'un polytope convexe

Du coup on va considére des envelopes convexes de cette espace

Ceci pour analyser la stabilité de ces envelopes en espérant trouver une qui soit stable et donc conclure que le système contenu dans l'envelope est lui aussi stable

Une envelope naturelle est de prendre le grand rectangle. Il contiendra trop de points mais sa construction est simple.

![](/assets/images/CR.DP.CM.BlackBoard.20220905-10.png)


### Autres Exemples

> HOMEWORK (Still ToDo)

Construire les polytopes des systèmes suivants :
![](/assets/images/CR.DP.CM.BlackBoard.20220905-11.png)

## Condition Nécessaire: Stabilité des Sommets

![](/assets/images/CR.DP.CM.BlackBoard.20220905-12.png)

Comme ce n'est pas une condition suffisante, il nous suffit de chercher un contre-exemple.

![](/assets/images/CR.DP.CM.BlackBoard.20220905-13.png)

- Ici on considère deux sommets qui sont tous les deux stables et on montre qu'il existe une combinaison linéaire de ces deux sommets qui n'est pas stable

- En effet on a un polytope construit sur deux sommets stable n'est pas nécessairement stable.

## Thm: Stabilité Quadratique

> Formulé initialement par Barnish et Bernussou

![](/assets/images/CR.DP.CM.BlackBoard.20220905-14.ThmStabQuad

> Ceci n'est qu'une **Condition Suffisante** !

Ce thm encadre aussi les temps variants !

### Def:  Matrice Définie Positive

![](/assets/images/CR.DP.CM.BlackBoard.20220905-15.DefDefiniePositive.png)

Rappel: De cette définition on est tempté de construire une fct de Lyapunov tel que $V(x) = x^T \cdot P \cdot x$

### Preuve: Inégalité Matricielle

![](/assets/images/CR.DP.CM.BlackBoard.20220905-16.png)

![](/assets/images/CR.DP.CM.BlackBoard.20220905-17.png)

### Exemple

![](/assets/images/CR.DP.CM.BlackBoard.20220905-18.png)

![](/assets/images/CR.DP.CM.BlackBoard.20220905-19.png)

> Une **matrice est définie négative** si sa **trace est négative** et son **det est positif**

### Autre formulation du Thm

![](/assets/images/CR.DP.CM.BlackBoard.20220905-20.png)

Donc il faut vérifier la stabilité pour chaque point du polytope... donc pour une infinité de points...

Cette formulation n'est clairement pas réalisable !


## Thm: Stabilité Robuste et Retour d'état

![](/assets/images/CR.DP.CM.BlackBoard.20220905-21.png)

Astuce:
![](/assets/images/CR.DP.CM.BlackBoard.20220905-22.png)
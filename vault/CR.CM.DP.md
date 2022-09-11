---
id: 2ptw0k5edovdl8fl7c1d5ev
title: Commande Robuste 
desc: ''
updated: 1662929666427
created: 1662924852208
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par D. Peaucelle

# Support de cours

- [CR.DP.NotesGEA.20220830.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.NotesGEA.20220830.pdf)
- [CR.DP.BlackBoard.20220905.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.BlackBoard.20220905.pdf)
- [CR.DP.NotesGEA.20220905.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.NotesGEA.20220905.pdf)

---

# Notes 2022/08/30 - D.P.

![](/assets/images/CR.SchemaBlocMultiVariab.png)

- Système dynamique (processus biochimique/robot)
- entrée u est placée à droite car représente alors la forme en équation du système

![](/assets/images/CR.SchemaBlocPerturbation.png)

- système exposé à des perturbations/bruits sur l'entrée, la sortie ou la dérivée

- cest pertubations vont faire travailler le correcteur beaucoup

- robustesse c'est savoir garantir une certaine stabilité malgré des perturbations mais aussi le garantir sachant l'incertude du système

- BF toujours plus stable que la BO
  - Boucle ouverte = fermer les yeux
  - Boucle fermée = ouvrir les yeux quand on cherche une salle

## Problématique:

Comment commander un système avec de grandes incertudes de modélisation

## Exemple: Incertitudes Multi/Addi

$$
\dfrac{1}{\;s^2 + 2 \zeta \omega_n s + \omega_n^2\;}
$$

avec $\quad0,8\leq\zeta\leq1,2\quad$ et $\quad3\leq\omega_n\leq7$

![](/assets/images/CR.SchemaBlocIncertitudeMultiAddit.png)

- pour définir la notion de "proche" on utilise la **norme H infinie**

## Exemple: Système d'ordre 1

Trouver $a \in \mathbb{R}$
$$
\dot x = a \cdot x
$$

- On regarde le polynome caractéristique
$$
P_a(s) = s - a
$$

- Les racines de $P_a(s)$ sont toutes à partie réelle négative alors le système est stable si $a<0$

- Si Hyp: $\underline{a} \leq a \leq \overline{a}$ alors système robustement stable si $\overline{a}<0$

## Exemple: Système du 2ème ordre

Déterminer $A$
$$
\dot X = \begin{bmatrix} a_{11} & a_{12}\\ a_{21} & a_{22}\\ \end{bmatrix} \cdot X
$$

- On regarde le polynome caractéristique

$
P_A(s) = s^2 - Tr(A) + det(A)\\
P_A(s) = s^2 - \big(a_{11} + a_{22}\big) + \big(a_{11}a_{22} - a_{12}a_{21}\big)
$

- ici on veut du coup que les racines respectent:
  - $\lambda_1 + \lambda_2 < 0\quad$ et
  - $\lambda_1 \cdot \lambda_2 > 0$

- du coup cela revient à vérifier le critère de Root-Hurwitz

- ainsi on en déduit les formules suivantes:

![](/assets/images/CR.SystOrdre2.png)

## Exemple: Système du 3ème ordre

![](/assets/images/CR.SystOrdre3.png)

- le poly caract peut se calculer avec $\alpha$ déterminer via les mineurs de la matrice A

- à l'ordre 3 la combinatoire sur les incertitudes de tous les $a_{ij}$ devient très vite difficile

- si l'on continue quand même on peut appliquer le critère de Root-Hurwitz sur $\alpha_1$, $\alpha_2$ et $\alpha_3$, on obtient alors :

![](/assets/images/CR.SystOrdre3Root.png)

- Admettons que l'on obtiennent un poly caractéristique avec la structure suivante:

$$
s^3 + (1+\delta_1)s^2 + (1+\delta_2)s + (1+\delta_1\delta_2)
$$

- en considérant mtnt l'hypothèse:
  - $0,1\leq\delta_1\leq3$
  - $0,1\leq\delta_2\leq3$

- vérifions si ce poly possède des racinces à partir réelle négative

![](/assets/images/CR.SystOrdre3Verif.png)

- Mais attention ! ici on a que deux incertitudes sont dépendantes du coup le système avec $\delta$ nous donne des solutions sur un ensemble plus grand que notre système avec $\alpha$

![](/assets/images/CR.SystOrdre3SousEnsembles.png)

- En effet, il y a dans P2 des polynomes avec des racines à parties réelles positives

- Pour poursuivre on applique Root sur P1 (donc sur les $\delta$ en oubliant les $\alpha$)

![](/assets/images/CR.SystOrdre3DeltaRoot.png)

## Convexité d'un espace

![](/assets/images/CR.Convexite.png)

## Critère Général pour P2

![](/assets/images/CR.Xaputohob.png)

Xaputohob a considéré la structure de P2 pour un ordre n qlqc et il a cherché s'il existe un critère pour résoudre la question de stabilité

Or il y a $2^{n+1}$ combinaisons des min et max possible

Mais on connait 4 polynomes assurant une stabilité robuste

## Contre Exemple

![](/assets/images/CR.ContreExemple.png)

- Lorsque le système varie dans le temps alors il ne fait aucun sens d'appliquer la méthode du polynome caractéristique avec des racines à parties réelles négatives

- Pourquoi ?

![](/assets/images/CR.ContreExempleExplication.png)

- Solution: Utiliser Lyapunov et Espace d'état

## Exemple: Lyapunov

![](/assets/images/CR.FctLyapunov.png)


# Notes 2022/09/05 - D.P.

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


## Polytopes

- **Interval** dim 1

- **Polygone** dim 2

- **Polyhedre** dim 3

- **Polytope** dim general

![](/assets/images/CR.DP.CM.BlackBoard.20220905-07.png)

## Identification d'espace incertain

On réalise des mesures et après un certain nombres, on étudie toutes les combinaisons linéaires convexes de ces points pour trouver la combinaison qui englobe tous les points.

Pb: très couteux en calcul (surtout pour des dims grandes)

### Exemple 


Considérant le système suivant :
![](/assets/images/CR.DP.CM.BlackBoard.20220905-08.png)

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

![](/assets/images/CR.DP.CM.BlackBoard.20220905-14.ThmStabQuad.png)

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
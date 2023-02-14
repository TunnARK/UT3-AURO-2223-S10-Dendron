
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par D. Peaucelle

# Support de cours

- [CR.DP.CM.BB20220905.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.BB20220905.pdf)
- [CR.DP.CM.BB20220912.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.BB20220912.pdf)
- [CR.DP.CM.BB20220921.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.BB20220921.pdf)

$\ \\[-0.5cm]$

- [CR.DP.CM.NotesGEA.20220830.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.NotesGEA.20220830.pdf)
- [CR.DP.CM.NotesGEA.20220905.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.NotesGEA.20220905.pdf)
- [CR.DP.CM.NotesGEA.20220912.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.NotesGEA.20220912.pdf)
- [CR.DP.CM.NotesGEA.20220921.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.DP.CM.NotesGEA.20220921.pdf)

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



# Notes 2022/09/12 - D.P.

## Exemple avec Matlab

On reprend l'exepmle dernier sur matlab pour l'analyser plus rapidement

![](/assets/images/CR.DP.CM.BlackBoard.20220912-01.png)

![](/assets/images/CR.DP.CM.BlackBoard.20220912-02.png)


- $P\leq0$ = semi-positive (i.e. autorise une valeur propre egal a zero)

- $P>0$ = positive strict. peut aussi s'ecrire $P>\epsilon$


### Matlab Toolbox

- [YALMIP](https://yalmip.github.io/download)
  - aller à `SetPath` puis Select et penser à `AddWithSubfolders`
  - permet de poser nos problèmes avec une ecriture matricielle mais necessite quand meme un solver

- Solvers
  - [YALMIP allsolvers](https://yalmip.github.io/allsolvers)
  - [SDPT3](https://github.com/SQLP/SDPT3)
  - [blog SDPT3](https://blog.nus.edu.sg/mattohkc/softwares/sdpt3/)


### Code Matlab

```matlab
% Definition  des sommets
A(:,:,1)=[0 1;-49 -21];
A(:,:,2)=[0 1;-49 -3];
A(:,:,3)=[0 1;-9 -3];
A(:,:,4)=[0 1;-9 -21];

vb = 4;

% pt au hazard dans le polytope
z=rand(1,4);
z=z/sum(z); % verifier que la sum(z(i)) = 1
Az=z(1)*A(:,:,1)+z(2)*A(:,:,2)+z(3)*A(:,:,3)+z(4)*A(:,:,4);
eig(Az); % verifer si nos sommets sont stables
% Construction des LMI pour le polytope
P=sdpvar(2,2,'symmetric')
quiz=[P>=eye(2)];
for v=1:vb
  quiz=quiz+[A(:,:,v)'*P+P*A(:,:,v)<=-eye(2)]
end % retourne un tableau avec 5 contraintes une pour P et 4 pour les sommets

% Resolution
res=optimize(quiz)
% Analyse du resultat
checkset(quiz)
% Si faisable obtention du resultat
double(P)
```

### Conclusion

- le rectangle rouge ne donne pas de solution
- le sous espace jaune lui donne une solution

$$
P=
\begin{bmatrix}
51.5100 & 3.437\\
3.477 &  2.4699
\end{bmatrix}
$$

## Normes

### Norme euclidienne

$x\in\mathbb{C}^n$

$$
||x||_2^2 = \sum|x_i|^2 = x^*x = x^*\mathbb{I}x
$$

Ici, $x^* = \overline{x}^T$ le **conjugé transposé**

### Norme induite L2

$M\in\mathbb{C}^{p \times n} \quad \quad y = Mu$

$$
||M||_2^2 = sup\{\dfrac{||y||_2^2}{\;||u||_2^2\;} \;|\; ||u||_2 \neq 0\}
$$

![](/assets/images/CR.DP.CM.BlackBoard.20220912-03.png)



$M^*M$ sym donc diag sur une base orthonormale donc on peut l'ecrire $T^*DT$ avec $T^*T = \mathbb{I}$ et $D=diag(\lambda(M^*M))$ 

![](/assets/images/CR.DP.CM.BlackBoard.20220912-04.png)

Or il se trouve que la pire des amplifications est donnée par $\lambda_{max}(M^*M)$

$$
||M||_2^2 = \sigma_{max}(M)^2
$$

où $\sigma_{max}(M)$ = la **valeur singulière** max de $M$

![](/assets/images/CR.DP.CM.BlackBoard.20220912-05.png)

Il se trouve que $u=(1,1)^T$ est la valeur propre de $M$ c'est pourquoi on avait aussi trouvé $4$

### Signaux

![](/assets/images/CR.DP.CM.BlackBoard.20220912-06.png)

$X(s) = \int_0^{\infin} \; x(t)e^{-st} \; dt$

$$
||x||_2^2 =
\int_0^{\infin} \; ||x(t)||_2^2 \; dt =
\int_{-\infin}^{\infin} \; ||x(j\omega)||_2^2 \; d\omega =
||X||_2^2
$$

### Norme induite L2 d'un système NL

> Pour les systèmes linéaire, la norme induite L2 est appelée la **norme** $H_{\infin}$

$$
||H||_2^2 = sup\{ \dfrac{||y||_2^2}{\;||u||_2^2\;} \;|\; ||u||_2 \neq 0 \;\wedge\; x(0)=0 \}
$$

![](/assets/images/CR.DP.CM.BlackBoard.20220912-07.png)

> **Attention:** lorsqu'on applique le laplace il faut toujours considérer des conditions initiales nulles

![](/assets/images/CR.DP.CM.BlackBoard.20220912-08.png)

$H^*H$ = module de la FT = Gain

```matlab
H=ss;
% tracer de ses valeurs sing
sigma(H)
% 
wcgain(H)

.... !!!!

% decale de +0.001 car on veut que le produit soit strict. plus petit que 1 et pas egal a 1
% feedback de - D
```

## Thm du Petit Gain

### Condition Suffisante

Si $\; ||H||_2^2 < \sigma^2 \;$ alors la Boucle Fermée suivante est **robustement stable** quelque soit $\;\Delta \;$ tel que $\; ||\Delta||_2^2 \leq \dfrac{1}{\;\sigma^2\;} \;$

![](/assets/images/CR.DP.CM.BlackBoard.20220912-09.png)

### Condition Nécessaire

Si $\; ||H||_2^2 < \sigma^2 \;$ alors il existe $\;\Delta \;$ tel que $\; ||\Delta||_2^2 \leq \dfrac{1}{\;\sigma^2\;} \;$ tel que la Boucle Fermée est "**instable**" (en limite de stabilité)

**Attention:** Cela ne signifie pas que si pour tous $\Delta$ on a $\; ||\Delta||_2^2 \leq \dfrac{1}{\;\sigma^2\;} \;$ la boucle fermée est instable

![](/assets/images/CR.DP.CM.BlackBoard.20220912-10.png)

### Code Matlab

#### Test Worst Case

Pour taper sur la pire amplification
- on tappe sur la valeur propre concernee
- ca donne une matrice de rang 1 (car une seule valeur propre)
- boucle fermee 
  - elle est 'presque' stable
  - mais tres proche de zero

```
l32 - l38
```

#### Test Matrice de norme 1

Donne un systeme 'carrément' stable

```
l38 - l41
```

### Exemple Processus Biochimique

> Conseil: donner des indices sur les matrices selon si elles correspondent à une entrée, une sortie ou un $\Delta$

Imaginons un processus biochimique pour nettoyer les eaux usées

Celui-ci dépendrait donc de la température et serait exposée à des incertitudes

![](/assets/images/CR.DP.CM.BlackBoard.20220912-11.png)

On cherche à controler ce processus donc on y implémente un correcteur

![](/assets/images/CR.DP.CM.BlackBoard.20220912-12.png)

Pour analyser sa stabilité, on va utiliser le **thm du petit gain**

Pour cela il nous faut transformer le schema bloc en y incluant $H$

Or, on a :
$$
U = K(y+w_{\Delta})
$$
$$
U = KC_yX + Kw_{\Delta}
$$

Donc,

![](/assets/images/CR.DP.CM.BlackBoard.20220912-13.png)


**Par le thm du petit gain:**

Si $||H||_2^2<\dfrac{1}{\;\mu^2\;}$ alors le système est **robustement stable**


**Comment vérifier cette égalité ?**

- En prenant sa fonction de transfert => Pb le système est temps variant donc on n'est pas autorisé à faire cette transformation
- On ne pourrait meme pas utiliser la norme $H_{\infin}$ a la limite on pourrait appliquer la norme induite L2
- Nous allons pour cela utiliser le thm suivant :

### Thm de Stabilité Quadratique pour une norme induite L2

![](/assets/images/CR.DP.CM.BlackBoard.20220912-14.png)

#### Preuve

![](/assets/images/CR.DP.CM.BlackBoard.20220912-15.png)

![](/assets/images/CR.DP.CM.BlackBoard.20220912-16.png)





> Notes du 2022/09/12 - End

---

> Notes du 2022/09/21 - Start



<!-- # Notes 2022/09/21 - D.P. -->

**Rappel:**

$$
||M||_{\infin} = ||M||_{2} < \sigma^2\\ \Longleftrightarrow \;\text{la boucle fermée est robustement stable}\; \forall \Delta \;\text{tq}\; ||\Delta||_{2}^{2} \leq \frac{1}{\;\sigma^2\;}
$$


#### Exemple d'utilisation

![](/assets/images/CR.DP.CM.BB20220921-01.png)
![](/assets/images/CR.DP.CM.BB20220921-02.png)
![](/assets/images/CR.DP.CM.BB20220921-03.png)

### Cas Général

**Notation:**
- $D_{\Delta u}$ le transfert entre $z_{\Delta}$ et $u$
- $D_{\Delta }$ le transfert entre $z_{\Delta}$ et $u$

![](/assets/images/CR.DP.CM.BB20220921-04.png)
![](/assets/images/CR.DP.CM.BB20220921-05.png)

Le problème de savoir si $(\mathbb{I}-D_{\Delta\Delta}\Delta)$ est inversible c'est le _**"problème du bien posé"**_ (c.a.d. que si elle n'est pas inversible alors c'est un système qui possede une infinité de solutions et a priori une infinité de points d'équilibre donc il ne fait plus de sens d'étudier leurs stabilité ; on aimerait plutôt avoir un point d'équilibre unique).

![](/assets/images/CR.DP.CM.BB20220921-06.png)

**Rem:** on peut voir $\Delta(\mathbb{I}-D_{\Delta\Delta}\Delta)^{-1}$ comme une **fraction rationnelle matricielle**

Ceci nous rappelle la matrice fractionnelle en $s$ comme suit

![](/assets/images/CR.DP.CM.BB20220921-07.png)

Ici, le $\Delta$ du cas général est représenté par l'intégrateur en $s$

Autre exemple, on peut aussi représenter $\Delta$ par un correcteur $K$ comme suit

![](/assets/images/CR.DP.CM.BB20220921-08.png)


## LFT - Linear Fractional Transform

![](/assets/images/CR.DP.CM.BB20220921-09.png)

> **Une représentation d'espace d'états est une LFT !**

**Exemple:** De LFT vers la forme fractionnelle de $\Delta$

![](/assets/images/CR.DP.CM.BB20220921-10.png)
![](/assets/images/CR.DP.CM.BB20220921-11.png)
![](/assets/images/CR.DP.CM.BB20220921-12.png)

**Pb:** Construire une LFT à partir de forme fractionnelle est bcp plus dur (mais comme $\Delta\star M$ représente une algèbre du coup les ordinateurs arrivent à se débrouiller pour trouver une LFT)

### Formule pour l'addition

![](/assets/images/CR.DP.CM.BB20220921-13.png)
![](/assets/images/CR.DP.CM.BB20220921-14.png)

Du coup, par exemple pour $\left[ \delta_1 \; \delta_2 \right]$ on peut l'écrire ainsi

![](/assets/images/CR.DP.CM.BB20220921-15.png)

Pour mieux comprendre comment passer du matricielle à une structure avec le produit LFT voici un autre exemple d'égalité:

![](/assets/images/CR.DP.CM.BB20220921-16.png)

En effet, on essaie de faire apparaître la structure de la formule de la LFT comme suit pour utiliser le produit LFT

$$
TODO!!!
$$

### Formule LFT pour la soustraction

![](/assets/images/CR.DP.CM.BB20220921-17.png)

### Formule LFT pour la multiplication

![](/assets/images/CR.DP.CM.BB20220921-18.png)

### Formule LFT pour la division

![](/assets/images/CR.DP.CM.BB20220921-19.png)

### Exercice

#### Cas Fonction Transfert

On considère le système suivante :
![](/assets/images/CR.DP.CM.BB20220921-20.png)

On obtient l'équation suivante :
![](/assets/images/CR.DP.CM.BB20220921-21.png)

Donc, on en déduit que :
![](/assets/images/CR.DP.CM.BB20220921-22.png)

Ainsi, on peut construire la boucle fermée suivante :
![](/assets/images/CR.DP.CM.BB20220921-23.png)

#### Cas Matriciel

On considère le système matriciel suivant :
![](/assets/images/CR.DP.CM.BB20220921-24.png)

Pour se débarasser de $\frac{\delta}{\;1+\delta\;}$, on va multiplier à gauche $\dot x$ par une matrice comme suit :
![](/assets/images/CR.DP.CM.BB20220921-25.png)

On cherche mtnt à extraire $w_{\Delta}$ comme suit :
![](/assets/images/CR.DP.CM.BB20220921-26.png)

Ceci pour ensuite trouver $z_{\Delta}$ comme suit :
![](/assets/images/CR.DP.CM.BB20220921-27.png)

Ainsi, on obtient le système suivant :
![](/assets/images/CR.DP.CM.BB20220921-28.png)

#### Cas Equation Dynamique

Considérons le contexte suivant :
![](/assets/images/CR.DP.CM.BB20220921-29.png)

Tout d'abord, ramenons-nous à des inéquations d'incertitude tel qu'on impose $\delta_i\leq1$ :
![](/assets/images/CR.DP.CM.BB20220921-30.png)

La deuxième étape consiste à faire apparaître les $W_{\Delta}$ comme suit
![](/assets/images/CR.DP.CM.BB20220921-31.png)

On cherche à appliquer le théorème du petit gain comme suit :
![](/assets/images/CR.DP.CM.BB20220921-32.png)

Ainsi, on obtient le système suivant :
![](/assets/images/CR.DP.CM.BB20220921-33.png)

> N.B.:
- La **théorie de la valeur singulière structuré** $\mu$ c'est l'équivalent du thm du petit gain mais prenant compte la structure du $\Delta$
- Cela prend en compte la partie diagonale de delta et on adapte le critère mais on ne sait pas calculer $\mu$ de façon exacte
![](/assets/images/CR.DP.CM.BB20220921-34.png)



> Notes du 2022/09/21 - End

---
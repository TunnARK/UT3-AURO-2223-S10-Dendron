---
id: 25nynh06pdn3f7anaqg3x36
title: '2022-08-30'
desc: ''
updated: 1661868438355
created: 1661840482827
traitIds:
  - journalNote
publishing: private
---

## 08H45 - Reunion Rentrée

### Partie ISTR

...

### Partie Sec Peda

Marylyne Lopez U3 salle 112
0561558274

### Partie AURO

![](/assets/images/reunion-rentree-slide1.png)

![](/assets/images/reunion-rentree-slide2.png)

- UE OptiEsti diminué passera sur la partie projet
- UE ComRobo modifié avec un merge de l'option auto commune en ISTR 
- UE option robo proba inclure partie optiesti

![](/assets/images/reunion-rentree-slide3.png)

- TP1/2 max 14
- TP AURO A/B A avec 18 personnes min et B en commun avec ISTR/INFO
- TP/BE bouge à la MFJA à cote du B612
  
  **(attention difficile d'accès et pas de restauration!!!)**

![](/assets/images/reunion-rentree-slide4.png)


# OE - 10H00/12H00

![](/assets/images/OE.CoursSlide1.png)

- TP sur Python !!! cf. palteforme **fun mooc**
- ROS utilise C++/Python

## Partie 1 - Concepts et ouitls de base pour l'optimisation

#### Pb Général :
**Minimiser une fonction sous contrainte(s)**

- Reveint à chercher le (ou les) minimum local (global)

![](/assets/images/OE.Cours.PbGeneral.png)

#### Objectif :

![](/assets/images/OE.Cours.Objectif.png)

- seulement minimiser car maximiser revient à minimiser -f

### 1.1 Modélisation mathématique

![](/assets/images/OE.CoursSlide7.png)

#### Tableau Terminologie

![](/assets/images/OE.CoursSlide8.TableauConceptsOpti.png)

- méthode du gradient pour la 4D

### 1.2 Application

![](/assets/images/OE.CoursSlide9.ApplicationsExemple.png)

#### Exemple 1 :

Nape de laser qui nous fournit des points

Chercher à modéliser Y = A X + B

resoudre y_i -ax_i -b = 0 à minimiser en fonction de a et b (les inconnus)

$$
min \sum_{i=1}^{n} (y_i -ax_i -b)
$$

pb d'optimisation sans contraintes

#### Exemple 2 : Construction Hangar

Volume $1500 m^3$ soit LxlxH = 1500

largeur = 2 x hauteur

cout N_1 / m^2 pour le mur

cout N_2 / m^2 pour le plafond

cout N_3 / m^2 pour le sol

Du coup:

$$
min \big( N_1 (2yz+2xz) + N_2 (xy) + N_3 (xy) \big)
$$

s.c. xyz=1500 et y=2z

Pb NLSC non linéaire sous contraintes

#### Exemple 3 : Entrepot Pb de logistique

n dépots et m points de ventes

cout transport C_{ij}

stocks depots X_i

niveau demande D_j

CdC flou car on ne sait si l'objectif est de vider tous les entrepots ou de vendre un maximum ou meme minimiser les couts

ces objectifs sont necessaire pour modéliser cad pour savoir si l'on va utliser une inégalité ou égalité et quelle serait sa structure

Les variables que l'on controle ici sont Xi et x_{ij} le nombre de marchandise transportée de i à j

$c_{ij} \cdot x_{ij} + ...$ 

$$
min_{x_{ij}} \sum_{i=1}^{n} \sum_{j=1}^{m} \Big( c_{ij} \cdot x_{ij} \Big)
$$

s.c. : 
- $X_i = \sum_{j=1}^{m} x_{ij}$
  - (cad vider les depots) -> donc n contraintes d'égalités
  - ou bien $\frac{X_i}{2} \leq \sum_{j=1}^{m} x_{ij} \leq X_i$ ou autre selon le CdC

- $D_j = \sum_{i=1}^{n} x_{ij}$
  - objectif ici : satisfaire la demande

Ici Pb est de type PL linéaire se résoud même avec des systèmes très grands


Exemple 1 => Bloc 1
Exemple 2,3 => Bloc 2

### 1.3 Rappels et Compléments

![](/assets/images/OE.CoursSlide10.Rappels.png)

- Dérivation de fonction scalaire

- Dérivation de fonction vectoriel -> définit un plan tangent

- Gradient de f
  - vector correspondant à la projection du vecteur perpendiculaire au plan tangent au point $x_0$
  - se trouve être perpendiculaire à la courbe de niveau

- Matrice Hessienne (symmétrique)

- les outils d'optimisation se base souvent sur le gradient (avec ordre 1 ou 2) ou la hessienne

- Attention dans le cas de fonction NL le gradient peut ne pas suffir pour minimiser

![](/assets/images/OE.CoursSlide11.DeriveeDirectionnelle.png)

- Dérivée directionnelle :

  ...

- Direction en descente :

  direction _d_ de descente si $d^t \cdot \grad f(x)$ 

- Theorem :

  ...

- Du coup le gradient nous permet de connaitre la directin menant à une minimisation c'est pourquoi bcp d'algorithm utilise le Gradient

#### Exemple : Fonction Quadratique

![](/assets/images/OE.CoursSlide12.FctQuadratic.png)

- Définition: Fonction Quadratique

  - dans ces cas le gradient est connu ! c'est $Qx+G$ du coup 'facile' à minimiser

### 1.4 Vitesse de Convergence d'un algorithme

![](/assets/images/OE.CoursSlide13.VistesseConvergence.png)

- Pq plus pratique d'avoir une convergence quadratique ?

  - supposant l'erreur vaut $10^{-3}$ alors à la prochaine itération elle sera de $10^{-5}$ puis de $10^{-9}$
  - du coup si solution la convergence de l'erreur est plus rapide dans un algo quadratique

### 1.5 Minimum

![](/assets/images/OE.CoursSlide14.Minimum.png)

- en NL les algo ne fonctionnent qu'en local (pas de global à moins d'avoir une chance) [sauf pour les focntions quadratiques ou linéaires]

- si min global nécessaire alors il faut appliquer l'algo sur plusieurs points initiaux

  - pb sur des milliers de min locaux il faut encore plus de point initiaux
    - d'où l'utilisation d'algo génétique
    - ou méthode montécalor (rajoute de l'aléatoire donc accpete que la fonction croisse pour esperer qu'elle descende plus loin)

![](/assets/images/OE.CoursSlide15.ExistenceMin.png)

- focntion coercive si sa limite tend vers l'infinie

### 1.6 Convexité

![](/assets/images/OE.CoursSlide16.Convexite.png)

- fonction convexe 
  - => tout min local est global et unique
  - si matrice hessienne est définie (semi-définie) positive pour tout x alors f est strict. convexe (convexe)

### 1.7 Optimisation d'une fonction d'une variable réelle

![](/assets/images/OE.CoursSlide17.MethodeDichotomie.png)

- f fonction unimodale si :
  - f admet un min unique $x*$ dans $I$
  - f strict. décroissante sur $[a,x*[$ et strict croissante sur $[x*,b[$

- unimodale = fct convexe en dimension 1 (seule la contrainte du strict. s'ajoute à la déf d'une fct convexe)

- méthode dichotomie

![](/assets/images/OE.CoursSlide18.MethodeSectionDoree.png)

- plus éfficace que la méthode de dichotomie car utilise le nombre d'or pour la division dichotomique

![](/assets/images/OE.CoursSlide19.MethodeRecherche.png)

- méthode numérique itérative

### 1.8 Méthode de résolution

![](/assets/images/OE.CoursSlide20.MethodeResolution.png)

- méhtode de _line search_

  - choisir une direction
  - détermine de combien y aller

- méthode de confiance _trust region_

  - approxime autour d'un voisinage

    -> donne la région de confiance

  - puis on cherche la direction de descente dans cette région

- principalement on utilisera la _line search_

![](/assets/images/OE.CoursSlide21.PbHypothenuse.png)

100m de plage

50m de nage

vitesse course 18km/h = 5m/s

vitesse nage 10km/h = (1/0,36)m/s

bombe explose dans 35sec

distance plage courue d_P
distance nage

$$
d_N = \sqrt{(100-d_P)^2+50^2}
$$

minimiser
$$
d_N \cdot \dfrac{1}{v_N} + d_P \cdot \dfrac{1}{v_P} \leq 35
$$

ici temps minimum est 34,96s avec x = 66,59m


# CR - 13H30/15H30

## Répartitions de parties de cours

- Commande linéaire avancée
  - Commande Robuste: Dimitry Peaucelle
  - Systemes Multivariables: F. Gouaisbaut

- Commande de Robots: P. Danès

## Notes 2022/08/30

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

### Problématique:

Comment commander un système avec de grandes incertudes de modélisation

### Exemple: Incertitudes Multi/Addi

$$
\dfrac{1}{\;s^2 + 2 \zeta \omega_n s + \omega_n^2\;}
$$

avec $\quad0,8\leq\zeta\leq1,2\quad$ et $\quad3\leq\omega_n\leq7$

![](/assets/images/CR.SchemaBlocIncertitudeMultiAddit.png)

- pour définir la notion de "proche" on utilise la **norme H infinie**

### Exemple: Système d'ordre 1

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

### Exemple: Système du 2ème ordre

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

### Exemple: Système du 3ème ordre

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

### Convexité d'un espace

![](/assets/images/CR.Convexite.png)

### Critère Général pour P2

![](/assets/images/CR.Xaputohob.png)

Xaputohob a considéré la structure de P2 pour un ordre n qlqc et il a cherché s'il existe un critère pour résoudre la question de stabilité

Or il y a $2^{n+1}$ combinaisons des min et max possible

Mais on connait 4 polynomes assurant une stabilité robuste

### Contre Exemple

![](/assets/images/CR.ContreExemple.png)

- Lorsque le système varie dans le temps alors il ne fait aucun sens d'appliquer la méthode du polynome caractéristique avec des racines à parties réelles négatives

- Pourquoi ?

![](/assets/images/CR.ContreExempleExplication.png)

- Solution: Utiliser Lyapunov et Espace d'état

### Exemple: Lyapunov

![](/assets/images/CR.FctLyapunov.png)
---
id: la6ag2ji4x99olfq54dtpfy
title: CR - Commandes Robots
desc: ''
updated: 1661870232517
created: 1661868245203
---

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


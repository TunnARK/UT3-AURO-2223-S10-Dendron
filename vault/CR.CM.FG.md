---
id: y2ldpz4tnbwwv24y591rjtv
title: Systèmes Multivariables
desc: ''
updated: 1662938041357
created: 1662925980552
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut

# Objectif

Étudier des systèmes MIMO (Multi Input Multi Output)

Décomposée en deux parties:
  - Performances et robustesses
  - Systèmes nominaux + modèles/réalisation commande

- Système **réalisable** si (considérant un input output) peut-on déterminer un système d'espace d'état

- souvent dans l'industrie les modèles sont déterminer par des physiciens et donc possède bcp de fonctions de transfert ce qui rend la command plus compliquée

# Support de cours

- [CR.FG.NotesGEA.20220831.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CR.FG.NotesGEA.20220831.pdf)
- ...

---




> Notes Cours 08/31 - Start




# I- Modélisation des Systèmes MIMO

## 1) Rappel sur les Systèmes MIMO

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

## 2) Les modèles MIMO

### 2.1) Les modèles E/S

#### Les modèles temporels

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

#### Les modèles fréquentiels

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

##### Définitions (Ordre/Zéro/Pôles) d'une FT

- si la matrice $F(s)$ est sous forme diagonale alors on peut facilement déterminer l'ordre/zero/pole
- donc on va diagonaliser les matrices
- MAIS comment diagonaliser des matrices non carrées ?!! => utiliser la forme SMITH




> Notes Cours 08/31 - End

---

> Notes Cours 09/07 - Start




##### Notion d'ordre/zéros/pôles pour une fonction de transfert

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


# II- Réalisation sous forme d'E.E.

**Exemple 1** 

$$
G(s) = \dfrac{1}{(s+1)(s+2)}
$$

1. Faire la décomposition en élément simple

2. Exprimer $y(s)=G(s)\;u(s)$

3. Faire un changement de variable

4. Écrire le système E.E.

CR.FG.Cours0907.ExempleRealisation

## II-1) La forme modale (forme de Guilbert)

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



> Notes du 2022/09/07 - End

---

> Notes du 2022/09/08 - Start




## II-2) Réalisation minimale

Pour obtenir une réalisation minimale, il faut étudier le rang des matrices résidus.

Soit, $\;\rho_i = rang(N_i)\;$ alors il existe $\;C_i\in\mathbb{R}^{p\times\rho_i}\;$ et $\;B_i\in\mathbb{R}^{\rho_i\times m}\;$ tel que $\;N_i=B_i\,C_i\;$

Finalement,
$$
y(s) = \sum_{i=1}^{n}\dfrac{\;C_i\,B_i\;}{s-p_i}\,u(s)
$$

Ainsi, on pose $\;x_i(s) = \dfrac{B_i}{s-p_i}u(s) \;\in\mathbb{R}^{\rho_i}$

On en déduit le système suivant avec $1\leq i \leq n$:

$$
\dot x_i(t) = p_ix_i(t) + B_i u(t)
$$
$$
y(t) = \sum_{i=1}^{n}C_ix_i(t) + D
$$

Dont le nombre d'états est égal à la somme des $\rho_i$ .

CR.FG.Cours0908.systemeABCD

> EXAMEN: $D\neq0$ alors il faut faire la div eucli de la frac ratio

**Thm:** Cette représentation est **minimale** !

> **Repr. minimale** = nb minimale d'etats qui sont cmble et obsble 

## II-3) Réalisation sous forme compagne de commande par bloc

**Exemple:** 
$$
G(s) = \dfrac{s+3}{\;s^2+4s+8\;}
$$

**Rem:** Forme Compagne de Commande
- Dans la forme comp. de cmmde, on peut lire facilement le poly. caractéristique
- Dans la forme comp. de cmmde, on sépare clairement le numérateur de la FT donc ça part dans C
- Très liée aux variables du plan de phase donc aux dérivées de la chaine d'intégrateur
- La difficulté est dans le numérateur donc récrire l'équation avec une variable intermédiaire $v(s)$

1. Transformer $y(s)$ avec la variable intermédiaire $v(s)$
2. Définir un plan de phase sur $v(s)$ en posant $\;x_1(t) = v(t)\;$ et $\;x_2(t) = \dot v(t)\;$

CR.FG.Cours0908.FormeCompABCDGS

> Dès qu'on arrive au plan de phase, il n'est plus nécessaire de se preoccuper du rang car d'office tous ces etats sont forcément comble et obsble

> Méthode de ? = Minimiser le nb de + et x 

## II-4) Cas général

Considérant $\;G(s)\in\mathbb{R}^{p\times m}\;$ et $\;G(s) = \dfrac{1}{\;d(s)\;}N(s)\;$, donc
$$
y(s) = \dfrac{1}{\;d(s)\;}N(s)\;u(s)
$$

On va essayer de réaliser une forme compagne de commande pour chaque $u(s)$.

On pose 
$\;N(s) = 
\begin{bmatrix}
  N_1(s) & \dots & N_m(s)
\end{bmatrix}\in\mathbb{R}^{p\times m}\;$ et donc $\;y(s) = \sum_{i=1}^{m}y_i(s)\;$ avec
$$
y_i(s) = \dfrac{1}{\;d(s)\;}N_i(s)\;u_i(s)
$$

> Forcément cmble car pour chaque entrée on crée un form comp cmde SISO

Soit $\;d(s) = s^n+a_{n-1}s^{n-1}+\dots+a_o\;$ et on pose $\;v_i(s) = \frac{1}{d(s)}u_i(s)\;$.

On choisit 
$$
\left\{
  \begin{array}{rcl}
    x_{1i}(t) & = & v_i(t) \\
    x_{2i}(t) & = & \dot v_i(t) \\
    &\vdots&\\
    x_{ni}(t) & = & v_i^{(n-1)}(t) \\
\end{array}\right.
$$

$$
\dot X_i(t) = AX_i(t) + BU_i(t)
$$

$$
A=
\begin{bmatrix}
  0 & 1 & & \\
  & \ddots & \ddots & \\
  & & 0 & 1\\
  -a_0 & -a_1 & \dots & -a_{n-1}
\end{bmatrix}
\quad\text{et}\quad
B=
\begin{bmatrix}
  0\\
  \vdots\\
  0\\
  1
\end{bmatrix}
$$

Or $\quad y(s) = N_i(s)v_i(s)\quad$ donc on pose $\quad N_i(s) = \sum_{j=1}^{n}N_{ji}\;s^{j-1}$

Du coup, $\quad y(t) = \sum_{j=1}^{n}N_{ji}\;x_{ji}(t)\quad$ et
$\quad B=
\begin{bmatrix}
  N_{1i} & \dots & N_{ni}
\end{bmatrix}$

On répète l'opération pour les $m$ entrées et on somme les contributions des états sur les sorties.

Finalement, on obtient $n\times m$ états **commandables**.

CR.FG.Cours0908.BlocDeFormCompCmde

**Exemple:** MISO 
$$
H(s) =
\begin{bmatrix}
  \dfrac{1}{\;s\;} & \dfrac{1}{\;s(s+2)\;} & \dfrac{1}{\;(s+1)(s+3)\;}
\end{bmatrix}
$$
Q1) Appliquer la méthode de Gilbert à $H(s)$

1. Mettre sous la forme de smith
2. Faire la decomposition matricielle en elmnts simple
3. Poser $x_i(s) = N_i(s)u(s)$
4. Remplir le système 


Q2) Appliquer la forme de compagne de commande à $H(s)$





> Notes du 2022/09/08 - End

---
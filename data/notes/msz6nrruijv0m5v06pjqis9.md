
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut

Support de cours:
- [Slide Partie 3](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/B2.CNL.CM.SlidePartie3.20221125.pdf)

---

> Notes du 2022/11/23 - Start




![](/assets/images/B2.CNL.CM.SlidePartie3-01.png)

# Présentation du cours

![](/assets/images/B2.CNL.CM.SlidePartie3-02.png)

# Sommaire

![](/assets/images/B2.CNL.CM.SlidePartie3-03.png)

# Partie III - Commandes : Linéaristation par bouclage

![](/assets/images/B2.CNL.CM.SlidePartie3-04.png)

## III-1. Introduction

### III-1.1) Elements d'introduction

#### Principales Sources

![](/assets/images/B2.CNL.CM.SlidePartie3-05.png)

#### Difficulté d'asservir des systèmes non linéaires

![](/assets/images/B2.CNL.CM.SlidePartie3-06.png)

#### Quels types de système pour la linéarisation ?

![](/assets/images/B2.CNL.CM.SlidePartie3-07.png)


#### Contexte de la linéarisation: choix du système

![](/assets/images/B2.CNL.CM.SlidePartie3-08.png)

### III-1.2) Un premier exemple

#### Principe de la régulation de niveau


![](/assets/images/B2.CNL.CM.SlidePartie3-09.png)

> [Infundibuliforme](https://www.lalanguefrancaise.com/dictionnaire/definition/infundibuliforme) (adj.) : Qui a la forme d'un entonnoir.

On ne pourra pas considérer une commande non affines vis-à-vis de $u$.

#### Modélisation du comportement dynamique

![](/assets/images/B2.CNL.CM.SlidePartie3-10.png)

#### Choix d'une commande

![](/assets/images/B2.CNL.CM.SlidePartie3-11.png)

#### Conclusion

![](/assets/images/B2.CNL.CM.SlidePartie3-12.png)




## III-2. Philosophie de la méthode

### III-2.1) Introduction

#### Remarques préliminaires

![](/assets/images/B2.CNL.CM.SlidePartie3-13.png)

Si $\gamma$ n'est pas inversible, alors on essaie de trouver un bassin d'attraction qui nous éloigne du point interdit. Si maintenant on veut se placer exactement sur ce point non invertible alors le fait meme que $\gamma(x_{desire})=0$ indique possiblement que le système n'est pas commandable sur ce point.

#### Une première classe de système

![](/assets/images/B2.CNL.CM.SlidePartie3-14.png)
![](/assets/images/B2.CNL.CM.SlidePartie3-15.png)

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-16.png)

Pourquoi ce changement de variable ?

Mais on veut que la non linéairité se trouve sur le meme niveau que la commande $u$ du coup on passe par le chgmt de variable en $z$ pour faire sauter la fonciton $\sin$ sur l'etat $z_2$

On trouve ainsi $\quad u=z_1^2 + \dfrac{v}{\;\sqrt{a^2-z_2^2\;}\;}$

![](/assets/images/B2.CNL.CM.SlidePartie3-17.png)

### III-2.2) Linéarisation entrée/état

#### Principe général

![](/assets/images/B2.CNL.CM.SlidePartie3-18.png)

#### Outil mathématique : le difféomorphisme

![](/assets/images/B2.CNL.CM.SlidePartie3-19.png)

#### Système linéarisable par bouclage

![](/assets/images/B2.CNL.CM.SlidePartie3-20.png)

#### Qlqs questions/remarques

![](/assets/images/B2.CNL.CM.SlidePartie3-21.png)

Il faut connaitre précisément chaque paramètre dont $z$ dépend sinon on loupe completement l'annulation de la NL.

Ceci pose des problemes de robustesse.

Au contraire, avec la méthode de Lyapunov, avoir une incertitude ne va que faire varier notre dérivée mais vu que notre condition impose seulement d'être négatif on possede plus de robustesse.

En outre, au final tout retour d'état minise un coût (voir [[B1.COI]]) or tout retour d'état possède une fonction de lyapunov derriere !

L'**inverse optimality** vise à synthétiser la commande en cherchant la minimisation du cout via des fct de lyapunov (méthode LQR).

### III-2.3) Linéarisation entrée/sortie

#### Principe de la linéarisation entrée/sortie

![](/assets/images/B2.CNL.CM.SlidePartie3-22.png)

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-23.png)

Faire un fowarding sur x_1 et x_2 en considerant x_3 comme une entree puis faire le backstepping sur x_2 et x_3 

![](/assets/images/B2.CNL.CM.SlidePartie3-24.png)

!!! On peut suivre n'importe quelle trajectoire du moment qu'elle est dérivable


#### Remarques

> Keywords: degré relatif

![](/assets/images/B2.CNL.CM.SlidePartie3-25.png)



- Il se trouve qu'on commence avec 3 etats pour finir seulement avec 2 etats ?? 
- Cela ne poserait pas de pb si l'on peut démontrer que ce troisieme etat est stable
- degré relatif = nb de fois qu'il est nécessaire de dérivée pour faire apparaître $u$

#### Exemple d'un système linéaire

![](/assets/images/B2.CNL.CM.SlidePartie3-26.png)

#### Remarque sur les deux exemples

> Keyword: dynamique interne

![](/assets/images/B2.CNL.CM.SlidePartie3-27.png)

En appliquant la loi de commande en BF, on a rendu non-observable une partie des etats --> cette partie s'appelle la **dynamique interne** et sa dimension vaut $n-r$

La dynamique interne depend de $u$ en NL (elle est fixe en linéaire).

Dans le cas de l'exemple, un etat est non observable puisque $n-r=3-2=1$.

Une façon de procéder pour poursuivre serait d'injecter $u$ dans le système et l'analyser.

### III-2.4) Notion de dynamique interne ou dynamique des zéros

#### Introduction

![](/assets/images/B2.CNL.CM.SlidePartie3-28.png)

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-29.png)
![](/assets/images/B2.CNL.CM.SlidePartie3-30.png)

#### Conclusion

![](/assets/images/B2.CNL.CM.SlidePartie3-31.png)

## III-3. Principaux outils mathématiques

### III-3.1) Introduction

#### Necessité de développer des outils théoriques

![](/assets/images/B2.CNL.CM.SlidePartie3-32.png)

#### Jacobienne

![](/assets/images/B2.CNL.CM.SlidePartie3-33.png)

### III-3.2) Dérivée de Lie & Crochets de Lie

#### Déf.: Dérivée de Lie

![](/assets/images/B2.CNL.CM.SlidePartie3-34.png)

> Attention il s'agit d'un produit scalaire entre la jacobienne et $f$

#### Calculs des Dérivée de Lie successives

![](/assets/images/B2.CNL.CM.SlidePartie3-35.png)

#### Exemple 

![](/assets/images/B2.CNL.CM.SlidePartie3-36.png)

$L_f h$ = la manière qu'une fonction évolue selon $f$

La force de la matrice de commandabilité est de nous indiquer à quel point $u$ peut influencer les dérivées de la sortie $y$

![](/assets/images/B2.CNL.CM.SlidePartie3-37.png)

#### Déf.: Crochets de Lie

![](/assets/images/B2.CNL.CM.SlidePartie3-38.png)

Si un champ de vecteur est subit alors on l'appelle un champ de dérive.

Le crochet de lie illustre la propriété de commutativité de deux fonctions. Si ce crochet est un vecteur nul alors $f$ et $g$ sont commutatives.
Si c'est un vecteur non nul alors il s'agit de la direction vectiorelle representant l'erreur/ecart de la non commutation.

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-39.png)
![](/assets/images/B2.CNL.CM.SlidePartie3-40.png)

#### Propriétés des Crochets de Lie

> Keywords: Bilinéarité ; Antisymétrie ; Identité de Jacobi

![](/assets/images/B2.CNL.CM.SlidePartie3-41.png)

### III-3.3) Difféomorphisme

![](/assets/images/B2.CNL.CM.SlidePartie3-42.png)

### III-3.4) Thm de Frobenius

#### Objectifs du Théorème de Frobenius

![](/assets/images/B2.CNL.CM.SlidePartie3-43.png)

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-44.png)

#### Idée du Thm de Frobenius

> Keywords: Intégrabilité

![](/assets/images/B2.CNL.CM.SlidePartie3-45.png)

#### Généralisation

![](/assets/images/B2.CNL.CM.SlidePartie3-46.png)

#### Champ involutif

![](/assets/images/B2.CNL.CM.SlidePartie3-47.png)

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-48.png)

#### Thm d'existence

![](/assets/images/B2.CNL.CM.SlidePartie3-49.png)

## III-4. Linéarisation entrée/état

### III-4.1) Introduction

![](/assets/images/B2.CNL.CM.SlidePartie3-50.png)

On va vouloir que le degré relatif du système soit égal à la dimension de ce système. Donc il faut dérivée $n$ fois ($n$ étant la dim du système) sans faire apparaitre la commande avant la $n$-ième dérivée.


![](/assets/images/B2.CNL.CM.SlidePartie3-51.png)

### III-4.2) Principaux résultats théoriques

#### Théroème entrée/état linéarisable

![](/assets/images/B2.CNL.CM.SlidePartie3-52.png)

#### Interprétation du résultat de linéarisation entrée/état

![](/assets/images/B2.CNL.CM.SlidePartie3-53.png)

#### Application

Reprenant le système présenté dans l'introduction (en supposant être en SISO pour ne pas compliquer $g$) :

$$
\dot x = f(x) + g(x)\;u
$$

Au final, faire une linéarisation entrée/état c'est faire une linéarisation entrée/sortie avec une dynamique interne nulle.

Donc ajoutant une sortie :
$$
\begin{cases}
\dot x = f(x) + g(x)\;u\\[0.2cm]
y = T_1(x)
\end{cases}
$$

Dérivons maintenant $y$ :
$$
\begin{matrix}
\dot y &=& d_t T_1(x) = \partial_x T_1 \; \dot x\\
&=& \partial_x T_1 \;\Big(\;f(x) + g(x)\;u\;\Big)
\end{matrix}
$$

On impose par choix que $\quad \partial_x T_1\;g(x)  = L_g\;T_1 = 0$

Dérivons à nouveau :
$$
\begin{matrix}
\ddot y &=&  ... !!!
\end{matrix}
$$

On obtient
$$
y^{(n)}(t) = L_f^n\;T_1(x) + L_g\;L_f^{n-1}\;T_1(x)\;u
$$

On suppose que $\quad L_g\;L_f^{n-1}\;T_1(x) \neq 0\quad$ et donc on pose la commande :
$$
u = - \dfrac{L_f^n\;T_1(x)}{\;L_g\;L_f^{n-1}\;T_1(x)\;} + \dfrac{v}{\;L_g\;L_f^{n-1}\;T_1(x)\;}
$$

Ce qui nous permet d'avoir $\quad y^{(n)}(t) = v \quad$ lorsqu'on respecte les deux séries de conditions suivantes :
$$
\begin{matrix}
\begin{cases}
L_g\;T_1(x) = 0\\
\quad\vdots\\
L_g\;L_f^{(n-2)}\;T_1(x) = 0\\
L_g\;L_f^{(n-1)}\;T_1(x) \neq 0
\end{cases} & \quad \text{et} \quad &
\begin{cases}
\partial_x T_1\;g(x) = 0\\
\partial_x L_f\;T_1\;g = 0
\end{cases}
\end{matrix}
$$

Remarque :
$$
\begin{cases}
L_g\;T_1(x) = 0\\
L_g\;L_f\;T_1(x) = 0\\
\end{cases}
\iff L_{[f\;g]}\; T_1 = 0
$$

De même,
$$
\begin{cases}
L_g\;L_f\;T_1(x) = 0\\
L_g\;L_f^2\;T_1(x) = 0\\
\end{cases}
\iff L_{\big[\,f\;\;[f\;g]\,\big]}\; T_1 = 0
$$

Et ainsi de suite, nous obtenons un regroupement de toutes les conditions en une seule équation :
$$
\partial_x\;T_1 \; \Big(\;g \;\; [f\;g] \;\; adj_f^2\;g \; = 0\; \dots \;\; adj_f^{n-1}\;g \;\Big)
$$

On constate ainsi que cette condition se traduit comme : "si ce champ de vecteur est intégrable"

#### Exemple

![](/assets/images/B2.CNL.CM.SlidePartie3-54.png)

En discret, on peut aller sur deux directions si maintenant c'est direction remplissent l'espace (la base formée par les directions est de même dimension que le système) alors on est commandable.



> Notes du 2022/11/24 - End

---
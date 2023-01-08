
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat

Support de cours:

![[VIRCRV#^vi-support-td2-start:#^vi-support-td2-end]]

Scans
![[VIRCRV#^vi-scangea-td2]]

---

> Notes du 2022/09/07 - Start

# part 2

Procedure de calibrage: 
- situation des deux robots
- position des objets

VI.TD2.FigRobotRPP

Coord. du point $P$ dans $\mathcal{R}_C\;$ :
$\;
\overrightarrow{CP}_{(C)} = 
\begin{pmatrix}
a\\ b\\ c\\
\end{pmatrix}
$

Coord. du point $O_0$ dans $\mathcal{R}_C\;$ :
$\;
\overrightarrow{CO}_{(C)} = 
\begin{pmatrix}
l_1\\ -l_2\\ -l_3\\
\end{pmatrix}
$

#### Question 2.1 - Localiser la pièce dans $\mathcal{R}_0$

VI.TD2.Question

Matrice de passage homogène :
$
T_{0C} = 
\begin{bmatrix}
R_{0C} & \overrightarrow{O_0C}_{(0)}\\
\mathcal{O}_{1 \times 3} & 1
\end{bmatrix}
$

Cette matrice est constante car les 2 repères sont fixes

On a
$$
T_{0C} = 
\begin{bmatrix}
0 & 1 & 0 & l_2\\
-1 & 1 & 0 & l_1\\
0 & 0 & 1 & l_3\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

ATTENTION le vecteur
$\overrightarrow{O_0C}_{(0)} \neq \begin{pmatrix}
l_1\\ -l_2\\ -l_3\\
\end{pmatrix}$

On a changé de repere !

Il faut donc appliquer la matrice de rotation:

$$
\overrightarrow{O_0C}_{(0)} = - R_{0C}\;\overrightarrow{O_0C}_{(C)} =
\begin{pmatrix}
l_2\\ l_1\\ l_3\\
\end{pmatrix}
$$

Ainsi, 

$$
\begin{pmatrix}
\overrightarrow{O_0P}_{(0)}\\ 
1
\end{pmatrix}
= T_{0C}
\begin{pmatrix}
\overrightarrow{CP}_{(C)}\\ 
1
\end{pmatrix}
= \begin{bmatrix}
b+l_2\\ 
-a +l_1\\
c+l_3\\
1
\end{bmatrix}
$$

où $\overrightarrow{O_0P}_{(0)}$ sont les coord. hom de $P$ dans $\mathcal{R}_0$ et $\overrightarrow{CP}_{(C)}$ corrd. de $P$ dans $\mathcal{R}_C$ (donc pas $\overrightarrow{O_0P}_{(C)}$)

#### Question 2.2 - Trouver la configuration (MGI)

> Quel est la configuration de .. = Calculer le MGI !

VI.TD2.Question2

Contexte :
- Coord. du point de saisie dans $\mathcal{R}_0$ :
$\begin{pmatrix}
a'\\ 0\\ c'
\end{pmatrix}$

- Orientation de $\mathcal{R}_P$ est identique à celle de $\mathcal{R}_0$

C'est deux points nous donne la **situation de la pièce à atteindre**.

**But:**
$$
T_{0P}^* = 
\begin{bmatrix}
1 & 0 & 0 & a'\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & c'\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

On calcule le MGD

VI.TD2.Question2-01

On cherche $\;T_{0E} (q_1,q_2,q_3)$

Pour faire cela on decompose chaque passage :

VI.TD2.Question2-02

On a alors
$$
T_{0E} (q_1,q_2,q_3) = T_{01}(q_1) \; T_{12}(q_2) \; T_{2E}(q_3) =
\begin{bmatrix}
c_1 & -s_1 & 0 & q_2c_1\\
s_1 & c_1 & 0 & q_2s_1\\
0 & 0 & 1 & h-q_3\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

avec

$$
T_{01}(q_1) = 
\begin{bmatrix}
c_1 & -s_1 & 0 & 0\\
s_1 & c_1 & 0 & 0\\
0 & 0 & 1 & h\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

$$
T_{12}(q_2) = 
\begin{bmatrix}
1 & 0 & 0 & q_2\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

$$
T_{2E}(q_3) = 
\begin{bmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & -q_3\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

Mtnt on peut calculer le MGI en identifiant : $\; T_{0E}(q) = T_{0P}^*$

Donc on obtient les equations suivantes

$$
\begin{matrix}
c_1 = 1 & 
s_1 = 0 &
\Longrightarrow &
q_1 = 0\\
q_2\;c_1 = a' &
q_2\;s_1 = 0 &
\Longrightarrow &
q_2 = a'\\
& h-q_3 = c' &
\Longrightarrow &
q_3 = h - c'
\end{matrix}
$$

#### Question 2.3 - Erreur de déplacement

VI.TD1.Question3

$$
\begin{matrix}
c_1 = 1 & s_1 = 0 & \Longrightarrow & q_1 = 0\\
q_2\;c_1 = a' & q_2\;s_1 = b' & \Longrightarrow &  b' = 0\\
& h-q_3 = c' & \Longrightarrow & q_3 = h - c'
\end{matrix}
$$

Or le système n'a de solution que pour $b'=0$

Du coup le robot ne peut pas physiquement effectué cette tache

#### Question 2.4 - Rajout d'une liaison rotoide

On calcule le MDD

$$
T_{0E} (q_1,q_2,q_3,q_4) = T_{01}(q_1) \; T_{12}(q_2) \; T_{2E}(q_3)\\[0.5cm]
=
\begin{bmatrix}
c_1c_4 - s_1s_4 & -c_1s_4 -c_4s_1 & 0 & q_2c_1\\
c_1s_4 + c_4s_1 & c_1c_4 -s_1s_4 & 0 & q_2s_1\\
0 & 0 & 1 & h-q_3-h_2\\
0 & 0 & 0 & 1
\end{bmatrix}\\[0.5cm]
=
\begin{bmatrix}
c_{14} & -s_{14} & 0 & q_2c_1\\
s_{14} & c_{14} & 0 & q_2s_1\\
0 & 0 & 1 & h-q_3-h_2\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

avec

$$
T_{01}(q_1) = 
\begin{bmatrix}
c_1 & -s_1 & 0 & 0\\
s_1 & c_1 & 0 & 0\\
0 & 0 & 1 & h\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

$$
T_{12}(q_2) = 
\begin{bmatrix}
1 & 0 & 0 & q_2\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

$$
T_{2E}(q_3,q_4) = 
\begin{bmatrix}
c_4 & -s_4 & 0 & 0\\
s_4 & c_4 & 0 & 0\\
0 & 0 & 1 & -q_3-h_2\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

Or 

$$
T_{0P}^* = 
\begin{bmatrix}
1 & 0 & 0 & a'\\
0 & 1 & 0 & b'\\
0 & 0 & 1 & c'\\
0 & 0 & 0 & 1
\end{bmatrix}
$$

On identifie $T_{0E}(q)$ à $T_{0P}^*$

$$
\begin{matrix}
c_{14} = 1 \quad\wedge\quad s_1 = 0 & \Longrightarrow & q_1 + q_4 = 0 & \Longrightarrow & q_4 = -q_1\\[0.5cm]
q_2\;c_1 = a' \quad\wedge\quad q_2\;s_1 = b' & \Longrightarrow & c_1 = \dfrac{a'}{q_2} \quad\wedge\quad s_1 = \dfrac{b'}{q_2} & \Longrightarrow & q_1 = atan2\Big(\dfrac{a'}{q_2},\dfrac{b'}{q_2}\Big)\\[0.5cm]
q_2^2\;c_1^2 + q_2^2\;s_1^2 = a'^2 + b'^2 & \Longrightarrow & q_2 = !!!\\[0.5cm]
h -q_3 - h_2 = c' & \Longrightarrow & q_3 = h - h_2 - c'\\[0.5cm]
q_4 = !!!
\end{matrix}
$$

Attention $q_2 \neq 0$


## Extra

Extra-01

Extra-02

Extra-03

## MCD

MCD donne le lien entre les vitesses de l'OT et les vitesses des liaisons

VI.TD2.ExtraMCD

Attention la jacobienne depend des $q_i$
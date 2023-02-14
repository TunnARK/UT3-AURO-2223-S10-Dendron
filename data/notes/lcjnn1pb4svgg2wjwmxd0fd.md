
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat

Support de cours:
![[VIRCRV#^vi-support-td1-start:#^vi-support-td1-end]]

Scans
![[VIRCRV#^vi-scangea-td1]]

---

> Notes du 2022/09/07 - Start

![](/assets/images/VIRCRV.TD1.Slide.01.png)

### I.1) Les trois rotations

![](/assets/images/VIRCRV.TD1.Slide.02.png)

- Vue 2D:
    - Cercle avec point $\Longrightarrow$ vecteur pointe vers le lecteur
    - Cercel avec croix $\Longrightarrow$ vecteur s'en va du lecteur

![](/assets/images/VIRCRV.TD1.Slide.03.png)

![](/assets/images/VIRCRV.TD1.Slide.04.png)


#### Question 1.1:

![](/assets/images/VIRCRV.TD1.Question1.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    1 & 0 & 0\\
    0 & cos\theta & -sin\theta\\
    0 & sin\theta & cos\theta
\end{bmatrix}
$$


#### Question 1.2:

![](/assets/images/VIRCRV.TD1.Question2.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    cos\theta & 0 & sin\theta\\
    0 & 1 & 0\\
    -sin\theta & 0 & cos\theta
\end{bmatrix}
$$

#### Question 1.3:

![](/assets/images/VIRCRV.TD1.Question3.png)

Réponse:
$$
R_{01} =
\begin{bmatrix}
    cos\theta & -sin\theta & 0\\
    sin\theta & cos\theta & 0\\
    0 & 0 & 1
\end{bmatrix}
$$

#### Question 1.4:

![](/assets/images/VIRCRV.TD1.Question4.png)

Réponse:
- 1er matrice est une rotation autour de $\overrightarrow{y}$ avec un angle de $\theta=\dfrac{\pi}{3}$
    $$
    R_{01} =
    \begin{bmatrix}
        0.5 & 0 & 0.87\\
        0 & 1 & 0\\
        -0.87 & 0 & 0.5
    \end{bmatrix}
    $$
- 2ème matrice est une rotation autour de $\overrightarrow{z}$ avec un angle de $\theta=\dfrac{\pi}{2}$
    $$
    R_{01} =
    \begin{bmatrix}
        0 & -1 & 0\\
        1 & 0 & 0\\
        0 & 0 & 1
    \end{bmatrix}
    $$
- 3ème matrice est une rotation autour de $\overrightarrow{x}$ avec un angle de $\theta=\dfrac{3\pi}{2}$
    $$
    R_{01} =
    \begin{bmatrix}
        1 & 0 & 0\\
        0 & 0 & 1\\
        0 & -1 & 0
    \end{bmatrix}
    $$

### I.2) Composition des rotations et changements de base


#### Question 2.1:

![](/assets/images/VIRCRV.TD1.Question21.png)

**Réponse:**

**a)**

VIRCRV.TD1.Question21a.NotesGEA

**b)**
$$
R_{01} =
\begin{bmatrix}
    0 & 0 & -1\\
    0 & 1 & 0\\
    1 & 0 & 0
\end{bmatrix}
$$

$$
R_{12} =
\begin{bmatrix}
    1 & 0 & 0\\
    0 & 0 & -1\\
    0 & 1 & 0
\end{bmatrix}
$$

**c)**

$$
R_{02} = R_{01} \times R_{12} =
\begin{bmatrix}
    0 & -1 & 0\\
    0 & 0 & -1\\
    1 & 0 & 0
\end{bmatrix}
$$

> **Attention:** $R_{02}$ n'a pas d'identification possible avec une des 3 matrices de rotation classiques !

**d)**

$$
\overrightarrow{v}_{(0)} = 
\begin{pmatrix}
    0 \\
    1 \\
    2
\end{pmatrix}
\Longrightarrow
\overrightarrow{v}_{(0)} = R_{01} \;\overrightarrow{v}_{(1)}

$$
...


![](/assets/images/VIRCRV.TD1.Slide.05.png)



> Notes du 2022/09/07 - End

---

> Notes du 2022/09/08 - Start





### I.3) Matrices de Passage Homogènes

#### Question 3.1:

![](/assets/images/VIRCRV.TD1.Question31.png)

Il s'agit de la composition d'une translation et d'une rotation.

Il nous faut donc une matrice de passage homogène.

$$
T_{01} =
\begin{bmatrix}
    R_{01} & {P_{01}}_{(0)}\\
    \mathcal{O}_{1\times 3} & 1
\end{bmatrix}
$$

avec 
$$
{P_{01}}_{(O)} = \overrightarrow{O_0O_1}_{(O)} =
\begin{pmatrix}
    a\\
    b\\
    c\\
\end{pmatrix}
$$

...

**Conclusion:** Rotation autour de $\overrightarrow{z}_0$ d'angle $\theta$

#### Question 3.2:

![](/assets/images/VIRCRV.TD1.Question32.png)

BM à 6 liaisons donc $\mathcal{R}_6$ est le repère lié à l'OT

VIRCRV.TD1.Question32.RepereO6

VIRCRV.TD1.Question32.RepereO7

Ici on s'interesse à $\;\overrightarrow{O_0O_7}_{(O)}$ soit la position de $O_7$ dans $\mathcal{R}_0$.

Pour calculer $\;\overrightarrow{O_0O_7}_{(O)}$,  on a besoin de $T_{06}$


- relation intrinsèque 
  $$
  \overrightarrow{O_0O_7} = \overrightarrow{O_0O_6} + \overrightarrow{O_6O_7}
  $$
  - position interne de l'outils
- relation extrinsèque
  $$
  \overrightarrow{O_0O_7}_{(O)} = \overrightarrow{O_0O_6}_{(O)} + \overrightarrow{O_6O_7}_{(O)}
  $$
  - postion outils dans l'environmmnet

$$
\overrightarrow{O_0O_7}_{(O)} = \overrightarrow{O_0O_6}_{(O)} + \overrightarrow{O_6O_7}_{(O)}
...  
$$

**Autre solution:**

$$
\begin{pmatrix}
    \overrightarrow{O_0O_7}_{(O)}\\
    1\\
\end{pmatrix}
= T_{06}
\begin{pmatrix}
    \overrightarrow{O_6O_7}_{(O)}\\
    1\\
\end{pmatrix}
= 
\begin{pmatrix}
    0 & 1 & 0 & 0\\
    0 & 0 & 1 & L\\
    1 & 0 & 0 & H\\
    0 & 0 & 0 & 1\\
\end{pmatrix}
\begin{pmatrix}
    d_1\\
    0\\
    d_2\\
    1
\end{pmatrix}
=
\begin{pmatrix}
    0\\
    d_2+L\\
    d_1+H\\
    1
\end{pmatrix}
$$

**Conclusion:** Situation de l'OT
$$
x = 
\begin{pmatrix}
    x_P\\
    x_R\\
\end{pmatrix}
\quad\text{avec}\quad
x_P = 
\begin{pmatrix}
    0\\
    d_2+L\\
    d_1+H
\end{pmatrix}
\quad\text{et}\quad
x_R = 
\begin{pmatrix}
    {\overrightarrow{x_6}}_{(0)}\\
    {\overrightarrow{z_6}}_{(0)}\\
\end{pmatrix}
=
\begin{pmatrix}
    0\\
    0\\
    1\\
    0\\
    1\\
    0
\end{pmatrix}
$$

cosinus directeurs partiels souvent choisit avec x et z



> Notes du 2022/09/08 - End

---
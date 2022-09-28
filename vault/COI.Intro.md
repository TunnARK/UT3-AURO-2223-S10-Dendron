---
id: n9exhzncgo4w717syg47ojd
title: Intro
desc: ''
updated: 1664354077846
created: 1663307233627
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par S. Fergani

---

> Notes du 2022/09/15 - Start


...


> Notes du 2022/09/15 - End

---

> Notes du 2022/09/16 - Start 

Application

**Equation Générale de Bellman :**

($\;d$ le nombre de division de l'intervalle $[t_0,t_f]\;$)

$$
\tilde J (x_0,t_0,\tilde u) =
\min_{u_{[t_0,t_f]}} \Big[ 
    \sum_{j=1}^{d} \Big[\; 
        \min_{u_{[t_0,t_f]}} \big(\; 
            \int_{t_0}^{t_{i_j}} \phi(x,t,u)\,dt
        \;\big)
        +
        \tilde J (x_{i_j},t_{i_j},\tilde u_j)
    \;\Big] \;\Big]
$$

## Commande LQ

### Horizon fini et infini

**Cas discret:**
- Si $x(k)$ est un point intermédiaire de la trajectoire optimale allant de $x(k_0)$ à $x(t_f)$ alors la portion terminale $x(k)$ à $x(t_f)$ de cette trajectoire est **optimale**
- D'après le principe de Bellman, la portion de la trajectoire $x(k)$ à $x(t_f)$ est d'écrite par : $x(k+1) = f(x_k,u_k)$ est **optimale** au sens du critère : 
$$
\min_u J(u_k) = J(x_k,u_k)=\frac{1}{2} \sum_{i=t_k}^{t_{f-1}}\big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}
$$
- le coût **immédiat** est $J=k$
- le coût **intermédiaire** est $\frac{1}{2} \sum_{i=t_k}^{t_{f-1}}\big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big)$

> Les matrices $Q_i$ , $R_i$ et $P_i$ sont choisis par le designer selon les objectifs du système

> u^*_{t_k} c'est la commande **optimale** entre $(x_k,t_k)$ et $(x_f,t_f)$ !

!!!

### Problématique

On cherche la commande $u$ qui minimise :
$$
\min_u J(u) = J(x_k,t_k) = \frac{1}{2} \sum_{i=t_k}^{t_{f-1}} \big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}
$$
sous la contrainte
$$
\begin{matrix}
x_{k+1} &=& Ax_k + Bu_k\\
y_k &=& Cx_k
\end{matrix}
$$

### Idée 

On part du point **optimale** $x(t_f)$ **connu** au point précédent $x(t_{f-1})$

La trajectoire à minimiser est donnée par le coût :
$$
\min_u J(u) = J(x_k,t_k) = \frac{1}{2} \sum_{i=t_k}^{t_{f-1}} \big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}
$$
avec le coût **immédiat** $\frac{1}{2} \sum_{i=t_k}^{t_{f-1}} \big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big)\;$ et le coût final $\;\frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}$

> Les matrices $Q_i$ , $R_i$ et $P_i$ sont choisis par le designer selon les objectifs du système

### Comment trouver cette commande optimale ?

1. Pour minimiser, on dérive $J(x_{t_{f-1}},u_{t_{f-1}})$ p.r.à $u_{t_{f-1}}$ soit :
$$
\partial_{u_{t_{f-1}}}J(x_{t_{f-1}},u_{t_{f-1}})
$$

2. On annule la dérivée, la solution est la **commande optimale** $u^*$ soit : 
$$
\partial_{u_{t_{f-1}}}J(x_{t_{f-1}},u_{t_{f-1}}) = 0
$$

3. On vérifie que la solution optimale $u^*$ minimise $J$ :
$$
\partial_{u_{t_{f-1}}}J(x_{t_{f-1}},u_{t_{f-1}}) > 0
$$
> On peut montrer qu'il faut que la dérivée seconde soit positive en utilisant les développements limités.

4. On remplace la solution optimale $u^*$ dans le critère $J(x_{t_{f-1}},u_{t_{f-1}})$ soit :
$$
J^*(x_{t_{f-1}},u_{t_{f-1}}) = \frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f} = \frac{1}{2} \, x_{t_{f-1}}^T\,P_{t_{f-1}}\,x_{t_{f-1}}
$$





> Notes du 2022/09/16 - End

---

> Notes du 2022/09/23 - Start




### Application

1. On dérive $J$ p.r.à $u$

    $\partial_{u_{t_{f-1}}}J(x_{t_{f-1}},u_{t_{f-1}}) =\\[0.2cm] \partial_{u_{t_{f-1}}} \Big[\frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \big) + \frac{1}{2} \, \textcolor{red}{x_{t_f}^T}\,P_{t_f}\,\textcolor{orange}{x_{t_f}}\Big]=\\[0.2cm]
    \partial_{u_{t_{f-1}}} \Big[\frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \big) + \frac{1}{2} \, \textcolor{red}{\big(x_{t_{f-1}}^T\,A^T+u_{t_{f-1}}^T\,B^T\big)}\,P_{t_f}\,\textcolor{orange}{\big(Ax_{t_{f-1}}+Bu_{t_{f-1}}\big)}\Big]\\$

    Du coût minimal désirée, on obtient une equation analytique de Riccati aux différences (EARD)

    **N.B.:**
    $$
    k^T = k\\
    \partial_x x^TA = A\\
    \partial_x x^TAx = (A+A^T)x
    $$

    Donc, on a :

    $\partial_{u_{t_{f-1}}} \Big[\frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \big) + \frac{1}{2} \, \big(\textcolor{red}{x_{t_{f-1}}^T\,A^T}+\textcolor{orange}{u_{t_{f-1}}^T\,B^T}\big)\,P_{t_f}\,\big(\textcolor{red}{Ax_{t_{f-1}}}+\textcolor{orange}{Bu_{t_{f-1}}}\big)\Big]=\\[0.2cm]
    \partial_{u_{t_{f-1}}} \Big[\frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \Big) +
    \frac{1}{2} \, \big(\textcolor{red}{x_{t_{f-1}}^T\,A^T}\,P_{t_f}\,\textcolor{red}{Ax_{t_{f-1}}}\big)+\big(\textcolor{orange}{u_{t_{f-1}}^T\,B^T\,P_{t_f}}\,+\textcolor{orange}{Bu_{t_{f-1}}}\big)\Big]=\\[0.2cm]
    !!!
    $

    **N.B.:**
    $$
    Q=Q^T\\
    R=R^T\\
    P=P^T
    $$

2. On annule la première dérivée
    
    $
    \partial_{u_{t_{f-1}}}J(x_{t_{f-1}},u_{t_{f-1}}) = 0 = \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)\, u_{T_{f-1}}^* + B^T\,P_{T_{f}}\,A\,x_{T_{f-1}} 
    $

    avec

    $
    u_{T_{f-1}}^* = - \textcolor{green}{\big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A}\,x_{T_{f-1}}
    $

    Ainsi, sous reserve que $\;\big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)\;$ soit inversible, une commande linéaire en fonction de l'état est :

    $
    u_{T_{f-1}}^* = -\textcolor{green}{L_{T_{f-1}}}\,x_{T_{f-1}}
    \quad$
    avec
    $\quad
    \textcolor{green}{L_{T_{f-1}} = \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A}
    $

3. On vérifie que c'est bien un minimum

    $
    \partial_{u_{t_{f-1}}}^2J(x_{t_{f-1}},u_{t_{f-1}}) > 0\\
    = \partial_{u_{t_{f-1}}} \Big[ \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)\, u_{T_{f-1}}^* + B^T\,P_{T_{f}}\,A\,x_{T_{f-1}} \Big]\\
    = \Big( R_{t_{f-1}} + B^T\,P_{t_{f}}\,B \Big)' > 0
    \quad$
    car
    $\quad B^T > 0$

    donc $u^*$ est la commande optimale qui minimise le critère $J$ sous la contrainte de la dynamique du système **sous reserve que** $\;\big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)\;$ soit inversible !

4. On remplace la solution optimale $u^*$ dans le critère $J(x_{t_{f-1}},u_{t_{f-1}})$ pour identifier le résultat avec le coût minimal désirée :

    $
    J^*(x_{t_{f-1}},u_{t_{f-1}}) = \frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \Big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f} = \frac{1}{2} \, x_{t_{f-1}}^T\,P_{t_{f-1}}\,x_{t_{f-1}}\\[0.2cm]
    = \frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + u_{t_{f-1}}^{*T}\,R_{t_{f-1}}\,u_{t_{f-1}}^{*} \Big) + \frac{1}{2} \, \big(\textcolor{red}{x_{t_{f-1}}^T\,A^T}+\textcolor{orange}{u_{t_{f-1}}^T\,B^T}\big)\,P_{t_f}\,\big(\textcolor{red}{Ax_{t_{f-1}}}+\textcolor{orange}{Bu_{t_{f-1}}}\big)\\[0.2cm]
    = \frac{1}{2} \Big( x_{t_{f-1}}^T\,Q_{t_{f-1}}\,x_{t_{f-1}} + \big( \textcolor{green}{-L_{T_{f-1}}\,x_{T_{f-1}}} \big)^T \,R_{t_{f-1}}\, \big( \textcolor{green}{-L_{T_{f-1}}\,x_{T_{f-1}}} \big) \Big)\\[0.2cm] + \; \frac{1}{2} \, \big(\textcolor{red}{x_{t_{f-1}}^T\,A^T}+\textcolor{orange}{ ( \textcolor{green}{-L_{T_{f-1}}\,x_{T_{f-1}}} )^T\,B^T}\big)\,P_{t_f}\,\big(\textcolor{red}{Ax_{t_{f-1}}}+\textcolor{orange}{B ( \textcolor{green}{-L_{T_{f-1}}\,x_{T_{f-1}}} )} \big)\\[0.2cm]
    = \frac{1}{2} x_{T_{f-1}} \big[ !!! \big]
    $

    Ainsi,

    $
    P_{T_{f-1}} = Q_{T_{f-1}} + A^T\,P_{T_{f}}\,A - L_{T_{f-1}}^T B^T \,P_{T_{f}}\, A\\[0.2cm]
    = Q_{T_{f-1}} + A^T\,P_{T_{f}}\,A - \Big( \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A \Big)^T B^T \,P_{T_{f}}\, A\\[0.2cm]
    = Q_{T_{f-1}} + A^T\,P_{T_{f}}\,A - A^T\,P_{T_{f}}\, B \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A \\[0.2cm]
    $

    On obtient une equation analytique de Riccati aux différences (EARD)

    $L$ est un gain construit qu'avec des sommes de termes calculable facilement $\\[1cm]$

C'est une equation une **equation à temps rétrograde** 

$$
Q_{T_{f}} \longrightarrow P_{T_{f}} \longrightarrow P_{T_{f-1}} \longrightarrow L_{T_{f-1}} \longrightarrow u^*_{T_{f-1}} \longrightarrow P_{T_{f-2}} \longrightarrow L_{T_{f-2}} \longrightarrow u^*_{T_{f-2}} \longrightarrow \dots\\[0.7cm]
$$

À $\;t=t_f\;$, on a :

$
P_{T_{f}} \;\; = Q_{T_{f}}\\[0.2cm]
L_{T_{f-1}} = \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A\\[0.2cm]
P_{T_{f-1}} = Q_{T_{f-1}} + A^T\,P_{T_{f}}\,A - L_{T_{f-1}}^T B^T \,P_{T_{f}}\, A\\[0.7cm]
$

À $\;t=t_{f-1}\;$, on a :

$
L_{T_{f-2}} = \big( R_{T_{f-2}} + B^T\,P_{T_f-1}\,B \big)^{-1}\;B^T\,P_{T_{f-1}}\,A\\[0.2cm]
P_{T_{f-2}} = Q_{T_{f-2}} + A^T\,P_{T_{f-1}}\,A - L_{T_{f-2}}^T B^T \,P_{T_{f-1}}\, A\\[0.7cm]
$

### Problème Général

Trouver $u^*(x,t)$ telle que le critère suivant soit **minimal** :

$$
J(u_0, \dots, u_{f-1}) = \sum_{i=t_k}^{t_{f-1}}\big( !!!
$$

Ceci sous la contrainte de la dynamique du système $x_{k+1} = F(x_k,k,u_k)$.

#### Solution

Le problème se réduit à trouver une fonctionnelle optimisée $V(x(t),t)$ (notée en discret $\;V(x(k),k)\;$) sur $[t_0,t_f]$ de $\R^n \rightarrow \R$ solution aux différences retrograde :

$$
V(x(t),t) = \min_u \Big[ L\big(x(t),t,u_t\big) + V\big(x(t+1),t+1\big) \Big]\\[0.2cm]
= \min_u \Big[ L\big(x(t),t,u_t\big) + V\Big(F\big(x(t),t,u_t\big),t+1\Big) \Big]
$$

Or $L\big(x(t),t,u_t\big)$ est le coût ??? indirect à minimiser et $V\Big(F\big(x(t),t,u_t\big),t+1\Big)$ le coût précédent optimisié

De ce fait,$\; V\big(x(k),k\big) = \sum_{t=k}^{T_f} L_t\big(x_t,t,u_t) \;$ représente bien la somme de l'ensemble des coûts intermédiaire sur la trajectoire optimal

La solution de ce problème au sens de _Bellman_ est donnée :
$$
u^* = arg \min_u \Big[ L\big(x(t),t,u_t\big) + V\Big(F\big(x(t),t,u_t\big),t+1\Big) \Big]
$$
c.à.d. $\quad \partial_u V\big(x(t),t\big)|_{u=u^*} = 0 \quad$ et $\quad \partial_u^2 V\big(x(t),t\big)|_{u=u^*} > 0 \quad$


#### Application

Considérons le système suivant :
$$
\begin{matrix}
x_{k+1} &=& Ax_k + Bu_k\\
y_k &=& Cx_k
\end{matrix}
$$

avec un coût à minimiser :

$$
\min_u J(u_k) = J(x_k,u_k)=\frac{1}{2} \sum_{i=t_k}^{t_{f-1}}\big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}
$$

**Problème:**

Déterminer une fonctionnelle $V\big(x(t_{f-1}),t_{f-1}\big)$ solution de l'équation aux différences suivante :
$$
V\big(x(t_{f-1}),t_{f-1}\big) = \Big[ L\big(x(t_{f-1})),t_{f-1}),u_{t_{f-1})}\big) + V\Big(x(t_f),t_f\Big) \Big]
$$

Du coup, on cherche :
$$
V^*\big(x(t_{f-1}),t_{f-1}\big) = \frac{1}{2} x_{t_{f-1}}^T\,P_{t_{f-1}}\,x_{t_{f-1}}
$$

On trouve :
$$
u_{T_{f-1}}^* = - \big( R_{T_{f-1}} + B^T\,P_{T_f}\,B \big)^{-1}\;B^T\,P_{T_{f}}\,A\,x_{T_{f-1}}
$$

En général, la commande LQ est une commande linéaire en fonction de l'état
$$
u_t = -L_t x_t
$$
avec 
$$
L_t = \big( R_{t} + B^T\,P_{t+1}\,B \big)^{-1}\;B^T\,P_{t+1}
$$
et
$$
P_t = Q_t + A^T\,P_{t+1}\,A - A^T\,P_{t+1}\,B \big( R_t + B^T\,P_{t+1}\,B \big)^{-1} B^T\,P_{t+1}\,A
$$

La solution d'équation de Riccati aux différemces obtenue d'une manière retrograde : $P_t = Q_{t_f}$

### Discusion

À n'importe quel instant $J^*$ est un coût optimisé

$u^* \rightarrow k$

$J(u_k) = \frac{1}{2} x_0^TP_0x_0$

**Comment ce système se comporte à l'infini ?**

But est de stabiliser le système

Sauf qu'à l'infini la dynamique du système va "s'éteindre" car à l'infini le système perd toute son energie

Du coup, $\quad\lim_{t\rightarrow\infty}P_{t_f} = 0$





> Notes du 2022/09/23 - End

---

> Notes du 2022/09/28 - Start



## Synthèse de régulateur LQ

### Horizon fini

**Problème:**

Déterminer $u^*$ tq
$$
\min_u J(u) = \frac{1}{2} \sum_{i=0}^{t_{f-1}}\big( x_i^T\,Q_i\,x_i + u_i^T\,R_i\,u_i \big) + \frac{1}{2} \, x_{t_f}^T\,P_{t_f}\,x_{t_f}
$$
sous la contrainte
$$
\begin{matrix}
x_{k+1} &=& Ax_k + Bu_k\\
y_k &=& Cx_k
\end{matrix}
$$
où $\quad Q_k = Q_k^T \geq 0 \quad R_k = R_k^T > 0 \quad P_{T_f} = Q_{T_f} \geq 0$ (matrices choisies par le designer)

**Solution:** $u^*_k = -L_k\;x_k$

$L_k$ est la solution de l'équation de Riccati à temps retrograde??? initialisé par $P_{T_f} = Q_{T_f}$ :

$$
L_k = (R_k + B_k^T\;P_{k+1}\;B_k)^{-1}\;B^T\;P_{k+1}\;A_k\\
P_k = Q_k + A_k^T\;P_{k+1}\;A_k - A_k^T\;P_{k+1}\;B_k\;L_k
$$

Le minimum du critère est alors donné par :
$$
\min_u J(u) = \frac{1}{2} x_0^T\;P_0\;x_0
$$
avec $P_0$ obtenue par l'équation précédente.

### Horizon infini

**Problème:**

Déterminer $u^*$ tq
$$
\min_u J(u) = \frac{1}{2} \sum_{i=0}^{\infty}\big( x_i^T\,\textcolor{red}{Q}\,x_i + u_i^T\,\textcolor{red}{R}\,u_i \big)
$$
sous la contrainte
$$
\begin{matrix}
x_{k+1} &=& Ax_k + Bu_k\\
y_k &=& Cx_k
\end{matrix}
$$
où $\quad Q_k = Q_k^T \geq 0 \quad R_k = R_k^T > 0$ (matrices connues par le designer)

Attention: $P_{T_f}$ est nul (le coût final dans le cas d'un horizon infini est nul [consommation de toute l'énergie]) !

**Solution:**

Le système bouclé est **assymptotiquement stable** sous reserve que le système dynamique soit **stationnaire, stabilisable** et le couple $(A, Q^{1/2})$ **détectable**

> Notions Fondamentales d'Automatique
- Système stationnaire = gain/dynamique/paramètre non variant dans le temps
- Système stabilisable = mode non cmble convergent
- Système détectable = modes non obsble convergent
- Pole dominant = dynamique la plus lente !
- Critère de Kalman pour Cmblité et Obsbilité
- Critère de PBH pour Stabilisable et Détectable

> ATTENTION:
- Cmmble $\Longrightarrow$ Stabilisable (pas d'équivlance)
- Obsble $\Longrightarrow$ Détectable (pas d'équivlance)

$Q^{1/2}$ : n'importe qu'elle matrice rectangulaire qui vérifie 
$$
(Q^{1/2})^T \cdot Q^{1/2} = Q
$$

> Matrice $Q$ est choisie par 

---

### $\textcolor{red}{\textbf{\underline{Théorème :}}}$

1. Si le système dynamique est **stabilisable** alors :
    - $P_{k+1} = P_k = \dots = P$ admet une limite constante semi définie positive qui est la solution de l'équation :
    $$
    P = Q + A^T\;P\;A = A^T\;P\;B\;(R+B^T\;P\;B)^{-1}\;B^T\;P\;A
    $$
    - La commande optimale est donnée par $u^* = -L\;x_k$ avec $L = (R+B^T\;P\;B)^{-1}\;B^T\;P\;A$
    - Le coût optimale est : $\quad \min_u J(u) = \frac{1}{2} x_0^T\;P\;x_0$
2. Si le système est **stabilisable** et le couple $(A,Q^{1/2})$ est **détectable** alors :
    - $P$ est l'**unique solution** semi définie positive de l'équation algébraique de Riccati :
    $$
    P = Q + A^T\;P\;A = A^T\;P\;B\;(R+B^T\;P\;B)^{-1}\;B^T\;P\;A
    $$
    - Le système bouclé est **assymptotiquement stable**
    - En plus, si $(A,Q^{1/2})$ est **observalbe** alors $P$ est définie positive

---

> Importance de la notion définie positive : il faut avoir cette notion pour permettre à la commande d'exister car il nous faut une matrice 'positive' pour pouvoir l'inverser et ainsi calculer la solution


### Exercice

Pour $x_{k+1} = 2 x_k + u_k$, déterminer la commande optimale $u^*$ qui stabilise $x$ et minimise :
$$
J(x_k,k) = \frac{1}{2} \sum_{k=0}^{T_{f-1}} \Big( x_k^T\;x_k + u_k^T\;R\;u_k \Big) + \frac{1}{2}\;x_{T_f}^T\;P_{T_f}\;x_{T_f}
$$
1. avec $T_f = 3$ et $P_{T_f} = 1$ montrer respectivement pour $R=1$, $R=10$ et $R=1000$ l'influence de la ponderation $R$ sur les pôles du système
2. avec $T_f = 3$ et $R = 1$ et respectivement pour $P_{T_f}=0.1$, $P_{T_f}=10$ et $P_{T_f}=1000$ déterminer $x_3$ en fonction de $L_0$,$L_1$, $L_2$ et $x_0$
3. Reprendre la question 1 avec $T_f \longrightarrow \infty$

#### Deux méthodes de résolutions pour la question 1

- Avec le critère optimale
    1. Calculer les $J(x_k,k)$
    2. Dériver ces $J(x_k,k)$ et trouver les racines 
    3. Vérifier que la dérivée seconde > 0
- Avec le formules du cours (selon horizon fini/infini)
    1. Commencer par $u_{t_f}$
    2. Appliquer la formule $u^*_k = -L_k\;x_k$
    3. Calculer $L_k$ (attention dépend de $P_k$) avec 
    $$
    L_k = (R_k + B_k^T\;P_{k+1}\;B_k)^{-1}\;B^T\;P_{k+1}\;A_k
    $$
    4. Calculer $P_k$ avec
    $$
    P_k = Q_k + A_k^T\;P_{k+1}\;A_k - A_k^T\;P_{k+1}\;B_k\;L_k
    $$


> Notes du 2022/09/28 - End

---
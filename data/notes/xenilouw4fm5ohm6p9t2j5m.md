
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

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

#### Solution Q1

Pour $x_{k+1} = 2 x_k + u_k$, déterminer la commande optimale $u^*$ qui stabilise $x$ et minimise :
$$
J(x_k,k) = \frac{1}{2} \sum_{k=0}^{T_{f-1}} \Big( x_k^T\;x_k + u_k^T\;R\;u_k \Big) + \frac{1}{2}\;x_{T_f}^T\;P_{T_f}\;x_{T_f}
$$

avec $T_f = 3$ et $P_{T_f} = 1$ montrer respectivement pour $R=1$, $R=10$ et $R=1000$ l'influence de la ponderation $R$ sur les pôles du système

##### Deux méthodes de résolutions pour la question 1

- Avec le critère optimale
    1. Calculer les $J(x_k,k)$
    2. Dériver ces $J(x_k,k)$ et trouver les racines 
    3. Vérifier que la dérivée seconde > 0
        >![](/assets/images/B1.COI.Chap1.SecondDerivativeForMaxMin.png)
        > [source](https://www.hec.ca/cams/rubriques/La_derivee_seconde.pdf)
- Avec le formules du cours (selon horizon fini/infini)
    1. Commencer par $u_{t_f}$
    2. Appliquer la formule $u^*_k = -L_k\;x_k$
    3. Calculer $L_k$ (attention dépend de $P_k$) avec 
    $$
    L_k = (R_k + B_k^T\;P_{k+1}\;B_k)^{-1}\;B_k^T\;P_{k+1}\;A_k
    $$
    4. Calculer $P_k$ avec
    $$
    P_k = Q_k + A_k^T\;P_{k+1}\;A_k - A_k^T\;P_{k+1}\;B_k\;L_k
    $$




> Notes du 2022/09/28 - End

---

> Notes du 2022/10/05 - Start





##### Réponse

Pour $T_f=3$, $R=1$ et $P_f=P_3=1$ :
1. Déterminer les commandes $u_0^*$, $u_1^*$, $u_2^*$ avec la méthode de Bellman

    Pour $u_2^*$,

    - On a sous la contrainte de $x_3=2x_2+u_2$
    $$
    J(x(2),2)
    = \frac{1}{2} x_2^2 + \frac{1}{2} u_2^2 + J^*(x(3),3)
    = \frac{1}{2} x_2^2 + \frac{1}{2} u_2^2 + \frac{1}{2} x_3^2
    $$

    - La commande est donnée par:
    $$
    \partial_{u_2} J(x(2),2) = \partial_{u_2} \frac{1}{2} x_2^2 + \frac{1}{2} u_2^2 + \frac{1}{2} \big(2x_2+u_2\big)^2 = 0
    $$
    Il vient que $u_2 + (2x_2+u_2)=0$ donc $$u_2^*=-x_2$$

    > Attention: pour être rigoureux, il faut vérifier que $\partial_{u_2}^2J(x(2),2)>0$

    - On calcule alors le coût optimal :
    $$
    J^*(x(2),2) = \frac{1}{2} x_2^2 + \frac{1}{2} u_2^{*2} + J^*(x(3),3) = \frac{1}{2} x_2^2 + \frac{1}{2} \big(-x_2\big)^2 + \frac{1}{2} \big(2x_2-u_2^*\big)^2 
    $$
    Ainsi,
    $$
    J^*(x(2),2) = \frac{3}{2} x_2^2
    $$

    Pour $u_1^*$,

    - On a sous la contrainte de $x_2=2x_1+u_1$
    $$
    J(x(1),1)
    = \frac{1}{2} x_1^2 + \frac{1}{2} u_1^2 + J^*(x(1),1)
    $$

    - La commande est donnée par:
    $$
    \partial_{u_1} J(x(1),1) = \partial_{u_1} \frac{1}{2} x_1^2 + \frac{1}{2} u_1^2 + \frac{1}{2} \big(2x_1+u_1\big)^2 = 0
    $$
    Il vient que 
    $$u_1^*=-\frac{3}{2}x_1$$

    - On calcule alors le coût optimal :
    $$
    J^*(x(2),2) = 2x_1^2
    $$

    Pour $u_0^*$,
    
    - On a sous la contrainte de $x_0=2x_0+u_0$
    $$
    J(x(0),0)
    = \frac{1}{2} x_0^2 + \frac{1}{2} u_0^2 + J^*(x(1),1)
    $$

    - La commande est donnée par:
    $$
    \partial_{u_0} J(x(1),1) = \partial_{u_0} \frac{1}{2} x_0^2 + \frac{1}{2} u_0^2 + \frac{1}{2} \big(2x_0+u_0\big)^2 = 0
    $$
    Il vient que 
    $$u_0^*=-\frac{8}{5}x_0$$

    - On calcule alors le coût optimal :
    $$
    J^*(x(2),2) = \frac{21}{10}x_0^2 = \frac{1}{2}\;x_0^T\;\frac{21}{5}\;x_0
    $$

##### Discussion

On constate que si l'on choisit **$R$ grand la commande optimale $u^*$ sera 'petite'**.

Rappel :
**On cherche à minimiser le $u$** donc il fait du sens de choisir un $R$ grand pour le sélectionner que des commandes petites

**Probleme :** 
**Si on force $u$ 'petit' alors on peut manquer d'énergie** pour amener notre système d'un état donné à un état final désiré

**Advantage :** 
Avoir un **$R$ grand garantie la non saturation** mais au prix d'avoir **moins d'influence sur la dynamique du système**

#### Solution Q2

Pour $x_{k+1} = 2 x_k + u_k$, déterminer la commande optimale $u^*$ qui stabilise $x$ et minimise :
$$
J(x_k,k) = \frac{1}{2} \sum_{k=0}^{T_{f-1}} \Big( x_k^T\;x_k + u_k^T\;R\;u_k \Big) + \frac{1}{2}\;x_{T_f}^T\;P_{T_f}\;x_{T_f}
$$
avec $T_f = 3$ et $R = 1$ et respectivement pour $P_{T_f}=0.1$, $P_{T_f}=10$ et $P_{T_f}=1000$ 

Déterminer $x_3$ en fonction de $L_0$,$L_1$, $L_2$ et $x_0$

##### Méthodes

1. Écrire les $u_k^*=-L_k\;x_k$
2. De $x_{k+1} = 2\;x_k + u_k$, calculer $x_3$ en fonction de $x_2$ et $x_1$
3. le 2. nous donne alors une formule pour calculer $x_3$ en fonction des $L_k$ et de $x_0$


##### Réponse

On a :
$$
x_3 = (2-L_2)\;x_2\\[0.2cm]
x_2 = (2-L_1)\;x_1\\[0.2cm]
x_1 = (2-L_0)\;x_0
$$

D'où,
$$
x_3 = (2-L_2)\;(2-L_1)\;(2-L_0)\;x_0
$$

Il ne reste plus qu'à faire les calculs selon les valeurs de $P_{t_f}$




> Notes du 2022/10/05 - End

---

> Notes du 2022/11/08 - Start




![](/assets/images/B1.COI.CM.BB20221107-01.png)

##### Discussion

Plus $P_{T_f}$ est grand, plus on converge vite (et aussi plus on consomme d'énergie).

## Commande LQ - Cas Continue

### Objectif

Trouver $u^*(x(t),t)$ qui minimise 
$$
\min_u J(u) = J(x_k,t_k) = \frac{1}{2} \int_{t_i}^{T_{f}} \big( x_t^T\,Q\,x_t + u_t^T\,R\,u_t \big)\;dt + \frac{1}{2} \, x_{T_f}^T\,P_{T_f}\,x_{T_f}
$$
sous la contrainte dynamique
$$
\begin{cases}
\dot x(t) &=& Ax(t) + Bu(t)\\
y(t) &=& Cx(t)
\end{cases}
$$

### Problème

$$
\min_u J(u) = \int_{t_i}^{T_f} L(x(t),u(t),t) dt + L_{T_f}(x_{T_f},T_f)
$$
sous la contrainte
$$
\dot x = F(x,u,t)
$$

D'après le principe de Bellman, ce problème se réduit à trouver une fonctionnelle $V(x(t),t)$ définie sur $[0,T_f]$ de $\mathbb{R}^n \rightarrow \mathbb{R}$ solution de l'équation de **Hamilton-Jacobi-Bellman (HJB)** :

$$
\begin{matrix}
& -\dot V(x(t),t) &=& \min_u L(x,u,t) &\\[0.2cm]
\iff & -\partial_t V &=& \min_u L(x,u,t) + \partial_x V\;F(x,u,t) & \textbf{HJB}  
\end{matrix}
$$

En effet,
$$
\dot V(x(t),t) = \partial_t V + \partial_x V\cdot\partial_t x = \partial_t V + \partial_x V \cdot\dot x = \partial_t V + \partial_x V \cdot F(x,u,t)
$$

Dans le cas général,
$$
V(x(t),t) = \int_{t_i}^{T_f} L(x,u,t) dt
$$

Dans le cas LQ,
$$
V(x(t),t) = \frac{1}{2} x_t^T\,P_t\,x_t = \frac{1}{2} \int_{t_i}^{T_{f}} \big( x_t^T\,Q\,x_t + u_t^T\,R\,u_t \big)\;dt + \frac{1}{2} \, x_{T_f}^T\,P_{T_f}\,x_{T_f}
$$


### Horizon fini

On considère $\dot x = A x + B u$ et un coût à minimiser : 
$$
J(u) = \frac{1}{2} \int_{t_i}^{T_{f}} \big( x_t^T\,Q\,x_t + u_t^T\,R\,u_t \big)\;dt + \frac{1}{2} \, x_{T_f}^T\,P_{T_f}\,x_{T_f}
$$

#### Problème

Déterminer une fonctionnelle définie sur $[0,T_f]$ solution de l'équation de **Hamilton-Jacobi-Bellman (HJB)** :
$$
-\dot V(x(t),t) = \frac{1}{2} \Big[\; x_t^T\,Q\,x_t + u_t^T\,R\,u_t \;\Big]
$$
où
$$
V(t)=\frac{1}{2} \int_{t_i}^{T_{f}} \big( x_t^T\,Q\,x_t + u_t^T\,R\,u_t \big)\;dt + \frac{1}{2} \, x_{T_f}^T\,P_{T_f}\,x_{T_f}
$$

#### Résolution

On pose: $V(x(t),t) = \frac{1}{2}\;x_{T_f}^T\,P_{T_f}\,x_{T_f}$

**HJB**

$$
\dot V(x(t),t) = -\frac{1}{2} x_{t}^T\,\dot P_{t}\,x_{t} -\frac{1}{2} \textcolor{purple}{\dot x_{t}}^T\,P_{t}\,x_{t} -\frac{1}{2} x_{t}^T\,P_{t}\,\textcolor{orange}{\dot x_{t}} = \frac{1}{2} \big(\; x_t^T\,Q\,x_t + u_t^T\,R\,u_t \;\big)\\[0.2cm]
\iff -\frac{1}{2} x_{t}^T\,\dot P_{t}\,x_{t} = \frac{1}{2} \big(\; x_t^T\,Q\,x_t + u_t^T\,R\,u_t \;\big) \textcolor{red}{+}\frac{1}{2} \textcolor{purple}{(Ax_t+Bu_t)}^T\,P_{t}\,x_{t} \textcolor{red}{+}\frac{1}{2} x_t^T\,P_{t}\,\textcolor{orange}{(Ax_t+Bu_t)}
$$

On regroupe les termes

...

puis on dérive **HJB** p.r.à $u$ pour trouver sa racine (c.à.d. résoudre en 0)

...

Il vient que 
$$
\begin{matrix}
&\partial_u \textbf{HJB} &=& 0\\[0.2cm]
\iff& \frac{1}{2} B^T\,P_t\,x_t + \frac{1}{2} x_t^{T}\,P_t\,B + R\,u_t &=& 0\\[0.2cm]
\iff& B^T\,P_t\,x_t + R\,u_t &=& 0
\end{matrix}
$$

On en déduit la solution suivante 
$$
u_t^* = - R^{-1}\,B^T\,P_t\,x_t
$$

On a obtenu un extremum maintenant il faut déterminer la condition sur pour que $u_t^*$ soit un minimum en dérivant **HJB** une deuxième fois :
$$
\partial_{u^2}^2 \textbf{HJB} = R > 0
$$

Remarque:
- Pour etre un min, il faut en plus que $R$ soit positive
- Or $R$ doit aussi être inversible et donc ne peut pas etre semi positive donc au max strictement positive (mais seuls qlqs matrices stric positive peuvent etre inversible)
    - si $R$ n'est pas inversible, il faudra appliquer un changement de base à l'aide de bonne matrice de passage pour obtenir la pseudo-inverse de $R$
    - mais dans ce cas il faudra refaire la preuve pour le nouveau critère $P^TRP$
- À noter que l'on a fait un choix au départ pour conditionner le critere selon la maximisation ou la minisation en mettant un **-** dehors ou dedans la fonctionnelle

Maintenant que l'on a $u_t^*$, il faut calculer $P_t$ directement (et non plus récursivement comme en discret) à l'aide de l'équation différentielle de Riccatti suivante :

$$
-\dot P_t = Q + A^T\,P_t + P_t\,A - P_t\,B\,R^{-1}\,B^T\,P_t
$$


...


La commande optimale est fonction linéaire de l'état :
$$
u_t^* = - R^{-1}\,B^T\,P_t\,x_t = -L_t\,x_t
$$
Avec $L_t$ le gain variable dans le temps où $P_t$ est solution de l'équation différentielle de Riccatti avec $P_t=Q_{T_f}$


### Horizon Infini

#### Problème

Minimiser le critère
$$
\min_u J(u) = \lim_{T_f\rightarrow\infty} \frac{1}{2}\, ...
$$

Dans le cas infini, la solution $P_t$ converge vers une constante P




> Notes du 2022/11/08 - End

---

> Notes du 2022/11/09 - Start



> À Rattraper !!! Voir les [Notes GEA du 2022/11/09](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/B1.COI.CM.NotesGEA.20221109.pdf)




> Notes du 2022/11/09 - End

---

> Notes du 2022/11/15 - Start

Vendredi 25 17h45


## Principe de maximisation de l'Hamiltonien (Pontryaguie)

### Cas Continue

Trouver $u^*(x(t),t)$ qui maximise l'Hamiltonien
$$
H(x(t),u,\lambda) = - L(x,u,t)+\lambda^T\;F(x,u,t)
$$
avec $\dot x = F(x,u,t)$

### Cas Discret

$$
H_{k+1} = - L(x,u,t)+\lambda^T_{k+1}\;F(x,u,t)
$$
avec $x_{k+1} = F(x,u,t)$

## Optimalité

### Cas Continue

Conditions d'optimalité $\iff$ minimiser le critère $J$ $\iff$ maximiser l'Hamiltonien

1. Condition finale $\quad \lambda^T_{T_f} = -x_{T_f}\;P_{T_f}$
2. $\dot\lambda = - \partial_x H$
3. $\dot x = \partial_\lambda H$

Recherche d'une commande optimale $\iff$ maximiser le $H$

1. $\partial_u H |_{u=u^*} = 0$
2. $\partial^2_{u^2} H |_{u=u^*} < 0$

### Cas Discret

Conditions d'optimalité (conditions du premier ordre d'Hamilton)

1. Condition finale $\quad \lambda_{T_f}^T = - x_{T_f}\;P_{T_f}$
2. $\lambda_k = - \partial_{x_{k}} H_{k+1}$
3. $x_{k+1} = \partial_{\lambda_{k+1}} H_{k+1}$

Commande optimale

1. $\partial_{u_k} H_{k+1} |_{u=u^*} = 0$
2. $\partial^2_{u_k^2} H_{k+1} |_{u=u^*} < 0$

### Horizon fini/infini

$$
\forall t, H = cste
$$

$$
\lim_{t\longrightarrow\infty} H = 0
$$


## Application PMP à la commande LQ

Soit un système $x_{k+1} = Ax_k + Bu_k$, on recherche la commande optimale LQ qui minimise le critère suivant :
$$
L(x,u,k) = \frac{1}{2}\Big( x_k^TQ_kx_k + u_k^TR_ku_k \Big)
$$
avec $Q_j = Q_j^T\geq 0 \quad P_j=P_j^T\geq 0 \quad R_j=R_j^T> 0$

On pose l'Hamiltonien :
$$
H(x,u,k+1) = -\frac{1}{2}\Big( x_k^TQ_kx_k + u_k^TR_ku_k \Big) + \lambda_k^T(Ax_k + Bu_k)
$$

Conditions d'optimalités vérifiées :

1. Condition finale $\quad \lambda_{T_f}^T = - x_{T_f}\;P_{T_f}$
2. Conditon extremum $\quad \partial_{u_k} H_{k+1} |_{u=u^*} = 0$
3. Conditon maximum $\quad \partial^2_{u_k^2} H_{k+1} |_{u=u^*} < 0$
4. Resultat $\quad \lambda_k = - \partial_{x_{k}} H_{k+1}$
5. Resultat $\quad x_{k+1} = \partial_{\lambda_{k+1}} H_{k+1}$

Il vient que
$$
x_{k+1} = \partial_{\lambda_{k+1}} H_{k+1} = Ax_k + Bu_k\\[0.2cm]
\lambda_k = - \partial_{x_{k}} H_{k+1} = A^T\lambda_{k+1}-Q_k x_k
$$

Or
$$
\partial_{u_k} H_{k+1} |_{u=u^*} = 0 \implies -R_k u_k + B^T\lambda_{k+1} |_{u=u^*} = 0
$$
Donc
$$
u_k^* = R_k^{-1}B^T\lambda_{k+1}\\[0.2cm]
\partial^2_{u_k^2} H_{k+1}= -R_k < 0
$$

On s'assure d'avoir la commande optimale :
$$
u^* = R_k^{-1}B^T\lambda_{k+1}\\[0.2cm]
\lambda_{T_f} = - P_{T_f}x_{T_f}
$$

On pose $\lambda_k = -P_kx_k$
$$
u_k^* = R_k^{-1}B^T\lambda_{k+1} = R_k^{-1}B^TP_{k+1}x_{k+1}
$$
Du coup,
$$
Ru_k^* = -B^TP_{k+1}x_{k+1} = -B^TP_{k+1}(Ax_k+Bu_k^*)
$$
Ainsi,
$$
(R+B^TP_{k+1}B)u_k^* = -B^TP_{k+1}Ax_k
$$
Il vient que
$$
u_k^* = -\textcolor{orange}{(R+B^TP_{k+1}B)\cdot(B^TP_{k+1}A)}\;x_k = - \textcolor{orange}{L_{k+1}}\;x_k
$$

Maintenant, il nous reste à calculer $P_k$, or nous savons que 
$\quad\lambda_k = A^T\lambda_{k+1} - Q_kx_k\quad$ et on avait posé $\quad\lambda_k = -P_kx_k\quad$ et $\quad\lambda_{T_f} = -P_{T_f}x_{T_f}$

Donc,
$$
\begin{matrix}
- P_kx_k &=& A^T\lambda_{k+1} - Q_kx_k\\[0.2cm]
- P_kx_k &=& A^T\big(P_{k+1}x_{k+1}\big) - Q_kx_k\\[0.2cm]
- P_kx_k &=& A^T\Big(P_{k+1}(Ax_k + Bu_k^*)\Big) - Q_kx_k\\[0.2cm]
- P_kx_k &=& A^T\Big(P_{k+1}\big(Ax_k + B(-L_{k+1}x_k)\big)\Big) - Q_kx_k\\[0.2cm]
\end{matrix}
$$

Ainsi,
$$
P_k = A^TP_{k+1}A - A^TP_{k+1}BL_{k+1}+Q_k
$$


## Exercice

Soit $\quad\dot x = -x+u\quad$,

Déterminer la commande optimale qui minimise
$$
J=\frac{1}{2}\int_{0}^1\big(3x^2+u^2\big)dt
$$
sous la contrainte de la dynamique du système sachant que le système évolue de $x=0$ à $t_0$ vers $x=2$ à $t=1$

> Si plusieurs critère, alors la solution sera une intersection des solutions de chaque critère

![](/assets/images/B1.COI.CM.NotesRKA.20221114.SolExo.png)



> Notes du 2022/11/15 - End

---

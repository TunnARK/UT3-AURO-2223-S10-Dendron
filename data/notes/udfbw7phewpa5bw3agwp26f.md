
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut

---

> Notes du 2022/12/02 - Start



# IV- Linéarisation entrée-sortie (Dynamique Interne)

## IV-1. Définition du degré

On suppose le système NL suivant :
$$
\begin{cases}
\dot x = f(x) + g(x)\,u\\
y = h(x)
\end{cases}
$$

### Définition

Un système siso admet un **degré relatif** $r$ si
$$
\begin{matrix}
\begin{cases}
L_g\,L_f\,h(x) = 0 \quad 0\leq i \leq(r-1)\\
L_g\,L_f^{r-1}\,h(x) \neq 0 \quad \forall x\in\Omega
\end{cases}\\
\iff
\begin{cases}
\dot\mu_1 = \mu_2\\
\vdots\\
\dot\mu_r = L_g....
\end{cases}
\end{matrix}
$$

Attention: cette définition est **locale**

### Explication
$$
...
$$

### Remarque
???
- Dans le cas d'un système linéaire défini par sa fct de transfert $r = n - m$ où $n$ est le nombre de pôles et $m$ le nombre de zéros

## IV-2. La forme normale

### En théorie

Une fois définie le **degré relatif** $r$, on peut proposer un **difféomorphisme** pour mettre en évidence les dérivées successives de $y$ (jusqu'à $y^{r-1}(t)$).

#### La notation de Slotine $\gamma(i)$

$$
\begin{cases}
\mu_1 = y(t) = h(x)\\
\mu_2 = \dot y(t) = L_f\,h(x)\\
\vdots\\
\mu_r = y^{r-1}(t) = L_f^{r-1}\,h(x) + L_g\,L_f^{r-1}\,h(x)\,u
\end{cases}
$$

On rajoute un certain nombre d'états $\phi_1(x)\dots\phi_{n-r}(x)$ pour compléter et obtenir ainsi :
$$
\begin{cases}
\mu_1\\
\vdots\\
\mu_2\\
\qquad\qquad\qquad \text{constitue un difféomorphisme}\\
\phi_1\\
\vdots\\
\phi_{n-r}\\
\end{cases}
$$

Il suffit de montrer que la Jacobienne de la transformation est non-singulière soit que $\{\nabla\mu_1 \dots \nabla\mu_r \nabla\phi_1 \dots \nabla\phi_{n-r}\}$ sont linéairement indépendants.


#### Début de preuve

Montrer que $\{\nabla\mu_1 \dots \nabla\mu_r \nabla\phi_1 \dots \nabla\phi_{n-r}\}$ son lin. indép. (par l'absurde).

Supposons qu'ils existent ${\alpha_1(x)\dots\alpha_r(x)}$ non identiquement nul.
$$
\begin{matrix}
&\alpha_1(x)\,\nabla\mu_1(x)+\dots+\alpha_r(x)\,\nabla\mu_r(x) = 0\\
\implies&\big(\alpha_1(x)\,\nabla\mu_1(x)+\dots+ \alpha_r(x)\,\nabla\mu_r(x)\big)\cdot g(x) = 0\\
\implies&\alpha_1(x)\,\nabla\mu_1(x)\,g(x)+\dots+\alpha_r(x)\,\nabla\mu_r\,g(x) = 0\\
\end{matrix}
$$
!!!
or
$$
\nabla\mu_1\,g(x) = L_g\,h(x) = 0
$$
idem jusqu'à $\nabla\mu_{r-2}\,g(x)$ et donc on a que:
$$
\alpha_r(x)\,\nabla\mu_r(x)\,g(x) = 0
$$
or $\nabla\mu_r(x)\,g(x)\neq0$ et donc $\alpha_r(x) = 0$ 

Continuons avec la même méthode pour montrer que $\alpha_{r-1}=0$
$$
\begin{matrix}
&\big(\alpha_1(x)\,\nabla\mu_1(x)+\dots+\alpha_r(x)\,\nabla\mu_r(x)\big)\cdot[f\,g] = 0\\
\implies&\alpha_1(x)\big(L_f\,L_g\,\mu_1-L_g\,L_f\,\mu_1\big)+\dots+\alpha_{r-1}(x)\,L_{[f\,g]}
\end{matrix}
$$

...


#### Remarque
- $\nabla\mu_1$ est orthogonale à $g$, $adj_f\,g$, $\dots$, $adj_f^{r-2}\,g$
- $\nabla\mu_2$ est orthogonale à $g$, $adj_f\,g$, $\dots$, $adj_f^{r-3}\,g$
- $\quad\vdots$
- $\nabla\mu_1$ n'est pas orthogonale à $g$

#### Géométriquement

![](/assets/images/B2.CNL.CM.P4S2.Geometriquement.png)

La dimension de l'hyperplan orthogonale à $g$ est de dimension $n-1=r-1+n-r$.

On pourrait alors considérer une "base" de cette hyperplan comme suit :
$$
\nabla\mu_1 \dots \nabla\mu_{r-1}\;\nabla\phi_1\dots\nabla\phi_{n-r}
$$

Un difféomorphisme serait alors :
$$
\begin{cases}
\mu_1\\
\vdots\\
\mu_2\\
\phi_1\\
\vdots\\
\phi_{n-r}\\
\mu_r
\end{cases}
$$

Il reste à calculer les $\nabla\phi$ tel que $\qquad\nabla_phi_i(x)\,g(x) = 0 \qquad \forall i\in{1,\dots,n-r}\qquad$ soient lin. indép. p.r.à $\nabla\mu_1\dots\nabla\mu_{r-1}$ et leur existence est garanti par le théorème de Frobinius.

Supposons que
$$
\begin{cases}
\mu_1\\
\vdots\\
\mu_2\\
\qquad\qquad\qquad \text{constitue un difféomorphisme}\\
\phi_1\\
\vdots\\
\phi_{n-r}\\
\end{cases}
$$
Alors le système NL s'écrit :
$$
\begin{cases}
\dot\mu_1(x) = \mu_2\\
\vdots\\
\dot\mu_r(x) = L_f^r\,\mu_1(x) + L_g\,L_f^{r-2}\,\mu_1(x)\,u\\
\dot\phi(x) = \omega(\phi,\mu)
\end{cases}
$$

La forme normale s'écrit alors :
$$
\begin{cases}
\dot\mu_1(x) = \mu_2\\
\vdots\\
\dot\mu_r(x) = a(\phi,\mu) + b(\phi,\mu)\,u\\
\dot\phi(x) = \omega(\phi,\mu)
\end{cases}
$$
avec $b(\phi,\mu)\neq0$

### Exemple

Considérons le système suivant :
$$
\begin{cases}
\dot x_1 = -x_1 + e^{2x_2}\,u\\
\dot x_2 = 2x_1x_2 + \sin x_2 + \frac{1}{2}u\\
\dot x_3 = 2x_2\\
y = x_3
\end{cases}
$$

1. Calculer le degré relatif
2. Trouver $\phi_1$
3. Proposer un chgmt de variable permettant de touver la forme modale

...
<!--image1-->

## IV-3. La dynamique des zéros

On choisit 
$$
\begin{cases}
\mu_1(0) = 0\\
\vdots\\
\mu_r(0) = 0
\end{cases}\qquad\text{et}\qquad v = 0
$$

Alors $\mu(t) = e^{At}\mu(0) = 0 \quad \forall t>0$

On trouve la commande de $u(t) = \frac{\;-a(\omega,\phi)\;}{b(\omega,\phi)}$ tel que la sortie et les dérivées successives jusqu'au degré relatif égale à 0.

La **dynamique des zéros** s'écrit : $\qquad\dot\phi = \omega(\phi,0)$

### Définition

On dit que le système est **à minimum de phase** si la dynamique des zéros est asymptotiquement stable.

### Rappel (en lénaire)

...
<!--image2-->

- On réalise le bouclage (soit trouver des espaces d'états)
- On choisit  :
    $$
    \begin{cases}
    \mu_1 = y(t)\\
    \vdots\\
    \mu_{n-m} = y^{n-m-1}(t)\\
    \end{cases}
    $$
    ainsi
    $$
    \dot \mu = 
    \begin{bmatrix}
    0 & 1 & 0 & \dots & 0\\
    \vdots & &\ddots & & \vdots\\
    \vdots & & & & 1\\
    0 & \dots & \dots & \dots & 0
    \end{bmatrix}
    +
    \begin{bmatrix}
    0\\ \vdots\\ 0\\ 1\\
    \end{bmatrix}
    \cdot
    \Big(e -\lambda^T\mu\Big)
    $$
- On choisit $m$ états $\omega_1 \dots \omega_m$ et on obitient
    $$
    \begin{cases}
    \dot\omega = A_{\omega} \omega + B_{\omega}y\\
    y_{\omega} = C_{\omega} \omega
    \end{cases}
    $$
- Le système s'écrit
    $$
    \begin{cases}
    \dot\mu = A_{\omega} \omega + B_{\omega}\Big(u -C_{\omega}\omega-\lambda^T\mu\Big)\\
    \dot\omega = A_{\omega} \omega + B_{\omega}C\mu \qquad \text{avec} \quad C = [1\;0 \dots 0]
    \end{cases}
    $$
    si on choisit $u=\lambda^T\mu + C_{\omega}+v$, on a :
    $$
    \begin{cases}
    \dot\mu = A_{c} \omega + B_{c}v\\
    \dot\omega = A_{\omega} \omega + B_{\omega}C\mu \qquad \text{avec}\\
    y = C\mu
    \end{cases}
    $$
    où $A_{\omega}$ est la **dynamique des zéros** (les vp de $A_{\omega}$ sont les zéros de $G$)

### Rappel minimum de phase

![](/assets/images/B2.CNL.CM.Extra.RappelMinimumPhase.png)

## IV-4. Résultats sur la stabilité

On suppose le système sous forme modale :
$$
\begin{cases}
\dot\mu_1(x) = \mu_2\\
\vdots\\
\dot\mu_r(x) = v\\
\dot\phi(x) = \omega(\phi,\mu)
\end{cases}
$$
On choisit $\;v=-\lambda^T\mu\;$ tel que la matrice $
\begin{bmatrix}
0 & 1 & 0 & \dots & 0\\
\vdots & &\ddots & & \vdots\\
\vdots & & & & 1\\
-\lambda_1 & \dots & \dots & \dots & -\lambda_r
\end{bmatrix}
$ soit **Hurwitz**

### Théorème

Si la dynamique des zéros est **localement asymptotiquement stable**, alors le système asservi est **localement asymptotiquement stable**.

> Attention: (Gros problème) ce théorème ne donne aucune garantie sur le bassin d'attraction !

### Exemple

Considérons
$$
\begin{cases}
\dot\epsilon_1(x) = \epsilon_2\\
\dot\epsilon_2(x) = v\\
\dot\eta(x) = \frac{1}{2} \big(1+\epsilon_2\big)\eta^2
\end{cases}
$$

Posons $\;v=-\alpha_1\epsilon_1-\alpha_2\epsilon_2\;$ et $
\begin{bmatrix}
0&1\\ -\alpha_1 & \alpha_2
\end{bmatrix}
$ est Hurwitz alors le système bouclé est LAS car $\dot\eta = -\frac{1}{2}\eta^3$ est GAS

## IV-5. Tracking et dynamique inverse

On définit une **trajectoire** $y_d(t) = \begin{bmatrix}y_d(t)\\\vdots\\y_d^{(r)}(t)\end{bmatrix}$ et l'**erreur de tracking** $\;\tilde\mu = \mu(t)-\mu_d(t)$.
$$
\begin{cases}
\dot{\tilde\mu}_1 = \tilde\mu_2\\
\vdots\\
\dot{\tilde\mu}_r = ...
\end{cases}
$$

Il est aisé de choisir $u$ pour que $\tilde\mu(t)$ tends vers 0 exponentiellement.

### Théorème

Supposons que la solution $\begin{cases}\dot\phi_d = \omega\big(\phi_d,\mu_d(t)\big)\\\phi_d=0\end{cases}$ **existe** et est **bornée** et **uniformément AS** alors le système asservi est tel que $\tilde\mu(t)$ tends vers 0 pour l'horizon infini.

Imaginons que $y(t) \equiv y_d(t)$ et dérivons :
$$
y^{(r)}(t) = y_d^{(r)}(t) = a(y_d(t),\phi) + b(\mu_d(t),\phi)\,u
$$
Considérons alors
$$
\begin{cases}
u(t) = \dfrac{\;y_d^{(r)}(t) - a(y_d(t),\phi)\;}{b(\mu_d(t),\phi)}\\
\dot\phi = \omega(\phi,\mu_d(t))\\
\phi(0) = ??
\end{cases}
$$

> cf Book: (Lyapunov: Kokotovic / Sepulchire) / Isodore




> Notes du 2022/12/02 - End

---
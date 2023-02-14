> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par S. Fergani

---

> Notes du 2022/11/25 - Start




# Introduction

Soit un système 
$$
\begin{cases}
\dot x = A\;x + B\;u\\
y = C\;x
\end{cases}
$$

Posons
$$
e = y_{ref} - y
$$
où $y_{ref}$ est la référence/trajectoire à suivre sur $[0,T_f]$.

Si $y_{ref} = 0$, alors il s'agit d'un problème de régulation donc se référer aux cours du M1.

Si $y_{ref} \neq 0$ (ou bien constante ou bien variable), alors il faut ajouter un **précompensateur** et il s'agit donc d'un **problème de poursuite**.

# Problème de poursuite optimale

## Horizon Infini avec $y_{ref}\;cste$

### Pose du problème

On considère la commande $\quad u_t = - L_t\;x_t + h\;v_{ref} \quad$ où :
- $L = R^{-1}\;B^T\;P \quad$ est la solution de l'équation de Ricatti pour la commande LQ ;

    Pour trouver la matrice $P$, aplliquer :
    $$
    0 = Q + A^T\;P + P\;A - P\;B\;R^{-1}\;B^T\;P
    $$
- $h\;$ est le précompensateur calculé de façon à amener une erreur de poursuite nulle.

### Synthèse du précompensateur

Cette commande stabilise le système en boucle fermée.

En régime permanent, on a $\quad\dot x = 0\quad$ et donc :
$$
\begin{matrix}
&\begin{cases}
\dot x = 0 = \big(\;A - B\;L\;\big)\;x_t + B\;h\;v_{ref}\\
y = C\;x_t
\end{cases}\\
\iff&
\begin{cases}
\dot x_t = -\big(\;A - B\;L\;\big)^{-1}\;B\;h\;v_{ref}\\
y = C\;x_t
\end{cases}\\
\iff&
\begin{cases}
\dot x_t = -\big(\;A - B\;L\;\big)^{-1}\;B\;h\;v_{ref}\\
y = -C\;\big(\;A - B\;L\;\big)^{-1}\;B\;h\;v_{ref}
\end{cases}\\
\end{matrix}
$$

À noter que pour avoir l'inversibilité, il ne faut pas que les valeurs propres soient pas nulles.

Ainsi, on obtient la fonction de transfert suivante :
$$
\dfrac{\;y(\infty)\;}{\;v_{ref}\;} = -C\;\big(\;A - B\;L\;\big)^{-1}\;B\;h
$$

Or,
$$
\dfrac{\;y(\infty)\;}{\;v_{ref}\;} = 1
$$

Donc, on a :
$$
h = -\Big(\;C\;\big(\;A - B\;L\;\big)^{-1}\;B\;\Big)^{-1}
$$

### Minimisation du critère

Posons, $\quad e_t = \big(y_{ref} - y_t\big)\quad$

$$
\begin{matrix}
\min_u J(u) &=& \lim_{T_f\rightarrow\infty}\;\frac{1}{2}\;\int_{T_i}^{T_f} \Big( e_t^T\,Q\,e_t + u_t^T\,R\,u_t \Big) dt\\
&=& \lim_{T_f\rightarrow\infty}\;\frac{1}{2}\;\int_{T_i}^{T_f} \Big( \big(y_{ref} - y_t\big)^T\,Q\,\big(y_{ref} - y_t\big) + u_t^T\,R\,u_t \Big) dt \\
&=& \lim_{T_f\rightarrow\infty}\;\frac{1}{2}\;\int_{T_i}^{T_f} \Big( \big(y_{ref} - (C\;x_t)\big)^T\,Q\,\big(y_{ref} - (C\;x_t)\big) + u_t^T\,R\,u_t \Big) dt \\
&=& \lim_{T_f\rightarrow\infty}\;\frac{1}{2}\;\int_{T_i}^{T_f} \Big( (C\;x_t)^T\,Q\,(C\;x_t) + u_t^T\,R\,u_t \Big) dt - \lim_{T_f\rightarrow\infty}\;\frac{1}{2}\;\int_{T_i}^{T_f} \Big( (C\;x_t)^T\,Q\,(C\;x_t) + u_t^T\,R\,u_t \Big) dt ....\\
...\\

\end{matrix}
$$

On prend la fonctionnelle :
$$
V\big(\;x(t),t\;\big) = \frac{1}{2}\;\big(\; x_t^T\,P\,x_t + y_t^T\,x_t + h_t\;\big)
$$
sous la contrainte de
$$
\begin{cases}
\dot x = A\;x + B\;u\\
y = C\;x
\end{cases}
$$

On cherche à avoir l'équation $HJB$ suivante :
$$
-\dot V\big(\;x(t),t\;\big) = \textcolor{red}{\frac{1}{2}\;\big(\; x_t^T\,C^T\,Q\,C\,x_t + u_t^T\,R\,u_t \;\big)} - \textcolor{green}{y_{ref}^T\,Q\,C\,x_t} + \textcolor{blue}{\frac{1}{2}\;y_{ref}^T\,Q\,y_{ref}}
$$
où les termes représentent respectivement le $\textcolor{red}{\text{coût état+commande}}$, le  $\textcolor{green}{\text{coût de poursuite}}$ et le  $\textcolor{blue}{\text{coût final}}$.

Maintenant, utilisant la `chain rule` pour calculer $\dot V$, on obtient :
$$
-\dot V\big(\;x(t),t\;\big) = -\frac{1}{2}\;\big(\; \dot x_t^T\,P\,x_t\;\big) -\frac{1}{2}\;\big(\; x_t^T\,P\,\dot x_t\;\big) -\frac{1}{2}\;\big(\; x_t^T\,\dot P\,x_t\;\big) - y_t^T\,\dot x_t - \dot h_t
$$

Or,
- $h$ est constante donc $\dot h = 0$ (précompensateur de trajectoire constante)
- $y_t$ est constante donc $\dot y_t = 0$ (pondération de trajectoire constante)
- $\dot P = 0$ (car on est à horizon fini)

Il vient que :
$$
-\dot V\big(\;x(t),t\;\big) = -\frac{1}{2}\;\big(\; \dot x_t^T\,P\,x_t\;\big) -\frac{1}{2}\;\big(\; x_t^T\,P\,\dot x_t\;\big)  - y_t^T\,\dot x_t
$$
$$
-\dot V\big(\;x(t),t\;\big) = -\frac{1}{2}\;\big(\; x_t^T\,\big(\; A^T\,P_t + P_t\,A \;)\,x_t\;\big) - u_t^T\,B^T\,P_t\,x_t - y^T\,A\,x_t - y_t^T\,B\,u_t
$$

On peut maintenant comparer les deux membres de l'équation $HJB$:
$$
-\frac{1}{2}\;\big(\; x_t^T\,\big(\; A^T\,P_t + P_t\,A \;)\,x_t\;\big) - u_t^T\,B^T\,P_t\,x_t - y^T\,A\,x_t - y_t^T\,B\,u_t = \textcolor{red}{\frac{1}{2}\;\big(\; x_t^T\,C^T\,Q\,C\,x_t + u_t^T\,R\,u_t \;\big)} - \textcolor{green}{y_{ref}^T\,Q\,C\,x_t} + \textcolor{blue}{\frac{1}{2}\;y_{ref}^T\,Q\,y_{ref}}
$$

Ceci nous donne bien $0$.

On peut alors poursuivre en imposons que :
$$
\partial_u HJB |_{u=u^*} = -R\,u^* - y^T\,B - B^T\,P_t\,x_t = 0
$$

Ainsi, on en déduit la commande optimale :
$$
u^* = R^{-1}\,y^T\,B - R^{-1}\,B^T\,P_t\,x_t
$$

Il ne reste plus qu'à vérifier qu'il s'agisse bien d'un minimum. En effet,
$$
\partial_{u^2}^2 HJB |_{u=u^*} = -R < 0
$$

À présent que nous avons la commande optimale, nous pouvons injecter $u^*$ dans $HJB$ ce qui nous donne :
$$
...
$$

On en déduit le système suivant
$$
\begin{cases}
...
\end{cases}
$$

Résolvons :
- de $(1)$, on tire la matrice $P_t$ ;
- de $(2)$, on trouve $g_t = y^T\,Q\,C\,\big(\;A-B\,L_t\;\big)^{-1}$ ; et
- de $(3)$, on obtient la condition nécessaire pour la poursuite optimale :
$$
g^T\,B\,R^{-1}\,B^T\,g_t = y_{ref}^T\,Q\,y_{ref}
$$

Conclusion:

On a trouvé une commande optimale pour suivre une trajectoire constante :
$$
u^* = - R^{-1}\,B^T\,P_t\,x_t - R^{-1}\,B^T\,g_t
$$

## Horizon Infini avec $y_{ref}\;variable$

> À faire à la maison



> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat et M. Thaix

---

> Notes RKA du 2023/01/30 - Start



# Sommaire

![](/assets/images/B3.RIA.CM.Slide-53.png)

# I- Introduction

## Problématique

![](/assets/images/B3.RIA.CM.Slide-54.png)

## Définitions

![](/assets/images/B3.RIA.CM.Slide-55.png)

## Contraintes

![](/assets/images/B3.RIA.CM.Slide-56.png)

## Schéma général

![](/assets/images/B3.RIA.CM.Slide-57.png)


## Problèmes dans l'espace opérationnel

![](/assets/images/B3.RIA.CM.Slide-58.png)

# II- Calcul de GM dans l'espace généralisé

## II-1. Loi Polynomiale

![](/assets/images/B3.RIA.CM.Slide-59.png)

### Problématique

On cherche
$$
q(t) = a_0 + a_1\;t + \dots + a_n\;t^n
$$
où l'on ne connaît pas $n$ ni les $a_i$
sous les contratintes
$$
q(0) = q_i\\
\dot q(0) = \dot q_i\\
q(t_f) = q_f\\
\dot q(t_f) = \dot q_f\\
$$

$n$ dépend du nb de contraintes sur $q(t)$

Vu qu'on a 4 contraintes, on en déduit que $n = 3$ et donc il faut déterminer 4 $a_i$.

Le problème deveint alors:
![](/assets/images/B3.RIA.CM.GM.BB20230130-01.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-02.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-03.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-04.png)

Il ne reste plus qu'à déterminer $t_f$.

### Calcul du $t_f$

![](/assets/images/B3.RIA.CM.Slide-60.png)

Cette variable est en fonction de la vitesse maximale $K_v$ et de l'accélération maximale $K_a$.

Pour la contrainte de vitesse:
![](/assets/images/B3.RIA.CM.GM.BB20230130-05.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-06.png)

On a que $t_f$ ne doit pas être plus petit que $\frac{\,3\,}{2}\frac{\;\Delta q\;}{K_v}$.

Pour la contrainte d'accélération:
![](/assets/images/B3.RIA.CM.GM.BB20230130-07.png)

On a que $t_f$ ne peut pas être plus petit que $\sqrt{6\;\frac{\;\Delta q\;}{K_v}\;}$

Du coup, $\quad t_f = \max\Big(\; \frac{\,3\,}{2}\frac{\;\Delta q\;}{K_v} , \sqrt{6\;\frac{\;\Delta q\;}{K_v}\;} \;\Big)$

### Discontinuité en accélération

![](/assets/images/B3.RIA.CM.Slide-61.png)

## II-2. Profile de vitesse trapezoidal

> Keywords: loi bang-bang

![](/assets/images/B3.RIA.CM.Slide-62.png)

$\tau$ représente les instants de communtation (l'instant auquel on augmente/maintient/diminue la vitesse).

Calcul des $\tau$:
![](/assets/images/B3.RIA.CM.GM.BB20230130-08.png)

Il ne nous reste plus qu'à calculer le $t_f$. Or, l'aire sous la courbe de $\dot q$ correspond à $\Delta q$. D'où,
![](/assets/images/B3.RIA.CM.GM.BB20230130-09.png)

Terminons:
![](/assets/images/B3.RIA.CM.GM.BB20230130-10.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-11.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-12.png)

À qu'il n'est pas possible de passer d'une vitesse nulle à une vitesse non nulle instantanément (car ceci requiererait une accélération infinie).

![](/assets/images/B3.RIA.CM.Slide-64.png)

## II-3. Synchronisation entre les axes

![](/assets/images/B3.RIA.CM.Slide-65.png)
![](/assets/images/B3.RIA.CM.Slide-66.png)
![](/assets/images/B3.RIA.CM.Slide-67.png)

Sur les robots de TPs, le profile trapézoidale s'implémente sur l'accélération.

Du coup le robot doit réaliser le calcul des $\tau_i$ en plus de ceux liés au modèle MGI à chaque période. (on est en temps réel dur).

## II-4. Points de passage

![](/assets/images/B3.RIA.CM.Slide-68.png)
![](/assets/images/B3.RIA.CM.GM.BB20230130-13.png)

## Remarque

En général, on donne une loi en $\dot q$ pour les vitesses faibles. Mais pour les vitesses grandes, les discontinuités en accélération générées par le profile trapézoidale en vitesse va causer des vibrations sur la structure. Dans ce cas, on utilise le profile trapézoidale sur l'accélération. Ce qui des portions parabolique sur la vitesse entre les passages linéaires, comme suit:
![](/assets/images/B3.RIA.CM.GM.BB20230130-14.png)

## Question typique Examen 

![](/assets/images/B3.RIA.CM.GM.BB20230130-15.png)



> Notes RKA du 2023/01/30 - End

---
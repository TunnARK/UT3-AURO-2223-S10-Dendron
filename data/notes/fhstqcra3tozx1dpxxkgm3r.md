
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par V. Cadenat

---

> Notes RKA du 2023/01/19 - Start



![](/assets/images/B3.RIA.MDC.Slide-01.png)


# I- Introduction

![](/assets/images/B3.RIA.MDC.Slide-02.png)

## Problématique

![](/assets/images/B3.RIA.MDC.Slide-03.png)

Modèle géométrique utile mais insuffisant pour réaliser une tâche vu qu'il ne présente pas de mouvement, d'où l'utilité du Modèle Cinématique.

Il existe deux modèles cinématique :
- le MCD - Modèle Cinématique Direct qui part de l'évolution de la configuration $\dot q$ pour exprimer l'évolution en $\dot x$ ; et
- le MCI - Modèle Cinématique Inverse qui part de l'évolution en $\dot x$ pour donner l'évolution de la configuration $\dot q$

Le modèle différentiel se structure de la même façon mais avec des unités infinitésimales $dq$ et $dx$ qui représentent resp. le déplacement élémentaire sur les articulations et l'OT.

![](/assets/images/B3.RIA.CM.MDC.BB20230119-02.png)

Remarque:
- On retrouve le MC dans la génération de trajectoire et la commande de bras manipulateurs.
- Mais Attention le MC ne prend pas en compte les effets dynamiques (inerties/frottements) !
- Ceci a pour concéquence que l'on ne peut pas autoriser le BM  de se déplacer à de grande vitesse.

## Structure du MC/MD

![](/assets/images/B3.RIA.CM.MDC.BB20230119-04.png)

Remarque:
- $dim(J) = (m,n)$ donc pas forcément carrée
- $J$ est fonction de $q$
- MDD est un système linéaire en $dq$
- $dx = J(q)\;dq$

Résoudre le syst. lin. pour trouver $dq$ donne le MDI

Le MCD est : $\dot x = J(q)\;\dot q$

Enfin, calculer le MDD revient à calculer le MCD et donc à calculer $J(q)$.

## Comment calculer $J$ ?

![](/assets/images/B3.RIA.CM.MDC.BB20230119-06.png)

Calcul numérique est très util pour les robots complexes (plusieurs bras) mais il reste basé sur le calcul analytique.

# II- Calcul de $J$

## II-1. Notions fondamentales

![](/assets/images/B3.RIA.CM.MDC.BB20230119-07.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230119-08.png)

- $d\overrightarrow{p}_{(0)}$: différentielle de position de l'OT
- $d\overrightarrow{\phi}_{(0)}$: différentielle d'orientation de l'OT

2 étapes:
- des $dq_i$ on déduit $d\overrightarrow{p}_{(0)}$ et $d\overrightarrow{\phi}_{(0)}$
- de $d\overrightarrow{p}_{(0)}$ et $d\overrightarrow{\phi}_{(0)}$ on obtient $dx$

![](/assets/images/B3.RIA.CM.MDC.BB20230119-09.png)

> La rotation est le mouvement nécessaire pour obtenir une certaine orientation.

## II-2. De $dq$ vers les différentiels de pos./orient.

### II-2.1) Seule la liaison $L_k$ bouge de $dq_k$

Si $L_k$ bouge de $dq_k$ alors l'OT se déplace de $d\overrightarrow{p}_{k}$ et $d\overrightarrow{\phi}_{k}$

**Cas:** $L_k$ est **prismatique**

![](/assets/images/B3.RIA.MDC.Slide-04.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230119-11.png)

Quand la liaison $L_k$ se déplace :
- $O_k$ devient $O_{k'}$
- $O_n$ devient $O_{n'}$
- mais $O_0$ reste $O_{0}$.

On utilise alors la relation de Chasles pour trouver $d\overrightarrow{p}_{k}$:
![](/assets/images/B3.RIA.CM.MDC.BB20230119-12.png)


**Cas:** $L_k$ est **rotoide**

![](/assets/images/B3.RIA.MDC.Slide-05.png)

Quand la liaison $L_k$ se déplace :
- $O_0$ reste $O_{0}$
- $O_k$ reste aussi $O_{k}$
- seul $O_n$ devient $O_{n'}$.

Même idée que précédemment:
![](/assets/images/B3.RIA.CM.MDC.BB20230119-13.png)

**Bilan:**
![](/assets/images/B3.RIA.CM.MDC.BB20230119-14.png)

Les $\sigma_k$ sont les mêmes que pour les params de D/H (ils indiquent si la liaison est rotoide ou prismatique).

### II-2.2) Si toutes les liaisons se déplacent ?

![](/assets/images/B3.RIA.MDC.Slide-06.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230119-15.png)

La matrice **Jacobienne vectorielle** se lit physiquement ainsi :
- chaque colonne indique la contribution en translation et rotation de la liaison concernée
- chaque ligne correspond à la contribution de toute les liaisons sur un déplacement
    - par exemple pour la première ligne il s'agit de toutes les contributions de chaque liaison en translation sur seulement l'axe $x$

![](/assets/images/B3.RIA.CM.MDC.BB20230119-16.png)

Cependant plus on s'éloigne de $O_0$ plus les calculs deviennent compliqués puisque les repères au bout du robot dépendent des liaisons précédentes.

Pour simplifier les calculs (historiquement on cherchait à optimiser les calculs algébirques), on choisit de calculer la **matrice Jacobienne préférentielle**. L'expérience montre que si l'on choisit un repère de référence à $j = E(n/2)$ (partie entière inférieure) et une origine à $i=j+1$ on obtient la Jacobienne la plus facile à calculer.

![](/assets/images/B3.RIA.CM.MDC.BB20230119-17.png)
![](/assets/images/B3.RIA.MDC.Slide-07.png)

![](/assets/images/B3.RIA.MDC.Slide-08.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230119-18.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230119-19.png)

Preuve entre la Jacobienne vectorielle et la référentielle : 

![](/assets/images/B3.RIA.CM.MDC.Slide-08-Preuve.png)


> Notes RKA du 2023/01/19 - End

---

> Notes RKA du 2023/01/24 - Start




# Rappels

![](/assets/images/B3.RIA.CM.MDC.BB20230124-1.png)
- $\dot X = J(q) \dot q$ dépend de la configuration car 
- jacobienne géométrique: de $x$ vers $\dot q$
- jacobienne analytique: de $\dot q$ vers $x$
![](/assets/images/B3.RIA.CM.MDC.BB20230124-2.png)


# III- Exemple MDD sur RRPRRR

## Calcul de $J$
![](/assets/images/B3.RIA.MDC.Slide-09.png)
![](/assets/images/B3.RIA.MDC.Slide-10.png)
![](/assets/images/B3.RIA.MDC.Slide-11.png)

### ???

![](/assets/images/B3.RIA.MDC.Slide-12.png)



### Déterminiation des $\overrightarrow{z}_{k(3)}$

![](/assets/images/B3.RIA.MDC.Slide-13.png)

- Point axe concurrant ==> les origines sont confondus ==> $\overrightarrow{O_4O_5} = \overrightarrow{O_5O_6} = 0$
    - Point axe concurrant = trois rotoides ayant un point immobile qlqsoit la config des trois rotoides = similaire au fonctionnement du poignet

Pour calculer $\overrightarrow{z}_1(3)$, on a deux options:
1. - On part de $\overrightarrow{z}_1(2) = s_2\;\overrightarrow{x}_{2(2)} + c_2\;\overrightarrow{y}_{2(2)}$ que l'on connait de $T_{12}$
    - On utilise ensuite $T_{23}$ pour calculer $\overrightarrow{z}_1(3) = s_2\;x_{2(3)} + c_2\;\overrightarrow{y}_{2(3)}$
2. On calcule directement la matrice de rotation $R_{13} = R_{12}\times R_{23}$

Pour calculer $\overrightarrow{z}_5(3)$:
![](/assets/images/B3.RIA.CM.MDC.BB20230124-3.png)

Pour calculer $\overrightarrow{z}_5(3)$:
![](/assets/images/B3.RIA.CM.MDC.BB20230124-4.png)

Pour calculer $\overrightarrow{{O_1O_4}_{(3)}}$:
![](/assets/images/B3.RIA.CM.MDC.BB20230124-5.png)

![](/assets/images/B3.RIA.MDC.Slide-14.png)
![](/assets/images/B3.RIA.MDC.Slide-15.png)
![](/assets/images/B3.RIA.MDC.Slide-16.png)
![](/assets/images/B3.RIA.MDC.Slide-17.png)
![](/assets/images/B3.RIA.MDC.Slide-18.png)


![](/assets/images/B3.RIA.MDC.Slide-19.png)
![](/assets/images/B3.RIA.MDC.Slide-20.png)
![](/assets/images/B3.RIA.MDC.Slide-21.png)
![](/assets/images/B3.RIA.MDC.Slide-22.png)

> Attention: $X_3 = [...]\;X_2$ et pas $X_3 = [...]\;X_1$
![](/assets/images/B3.RIA.MDC.Slide-23.png)

> Attention: $[...] = [...]\;X_3$ et pas $[...] = [...]\;X_1$
![](/assets/images/B3.RIA.MDC.Slide-24.png)
![](/assets/images/B3.RIA.MDC.Slide-25.png)

![](/assets/images/B3.RIA.MDC.Slide-26.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230124-6.png)


![](/assets/images/B3.RIA.MDC.Slide-27.png)
![](/assets/images/B3.RIA.MDC.Slide-28.png)

## Validation

![](/assets/images/B3.RIA.MDC.Slide-29.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230124-7.png)


# Compléments

![](/assets/images/B3.RIA.CM.MDC.BB20230125-1.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230125-2.png)
![](/assets/images/B3.RIA.CM.MDC.BB20230125-3.png)



> Notes RKA du 2023/01/24 - End

---
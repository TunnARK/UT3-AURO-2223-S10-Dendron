
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut et P. Ribot

---

> Notes du 2023/01/12 - Start




![](/assets/images/PSH.Slide4.Proprietes-01.png)

# Sommaire

![](/assets/images/PSH.Slide4.Proprietes-02.png)

# Prop SED

## Rappel

> Keywords: Accessibilité , Coacessibilité, ...

![](/assets/images/PSH.Slide4.Proprietes-03.png)


Accessibilités:
- chemin de $x_0$ à $x$

CoAccessibilités:
- chemin de $x$ à $x_{marqué}$
- introduit la notion d'objectif

## Analyse

> Keywords: blocage ; observabilité ; contrôlabilité ; stabilité ; model-checking

![](/assets/images/PSH.Slide4.Proprietes-04.png)

## Contrôlabilité de la commande supervisée

> Keywords: procédé ; commande supervisée ; contrôlabitié ; non-blocage

![](/assets/images/PSH.Slide4.Proprietes-05.png)
![](/assets/images/PSH.Slide4.Proprietes-06.png)

Attention:
- qand la commande supervisée ne contient pas des elemetns non controlable (comme un capteur) alors la commande concut pourra s'interrompre lors d'une apparition aléatoire d'un evenements non controlable
- dans ce cas la commande supervisée ne sera plus controlable
- pour la rendre controlable a nouveau il faudra complementer/inclure cette commande avec des elements non controlabe

## Observabilités

> Keywords: observabilités

![](/assets/images/PSH.Slide4.Proprietes-07.png)

## Stabilité

> Keywords: commande supervisée de Ramadge & Wonham ; états autorisés/interdits

![](/assets/images/PSH.Slide4.Proprietes-08.png)

## Exemple

### Etat vivant/bloquant

> Keywords: dead state

![](/assets/images/PSH.Slide4.Proprietes-09.png)

### Etats autorisés/interdit

> Keywords: superviseur ; stabilisabilité (stabilisability) ; régions d'attraction

![](/assets/images/PSH.Slide4.Proprietes-10.png)

# Stabilité en Syst. Hybrides

## Définitions

> Keywords: etat fictif ; globalement exponentiellement stable (GES) ; fonction de lyapunov ; moindres carrés

![](/assets/images/PSH.Slide4.Proprietes-11.png)

Problème:
- comment définir la notion de stabilité d'un ensemble et non plus d'un point d'équilibre
- Sii timer on peut pas montrer que x converge vers 0
- comment définir la notion d'écartement vis-à-vis d'un ensemble ?
    - il faudrait définir la distance minimale sur tous les points de l'ensemble
    - or faire $\min\dfrac{1}{x}$ n'est pas défini car le min implique l'hypothèse d'existence
    - du coup on utilise le $\inf$
    $$
    | x |_{\mathcal{A}} = \inf_{y\in\mathcal{A}} |x-y|
    $$
    - au final cela est assimilable au moindres carrés !!!

![](/assets/images/PSH.Slide4.Proprietes-12.png)

## Utilisation d'une fonction de Lyapunov

![](/assets/images/PSH.Slide4.Proprietes-13.png)

$$
V(\phi(t,j)) \quad tq \\
\begin{cases}
\dot V(\phi) < 0 \quad \forall\;\phi\in\mathcal{C}\\
V(G(\phi)) < V(\phi)
\end{cases}
$$

du coup la fct le lyap. doit décroitre durant les flots et/ou durant les sauts

mais si elle doit décroitre dans les flots cela impose que le procédé doit rester assez de temps dans le flot (_dwell-time_)

mais si elle décroit seulement durant les sauts là il faut alors suffisament de sauts (donc le procédé ne peut pas s'arreter sur un flots)

# Bibliographie

![](/assets/images/PSH.Slide4.Proprietes-14.png)
![](/assets/images/PSH.Slide4.Proprietes-15.png)




> Notes du 2023/01/12 - End

---
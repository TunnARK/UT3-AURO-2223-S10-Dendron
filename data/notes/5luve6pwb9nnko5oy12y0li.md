
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut et P. Ribot

---

> Notes du 2023/01/06 - Start

![](/assets/images/PSH.Slide2.Modelisation-01.png)

> Syst. Hyb. au sens de Teel (mathematicien qui définit les syst. hyb.)

> Cassandras a travaillé sur les syst. continu pour ensuite passé sur les syst. discret

> Lafontaine a définit les automates

# Sommaire

![](/assets/images/PSH.Slide2.Modelisation-02.png)

# 1) Balle rebondissante

![](/assets/images/PSH.Slide2.Modelisation-03.png)

Notation: 
- espace de flot pour décrire la dynamique continu
- espace de saut pour décrire la ré-initialisation

# 2) Observateur

![](/assets/images/PSH.Slide2.Modelisation-04.png)

$y(t) = y(t_k)$ indique que la mesure n'arrive pas continuement mais à des instants cadensés ou non (les mesures sont spontanées) sous l'hypothèse que des mesures sont bien captés

Observateur = Syst dyn dont l'objectif est de poursuivre un etat

Obs naif:
$$
\dot x = A x + B u\\
\hat x = A x + B u\\
\epsilon = x - \hat x\\
\dot\epsilon = e^{At} \epsilon(0)
$$

On peut alors crée un syst. hyb. avec une bulle contenant le simulateur (l'obs naif) avec à chaque mesure une ré-initiliasation de $\epsilon$.

> cf Ferrante FRANSCESCO "observer" 2016

# 3) Thermostat

![](/assets/images/PSH.Slide2.Modelisation-05.png)

2 garde 1 etat continu 1 etat discret

dans les etats il est en flot

il n'y a pas de ré-initialisation

ce syst est hyb car le changement de mode dépend d'un etat continu

c'est une hystéresis où il y a un moment nominal et des moments de changement donc le choix des CI devra respecter le domaine de définition de $x$ (sinon il y a ou bien un changement directe au depart ou un blocage du syst au quel cas la modelisation n'est pas la bonne)

![](/assets/images/PSH.Slide2.Modelisation-06.png)

$f$ et $\phi$ sont des fonctions multivaluées

Le phenomene de zenon (switch infinie) n'est pas désirée en général exception pour les convertisseurs d'énergie où le phénomène de zenon est l'objectif meme de ces procédés car le zenon au final mène la dynamique vers la variable de changement.

Pour le bac d'eau "tout ou rien" on aura un zenon et pour le faire disparaitre on peut inserer un interval pour donner le temps au syst de rester sur un flot ou autre facon on peut inserer un timer-dual pour cadenser le changement.

Au final si un zenon est voulu on perd l'interet d'une modelisation hyb car les flots ne présente plus d'interets vu que la dynamique est dictée par la variable de changement

![](/assets/images/PSH.Slide2.Modelisation-07.png)

# 4) Réservoir avec délais

On pourrait modéliser ce procédé avec du temps invariant ou avec des automates temporisés (mais les deux options sont très difficiles).

![](/assets/images/PSH.Slide2.Modelisation-08.png)

Dans Q1, le bac se vide s'il descend en dessous de 1 on réinitialise le timer à zero et dans Q2 on commence à compter. Si on atteint $\tau \geq 0.5$ alors on passe à Q3 pour ré-initialise le timer et on commence a remplir. Lorsque le niveau arrive à 2 on passe à Q4 qui correspond a continuer de remplir mais en commencant le count down.

On peut imaginer que l'intéret du timer virtuelle (d'où pourquoi on peut si facilement ré-initialiser les CI de $\tau$ sans soucis) est de modéliser par exemple la dynamique de la pompe (qui nécessite du temps pour atteindre son régime permanant)

![](/assets/images/PSH.Slide2.Modelisation-09.png)

# 5) Machine avec réparation

![](/assets/images/PSH.Slide2.Modelisation-10.png)
![](/assets/images/PSH.Slide2.Modelisation-11.png)

Ici il y a une grande modification : l'invariant dans Q2 ainsi que l'apparition d'évènement exogène $\alpha$, $\beta$ et $\gamma$

![](/assets/images/PSH.Slide2.Modelisation-12.png)
![](/assets/images/PSH.Slide2.Modelisation-13.png)

# 6) Modélisation formelle

## SED

![](/assets/images/PSH.Slide2.Modelisation-14.png)

$X$ à temps continu
$f$ pour l'evolution du flot
$\phi$ pour les "fleches"
$Inv$ continu ou discret

## STC

![](/assets/images/PSH.Slide2.Modelisation-15.png)

$F$ et $G$ sont des fonctions mutlivaluées

## Bilan

On retrouve en SED et STC :
- C = flot
- D = garde
- F et G = $\rho$

Grosses différences entre hybride SED et STC :
- les CI ne peuvent pas etre imposé en STC (c'est l'objectif meme d'analyse de stabilité où l'on fait varier les CIs pour etudier la robustesse du syst. ou meme dans un observateur où l'on estime les CI pour retrouver l'etat actuel à partir du CI trouvé)
- even. et etat discret n'apparaissent pas en STC
    - on fait les etats discret sont modéliser en etat continu (extension)
    - durant le flot on maintient ou met a zero les etats discret
    - les $q^+$ remplace le $\phi$

Ces différences s'expliquent par la divergence des objectifs respectif en SED et STC.

Ici la STC va prouver la stabilité d'un ensemble plustôt que d'un point d'équilibre.

![](/assets/images/PSH.Slide2.Modelisation-16.png)

## Exercices

![](/assets/images/PSH.Slide2.Modelisation-17.png)

# 7) Simulation

![](/assets/images/PSH.Slide2.Modelisation-18.png)

zero crossing detection
- pour le franchissement d'une guarde
- comment faire algorithimiquement pour verifier et franchir les conditions de changement (inégalité et autres)

# 8) A retenir

![](/assets/images/PSH.Slide2.Modelisation-19.png)



> Notes du 2023/01/06 - End

---
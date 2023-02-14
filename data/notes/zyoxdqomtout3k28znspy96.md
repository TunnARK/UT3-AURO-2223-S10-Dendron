
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut et P. Ribot

---

> Notes du 2023/01/11 - Start


![](/assets/images/PSH.Slide3.Trajectoires-01.png)

# Sommaire

![](/assets/images/PSH.Slide3.Trajectoires-02.png)


# 1) Remarques sur les automates hybrides

## Retour sur le modèle en SED

![](/assets/images/PSH.Slide3.Trajectoires-03.png)

trajectoire en SED = séquence d'ev. du coup assez evidante comparé au STC car une fois un ev. passé on ne peut pas faire demi-tour

Certains pb en SED :
- deadlock
- feuille non co-accessible

## Deadlock

![](/assets/images/PSH.Slide3.Trajectoires-04.png)

Pour eviter un deadlock, il faudrait respecter la formule suivante :
$$
x \notin Inv
$$

C.à.d. que l'on définit l'$Inv$ selon l'union des gardes.

## Comportement Zenon

![](/assets/images/PSH.Slide3.Trajectoires-05.png)

Solution:
Implémenter un timer pour donner le temps  a un flot de s'établir (_waittime_)
- Dans ce cas, le temps d'attente dépend de la dynamique du systeme
- En fait ce délai rend le délai fini infini c'est ce qui fait tomber le phenomene zenon (on peut continuer a switcher sur un meme etat une infinité de temps mais comme a chaque fois on attend on ne fait plus c'est switch sur un temps fini)

## Automate non déterministe

![](/assets/images/PSH.Slide3.Trajectoires-06.png)

Lors de la modelisation on rajoute des incertitudes ce qui peut amener des indeterministes. Ce qui amene a donné les trois modification de définition ci-dessus.

Si on veut faire une simulation on fait un model pour chaque CI.

Ici l'idée des etudes faites sur de tels models incertains est de partir de l'etat final et reconstruire le comportement.

# 2) Notions de trajectoires en STC

## Le temps hybride

> Keywords: domaine temporel ; temps hybride/ordinaire

![](/assets/images/PSH.Slide3.Trajectoires-07.png)

## Remarques

![](/assets/images/PSH.Slide3.Trajectoires-08.png)

## Trajectoires Hybrides (STC)

> Keywords: fonction absolument continue ; arc hybride

![](/assets/images/PSH.Slide3.Trajectoires-09.png)

Représentation graphique :
![](/assets/images/PSH.BB20230111-2.png)


## Différents types d'arc hybride

> Keywords: non trivial ; complet ; zéno ; eventuellement discret/continu ; continu

> ERROR: J = $sup_j(dom\phi)$
![](/assets/images/PSH.Slide3.Trajectoires-10.png)

- Zenon
    ![](/assets/images/PSH.BB20230111-1.png)
- Discret
    ![](/assets/images/PSH.BB20230111-3.png)

## Solutions

![](/assets/images/PSH.Slide3.Trajectoires-11.png)

> On a besoin d'ouvert pour potentiellement bien définir la dérivée

## Exemple


![](/assets/images/PSH.Slide3.Trajectoires-12.png)

<!-- ![](/assets/images/PSH.BB20230111-4.png) -->
![](/assets/images/PSH.BB20230111-5.png)

![](/assets/images/PSH.Slide3.Trajectoires-13.png)

![](/assets/images/PSH.BB20230111-6.png)

Que se passe-t-il:

- en (0,0) ?

    On se trouve alors dans D mais on switch constament en restant sur le meme point (donc purement discret) comme une sorte de point d'équilibre (on ne passe jamais sur le flot)

- en (2,-1) ?

    On ne va jamais taper D donc on reste sur C donc diverge (attention on peut diverger tout en faisant des switch)

- en (2,2) ?

    On va se diriger vers la frontiere de D sans jamais (ou pas) le franchir. Pour fixer si il y a franchir il faut etudier la limite

## Paradoxe de Zenon

![](/assets/images/PSH.Slide3.Trajectoires-14.png)


Achile donne de l'avance au lapin

achile court 2x plus vite

pendant que achile court le lapin fait 50min

achile court 50m et le lapin 25m de plus 

et ainsi de suite

mais ce ainsi de suite ne doit pas nous faire penser que le sup_t C est infini il se peut qu'il existe une limite

en effet $lim_i \sum (1/2)^i = 2$

# Bibliographie

![](/assets/images/PSH.Slide3.Trajectoires-15.png)




> Notes du 2023/01/11 - End

---
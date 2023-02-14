
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par S. Durola

---

> Notes RKA du 2023/01/27 - Start



## Modèle de connaissance

Le modèle de connaissance correspond au processus de modélisation qui consiste à construire étape par étape un modèle.

Contrairement au modèle de comportement qui lui correspond à choisir une modélisation spécifique et réaliser des expériences en espérant que les propriétés du système se retrouve sur celles dictées par le modèle choisi.

![](/assets/images/B3.CCTR.TP1.BB20230127-01.png)
![](/assets/images/B3.CCTR.TP1.BB20230127-02.png)
![](/assets/images/B3.CCTR.TP1.BB20230127-03.png)
![](/assets/images/B3.CCTR.TP1.BB20230127-04.png)

## 1) Représentation d'état

### Etape 1 - Identification

Identifier les variables d'états, d'entrées et de sorties


### Etape 2 - Restructuration

Restructurer les equations pour aboutir vers un système de la forme:
$$
\begin{cases}
\dot x(t) = f\big(x(t), u(t), \delta(t)\big)\\
y(t) = g\big(x(t), u(t), \delta(t)\big)
\end{cases}
$$

### Etape 3 - Choix de simplification sur les incertitudes

#### Couple de frottement sec

Cette caractéristique pose problème car elle est très compliquer à linéariser.

Le syst. se trouverait après linéarisation dans une zone morte où tout serait égale à 0. Le moteur resterait immobile au point d'équilibre.

On va du coup rechercher à le négliger (en le considérant constant pour le moment) tout en gardant en tête

Primo le module sera toujours inférieure à C0

donc si la vitesse est grande il y a pas de soucis de le négliger

probleme pour des vitesses faibles ou on a pas le droit de le negliger

donc comme on aura des imprecisions en vitesse faible ile au point d'équilibre.

On va du coup rechercher à le négliger (en le considérant constant pour le moment) tout en gardant en tête

Primo le module sera toujours inférieure à C0

donc si la vitesse est grande il y a pas de soucis de le négliger

probleme pour des vitesses faibles ou on a pas le droit de le negliger

donc comme on aura des imprecisions en vitesse faible on va implémenter un commande par retour d'état avec effet intégrale à la question 6.

![](/assets/images/B3.CCTR.TP1.BB20230127-05.png)

## 3) Réduction d'ordre

Méthodes pour la réduction d'ordre:
- négiglér une variable p.r.à une autre
- passer par la forme modale
    - soit mode très rapide (bande aténuée)
    - soit mode d'amplitude très faible (bande passante) (proche de zéro)

Pourquoi réduire l'ordre ?

- c'est plus simple et comme on a une approche robuste cela ne poserait pas probleme

- modele 4 valeur tres grande donc sur le microcontroleur on pourra pas gerer les approximation pour des valeurs s'y ecarter (apparition de saturation et la difficulté du microcontroleur pour gerer les quantifications)

## 4) Analyse

### Etude des valeurs propres

On a 4 valeurs propres une en 0 une en -4 et 2 très loin en -7'000 et -100'000.

Cela nous indique que l'on pourra négliger les deux valeurs propres en -7'000 et -100'000.

Car surement que ces valeurs seront atténué par le filtre passe bas.

De plus si on analyse le fonction de transfert (entrées/états) on constate qu'ils sont aussi des zéros et donc peuvent être simplifier.

### Etude des bodes

On peut aussi argumenter nos simplifications par l'analyse des diagrammes de bodes.

...

Pour une pulsation $\omega < \omega_0$, le module de $\dfrac{I_1(p)}{\;U_m(p)\;} = 0.085 \;\;\Omega^{-1}$.

Ceci nous autorise de remplacer la première équation par:
$$
i_1(t) = {R_{eq}}^{-1}\; U_m(t)
$$

Analytiquement on écrirait:
![](/assets/images/B3.CCTR.TP1.BB20230127-06.png)

Simplification equation 2:

Bode

Anaylitiquement sur les fonctions de transfert entrées sorties
![](/assets/images/B3.CCTR.TP1.BB20230127-07.png)


observateur

schema bloc




> Notes RKA du 2023/01/27 - End

---
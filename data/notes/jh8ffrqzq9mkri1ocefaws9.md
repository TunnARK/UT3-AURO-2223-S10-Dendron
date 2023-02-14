
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par S. Durola

Support de Cours:
- [B3.CCTR.CM.Modalites.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.CCTR.CM.Modalites.pdf)
- [B3.CCTR.CM.BB20230118.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.CCTR.CM.BB20230118.pdf)
- [B3.CCTR.CM.NotesGEA.20230118.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.CCTR.CM.NotesGEA.20230118.pdf)

---

> Notes RKA du 2023/01/18 - Start



# Modalités

![](/assets/images/B3.CCTR.CM.BB20230118-01.png)

# Synthèse

![](/assets/images/B3.CCTR.CM.BB20230118-02.png)

# I- Positionnement du module

![](/assets/images/B3.CCTR.CM.BB20230118-03.png)

## Première Hypothèse: Causalité et Existence de l'état

![](/assets/images/B3.CCTR.CM.BB20230118-04.png)

Etat = representation interne suffisament riche pour expliquer un processus et son evolution de manière univoque et un???

Temps = ensemble orienté et mono-dimensionnel

## Représentation d'état

![](/assets/images/B3.CCTR.CM.BB20230118-05.png)

## Autres Hypothèses 

![](/assets/images/B3.CCTR.CM.BB20230118-06.png)
![](/assets/images/B3.CCTR.CM.BB20230118-07.png)

- $H_i$: Invariance Temporelle
- $H_a$: Autonome
- $H_d$: Déterministe
- $H_{sm}$: Sans Mémoire (combinatoire ou séquencielle)

## Exemple: la dérivée


![](/assets/images/B3.CCTR.CM.BB20230118-08.png)
![](/assets/images/B3.CCTR.CM.BB20230118-09.png)

## Problématique

Si un modèle asservi $i$ pose problème il faut revenir au modèle physique $i$ et corriger ce modèle. Ce ne sera pas toujours possible ensuite de poursuivre vers une simplification avec un modèle $i+1$. Dans ce cas, il faudra trouver la commande pour le modèle asservi $i$ directement du modèle physique $i$.

# II- Prototypage

## Simulation vs Emulation

![](/assets/images/B3.CCTR.CM.BB20230118-10.png)

> Emuler un vieux jeux video sur un nouveau PC puissant ne fera pas améliorer les performances du jeux ! Emulation conservera les performances telles qu'elles étaient dans le PC d'origine.

- Modèle In the Loop --> Simulation
- Système In the Loop --> Emulation
- Hardware In the Loop --> Emulation avec le système physique

## Hiérarchie

![](/assets/images/B3.CCTR.CM.BB20230118-11.png)

- $C_{(m)}$ Commande modèle
- $P_{(m)}$ Procédé modèle

### Stratégie 1: Prototypage rapide

> Ce que nous faisant en salle de TP.

![](/assets/images/B3.CCTR.CM.BB20230118-12.png)

- La boite représente la carte d'acquisition.

Si ce prototypage ne marche pas on passe à une stratégie itérative.

### Stratégie 2: Prototypage itératif

> Idée: découpler la commande et le procédé

#### Etape 1: Tester l'échantillonage

![](/assets/images/B3.CCTR.CM.BB20230118-13.png)

#### Etape 2: Passer en temps concret

![](/assets/images/B3.CCTR.CM.BB20230118-14.png)

C'est ce que l'on peut faire sur Matlab en faisant tourner la simulation en temps externe.

#### Etape 3: Tester la carte d'acquisition

![](/assets/images/B3.CCTR.CM.BB20230118-15.png)

#### Etape 4: Tester la communication de la carte

![](/assets/images/B3.CCTR.CM.BB20230118-16.png)

#### Etape 5: Tester sur deux ordinateurs

![](/assets/images/B3.CCTR.CM.BB20230118-17.png)

#### Etape 6: Retester sur deux ordinateurs

Refaire le test mais avec des temps différents

#### Etape 7: Fixer ou la commande ou le procédé

![](/assets/images/B3.CCTR.CM.BB20230118-18.png)

#### Etape 8: Fixer la composante restante

![](/assets/images/B3.CCTR.CM.BB20230118-19.png)


## Exemples

Satellite présente 3 composantes:
- l'environnement
- le satelite
- la commande

Centrale Nucléaire peut aussi présenter 3 composantes:
- Centrale
- Commande
- Comportement humain

# III- Mise en Oeuvre temporel

Ceci est la dernière étape de la création de la commande.

On fait le choix du microcontroleur, des paramétrages, de la programmation et de l'expérimentation.

## Problématique Temps réel

On est sousmis à des contraintes lié à la nature du microcontroleur.

Parmis celles-ci, il y a les contraintes liées aux :
- temps: fréquence ; RDV ; ordonnancement ; ...
- valeurs: quantification ; numérique ; saturation ; ...
- compléxités: puissance de calcul ; mémoire ; ...

# IV- Modèle 0

On considère ici le moteur à courant continu de la salle I1.

## Dessin

![](/assets/images/B3.CCTR.CM.BB20230118-20.png)

## Schéma

![](/assets/images/B3.CCTR.CM.BB20230118-21.png)

- $J$ représente l'inertie de l'axe.

## Equations

On néglige les changements de comportements liés à l'humidité de la salle ou la température du moteur.

### Loi de la Mécanique
$$
u_m(t) = R_1\;i_1(t) + L_1\;d_t i_1(t) + e_1(t)\\
e_2(t) = R_2\;i_2(t) + R_{ch}\;d_t i_1(t) + L_2\;d_t i_2(t)
$$

### Principe Fondamental de la Dynamique
$$
J\;d_t\omega(t) = C_1(t) + C_2(t) + C_f(t)
$$

où $\quad \omega(t) = d_t \theta_m(t)$

### Réducteur
$$
\theta_s(t) = K_n\;\theta_m(t)
$$

### Forttements
$$
C_f(t) = - \mu_\omega(t) + C_S(t)
$$

Si $\;\;\omega(t) = 0\;\;$ et $\;\; |C_1(t) + C_2(t)| < C_0 \;\;$ alors $\;\; C_S(t) = -C_1(t) - C_2(t) \;\;$ sinon $\;\; C_S(t) = \pm C_0\;\;$.

Si $\;\;\omega(t) \neq 0\;\;$ alors $\;\; C_S(t) = \pm C_0\;\;$ opposé à $\;\omega(t)\;$.

### Electromécanique
$$
e_1(t) = K_{e_1}\;\omega(t)\\
e_2(t) = K_{e_2}\;\omega(t)\\
C_1(t) = K_{C_1}\;\omega(t)\\
C_2(t) = K_{C_2}\;\omega(t)\\
$$

### Capteurs
$$
u_g(t) = K_g\;\omega(t)\\
u_S(t) = \Big( K_S\;\omega(t) + \frac{\;K_S\;}{2} \Big)\;[K_S] - \frac{\;K_S\;}{2}
$$
![](/assets/images/B3.CCTR.CM.BB20230118-22.png)

### Incertitudes
$$
R_{ch} = R_{ch_0} + r_{R_{ch}}\;\delta_1\\
C_0 = C_{0_0} + r_{C_0}\;\delta_2
$$

avec $\quad |\delta_1|<1 \quad\wedge\quad |\delta_2|<1$



> Notes RKA 2023/01/18 - End

---
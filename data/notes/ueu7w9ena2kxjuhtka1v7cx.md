
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par P. Danès

Support de cours:
- BlackBoard:
    - [B3.RP.CM.BB20230117.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.RP.CM.BB20230117.pdf)
    - [B3.RP.CM.BB20230118.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.RP.CM.BB20230118.pdf)
- Notes GEA:
    - [B3.RP.CM.NotesGEA.20230117.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.RP.CM.NotesGEA.20230117.pdf)
    - [B3.RP.CM.NotesGEA.20230118.pdf](https://github.com/TunnARK/UT3-AURO-2223-S10-Dendron/blob/main/vault/assets/B3.RP.CM.NotesGEA.20230118.pdf)

---

> Notes RKA du 2023/01/17 - Start





![](/assets/images/B3.RP.CM.BB20230117-01.png)

- Sequential Monte Carlo methods
- Particle filtering

# Pourquoi ?

- Très utilisé pour le filtrage Bayésien NL non Gaussien
- Existence d'une solution emblématique du SLAM (algo FAST SLAM / "gmapping")

# I- Rappels

## 1) Filtrage Bayésien

![](/assets/images/B3.RP.CM.BB20230117-02.png)

<!-- graphe x_0 -->

- séquence d'**états cachés** $x_{0:k} = (x_0, \dots, x_k)$
- séquence d'**observations** $z_{1:k} = (z_1, \dots, z_k)$

### Contexte incertain (approche probabiliste)

![](/assets/images/B3.RP.CM.BB20230117-03.png)

- $x_{0:k}$ réalisation de $X_{0:k}$ processus aléatoire d'**état** (séquence de variable aléatoire $X_0$, $\dots$, $X_k$)
- $x_{0:k} = X_{0:k}(\omega)$ résultat de l'expérience en cours / **caché**
- $z_{0:k}$ réalisation de $Z_{0:k}$ processus aléatoire de **mesure**
    - $z_{0:k} = Z_{0:k}(\omega)$ résultat de l'expérience en cours / **accessible**

### Connaissance a priori

Description de la **connaissance a priori** en termes probabilistes

- P.A. d'état caché Markonien
    - loi de $X_{0:k}$ décrite par
        - loi de $X_0$ (**loi initiale**)
        - loi statistique entre $X_{k-1}$ et $X_k$ (**loi/modèle de dynamique a priori**)
- P.A. de mesure
    - loi entre $X_k$ caché et $Z_k$ la **loi/modèle d'observation**

### Objectif: Loi A Posteriori/Postérieure

$$
P_{X_{0:k} \,|\, z_{1:k}}\big( x_{0:k} \,|\, z_{1:k} \big)\\
\ \\\text{ou}\\ \ \\
P_{X_{k} \,|\, z_{1:k}}\big( x_{k} \,|\, z_{1:k} \big)\\
$$

![](/assets/images/B3.RP.CM.BB20230117-04.png)

<!-- 
## Discussion

image graph + audio 1 
-->

### Exemple: Loi Postérieure

![](/assets/images/B3.RP.CM.BB20230117-05.png)

<!-- audio 2 -->

Imaginons que l'on sache trier les expériences qui donne pair, ceci nous permettrait d'avoir un modèle d'observation.

Idem pour les impairs, en calculant $\mathbb{P}(Z=z \,|\, X = 2)$ on peut en déduire un modèle d'observation.

C'est à dire qu'ici on décrit notre connaissance a priori.

Maintenant si on observe du vert quel est l'etat caché (le numéro sous la couleur verte) ?

On ne sait pas la valeur exacte mais on est sûr que cette valeur peut être 1, 3 ou 5.

Ceci est un problème d'estimation.

<!-- Audio 3 -->

On peut faire de même pour la couleur rouge et bleu (avec la différence particulière que pour le bleu on connait l'état avec certitude).

Dans notre contexte, on va travailler sur un continium et non plus une "grille"/dans du discret. Ceci va nous amener à introduire la notion de densité probabliste.

### MMSE - Estimé

> MMSE = Minimum Mean Square (Error) Estimate

![](/assets/images/B3.RP.CM.BB20230117-06.png)

$$
\mathbb{E} \big[ X_k \,|\, Z_{1:k}=z_{1:k} \big] = \int x_k \, P_{X_k \,|\, Z_{1:k}} \big( x_k \,|\, z_{1:k} \big) \, dx_k
$$

<!-- audio 4 -->

### Densité de probabilité

#### Continium

![](/assets/images/B3.RP.CM.BB20230117-07.png)

Soit $x \in \mathbb{R}$, $P_X(x)$ est une densité de probabilité (dont la variable est $x$ et $X$ sa réalisation possible) tel que :
- $P_X(x) \geq 0$
- $\int_{\mathbb{R}} P_X(x)\, dx = \mathbb{P}(x\in\mathbb{R}) = 1$
- $\int_{\epsilon} P_X(x)\, dx = \mathbb{P}(x\in\epsilon)$

<!-- audio 5 -->

![](/assets/images/B3.RP.CM.BB20230117-08.png)

Quelle est l'**espérance de X** ? Est-ce la valeur moyenne des issues possibles de $X$ ?

$$
\mathbb{E}\big[X\big] = \mathbb{E}_{P_X(x)}\big[X\big] = \int_{\mathbb{R}} x\,P_X(x)\,dx = \bar x
$$

Comment se disperse $X$ autour de $\mathbb{E}\big[X\big]$ ?

$$
Var\big[X\big] = \mathbb{E}_{P_X(x)}\Big[ \big( X - \mathbb{E}[X] \big)^2 \Big] = \mathbb{E}\big[ X^2 \big] - \Big(\mathbb{E}\big[ X \big]\Big)^2
$$

#### Discret

Si maintenant $x\in\mathbb{R}$ est à valeurs discrètes.

![](/assets/images/B3.RP.CM.BB20230117-09.png)


<!-- audio 6
implusion de dirac pour passer du continu au discret -->

![](/assets/images/B3.RP.CM.BB20230117-10.png)


<!-- audio 7 -->


$$
\int_{\mathbb{R}} f(x)\,\delta(x-x_i)\,dx = f(x_i)\\
$$

Convolution d'une impulsion de dirac
$$
\int_{\mathbb{R}} f(x)\,\delta(x-x_i)\,dx = f(x-x_i)\\
$$

#### Multi-variable

![](/assets/images/B3.RP.CM.BB20230117-11.png)
![](/assets/images/B3.RP.CM.BB20230117-12.png)
![](/assets/images/B3.RP.CM.BB20230117-13.png)
<!-- audio 8 -->

## 2) Lois Gaussiennes

<!-- audio 9 -->

### Mono-variable

![](/assets/images/B3.RP.CM.BB20230117-14.png)

- $m\pm\sigma$ correspond au point de flexion de la cloche gaussienne

![](/assets/images/B3.RP.CM.BB20230117-15.png)

### Multi-variable

![](/assets/images/B3.RP.CM.BB20230117-16.png)



> Notes RKA du 2023/01/17 - End

---

> Notes RKA du 2023/01/18 - Start



### Comment échantillonner une loi Gaussienne multivariée ?

> i.i.d. Indépendant Identiquement Distribué

Se pose deux problèmes :
- Comment tirer une colonne avec les variables voulues (e.g. `Y = randm(M,N)` )
- Trouver le bon $L$ tq $LL^T = P$

![](/assets/images/B3.RP.CM.BB20230118-01.png)
![](/assets/images/B3.RP.CM.BB20230118-02.png)

### Nota: Estimation Bayésienne

##### Loi A Posteriori

![](/assets/images/B3.RP.CM.BB20230118-03.png)
![](/assets/images/B3.RP.CM.BB20230118-04.png)
![](/assets/images/B3.RP.CM.BB20230118-05.png)

L'estimateur $\hat X_{MMSE}$ est indépendant de la métrique utilisé (i.e. $Q$ ) du coup il n'est pas possible d'affiner l'estimateur pour être plus précis sur un bloc de variable et pas un autre. On estime le tout d'office.

##### Covariance A Posteriori

![](/assets/images/B3.RP.CM.BB20230118-06.png)

### Compléments Estimation Dynamique

> Attention: pour simplifier les notations on ne va plus distinguer entre une var. al. et sa réalisation !!! 

> Sauf contre-indication tous les bruits seront considérés blanc (i.e. "_indépendance des echantillons_")

> Attention: $\quad P_0 \geq 0 \quad\wedge\quad Q_{k-1} \geq 0 \quad\wedge\quad W_{0:k}\;\;blanc$

> Trois cas:
- $k'\leq k$ alors **prédiction**
- $k'= k$ alors **filtrage**
- $k'\geq k$ alors **lissage**

![](/assets/images/B3.RP.CM.BB20230118-07.png)
![](/assets/images/B3.RP.CM.BB20230118-08.png)
![](/assets/images/B3.RP.CM.BB20230118-09.png)
![](/assets/images/B3.RP.CM.BB20230118-10.png)
![](/assets/images/B3.RP.CM.BB20230118-11.png)
![](/assets/images/B3.RP.CM.BB20230118-12.png)
![](/assets/images/B3.RP.CM.BB20230118-13.png)

# II- Approximation (ponctuelle) de Monte Carlo (d'une pdf)

## Contexte de tirage

![](/assets/images/B3.RP.CM.BB20230118-14.png)



> Notes RKA du 2023/01/18 - End

---

> Notes RKA du 2023/01/25 - Start



![](/assets/images/B3.RP.CM.BB20230125-01.png)
![](/assets/images/B3.RP.CM.BB20230125-02.png)

$\bar x_{k|k}$ va se distribuer autour de $\hat x_{k|k}$.

On tire des nuages de particules pondérées. Donc chaque run (chaque tirage donc chaque lot de $x_i$) donnera des estimées différents à chaque proche autour de la valeur réelle avec une certaine probablité.

On fait de la proba de proba.

![](/assets/images/B3.RP.CM.BB20230125-03.png)

## Echantillonage idéal

![](/assets/images/B3.RP.CM.BB20230125-04.png)

Problématique si on ne peut pas normaliser nos échantilons cette méthode ne marche pas. Mais si cela est possible 

Ceci requiert de pouvoir connaître la cumulative distribution function cdf $P(x) = P(X\leq x)$ qui suit:
![](/assets/images/B3.RP.CM.BB20230125-05.png)

$\hat I$ est l'estimateur et $I$ est la vraie valeur.

Étonnament c'est la taille du nuage et non pas la dimension du vecteur "qui fait la qualité" --> "_beat the curse of dimensionality ?_"

## Echantillonage d'importance

![](/assets/images/B3.RP.CM.BB20230125-06.png)

- loi du $\chi 2$ de un degré de liberté
    - c.à.d. tirer un échantillon d'une loi gaussienne standard
    - puis fixer $q(x) = x^2$
    - alors il est très difficile de déterminer la densité de proba de cette loi
    - plus d'infos sur [Bibm@th.net](https://www.bibmath.net/dico/index.php?action=affiche&quoi=l/loichideux) ou [Wikipedia](https://fr.wikipedia.org/wiki/Loi_du_%CF%87%C2%B2)

### Choix des poid non normalisés

![](/assets/images/B3.RP.CM.BB20230125-07.png)

### Propriétés de l'estimateur

![](/assets/images/B3.RP.CM.BB20230125-08.png)

### Nota

![](/assets/images/B3.RP.CM.BB20230125-09.png)

## Exercice

![](/assets/images/B3.RP.CM.BB20230125-10.png)
![](/assets/images/B3.RP.CM.BB20230125-11.png)

On est en présence d'un $p(x)$ que l'on ne peut pas calculer analytiquement.

Faisant 3 approximation de Monte Carlo

> À noter qu'il faudrait tracer des inflexions en $m\pm\sigma$ pour une courbe en pointiller plus correcte/précise
![](/assets/images/B3.RP.CM.BB20230125-12.png)

A. Ech. Ideal.
![](/assets/images/B3.RP.CM.BB20230125-13.png)

B. Ech. d'importance standard
![](/assets/images/B3.RP.CM.BB20230125-14.png)

- méchanisme d'**acceptation-rejet**
    - si on a 100 particules dont 25 sont en dehors de la zone concerné
    - alors les 25 hors zone seront mis à zéro et les 75 autres aurant un poids de $\frac{1}{\,75\,}$

**Rem.:**
- En A. les echantillons sont tous dans la porte puisque qu'on tire un ech. selon $p(x)$ directement
- En B. puisqu'on tire notre ech. selon $q(x)$ une partie des ech. sont à écarter/rejeter

C. Ech. d'importance "portique"
![](/assets/images/B3.RP.CM.BB20230125-15.png)
![](/assets/images/B3.RP.CM.BB20230125-16.png)


# III- Apllication au filtrage Bayésien

## 1) Les équations récursives exactes

![](/assets/images/B3.RP.CM.BB20230125-17.png)
![](/assets/images/B3.RP.CM.BB20230125-18.png)





> Notes RKA du 2023/01/25 - End

---

> Notes RKA du 2023/02/06 - Start




### Rappel filtrage de kalman (linéaire gaussien)

![](/assets/images/B3.RP.CM.WB20230206-01.png)

Dans le cas linéaire gausienne, Kalman permet de propager les moments et covariances au fil du temps. On a bien un osbservateur récursif de façon analytique.

### Cas général

![](/assets/images/B3.RP.CM.WB20230206-02.png)

Ici le dénominateur est une normalisation qui ne dépend pas de $x$ et il est très difficile à calculer dans le cas général (seulement dans le linéaire gaussien on est capable de calculer l'intégral pour la normaliser à 1). Le numérateur lui est accessible.

On s'en sort à une constante de normalisation près.

### Lois marginals

> Keywords: équation de Chapman-Kolmogorov

![](/assets/images/B3.RP.CM.WB20230206-03.png)

#### Idée de preuve

Pour la prédiction:
![](/assets/images/B3.RP.CM.WB20230206-04.png)

Pour la mise à jour:
![](/assets/images/B3.RP.CM.WB20230206-05.png)

## 2) Approximation recursive de Monte Carlo de la loi jointe/marginale de filtrage

### Le filtre particulaire "SIS" (Sequential Importance Sampling)

Pour la jointe:
![](/assets/images/B3.RP.CM.WB20230206-06.png)

Pour la marginale:
![](/assets/images/B3.RP.CM.WB20230206-07.png)
![](/assets/images/B3.RP.CM.WB20230206-08.png)

Une fois posée l'expression des approximations MC des lois jointes et marginales de filtrage, tout le problème est ramené à la définition des particules trajectorielles et à leur pondérations au fil du temps.

Si $\{\;x_{0:k-1}^{(i)} \,,\, w_{0:k-1}^{(i)}\;\}_{i=0,\dots,N}$ constitue $\hat P_N(x_{0:k-1}\,|\,z_{1:k-1})$ une approximation MC de $p(x_{0:k-1}\,|\,z_{1:k-1})$ alors comment définit-on $\{\;x_{0:k}^{(i)} \,,\, w_{0:k}^{(i)}\;\}_{i=0,\dots,N}$ qui constitue $\hat P_N(x_{0:k}\,|\,z_{1:k})$ une approximation MC de $p(x_{0:k}\,|\,z_{1:k})\;$ ?

![](/assets/images/B3.RP.CM.WB20230206-09.png)
![](/assets/images/B3.RP.CM.WB20230206-10.png)

### Algorithme SIS - Sequential Importance Sampling

![](/assets/images/B3.RP.CM.BB20230206-01.png)
![](/assets/images/B3.RP.CM.BB20230206-02.png)
![](/assets/images/B3.RP.CM.BB20230206-03.png)
![](/assets/images/B3.RP.CM.BB20230206-04.png)

Pour eviter des problèmes numériques de types underflow, il est conseillé de calculer la somme des logs avant de passer à l'exponentielle (surtout dans le cas de particules "très petites").

La covaraince va très vite être à zéro. 

### Algorithme SIR - Sampling Importance Resampling

![](/assets/images/B3.RP.CM.BB20230206-05.png)
![](/assets/images/B3.RP.CM.BB20230206-06.png)
![](/assets/images/B3.RP.CM.BB20230206-07.png)

Tout étape de réchantillionage rajoute de la variance/dispertion dans l'estimateur (ceci est appelé la variance de Monte Carlo).

C'est pourquoi on evalue les estimés des moyennes et des covariances a posteriori avant le rééchantillionnage.

En outre, il est important que ce rééchantillionnage se réalise uniquement si on est en dessous du seuil.

![](/assets/images/B3.RP.CM.BB20230206-08.png)

### Remarques

Tout filtre particulère peut être vu comme une instance du filtre SIR pour un choix de la fonction d'importance et de la stratégie de rééchantillionage.

Par contre, l'étape de rééchantillionage inhinibe la possibilité de parallélisme et il est plus difficile de prouver les propriétés de convergence du filtre (car après le rééchantillionage toutes les variables deviennent dépendente mutuellement).

## 3) Choix de la fonction d'importance

### A- Bootstrap Filter / CONDENSATION

> CONDENSATION = Conditional Density Propagation

> Likelihood = vraisemblance

![](/assets/images/B3.RP.CM.BB20230206-09.png)
![](/assets/images/B3.RP.CM.BB20230206-10.png)

#### Illustration

![](/assets/images/B3.RP.CM.BB20230206-11.png)
![](/assets/images/B3.RP.CM.BB20230206-12.png)
![](/assets/images/B3.RP.CM.BB20230206-13.png)
![](/assets/images/B3.RP.CM.BB20230206-14.png)

Attention de nombreuses de particules peuvent s'avérer intutiles si leur vraisemblance relative à la mesure est faible.

L'effet est d'autant plus important que la dynamique a priori est peu bruitée et que la mesure est infomative.

Ce n'est pas une bonne stratégie que d'échantillonner le nuage sans tenir compte des observations disponibles.

### B- Loi d'importance guidée par la mesure

![](/assets/images/B3.RP.CM.BB20230206-15.png)

Le lien de compatibilité est très importante pour ne pas perdre de l'information comme illustré dans le scénario pessimiste suivant:
![](/assets/images/B3.RP.CM.BB20230206-16.png)

### C- Exemple de mélange de lois   

![](/assets/images/B3.RP.CM.BB20230206-17.png)




> Notes RKA du 2023/02/06 - End

---

> Notes RKA du 2023/02/08 - Start



![](/assets/images/B3.RP.CM.BB20230208-01.png)

C'est trois valeurs H_i sont exclusives et exhaustives.

À noter que $\;\mathbb{P}(H=H_h)\;q(x_k|x_{k-1},z_k,H_h) = q(x_k\;H_h|x_{k-1}z_k)$

Nota:
- Il existe toute une litérature sur les GMM - Gaussian Mixture Model
$$
p(x) = \sum_{k=0}^{H-1} \lambda_h \; \mathcal{N}(x,\;m_h,\;P_h) = \sum_{k=0}^{H-1} \mathbb{P}(H=h) \; p(x|H=h)
$$
où $p(x|H=h)$ est la loi de $x$ sous l'hypothèse $H=h$ qui suit une loi gaussienne d'espérance $m_h$ et de covariance $P_h$

![](/assets/images/B3.RP.CM.BB20230208-02.png)


### D- Loi d'importance optimale

On a vu que la variance des poids $w_k^{(i)}$ augmente lorsque $k$ augmente (dûe à la stratégie récursive).

La loi d'imprtance optimale serait $q(x_{0:k}|z_{1:k}) = p(x_{0:k}|z_{1:k})$.  
(On échantillionne les particules de trajectoires selon la loi postérieure.)

Or cette loi d'importance est impossible car:
- on ne connait pas $p(x_{0:k}|z_{1:k})$ ; et
- ce schéma ne serait pas récursif.

Nota: ceci implique $N_{eff} = N\;$ car $\;\forall h,\;\forall i,\;w_k^{(i)}=\frac{1}{\;N\;}$

On définit la loi d'importance optimale $q^*(x_k|x_{k-1},z_k)$ comme la loi $q(x_k|x_{k-1},z_k)$ qui minimise la variance des poids conditionnés à $x_{0:k-1}$ et $z_{1:k}$.

On montre que : 
$$
q^*(x_k|x_{k-1},z_k) = p(x_k|x_{k-1},z_k) \;\varpropto\; p(x_k|x_{k-1})\cdot p(z_k|x_k)\\
= \dfrac{p(x_k|x_{k-1})\cdot p(z_k|x_k)}{\;\int p(x_k|x_{k-1})\cdot p(z_k|x_k) dx_k\;} = \dfrac{\;p(x_k|x_{k-1})\cdot p(z_k|x_k)\;}{p(z_k|x_k)}
$$
de sorte que 
$$
x_k^{(i)} \sim q^*(x_k|x_{k-1}^{(i)},z_k)\\
w_k^{(i)} \varpropto w_{k-1}^{(i)}\;p(z_k|x_{k-1}^{(i)})
$$

> $\varpropto$ indique que le membre de gauche est proportionnelle égale au membre droite à une constante près.

En général, la loi d'importance $q^*(x_k|x_{k-1}^{(i)},z_k)$ ne peut pas être calculée analytiquement et/car la vraisemblance $p(z_k|x_{k-1})$ de $x_{k-1}$ p.r.à $z_k$ ne peut pas être évaluée. 

Mais il existe de nombreuses approximations : _auxiliary particle filter_, _auxiliary unseential PF_.

> **_Beat the curse of dimensionality_** marche bien mais le soucis est que l'on a du mal à produire des échantillonage propre dans des espaces de grandes dimensions.

## 4) Exercice: application au cas linéaire gaussien

![](/assets/images/B3.RP.CM.BB20230208-03.png)
![](/assets/images/B3.RP.CM.BB20230208-04.png)
![](/assets/images/B3.RP.CM.BB20230208-05.png)
![](/assets/images/B3.RP.CM.BB20230208-06.png)
![](/assets/images/B3.RP.CM.BB20230208-07.png)
![](/assets/images/B3.RP.CM.BB20230208-08.png)
![](/assets/images/B3.RP.CM.BB20230208-09.png)

Pour plus d'information : [Factorisation de Cholesky (wikipedia)](https://fr.wikipedia.org/wiki/Factorisation_de_Cholesky)

<!-- ### Rappel (étapes pour CONDENSATION)

Étapes pour l'implémentation de l'algo CONDENSATION à N particules :
1. Échantillonnage du nuage initial et Pondération ($k=0$)
2. Condensation -->

# IV - Filtre particulaire Rao-Blackwellisé

Pour plus d'information : [Rao-Blackwell Theorem (wikipedia)](https://en.wikipedia.org/wiki/Rao%E2%80%93Blackwell_theorem)

## Position du problème

Considérant un robot paramétré par $x_k$ de dimension 20'003 (3 param. coord. du robot $r_k$ et 10'000 amers $m_k$ en $(x,y)\;$).

![](/assets/images/B3.RP.CM.BB20230208-10.png)
![](/assets/images/B3.RP.CM.BB20230208-11.png)

## "FP classique"

![](/assets/images/B3.RP.CM.BB20230208-12.png)

## Approximation

![](/assets/images/B3.RP.CM.BB20230208-13.png)
![](/assets/images/B3.RP.CM.BB20230208-14.png)

## Illustration

Sur l'espace des amers on obtient avec cette approximation des données calculées analytiquement et sur l'espace du robot on aura des données de dirac.

![](/assets/images/B3.RP.CM.BB20230208-15.png)



![](/assets/images/B3.RP.CM.BB20230208-16.png)


---
id: y2ldpz4tnbwwv24y591rjtv
title: Systèmes Multivariables
desc: ''
updated: 1662927064848
created: 1662925980552
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par F. Gouaisbaut

## Objectif

Étudier des systèmes MIMO (Multi Input Multi Output)

Décomposée en deux parties:
  - Performances et robustesses
  - Systèmes nominaux + modèles/réalisation commande

- Système **réalisable** si (considérant un input output) peut-on déterminer un système d'espace d'état

- souvent dans l'industrie les modèles sont déterminer par des physiciens et donc possède bcp de fonctions de transfert ce qui rend la command plus compliquée

---


> Notes Cours 08/31 - Start

## I- Modélisation des Systèmes MIMO

### 1) Rappel sur les Systèmes MIMO

> Hyp: Les modèles considérés sont **linéaires**

Les différents types de modèle :
- fréquentiel vs temporelle 
  - classement selon la technique d'analyse voulu par après
- Entrée/Sortie
  - fonctions de transferts
  - EDOs
- Espace d'État

CR.Cours0831.DiagModeles

- EDO
  - Transformé de Laplace $\mathcal{L}$ oublie les CIs
- G(p) (fct transfert)

- EE
  - difficile d'y entrer car création de variable ce qui est appelé la **réalisation**
    - se fait à travers de la **forme modale** (Decomp. en éléments simple) ou la **forme de compagne** (approches polynomiales)
  - facile de passer de EE à G ou EDO via la transformé de laplace

### 2) Les modèles MIMO

#### 2.1) Les modèles E/S

##### Les modèles temporels

Ils représentent des EDOs couplés entre les différentes entrées et sorites d'un système.

Considérant $m$ entrées, $p$ sorites, le modèle EDO s'écrit

CR.Cours0831.Eq1

**Rem:**
- Le système est causal donc $s \geq r$
  - **Causalité** les effets ne peuvent pas précéder les causes
  - si $s=r$ alors système directe (strict. causal)
- il y a autant d'EDO que de sorties donc p EDO pour p sorties
  - si plus d'EDO que de sorties alors on contraint trop le système qui peuvent passer de contraintes dynamiques à des contraintes algébriques (potentiellement)
  - contraintes dynamiques = equations que les variables doivent respectées qui sont propres au système ($x_1= ax_2+b$)
  - contraintes algébriques = fixer des variables ($x_1 = x_3 = 0$)

- si pas assez d'EDO que de sorties alors l'unicité des solutions n'est pas assurée


On introduit l'opérateur différentiel: $D = \dfrac{d}{dt}$
  - donc si on écrit $D^k$ on comprend la composition D avec lui meme k fois

Ceci pour concaténer le modèle précédent dans un **modèle compact**

CR.Cours0831.Eq2

On obtient un **modèle temporel E/S** :

$$
L(D) \cdot y(t) = M(D) \cdot u(t)
$$

Exemple:
CR.Cours0831.Ex1

- $M(D)$ ne fait que combiner les entrées
- $L(D)$ contient la dynamique du système
- Méthode de résolution d'une EDO
  - primo on se pose la question de l'ordre
    - ceci nous permet de connaitre le nombre de CIs nécessaire à la résolution du systeme

Rem: Comment déterminer l'ordre grâce à $L(D)$
- Si $L(D)$ est tri. inf./sup. et les degrés de D sur les colonnes sont croissant alors 


pivot de gaus forme algo de la forme Lu

Lemme:
CR.Cours0831.Lemme1

Théorème:
CR.Cours0831.Thm1

Donc on pourrait avoir des situations où le degré est diminuer par le $det$ ce qui nous permettrez d'avoir besoin de moins de CIs.

Exemple:
CR.Cours0831.Ex2

- On a besoin que d'une CI sur l'une des deux entrées

##### Les modèles fréquentiels

Les modèles fréquentiels utilisent la transformée de laplace (partant par exemple d'EDO).

Dans le cas monovariable, le modèle s'écrit: $F(s) = \dfrac{Y(s)}{\;U(s)\;}$

Dans le cas multivariable, le modèle s'écrit: $Y(s) = F(s) \cdot U(s)$ avec $Y(s) \in \mathbb{C}^p[s]$ et $U(s) \in \mathbb{C}^m[s]$ donc $F(s) \in \mathbb{C}^{p\times m}[s]$

Exemple:
$$
F(s) = \begin{bmatrix} \frac{1}{s+1}&\frac{1}{s}\\ \frac{1}{s+2}&\frac{1}{(s+1)(s+2)}\\ \end{bmatrix}
$$

Du coup, 

CR.Cours0831.

Mtnt que peut-on faire avec cette matrice F, on va chercher à :
- définir l'ordre du modèle
- définir les pôles
  - important pour analyser la stabilité
  - savoir bloquer les pertubations via les zéros
    - mais attention si on factorise $F(s)$ on risque de créer des zéros artificiels et donc on peut changer la dynamique du système
  - si mtnt on ajoute au Num et au Den un poly on se retrouve par imposer une nouvelle CI fictive qui sera ou pas observable

###### Définitions (Ordre/Zéro/Pôles) d'une FT

- si la matrice $F(s)$ est sous forme diagonale alors on peut facilement déterminer l'ordre/zero/pole
- donc on va diagonaliser les matrices
- MAIS comment diagonaliser des matrices non carrées ?!! => utiliser la forme SMITH

> Notes Cours 08/31 - End

> Notes Cours 09/08 - Start

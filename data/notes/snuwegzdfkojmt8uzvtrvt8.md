
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par P. Muller, T. Pellegrini

---

> Notes RKA du 2023/02/02 - Start


Convolution fait une synthese local de la region couverte par le kernel.

# Exercice 1: VGG16

![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex01-01.png)
![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex01-02.png)

## Question 1

**Combien de paramètres ?**

$\text{nb params}\\
= \big(\text{kernel cols}\times\text{kernel lines}\times\text{canals}+\text{bias}\big)\times\text{number of filters}\\
= (3 \times 3 \times 3 + 1) \times 16 = 448$

## Question 2

1. **Quelle fonction d'activation pour classification binaire ?**

    On peut mettre n'importe qu'elle fonction entre 0 et 1 (par exemple [[sigmoide|B3.AA.CM.Intro#activation-sigmoide]]) puis une loss type [[BCE|B3.AA.CM.Intro#bce---binary-cross-entropy]]

2. **Même question pour une classification avec 10 classes mutuellement exclusives à
distinguer.**
    Avec plusieurs sorties, on utilise [[softmax|B3.AA.CM.Intro#softmax]]

3. Toujours avec 10 classes différentes, comment coder ces classes pour un reseau de neuronnes ? Donner le nom de ce type d'encodage.

    - Dans des applications discrètes (type catégories d'age pour les assurances), on définit un vecteur de taille 10 avec des 0 et un 1 pour la classe à prédire.
    - On appele cette encodage le "**_one-hot encoding_**".

4. **Donner deux pré-traitements possibles sur des images données en entrée d'un réseau de neurones.**

    - Il faut normaliser l'image autrement le réseau de neuronnes peut être sensible ou variation de couleur/contraste
    - Une méthode de normalisation serait de diviser par le nb total de valeurs possible pour avoir des valeurs entre 0 et 1
    - Sinon on etale le spectre de l'image pour que la valeur min soit mise sur 0 et la valeur max soit mise sur 255.
    - L'autre pré-traitement possible serait de s'assurer que chaque entrée soit de meme taille.

## Question 3

1. **Combien de classes à prédire ?**

    - $1000$ classes vu que la sortie est de $1 \times 1 \times 1000$

2. **Quelle loss utiliser sachant que les classes sont exclusivwes ?**  
La _cross-entropy loss_ se définit comme suit:
$$
\mathcal{L}(y,\hat y) = -log(\hat y_c) = \mathbb{I}\{ i = c \} \overrightarrow{y} \; log \overrightarrow{\hat y} 
$$
C'est ici qu'il est intéréssant d'avoir du "**_one-hot encoding_**".

3. Quelle est le rôle du [[maxpooling|B3.AA.CM.CNN#max-pooling]] ?

    - Le rôle est de synthétiser l'entrée pour n'extraire que le plus important à la fin.
    - C'est pourquoi on l'applique après plus couches de convolution (à noter que sur l'image les pavés représentent le résultat après application du maxpooling ou des autres fontions en légende).
    - Voir ce site pour plus d'informations [step-by-step-vgg16-implementation-in-keras-for-beginners](https://towardsdatascience.com/step-by-step-vgg16-implementation-in-keras-for-beginners-a833c686ae6c).


# Exercice 2: Convolution 1-d

![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex02-01.png)

1. Calculer le résultat de la [[convolution|B3.AA.CM.CNN#implémentation]] sur $x$ avec le kernel $w$.

    - On assume pas padding et un slide de 1 et du coup une sortie de taille 2x1
    - $x = [2, 3, 0, -1]$
    - $w = [1, 2, -1]$
    - $y = [ 1 \times 2 + 2 \times 3 + -1 \times 0\;,\; 1 \times 3 + 2 \times 0 + -1 \times -1 ] = [8, 4]$

2. **Donner la matrice $W$ pour une multiplication $y = W x$**

    - $\begin{bmatrix} 8\\ 4\end{bmatrix} = \begin{bmatrix}1&2&-1&0\\0&1&2&-1\end{bmatrix}\times\begin{bmatrix}2\\3\\0\\-1\end{bmatrix}$

3. **Quelle est la taille du résultat de cette convolution ?**
    
    - Elle est de $2\times 1$.

![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex02-02.png)

1. Calculer $z = W^t\times y$ (sans y transposée)

    - Ceci est la **convolution transposée**
    - Unet

2. $4 \times 1$

<!-- # Exercice 3: Champ récepteur
!!!
... -->

# Exercice 4: Convolution 2D Standard

## Question 1)

![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-01.png)
![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-02.png)
![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-03.png)
![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-04.png)


1. **Dimension du résultat ?**

    - Le résultat de cette convolution serait de $4\times 2$

2. **Quel est le tenseur résultat `m(input,w)` ?**

    ![](/assets/images/B3.AA.TD2.Convolution.BB20230202-1.png)
    $a = 1 +2\times 1/2 + 5/3 + 3/2 + (-1)\times(-1) + 1 + 5/3 + 3/2 = 31/3$

3. **Application matricielle:**

    ![](/assets/images/B3.AA.TD2.Convolution.BB20230202-2.png)  


<!-- ## Question 2)

![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-05.png)
![](/assets/images/B3.AA.TD2.Convolution.Sujet-Ex04-06.png) -->




> Notes RKA du 2023/02/02 - End

---
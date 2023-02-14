
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par P. Muller, T. Pellegrini

---

> Notes RKA du 2023/01/30 - Start





![](/assets/images/B3.AA.CM.CNN.Slide-01.png)

# Problématique

## Qu'est-ce qu'une image pour l'ordinateur ?

![](/assets/images/B3.AA.CM.CNN.Slide-02.png)
![](/assets/images/B3.AA.CM.CNN.Slide-05.png)

La problématique est de pourvoir reconnaître des motifs à partir de cette information.

## Exemple de tâche en Computer Vision

![](/assets/images/B3.AA.CM.CNN.Slide-06.png)
![](/assets/images/B3.AA.CM.CNN.Slide-07.png)

Pour reconnaitre des motifs, il faut d'abord définir ces motifs. C'est le role des _features_ (i.e. des descripteurs).

## Premières approches possibles

![](/assets/images/B3.AA.CM.CNN.Slide-08.png)

- Approche par descripteurs --> dépendant des choix descripteurs
- Approche vectorielle --> pb changement d'échelle

### Approche connectée

![](/assets/images/B3.AA.CM.CNN.Slide-10.png)
![](/assets/images/B3.AA.CM.CNN.Slide-11.png)

### Approche hiérarchique/convolutive

> Keywords: Representation Learning

![](/assets/images/B3.AA.CM.CNN.Slide-13.png)

# Sommaire

![](/assets/images/B3.AA.CM.CNN.Slide-14.png)

# I- Introduction

## Suivre ISS

![](/assets/images/B3.AA.CM.CNN.Slide-15.png)
![](/assets/images/B3.AA.CM.CNN.Slide-16.png)

## Terminologie

> Keywords:
- entrée ; 
- noyau/kernel ;
- carte de caractéristiques/feature map

![](/assets/images/B3.AA.CM.CNN.Slide-17.png)

On n'utilise pas la convolution sur des entrées de mots ou de texte car il existe de meilleurs algorithmes (même si on peut classifier des mots avec un CNN).

## Implémentation

> Keywords:
- Tenseurs

![](/assets/images/B3.AA.CM.CNN.Slide-18.png)

## Propriétés

> Keywords:
- Corrélation croisée
- commutative (non pertinente ici)

![](/assets/images/B3.AA.CM.CNN.Slide-19.png)

## Illustration

> Keywords:
- Activation map = feature map

Ici on fait de la convolution valide (l'algo s'éxécute jusqu'à qu'il n'y ait plus de pixel). D'où le fait que l'image de sortie n'est pas la même taille (il existe des formules pour connaître la taille de la sortie à l'avance).

![](/assets/images/B3.AA.CM.CNN.Slide-20.png)
![](/assets/images/B3.AA.CM.CNN.Slide-21.png)
![](/assets/images/B3.AA.CM.CNN.Slide-22.png)

## Ex: Détection de bords verticaux

### Bords Verticaux

![](/assets/images/B3.AA.CM.CNN.Slide-24.png)
![](/assets/images/B3.AA.CM.CNN.Slide-25.png)

### Bords Horizentaux

![](/assets/images/B3.AA.CM.CNN.Slide-26.png)

### Bords Complexes

![](/assets/images/B3.AA.CM.CNN.Slide-27.png)
![](/assets/images/B3.AA.CM.CNN.Slide-28.png)

## Apprentissage

![](/assets/images/B3.AA.CM.CNN.Slide-29.png)

### Exemple

![](/assets/images/B3.AA.CM.CNN.Slide-30.png)

## Couche de convolution

> Keywords:
- connectivité locale ;
- partage des poids ;
- invariance par translation

![](/assets/images/B3.AA.CM.CNN.Slide-31.png)

## Multicanal

![](/assets/images/B3.AA.CM.CNN.Slide-32.png)

Un filtre ici est composé de 3 matrices (et optionnellement un biai). C'est pour appliquer un ou des filtres sur chaque canal. Ici il y a deux filtres donc la sortie est à deux canaux et donc la couche suivante appliquerait un filte à 2 canaux.

![](/assets/images/B3.AA.CM.CNN.Slide-33.png)

- [source](https://cs231n.github.io/convolutional-networks/)


## Conv2d en Pytorch

![](/assets/images/B3.AA.CM.CNN.Slide-34.png)

```python
import torch
import torch.nn as nn

m = nn.Conv2d(8, 16, 3)
# 8 canals
# 16 filters
# kernel size of 3 by 3

x = torch.randn(2, 8, 50, 100)
# 2 images
# with 8 canals
# of size 50 by 100

out = m(x)
out.size()
```

Combien de paramètres ?

$\text{nb params}\\
= \big(\text{kernel cols}\times\text{kernel lines}\times\text{canals}+\text{bias}\big)\times\text{number of filters}\\
= (3 \times 3 \times 8 + 1) \times 16 = 1168$

![](/assets/images/B3.AA.CM.CNN.Slide-35.png)

```python
import torch
import torch.nn as nn

m = nn.Conv2d(8, 16, 3)
# 8 canals
# 16 filters
# kernel size of 3 by 3

x = torch.randn(2, 8, 50, 100)
# 2 images
# with 8 canals
# of size 50 by 100

out = m(x)

print("Taille de la sortie:", out.size())
print("Taille des tenseurs de m:")
print("  Poids: ", m.weight.shape)
print("  Biais: ", m.bias.shape)
```


## Convolition Vizualizer

![](/assets/images/B3.AA.CM.CNN.Slide-36.png)

Dans ce [Convolition Vizualizer](https://ezyang.github.io/convolution-visualizer/), on peut visualiser:
- comment se calcul la convolution ;
- l'utilité de la dilation (dilater le filtre)
- l'utilité de la stride (sauter le pas)
- l'utilité du zero-padding (rajouter des pixels à zero pour contrôler la taille de l'image en sortie)

```python
nn.Conv2d(
    in_channels = 3, # RGB
    out_channels = 32, # 32 filters each with 3 layers
    kernel_size = (3,5), # filter of size 3 by 5
    bias = True, # bias is by default at true !
    padding = 0, # no zero-padding
    dilation = 2 # weights spread each 2 pixels
)
```

## Implémentation sous-jacente de PyTorch

### GEMM - General Matrix Multiplication

> Keywords: Matrices denses

![](/assets/images/B3.AA.CM.CNN.Slide-37.png)

### Im2Col

![](/assets/images/B3.AA.CM.CNN.Slide-38.png)

### Forward

> Keywords: poids ; flatten operation

![](/assets/images/B3.AA.CM.CNN.Slide-39.png)

### Backward

> Keywords: gradient de la sortie ; cuBlas

![](/assets/images/B3.AA.CM.CNN.Slide-40.png)
![](/assets/images/B3.AA.CM.CNN.Slide-41.png)

### Winograd

![](/assets/images/B3.AA.CM.CNN.Slide-42.png)

Cela peut être intéressant en fonction de la taille du kernel de faire la transformée de fourrier pour que le calcul de la convolution deviennent une simple opération matricielle.

## Bilan

![](/assets/images/B3.AA.CM.CNN.Slide-43.png)

## Max-Pooling

![](/assets/images/B3.AA.CM.CNN.Slide-44.png)

Ce n'est plus de la convolution, on calcul ici le max des 4 pixels de la zone rouge et ainsi de suite.

## Champ réceptif (Receptive Field)

![](/assets/images/B3.AA.CM.CNN.Slide-45.png)

## Réseau LeNet

![](/assets/images/B3.AA.CM.CNN.Slide-46.png)

## Réseau AlexNet

![](/assets/images/B3.AA.CM.CNN.Slide-47.png)

## Réseau VGGNet

![](/assets/images/B3.AA.CM.CNN.Slide-48.png)

## Démo en ligne

![](/assets/images/B3.AA.CM.CNN.Slide-49.png)
![](/assets/images/B3.AA.CM.CNN.Slide-50.png)

## Couche de Batch-normalisation

![](/assets/images/B3.AA.CM.CNN.Slide-51.png)
![](/assets/images/B3.AA.CM.CNN.Slide-52.png)

## Autres couches de normalisation

![](/assets/images/B3.AA.CM.CNN.Slide-53.png)

## FCN - Fully convolutional Network
![](/assets/images/B3.AA.CM.CNN.Slide-54.png)
![](/assets/images/B3.AA.CM.CNN.Slide-55.png)

## Residual Networks (ResNet)

![](/assets/images/B3.AA.CM.CNN.Slide-56.png)

sur-apprentissage

![](/assets/images/B3.AA.CM.CNN.Slide-57.png)
![](/assets/images/B3.AA.CM.CNN.Slide-58.png)
![](/assets/images/B3.AA.CM.CNN.Slide-59.png)
![](/assets/images/B3.AA.CM.CNN.Slide-60.png)

## Autres types de convolution

![](/assets/images/B3.AA.CM.CNN.Slide-61.png)
![](/assets/images/B3.AA.CM.CNN.Slide-62.png)

depthwise c'est rajouté le groups = 8

![](/assets/images/B3.AA.CM.CNN.Slide-63.png)

on somme comb lin

## L'architecture Xception

![](/assets/images/B3.AA.CM.CNN.Slide-64.png)

## L'architecture Convmixer

![](/assets/images/B3.AA.CM.CNN.Slide-65.png)

## La convolution dilatée

![](/assets/images/B3.AA.CM.CNN.Slide-66.png)

## La convolution sur un signal sonore

![](/assets/images/B3.AA.CM.CNN.Slide-67.png)

## La convolution sur des données textuelles

![](/assets/images/B3.AA.CM.CNN.Slide-68.png)

### Plongements de mots (word embeddings)

![](/assets/images/B3.AA.CM.CNN.Slide-69.png)
![](/assets/images/B3.AA.CM.CNN.Slide-70.png)

### Remarques

![](/assets/images/B3.AA.CM.CNN.Slide-71.png)
![](/assets/images/B3.AA.CM.CNN.Slide-72.png)

## Vers l'interpratibilité des CNN

> Keywords:
- visualisation de cartes par maximisation des activations
- Deepviz: Deep Visualization Toolbox
- Images adversaires
- Softmax
- Régularisation
- Flouttage gaussien
- Mise à zéro

![](/assets/images/B3.AA.CM.CNN.Slide-73.png)
![](/assets/images/B3.AA.CM.CNN.Slide-74.png)
![](/assets/images/B3.AA.CM.CNN.Slide-75.png)
![](/assets/images/B3.AA.CM.CNN.Slide-76.png)
![](/assets/images/B3.AA.CM.CNN.Slide-77.png)
![](/assets/images/B3.AA.TP2.BB20230130-1.png)
![](/assets/images/B3.AA.TP2.BB20230130-2.png)

Dans l'idée on cherche à approximer un nuage de point par une fonction qui passe aux plus proche de ces points. Plus la fonction sera précise plus cela induira de variance. C'est pourquoi il est parfois préférable de régulariser le taux d'apprentrissage pour éviter ces excès de variations tout en ayant un apprentissage efficace/optimal.

## Résumé CNN

![](/assets/images/B3.AA.CM.CNN.Slide-78.png)




> Notes RKA du 2023/01/30 - End

---
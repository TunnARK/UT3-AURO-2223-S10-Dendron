
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par F. Lerasle

---

> Notes du 2022/09/29 - Start





![](/assets/images/VIRCRV.CM.Vision-01.png)

# Introduction

![](/assets/images/VIRCRV.CM.Vision-02.png)


## Traitement et niveaux de représentation

<!--![](/assets/images/VIRCRV.CM.Vision-03.png)-->
![](/assets/images/VIRCRV.CM.Vision-03-notesprof.png)

Photos: Compagnie agricole ??? 
- encemencement des graines de tournesol
- graines non fertile appelé sclérote
- du coup utiliser une camera pour decteter les sclerote afin de les trier

Rem.: Incroyable comment on peut réaliser des mesures sans intéragir avec l'objet

- Controles de conformite sur produit fini = faire le control en fin de chaine
- Controles de conformite sur matiere premiere = faire le control en debut de chaine
- Controles aussi pour les moments critiques

> Dissocier le processus hors-ligne de prototypage liée à la conception au processus enligne que le client utilise

## Définitions

### Image

<!--![](/assets/images/VIRCRV.CM.Vision-04.png)-->
![](/assets/images/VIRCRV.CM.Vision-04-notesprof.png)


### Colorimétrie

<!--![](/assets/images/VIRCRV.CM.Vision-05.png)-->
![](/assets/images/VIRCRV.CM.Vision-05-notesprof.png)
![](/assets/images/VIRCRV.CM.Vision-06.png)
![](/assets/images/VIRCRV.CM.Vision-07-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-07.png)-->

pixel achrome = pixel avec meme valeur en RGB -> donne toute la palette du noir au blanc en passant par seulement les nuances de gris

Synthèse additive -> primaire = Rouge Vert Bleu
Synthèse soustractive -> primaire = Cyan Vert Bleu

Systèmes perceptuels -> rouge foncé (précise la teinte et luminosité)

Analyse Composante Principale (ACP)

![](/assets/images/VIRCRV.CM.Vision-08-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-08.png)-->

Changer d'espace colorimétrique pour se placer dans un espace colorimétrique moins affecter par les conditions de luminosité

![](/assets/images/VIRCRV.CM.Vision-09-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-09.png)-->

Intensité Teinte Saturation (ITS)
- Rouge par convention à une teinte noté avec un angle de 0 deg

Hue Saturation Values (HSV)

Idée: Se placer dans un espace ITS pour ignorer le plan 'luminosité' et ne considérer que les axes de 'teinte' et de 'saturation' pour ne plus avoir les problemes liées aux conditions d'illumination

### Segmentation HSV

Méthode :
1. Passer du RGB en HSV
2. Faire un seuillage sur H et un autre sur S
3. Calculer le ET logique de ces deux seuillages
4. Appliquer la huit-conexité (ou la 4 connexité) pour avoir le contour

![](/assets/images/VIRCRV.CM.Vision-10.png)

![](/assets/images/VIRCRV.CM.Vision-11-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-11.png)-->
![](/assets/images/VIRCRV.CM.Vision-12-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-12.png)-->
![](/assets/images/VIRCRV.CM.Vision-13-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-13.png)-->
![](/assets/images/VIRCRV.CM.Vision-14.png)

![](/assets/images/VIRCRV.CM.Vision-15.png)

# Acquisition des images

![](/assets/images/VIRCRV.CM.Vision-16-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-16.png)-->

## Optique de caméra

![](/assets/images/VIRCRV.CM.Vision-17.png)

## Paramètre d'une optique

![](/assets/images/VIRCRV.CM.Vision-18-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-18.png)-->

> Mise au point automatique dans les cameras du publique mais en industrie elle est faite manuellement pour plus de precision

![](/assets/images/VIRCRV.CM.Vision-19-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-19.png)-->
suite geometrique de raison $\sqrt2$ car l'optique se compose d'un cylindre avec la hauteur (diaphragme) et la section

- temps d'acquisition = frame per seconds => 40ms pour une image
temps d'exposition = duree entre ouverture et fermeture du diaphragme


![](/assets/images/VIRCRV.CM.Vision-20.png)

Si image dynamique reflexe augmenter le diaphragme et diminuer le temps d'exposition

Ex: controle qualite de bobine photo
- pb de compromis entre temps exposition et vitesses d'acquisition 
    - si temps exposition trop court alors manque de contraste
    - du coup rajout d'un flash synchronisé avec la camera pour avoir assez de contraste tout en gardant un temps d'exposition court

![](/assets/images/VIRCRV.CM.Vision-21-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-21.png)-->

Taille de capteur très petite => trop peu sensible (donc très sombre)

## Comment choisir une optique

![](/assets/images/VIRCRV.CM.Vision-22.png)

> Attention avec les montures C et CS qui ne sont pas compatibles !

## Aberrations optiques

![](/assets/images/VIRCRV.CM.Vision-23-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-23.png)-->

![](/assets/images/VIRCRV.CM.Vision-24-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-24.png)-->





> Notes du 2022/09/29 - End

---

> Notes du 2022/10/07 - Start




# Capteurs vidéo

![](/assets/images/VIRCRV.CM.Vision-25.png)

- On dissocie l'optique du capteur
- Le capteur contient la rétine

## Technologie CCD

![](/assets/images/VIRCRV.CM.Vision-26-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-26.png)-->

- **photo-élément**: surface élementaire sur la rétine (analogie aux pixel sur les cams du smarthone)
- Bande de valence: energie de la lumière impacte le comportement des electrons ce qui peut etre traduit en niveau de gris 
- à la base (à la sortie de la rétine) on peut lire avec un oscilloscope une ondulation
- **obturateur** paramètré par le temps d'exposition
    - utile pour les scenes dynamiques
- CCD est une technologie industrielle car la CMOS est moins chères

## Capteur CMOS

![](/assets/images/VIRCRV.CM.Vision-27-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-27.png)-->

- CMOS complémentaire
- Technologie moins chère
- Différence principale: conversion directe de la charge avant transfert
    - photo-élément à une double fonction la lecture en tension de la lumière et la conversion directe
- _rolling shutter_
    - propre au CMOS
    - problème historique du CMOS: 
        - photo element partage sa partie sensible avec une partie electronique
        - du coup un photo-element est moins sensible qu'un CCD
        - mais de nos jours il y a une tendance de faire du multi couche donc continue à s'améliorer
    - obturateur déroulant: obturateur fonctionne ligne par ligne
    - du coup probleme de floutage (trainée) dans les scenes dynamique avec obturateur deroullant

## Numérisation

![](/assets/images/VIRCRV.CM.Vision-32-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-32.png)-->

- 4/3 dû au dimension de la rétine
- Quantification:
    - les tensions sont des valeurs non entières
    - similaire à l'approximation d'une courbe par palier
- Pourquoi un pixel est codé sur 8 bits ?
    - Lié au rapport signal sur bruit
    - Quantification de la tension en 256 niveaux donc 8 bits
    
## Caméra couleur

![](/assets/images/VIRCRV.CM.Vision-28-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-28.png)-->

- Mosäique Bayer très utilisée
- Problème chaque photoE n'a qu'une couleur associée donc pour avoir sur chaque photoE les trois couleurs on fait un moyennage des vosins pour créer artificiellement un trio RVB
- Video projecteur plus sensible au vert donc plus de vert dans la mosäique de Bayer
- Probleme le moyennage introduit du floutage

![](/assets/images/VIRCRV.CM.Vision-29-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-29.png)-->

- Application très spécifique industrielle avec un besoin coloréfique important

## Caméra linéaire

![](/assets/images/VIRCRV.CM.Vision-30-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-30.png)-->

- Scannères sont des caméras linéaires et non pas matricielle
- Résolution horizental fixé par la caméra linéaire mais la résolution vertical est libre et dépend de l'application
- Résolution image (en pixel) et différente de la résolution spatiale
- Meme si on paramètre le groupe de lignes à 480 avec une caméra de 640 photoE (donc on aurait une résolution image en pixel de 640x480) il reste que l'on controle le mouvement et donc la résolution spatiale

## Caméra Infra Rouge

![](/assets/images/VIRCRV.CM.Vision-31-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-31.png)-->

## Transmission de l'image

![](/assets/images/VIRCRV.CM.Vision-33.png)

## Exercices 

![](/assets/images/VIRCRV.CM.Vision-34-notesprof.png)
<!--![](/assets/images/VIRCRV.CM.Vision-34.png)-->

### Solutions

- [VIRCRV.Vision.ExoCapteurs2D.Correction.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/VIRCRV.Vision.ExoCapteurs2D.Correction.pdf)

![](/assets/images/VIRCRV.CM.Vision-34-exonotesprof.png)


#### Q1

- Focal très grande car on veut bcp de précision sur la scène qui se trouve à 2m
- si pixel n'était pas carré alors une boite carré apparaitré non carrée dans l'image idem pour un cercle qui sera vue comme une ellipse
- On pourrait adapter ce probleme à une caméra linéaire

#### Q2

- F nombre d'ouverture
- Coincé par le contexte pour faire la mise au point => solution ajouter une bague entre optique et capteur et ainsi pouvoir continuer à paramétrer $p_1$
- Indirectement c'est un système de mesure/réalisation 3D car selon le floutage on peut déduire si la scène se trouve devant ou derrière le plan à 45mm




> Notes du 2022/09/29 - End

---

> Notes du 2022/11/15 - Start

> ! Cf [Notes GEA 2022/11/15]()

> Notes du 2022/11/15 - End

---

> Notes du 2022/11/16 - Start

# Exemples

## Métrologie

![](/assets/images/VIRCRV.CM.Vision-47.png)

Les tests sont au final des expériences probabilistes. On compare les tolérances a priori pour conclure sur la conformité.

![](/assets/images/VIRCRV.CM.Vision-Extra26.png)

on cherche a maximiser les True Positive (TP) et minimiser les False Positive (FP)

> Courbe ROC: TPR vs FPR (on cherche a etre au coin haut gauche pour 100% de TP et 0% de FP)

Dans le cas de l'application pour les motards pour detecter les chutes on cherche à minimiser les FN

## Vérifciation de présence

![](/assets/images/VIRCRV.CM.Vision-48.png)

éclairage diffu pour eviter la saturation

faire un sous zone de recherche pour limiter le temps de calcul et aussi pour mieux trouver la valeur de seuil (seuillage)

au final il y a pas forcement besoin de connaitre la position precise ni approximative pour placer les zones de test

en effet on peut positionner ces sous-zones relative à la position d'un point caractéristique utiliser comme ancrage

![](/assets/images/VIRCRV.CM.Vision-49.png)

transformation logarithmique des fréquences occurences de nuance de gris (ndg) ce qui conduit a un tassement des ndg de forte occurence

On peut aussi juste faire du block matching (ou aussi template matching) (comparer l'image test avec une image de reference)


![](/assets/images/VIRCRV.CM.Vision-50.png)


## Identification de marqueurs

![](/assets/images/VIRCRV.CM.Vision-51.png)
![](/assets/images/VIRCRV.CM.Vision-52.png)

Approche non ascendante car pas de segmentation

![](/assets/images/VIRCRV.CM.Vision-53.png)

> ROI: Region of Interet

Attention a la variation d'echelle quand des pieces sont en vracs tout en etant empiller les unes sur les autres (multi-template matching)

discretisation en position, orientation et echelle

ATTENTION la discretisation en ndg dépend fortement des conditions d'illumination (donc ne marche que pour un environement controlé)

## Contrôles de conformité multiples

![](/assets/images/VIRCRV.CM.Vision-54.png)
![](/assets/images/VIRCRV.CM.Vision-55.png)

les cameras sont a 90 deg pour s'assurer de percevoir l'orientation en z de la bouteille

![](/assets/images/VIRCRV.CM.Vision-56.png)

# Descripteurs de région

## Géométrique

![](/assets/images/VIRCRV.CM.Vision-57.png)

direction par intercepts: on compte les nombres d'entrées dans une région sur une direction donnée

![](/assets/images/VIRCRV.CM.Vision-58.png)

$\mu_{20} = \sum \sum (x-\bar x)^2f(x,y)$ calcule la dispersion p.r.à l'image de ref le long de l'axe $x$

invariance à la translation grace aux centre de gravité

invariance à l'echelle grace à la normalisation par $\mu_{00}$

> 7 moments de Hu: hors programme

![](/assets/images/VIRCRV.CM.Vision-58-extra.png)


![](/assets/images/VIRCRV.CM.Vision-59.png)

mesure de changement de pente de la tangente à la courbe 

calcul compliqué donc calcul estimé

pas aisé de fixer la longeur de corde

> corde: distance en pixel

exemple roulement à bille: on a calculer lecart type sur la courbure pour determiner si la piece est conforme

## Couleur

![](/assets/images/VIRCRV.CM.Vision-60.png)

> skew: mesure de distribution asymétrique

> NbL: Nombre Ligne

> NbC: Nombre Colonne

Exemple histogramme couleur pour discretiser des personnes dans une foule

Flot de drone avec camera pour trouver les pommes mûres dans le champs

![](/assets/images/VIRCRV.CM.Vision-60-Extra.png)





> Notes du 2022/11/16 - End

---

> Notes du 2022/11/18 - Start


## Texture

![](/assets/images/VIRCRV.CM.Vision-61.png)

Stats d'ordre 1 ne prenne pas en compte les charactéristiques spatiales de l'image alors que les stats d'ordre 2 les prend en compte grace aux paires de pixel.

> BRODATZ: peintre qui a classifié les différents types de textures en peintures

# Descripteurs et recalage

## En Position

![](/assets/images/VIRCRV.CM.Vision-62.png)

Recalage:
- on prend l'objet entier avec eclairage arriere (backlit) pour calculer le Centre de Gravité (pb les reflets peuvent rendre imprécis le CdG)
- chercher un pattern caractéristique pour loacaliser plus précisemment l'objet dans l'image

## En Orientation

![](/assets/images/VIRCRV.CM.Vision-63.png)

Pour eviter les pb de temps de calcul, on peut n'exploiter que les points de contour

Autre option, c'est d'echantillonner l'objet avec un pas angulaire constant pour mesurer la distance entre le CdG et le coutour

On obtient ainsi un courbe caractéristique de l'objet (comme une signature) (droite pour le cercle, ...)

Pour calculer l'équation du cercel, on peut utiliser la transformé de Hough

![](/assets/images/VIRCRV.CM.Vision-64.png)

# Identification de marqueurs

> OCR Optical Character Recognition

![](/assets/images/VIRCRV.CM.Vision-65.png)

- éclairage rasant permet de trouver les caract. via le contrast entre fond lisse et partie imprimée
- ceci permet de définir ensuite des zones de region contenant le caract.
- cette zone sera ensuite traité par un reseau de neurones pour identifier le caract.

![](/assets/images/VIRCRV.CM.Vision-66.png)
![](/assets/images/VIRCRV.CM.Vision-67.png)

# Controles de conformité multiples

![](/assets/images/VIRCRV.CM.Vision-68.png)
![](/assets/images/VIRCRV.CM.Vision-69.png)
![](/assets/images/VIRCRV.CM.Vision-70.png)

# Manipulation robotique

![](/assets/images/VIRCRV.CM.Vision-71.png)

## Edge-based Template Matching

![](/assets/images/VIRCRV.CM.Vision-72.png)

- extraction de contour pour ensuite faire des statistiques et discrétiser les orientations des contours
- ceci permet diminuer le bruit et le cout CPU

![](/assets/images/VIRCRV.CM.Vision-73.png)

## Exemple 

![](/assets/images/VIRCRV.CM.Vision-74.png)
![](/assets/images/VIRCRV.CM.Vision-75.png)

Voir l'annale 2 pour une démonstration de l'homographie

# Bibliographie

![](/assets/images/VIRCRV.CM.Vision-76.png)



> Notes du 2022/11/18 - End

---



<!--


> Notes du 2022/ - Start

VIRCRV.CM.Vision--notesprof



# Techniques d'éclairage

![](/assets/images/VIRCRV.CM.Vision-35.png)

## Types d'éclaire

![](/assets/images/VIRCRV.CM.Vision-36.png)
![](/assets/images/VIRCRV.CM.Vision-37.png)
![](/assets/images/VIRCRV.CM.Vision-38.png)
![](/assets/images/VIRCRV.CM.Vision-39.png)
![](/assets/images/VIRCRV.CM.Vision-40.png)
![](/assets/images/VIRCRV.CM.Vision-41.png)
![](/assets/images/VIRCRV.CM.Vision-42.png)
![](/assets/images/VIRCRV.CM.Vision-43.png)
![](/assets/images/VIRCRV.CM.Vision-44.png)
![](/assets/images/VIRCRV.CM.Vision-45.png)
![](/assets/images/VIRCRV.CM.Vision-46.png)






-->
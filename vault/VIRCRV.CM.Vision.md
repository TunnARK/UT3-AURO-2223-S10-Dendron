---
id: 5ik24tbt9rliemwqv3srnf1
title: Chap 4 - Vision Industrielle
desc: ''
updated: 1664458180987
created: 1664451302770
---

> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

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

<!--
> Notes du 2022/09/??? - Start





VIRCRV.CM.Vision--notesprof


# Capteurs vidéo
![](/assets/images/VIRCRV.CM.Vision-25.png)
![](/assets/images/VIRCRV.CM.Vision-26.png)
![](/assets/images/VIRCRV.CM.Vision-27.png)
![](/assets/images/VIRCRV.CM.Vision-28.png)
![](/assets/images/VIRCRV.CM.Vision-29.png)
![](/assets/images/VIRCRV.CM.Vision-30.png)
![](/assets/images/VIRCRV.CM.Vision-31.png)
![](/assets/images/VIRCRV.CM.Vision-32.png)
![](/assets/images/VIRCRV.CM.Vision-33.png)
![](/assets/images/VIRCRV.CM.Vision-34.png)
![](/assets/images/VIRCRV.CM.Vision-35.png)
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
![](/assets/images/VIRCRV.CM.Vision-47.png)
![](/assets/images/VIRCRV.CM.Vision-48.png)
![](/assets/images/VIRCRV.CM.Vision-49.png)
![](/assets/images/VIRCRV.CM.Vision-50.png)
![](/assets/images/VIRCRV.CM.Vision-51.png)
![](/assets/images/VIRCRV.CM.Vision-52.png)
![](/assets/images/VIRCRV.CM.Vision-53.png)
![](/assets/images/VIRCRV.CM.Vision-54.png)
![](/assets/images/VIRCRV.CM.Vision-55.png)
![](/assets/images/VIRCRV.CM.Vision-56.png)
![](/assets/images/VIRCRV.CM.Vision-57.png)
![](/assets/images/VIRCRV.CM.Vision-58.png)
![](/assets/images/VIRCRV.CM.Vision-59.png)
![](/assets/images/VIRCRV.CM.Vision-60.png)
![](/assets/images/VIRCRV.CM.Vision-61.png)
![](/assets/images/VIRCRV.CM.Vision-62.png)
![](/assets/images/VIRCRV.CM.Vision-63.png)
![](/assets/images/VIRCRV.CM.Vision-64.png)
![](/assets/images/VIRCRV.CM.Vision-65.png)
![](/assets/images/VIRCRV.CM.Vision-66.png)
![](/assets/images/VIRCRV.CM.Vision-67.png)
![](/assets/images/VIRCRV.CM.Vision-68.png)
![](/assets/images/VIRCRV.CM.Vision-69.png)
![](/assets/images/VIRCRV.CM.Vision-70.png)
![](/assets/images/VIRCRV.CM.Vision-71.png)
![](/assets/images/VIRCRV.CM.Vision-72.png)
![](/assets/images/VIRCRV.CM.Vision-73.png)
![](/assets/images/VIRCRV.CM.Vision-74.png)
![](/assets/images/VIRCRV.CM.Vision-75.png)
![](/assets/images/VIRCRV.CM.Vision-76.png)

-->
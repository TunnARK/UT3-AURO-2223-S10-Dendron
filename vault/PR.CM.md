---
id: m8oulcohrr23un16nfj1t1x
title: Notes de Cours
desc: ''
updated: 1663667555102
created: 1662990640798
---

- [lien moodle](https://moodle.univ-tlse3.fr/course/view.php?id=9035)

lerasle@laas.fr

---

> Notes du 2022/09/12 - Start



![](/assets/images/PR.CM.Poly-01.png)

# Introduction

![](/assets/images/PR.CM.Poly-02.png)

- pb de l'imagerie => distance ne sont pas conservé lors d'un changement de perspective
- de plus en plus de capteurs 3D
- capteur passif = n'emet pas de lumière pour percevoir / ne fait que les recevoir
- RGBD = couleur + depth
    - capture une image ou un flut RGB en couleur + une image de profondeur
    - s'appuit sur les apparances mais aussi sur des informations geométriques 

## Sommaire 

![](/assets/images/PR.CM.Poly-03.png)

## Optique d'une caméra

![](/assets/images/PR.CM.Poly-04.png)

Choix de caméra selon la problématique:
- il faut choisir une optique adaptée
- mais aussi le capteur qui correspond

Un pixel correspond à la disposition spatiale de la scène
Du coup plus on a besoin d'echantillon de la scene pour avoir des data precises plus il nous faudra de 'pixel'

Le capteur recoit des photos et les traduit en signal digital

![](/assets/images/PR.CM.Poly-05.png)

- AO point de la scene
- FO foyer objet
- centre optique = intersection entre axe optique et plan lentille ?
    - quand on change la mise au point on deplace le plan des lentilles sur l'axe optique
- axe optique (horizental)
- plan capteur
- p1 tirage optique (de l'epoque des camera avec accordeon car il tirer l'optique)
- p0 distance entre scene et optique
- F1 distance focal => modifie l'angle de champ
    - focal petit => grand champ
    - focal optimale pour ne pas perdre en precision et ne pas traiter des pixels inutiles

> grandissement transversal

> Relation de conjugaison

Pour objet loin p_0 -> infinie => f_1 = p_1 donc joue sur la mise en point du plan image

En 3D on assume souvent l'approximation que f_1 = q_1

![](/assets/images/PR.CM.Poly-06.png)

...




> Notes du 2022/09/12 - End

---

> Notes du 2022/09/14 - Start






![](/assets/images/PR.CM.SchemaResume.png)

- $\mathcal{R}_m$ référentiel de l'objet de référence (objet que l'on étudie)
- on passe au paramètre extrinsèque: 3 ; angle d'euler $\alpha_x \; \beta_y \; \gamma_z$
- $\mathcal{R}_C$ repere camera
- $u_0$ et $v_0$ sont presque le milieu de la photo
- $\alpha_u$ et $\alpha_v$ sont souvent egaux car les cameras sont souvent carree
    - $\alpha_u = ku f$
    - $\alpha_v = kv f$
- attention au signe va deprendre du repere camera

> Signe $\alpha_u$ et $\alpha_v$ important de le comprendre pour le TP d'etallonnage de camera

> Un francais qui a sorti le concept d'imagerie 3D

![](/assets/images/PR.CM.Poly-12.png)

### Distortion Optique

![](/assets/images/PR.CM.Poly-13.png)

> Toute image possede une distortion (surtout au bord)

En traitement image on n'est pas problematise par ce phenomene mais en traitement spatiale on a de suite un probleme (mais bcp de logiciel arrive a regle ce probleme)

- focal = distance du centre de l'objet p.r.à $\mathcal{R}_C$
- plus la focal est petit plus il y a de distortion
- image exemple de continental
- les corrections de distortion ne sont jamais parfaite

![](/assets/images/PR.CM.Distortion.png)

- terme radial $\Delta_ur$ et $\Delta_vr$
- terme tangentiel $\Delta_ut$ et $\Delta_vt$
- simplification: on assume que la distortion tangentiel est negligeable p.r.à la distortion radial 

![](/assets/images/PR.CM.RadialTangentiel.png)

- différent type de modele
    - radial ordre 1 et tangentiel ordre 0 -> r1t0 : k1 (k2=k3=p1=p2=0)
    - r3t0 : k1 k2 k3
    - r3t0 : k1 k2 k3 p1 p2

- de maniere empirique :
    - f>7mm => r1t0
    - f<7mm => r3t0 ou r3t2
    - il sera important de choisir le modele qui correpond à notre situation en expliquant le choix fait

![](/assets/images/PR.CM.DistortionEqModele.png)

Comment corriger une distortion ?

Idée:
1. de limage final prendre un pixel en (u,v) 
2. calculer (u_d,v_d)
    - Sauf qu'on va tomber sur des nombres non entier
3. considerer les pixel voisins
4. faire une ponderation de ce voisinage (interpolation biliniaire)
5. creer un pixel dans l'image final selon cette ponderation

![](/assets/images/PR.CM.Poly-14.png)

> Attention: $C(X) = \frac{1}{\;n\;} \sum (u_i ...$

- objet etalon (ou mir)
    - planche cadrier
    - openCV utilise un damier
- on va faire plusieurs mesures
    - extrinsèque vont changer (normal)
- N.B.: le choix du ref de l'etatlon n'impacte que les param extrinsèque

exemple:

![](/assets/images/PR.CM.ChangementBase.png)

- on prend un point etalon Pm
- on obtient le point camera Pc
- on cherche à avoir un changement de base qui nous amene de Pm à Pc en pasant par limage 3D produit (on doit tomber le meme pixel)
- sauf qu'on aura tj une erreur du coup on va minimiser ce delta

- N.B.: si l'etalon n'est pas parfaitement de niveau il faudra utilise une precision subpixel (optimisation non lineaire) pour chercher une croix dans une sous zone mise à jour à chaque iteration selon leloignement p.r.à un point ref

![](/assets/images/PR.CM.TableCorrective.png)

Apparrements 2D/3D

![](/assets/images/PR.CM.Apparrement2D3D.png)

![](/assets/images/PR.CM.Apparrement2D3DEq.png)



![](/assets/images/PR.CM.Poly-15.png)


### Mise en oeuvre

![](/assets/images/PR.CM.Poly-16.png)

![](/assets/images/PR.CM.Stereo.png)

![](/assets/images/PR.CM.StereoEqDroite.png)

![](/assets/images/PR.CM.StereoEqRotation.png)

### Stereo Passive

![](/assets/images/PR.CM.Poly-17.png)

![](/assets/images/PR.CM.StereoPassive.png)

QUESTION: si point 3D est tres lointin alors sur les plans stereo il sera tres proche => disparité




> Notes du 2022/09/14 - End

---

> Notes du 2022/09/16 - Start





PR.CM.BB20220916-01

- champ commun = intersection des champs respectifs des cameras
    > Attention 
- stereo == camera proche
- vision binoculaire == camera eloigne
- vergence = angle des axes optique
- profondeur de vision = region net
- phenoneme d'olcutation = trou d'ombre dans le champ commun
- une fois les deux images réalisées on va **appareiller** les pixels communs (mais comment savoir qu'un pixel est commun ?!)

- **la notion de camera synchrone:**
    - Stereo peut aussi se faire avec une seule qui prend un premier champ puis se deplace pour prendre un deuxieme champ => les prises de champs sont asynchrone
    - pour toute prise d'evenement dynamique (e.g. du mouvement relatif) il nous faut un certain niveau de synchronisation 
    - plus le mouvement relatif est rapide moins de retard il faut entre les deux prises de vues

#### Principe

![](/assets/images/PR.CM.Poly-18.png)

- denses ou eparse
    - quantité d'information collecté
    - depend de l'application
    - souvent du dense (prentendant qui a plus peut faire plus)
    - reconstruction dense => apparaiment dense (du coup peu optimal)

> CNES pro mondiaux de la stereo

- apparemment peut se faire sur des regions ou des formes (segments, points) mais ici on va rester sur les pixels
    - par exemple apparemment de segment est tres util pour des environnment "humains" car les formes sont tres geometriques
    - stereo segment = app. eparse de segment image
    - stereo correlation = app. dense de pixel

#### Appariemment (Block Matching???)

![](/assets/images/PR.CM.Poly-19.png)

- on suppose que l'effet perspective est faible car les cameras sont proches
- SSD = Sum Square Difference (square pour eviter d'avoir des cas n'annulation +1-1=0)
- cette app. ne marche pas sur des textures uniformes (murs de meme couleur, quadrillage, ...)
- la zone de recherche depend de la profondeur/distance de l'objet
    - plus l'objet est proche plus la zone de recherche sera décalée de la zone initiale
    - la connaissance de cette profondeur/distance est faite empiriquement (souvent on prend la zone la plus pessimiste)
- CC Cross Correlation
    - produit scalarie utilisé pour trouver le pixel commun
- **Zero Normalized Cross Correlation**
    - I et I' sont la moyenne des niveaux dans la fenetre
    - ecart type pour ???
    - on soustrait l'offset entre les deux images
    - on normalise car cela nous permet de plus facilement maitriser le seuil de validation (score de validation par exemple 0.6 en exterieur)
- l'app. impose un temps de calcul tres grand

#### Contrainte épipolaire

PR.CM.Epipolaire

La droite épipolaire est une droite image qui inclut tous les pixels candidats $p_2\in I_D$ du pixel $p_1\in I_G$

Or si cette droite epipolaire balaye une ligne du tableau de pixel (au lieu d'une diagonal) on a gagné car ce sera tres facile de parcourrir le tableau de pixel

Pour avoir un tel contexte il faut que les cameras soient **coplanaire**

De plus, on a meme pas besoin de balayé toute la ligne du tableau car quand le point est loin alors le pixel se trouve au meme endroit sur l'image de droite et donc selon à quelle distance on anticipe que l'objet est on va plus ou moins balayer un sous ensemble de cette ligne (c'est ce qu'on appele la disparité des pixels)

Cette disparité se calcule ainsi :$|v_1-v_2$

PR.CM.Disparite

Pour obtenir une configuration coplanaire (avec ou sans vergence), on peut :
- utiliser un logiciel virtuel pour realiser des rotations de l'image et avec un algo arriver vers une conf. coplanaire
- au CNES ils utilisent une methode mechanique pour trouver la conf afin d'eviter les temps de calculs

![](/assets/images/PR.CM.Poly-20.png)

#### Exemple

- chaise avec courbe en haut a droite 
- ocultation avec courbe en bas a gauche
- goudron avec courbe en bas a droite
- mur blanc avec courbe milieu

> si vous avez une reconstruction eparse jamais vous faites ???

![](/assets/images/PR.CM.Poly-21.png)

#### Reconstruction

![](/assets/images/PR.CM.Poly-22.png)

PR.CM.ReconstructionEq01

PR.CM.ReconstructionEq02

#### Recapitulatif

1. Reduction
    - On change la resolution (par exemple prendre qu'un pixel sur deux) consequence on reduit la resolution 3D
2. Filtre
3. Rectification+Correction Distortion
4. Calcul des variances
5. Calcul des scores de correlation
6. Estimation des disparités
7. Blob Filter

    Pour les valeurs homogenes on a de grand risque d'erreur d'app. (c'est cela que l'on filtre)
8. Reconstruction 3D

Limitations fortes = temps de calcul et textures non adaptés => peut amener à avoir des trous dans notre reconstruction 3D

#### Video LAAS 2001 Cartography

Comment savoir si une surface est navigable ?

1. Prendre 3 points
2. Faire le product vectoriel de ces points
3. Deduire la normal de la surfuce entre ces 3 points
4. Exclure les normal qui presente un angle trop fort entre la normal la vertical de notre repere de reference

Pour franchir un obstacle on va deduire des ces normals le plan d'élévation des obstacles

#### Video Dirigeable Karma-Slam

> Modélisation incrémentable = prendre pls perceptions d'une reconstruction 3D pour avoir un modele de l'envirronement qui soit perceptible sur 360 deg

#### Resoudre le probleme de texture repetee

Idée: Ajouter un eclairage qui va projeter un motif sur l'objet pour

Kinex => un des premier a avoir rajouté au stereo un projecteur

capteur a lumiere structuré = une camera et un projecteur

![](/assets/images/PR.CM.Poly-23.png)


#### Airbag

pour s'affranchir de perturbations de lumières extérieures ils ont travailler sur du proche infrarouge

![](/assets/images/PR.CM.Poly-24.png)

#### Exercice

![](/assets/images/PR.CM.Poly-25.png)

- config. de rectification ???

1. Lister les advantages/desadvantages de cette focale 

    Focal petite = grand champ mais distortion

2. Calculer le champ de vue vertical

    - $L_{min}$ distance aveugle
    - $\theta v$ demi-angle de champ 

    PR.CM.ExVoitQ2-01
    PR.CM.ExVoitQ2-02

3. Montrer $\alpha v = 105$ et en déduire la disparité à la distance min de perception puis celle à 3m et enfin à 5m

    PR.CM.ExVoitQ2-01
    PR.CM.ExVoitQ2-02
    PR.CM.ExVoitQ2-03
    PR.CM.ExVoitQ2-04

4. Conclure sur l'utilisation
    Créer une image de référence d'un sol plat pour le soustraire à l'acquisition réalisé sur le moment ce qui va alors faire resortir les delta entre vue reelle et vue de reference qui correspondent aux obstacles present sur le sol


### Stereo Active

![](/assets/images/PR.CM.Poly-27.png)

- RADAR
    - economique
- ultrasond
    - delta entre emission et reception
    - seulement precis sur courte distance
- lumiere structuree
    - profilometrie
    - RGB-D Red Green Blue and Depth (i.e. kinex) => geometrie de la salle (avec aussi l'apparence)
    - advantage p.r.à la stereo pour les surfaces repetitive et uniformes




> Notes du 2022/09/16 - End

---

> Notes du 2022/09/20 - Start



#### Télémètre Laser

![](/assets/images/PR.CM.Poly-28.png)
![](/assets/images/PR.CM.Poly-29.png)
PR.CM.ReflexionSpeculaire

- Selon l'angle choisit pour la déflexion on peut louper des pieds de table à chaque pas angulaire

#### Lumière structurée

![](/assets/images/PR.CM.Poly-30.png)

- En stereo les calculs d'apparai. necessite bcp de puissance alors qu'en structurée on ne qu'un apparai. de pixel à faisceau
- De plus on peut aussi projeter des couleurs et ainsi simplifier l'apparai.
- Rayure Noir Blanc = projection temporelle pour image statique
- Nape de couleur = projection statique color-coded pour image dynamique

![](/assets/images/PR.CM.Poly-31.png)


- Modèle Sténopé

![](/assets/images/PR.CM.Poly-32.png)

- La lumière structurée est utilisé pour trouver l'équation du plan et non pas pour reconstruire l'image car la camera seule peut reconstruire la scène connaissant l'equation du plan

##### Codage Binaire

![](/assets/images/PR.CM.Poly-33.png)
![](/assets/images/PR.CM.Poly-34.png)

- image virtuelle = construction de l'image mais projeté sur un plan focal

![](/assets/images/PR.CM.Poly-35.png)

Video debracage 3D resolut seulement récemment
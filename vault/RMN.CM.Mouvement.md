---
id: 0fi8ldj5eumhpm025u315bx
title: Mouvement
desc: ''
updated: 1664519795833
created: 1663336092100
---

> Notes du 2022/09/16 - Start

## Definition

![](/assets/images/RMN.CM.Mouvement-01.png)

> Pb non traité ici le dilem de bouger pour percevoir ou faire bouger l'objet pour le percevoir

## Problématique

![](/assets/images/RMN.CM.Mouvement-02.png)

![](/assets/images/RMN.CM.Mouvement-03.png)

![](/assets/images/RMN.CM.Mouvement-04.png)

> Couvrir un terrain est un probleme 'resolu' de nos jours

## Plannification

![](/assets/images/RMN.CM.Mouvement-05.png)

> Traduit le probleme sous forme geometrique

![](/assets/images/RMN.CM.Mouvement-06.png)

![](/assets/images/RMN.CM.Mouvement-07.png)

![](/assets/images/RMN.CM.Mouvement-08.png)

![](/assets/images/RMN.CM.Mouvement-09.png)

## Modélisation

### Carte Métrique

![](/assets/images/RMN.CM.Mouvement-10.png)

> Carte Métrique est une représentation des obstacles tres utile pour la plannification mais difficile à construire

### Carte d'amers

![](/assets/images/RMN.CM.Mouvement-11.png)

> Tres facile pour se localiser mais plannification difficile car informations eparses

### Carte grille d'occupation

![](/assets/images/RMN.CM.Mouvement-12.png)

### Carte d'élévation MNT

![](/assets/images/RMN.CM.Mouvement-13.png)

> Tres utile pour les terrains accidentés

> Probleme de passage à l'echelle (plus la surface est grande plus il y aura de points pour une meme resolution)

### Carte Topologique


![](/assets/images/RMN.CM.Mouvement-14.png)

> Creer des graphes topologiques pour trouver un chemin

> Pb: ne resoud pas le probleme de plannification

### Conclusion sur les cartes

![](/assets/images/RMN.CM.Mouvement-15.png)

> Attention lors de la correspondance entre carte (chaque carte peut avoir ses erreurs respectives)

## Espace de configuration

![](/assets/images/RMN.CM.Mouvement-16.png)

![](/assets/images/RMN.CM.Mouvement-17.png)

> Au lieu de faire bouger un objet 3D dans un espace 3D, on va faire bouger un point dans un espace 3D

La difficulté viendra lorsqu'on se deplace proche d'un obstacle (comme un poto) il faudra garder en tete que notre point represente un objet volumineux

Pour eviter cela on calculer la transformée de l'obstacle pour le faire apparaitre dans l'espace de configuration

### De l'espace de travail vers l'espace de configuration

![](/assets/images/RMN.CM.Mouvement-18.png)

![](/assets/images/RMN.CM.Mouvement-19.png)

![](/assets/images/RMN.CM.Mouvement-20.png)

![](/assets/images/RMN.CM.Mouvement-21.png)

![](/assets/images/RMN.CM.Mouvement-22.png)

### Exemple

![](/assets/images/RMN.CM.Mouvement-23.png)

### Différents sous-espaces de EC

![](/assets/images/RMN.CM.Mouvement-24.png)

#### EC de dim 3

![](/assets/images/RMN.CM.Mouvement-25.png)

> La complexite de plannification explose en passant d'un espace 2D à 3D

![](/assets/images/RMN.CM.Mouvement-26.png)

![](/assets/images/RMN.CM.Mouvement-27.png)

![](/assets/images/RMN.CM.Mouvement-28.png)

> La plannification va se traduire sur la surface du TOR


### Existence d'un chemin solution

![](/assets/images/RMN.CM.Mouvement-29.png)

> La métrique qu'on va utiliser dans l'espace de travail devra être bien choisie pour garantir que les algos converge de facon optimale lors de la resolution dans l'espace de configuration

> FREE-FLYER = un robot sans contrainte cinématique

![](/assets/images/RMN.CM.Mouvement-30.png)

## Plannification déterministe

![](/assets/images/RMN.CM.Mouvement-31.png)

> Attention ces méthodes sont obselètes de nos jours

### Roadmap

![](/assets/images/RMN.CM.Mouvement-32.png)
![](/assets/images/RMN.CM.Mouvement-33.png)
![](/assets/images/RMN.CM.Mouvement-34.png)

### Diag de Voronoï
![](/assets/images/RMN.CM.Mouvement-35.png)

## Décomposition polygonale exacte

![](/assets/images/RMN.CM.Mouvement-36.png)
![](/assets/images/RMN.CM.Mouvement-37.png)

## Décomposition approchée

![](/assets/images/RMN.CM.Mouvement-38.png)

> Advantage ceci nous donne aussi une notion de marge de manoeuvre car on sait que dans une cellule vide on peut faire des erreurs de commande de tant

![](/assets/images/RMN.CM.Mouvement-39.png)

> Methode superbe mais complexité exponentielle

Utile pour la vehicule autonome mais pas pour la robotique humanoide

## Champs de potentiel

![](/assets/images/RMN.CM.Mouvement-40.png)

> Le potentiel repulsifs et attractif peuvent se compenser et donc immobiliser le robot sans atteindre son but

![](/assets/images/RMN.CM.BB20220916-01.png)

![](/assets/images/RMN.CM.Mouvement-41.png)
![](/assets/images/RMN.CM.Mouvement-42.png)

Les mathématiciens ont essayé de trouver des fonctions de potentiel qui possèdent un minimaux global en continu mais comme ils n'ont pas reussi ils sont restés sur le cas discret.

## Plannification pour des robots non-holonomes

> CNH = Contrainte Non Holonome

![](/assets/images/RMN.CM.Mouvement-43.png)

### Small Time Controllable STC

![](/assets/images/RMN.CM.Mouvement-44.png)

> N.B.:
D'après Jean Michel Coron, la notion de Small Time Controllable se définit ainsi en autonomatique 
![](/assets/images/SmallTimeControllable.png)

### Existence d'un chemin pour robot NH-STC

#### Approche sur chemin holonome

> On calcul un chemin holonome puis on l'apprixme en chemin non holonome qui respecte la contrainte non holonome

![](/assets/images/RMN.CM.Mouvement-45.png)

> Si la méthode de calcul de la trajectoire dans ECL est complète alors la méthode de calcul de la trajectoire pour le robot NH est complète

![](/assets/images/RMN.CM.Mouvement-46.png)

> La trajectoire noire n'est pas le chemin réalisé par le robot mais la preuve qu'un chemin existe. La trajectoire rouge est la trajectoire du robot car elle respecte la contrainte non holonome

> Il a été montré qu'il n'existe que 48 types de courbes de _Reeds & Cheeps_ (RS)

![](/assets/images/RMN.CM.Mouvement-47.png)
![](/assets/images/RMN.CM.Mouvement-48.png)

> Si marche arriere non autorisée il existe d'autres types courbes dubins

TODO

> Premier algo de plannification resolu dans les annees 90 (il ne reste plus qu'à trouver les bons capteurs)

#### Approche par grille discrète

> Utile pour les robots qui sont limitées physiquement dans leurs mouvements (e.g. le robot CNES ne possède que 9 commandes avant et 9 commandes arrières)

![](/assets/images/RMN.CM.Mouvement-49.png)

> Attention avec l'heuristique : celle-ci dépend de la métrique choisie

![](/assets/images/RMN.CM.Mouvement-50.png)

## Méthodes Probabilistes

![](/assets/images/RMN.CM.Mouvement-51.png)

##### Exercice

![](/assets/images/RMN.CM.Mouvement-52.png)

> Ces méthodes sont tres utilisés en bioinformatique pour par exemple determiner des classes de configuration spatiale pour extraire ou faire evoluer des molécules d'ADN/atomes dans un environnment biologique. Ceci pour restreindre les nombres de test lors de la conception d'un prototype de medicament.

> Notes du 20220916 - End

---

[[Next Page|RMN.CM.MethodeProba]]

---
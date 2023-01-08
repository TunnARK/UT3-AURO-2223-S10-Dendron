
# Ressources

- [P1K.SLAM.Sujet.Highlighted.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/P1K.SLAM.Sujet.Highlighted.pdf)
- [](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/)

# Presentation du sujet

## Scratch Notes du 2022/10/31

robot non holonome

plustot que faire un vecteur qui connait deja tous les amers

on suppose que le nb damer n'est pas connu davance

juste assurer qu'il voit 3 premiers 

au fur et a mesure que le robot il va decouvrir ou non de nouveau amers donc il devra augmenter le vecteur detat

probabilistic robotics thrun burgard fox

## Objectifs

![](/assets/images/P1K.SLAM.SujetObjectifs.png)
![](/assets/images/P1K.SLAM.SujetProblemDef.png)

## Rappels

### Variables

![](/assets/images/P1K.SLAM.SujetRappelVariables.png)

### Models

![](/assets/images/P1K.SLAM.SujetRappelModels.png)

### Posterior Marginal

![](/assets/images/P1K.SLAM.SujetRappelPostMargin.png)

### Outline

#### State/Control Input/Measurement Output Variables

![](/assets/images/P1K.SLAM.SujetRappelStateVars.png)
![](/assets/images/P1K.SLAM.SujetRappelStateVars2.png)

#### Prior Dynamics

![](/assets/images/P1K.SLAM.SujetRappelPriorDynamics.png)

#### Observation Models

![](/assets/images/P1K.SLAM.SujetRappelObsModels.png)

#### SLAM Initialization

![](/assets/images/P1K.SLAM.SujetRappelInitialization.png)

#### SLAM Time Update

![](/assets/images/P1K.SLAM.SujetRappelTimeUpdate.png)
![](/assets/images/P1K.SLAM.SujetRappelTimeUpdate2.png)

#### SLAM Measurement Update

![](/assets/images/P1K.SLAM.SujetRappelMeasUpdate.png)
![](/assets/images/P1K.SLAM.SujetRappelMeasUpdate2.png)

#### Data Association Handling

![](/assets/images/P1K.SLAM.SujetRappelDataAssociation.png)

# Feuille de Route

1. Description du scénario (pose d’hypothèses, nombre d’instants …)
2. Trouver le modèle du robot (non holonome)
3. Modélisation de l’environnement (la map)
4. Définition des vecteurs : d’état, de mesure, la commande.
5. Association de données (telle mesure pour telle amer)
6. Construction d’un modèle des dépendances pour une boucle de
fonctionnement du robot.
7. Modélisation des évolutions des éléments du modèle de Kalman étendu
(les jacobiennes, les vecteurs, les matrices de covariances, les autres
éléments qui interviennent durant le processus du SLAM)
8. Elaboration de l’algorithme EKF-SLAM
9. Programmation et simulation (si possible le robot en déplacement pour
effectuer une boucle complète en passant entre les amers et tout).
10. Résultats et discussion (lissage, filtrage, estimation, ……)
11. Rédaction d’un Jupyter Notebook-Matlab (pour plus d’infos :
https://am111.readthedocs.io/en/latest/jmatlab_install.html )
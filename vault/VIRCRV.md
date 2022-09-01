---
id: 3nx1o8j8h3vbt6lu2fqlpq3
title: VIRCRV
desc: ''
updated: 1662025379418
created: 1662025359124
---

# Notes Cours 2022/08/31 - Intro

> À Retenir:
  - Indice Mobilité
  - Configuration
  - Situation
  - Degré de liberté

## Introduction à la robotique

![](/assets/images/VIRCRV.SlideIntro.01.png)

### Bref survol de la planète robotique

![](/assets/images/VIRCRV.SlideIntro.02.png)

- _robota_ mot tchèque pour "travail forcé"

- remplacer l'opérateur de main pour les tâches pénibles, impossibles ou dangeureuses

Dates clés:
- 1947 premier manipulateur télé-opéré
- 1954 premier robot programmable (séquence de commande avec bras manipulateur sans retour sur l'environnement)
- 1961 premier bras manipulateur sur chaîne d'assemblage (i.e. General Motors)

> Différence entre automate et robot car les automates eux peuvent remonter jusqu'à l'antiquité

![](/assets/images/VIRCRV.SlideIntro.03.png)

Définition: Robot

  - sytème mécanique _articulé_ ou _doué de mouvement_ capable d'effectuer _automatiquement_ cetaines tâches

  - structures mécaniques adaptées à la tâche à réaliser 

  - le mouvement fait la spéificité du robot
    - interaction avec l'environment
    - ce n'est pas un ordinateur
  
  - on peut décomposer un robot par :
    - structure mécanique
    - capteurs
    - pc

![](/assets/images/VIRCRV.SlideIntro.04.png)

- tâches nécessitant bcp de dextérité le robot n'arrive pas à égaler les humains du coup l'industrie du futur veut se tourner vers de la robotique collaborative appelé  (i.e. RACE)

- manipulation
  - problématique résolu par le robot
  - implique un environnement connu est maitrise

![](/assets/images/VIRCRV.SlideIntro.05.png)

- navigation 
  - problématique résolu par le robot
  - implique un environnment non contrôlé non maîtrisé


![](/assets/images/VIRCRV.SlideIntro.06.png)

- robotique de service sans interaction humaine
  - thématique très récente


![](/assets/images/VIRCRV.SlideIntro.07.png)

- robotique de service avec interaction humaine

- robotique de service sans interaction humaine

![](/assets/images/VIRCRV.SlideIntro.08.png)

- 3 niveaux d'utilité
  - agir dans le monde réel
  - s'adapter à son environment
  - collaborer avec l'homme/l'environnement


- Principe: Boucle sans fin
  - Perception: voir via des capteurs embarqués/déportés (e.g. proprioceptifs/extéroceptifs)
    - **capteur proprioceptif** reseigne le robot sur lui-même
    - **capteur extéroceptif** reseigne le robot sur l'environnement
    - **embarqués** = sur le robot
    - **déportés** = sur l'environnement
    - traitement de données
  - Décision
    - déterminer le mouvement à réaliser
    - Automatique
  - Action
    - réalise le mouvement souhaité
    - IA our SED

- traitement de donné se fait dans la perception mais les frontières sont flous

### Focus sur la robotique industrielle

#### SM à chaîne simple

![](/assets/images/VIRCRV.SlideIntro.09.png)

Deux parties sur un robot:
- OT: **organe terminal** ou effecteur
  - réalise la tâche

- SM: Structure mécanique
  - positionne l'OT
  - il en existe 3
    - **Robot manipulateur à chaine simple**
      - corps et liaison
      > **Liaison**: mets en mouvement un **corps** par rapport à un autre
      - antécédent et succésseur

#### SM à chaîne arborescente

![](/assets/images/VIRCRV.SlideIntro.10.png)

#### SM à chaîne complexe

![](/assets/images/VIRCRV.SlideIntro.11.png)

- ici chaine fermée alors que les précedentes étaient ouvertes

#### Liaisons rotoïdes et prismatiques

![](/assets/images/VIRCRV.SlideIntro.12.png)

- cylindre: rotation
- prisme: translation

- robot souvent nommé selon sa séquence de liaison en P et R

#### Exemple de différentes séquences de liaisons

![](/assets/images/VIRCRV.SlideIntro.13.png)

#### Notions de Bases sur BM Fixe

![](/assets/images/VIRCRV.SlideIntro.14.png)

![](/assets/images/VIRCRV.SlideIntro.15.png)

- $C_i$: corps illustré en oval
- $L_i$: liaison illustré en cercle
- $BM$: Bras Manipulateur
- **indice de mobilité** ($M$): nombre de liaison
- **Configuration**: position de la SM
  - définit par un **vecteur de configuration** $q = \begin{pmatrix} q_1 \\ ... \\ q_n 
\end{pmatrix}
$
  - $q_i$ angle de rotation si $L_i=R$ sinon allongement si $L_i=P$
  - $q$: **coordonnée générale** lisée ou **coordonnée articulaire**

- **Position**: situation + ortientation de l'OT
- $R_0$: Repère de base qui est fixe
- $x = \begin{pmatrix} x_P \\ x_R\end{pmatrix}$ **coordonnées opérationnelles** avec $x_P$ la coord. de position et $x_R$ la coord. d'orientation

- **Degré de liberté** (DDL): 
  - peut être confondu par l'indice de mobilité
  - ici il faut le comprendre comment le degré de liberté de l'OT

![](/assets/images/VIRCRV.SlideIntro.16.png)

- DDL: Nb de mouvement permis par l'OT
  - dans une configuration donnée (**DDL Local $d$**)
  - pour toutes les configurations possibles (**DDL Global $D$**)
- Robot gauche: $(M,d,D) = (2,2,2)$
- Robot droite: $(M,d,D) = (2,1,1)$ (robot **redondant**)

![](/assets/images/VIRCRV.SlideIntro.17.png)

- Robot gauche: $(M,d,D) = (3,3,3)$
- Robot droite: $(M,d,D) = (3,2,3)$ (**config. singulière**)
- ici on regarde deux configurations différentes sur le même robot

### Problématique

![](/assets/images/VIRCRV.SlideIntro.18.png)

- L'opérateur définit la tâche dans l'espace opérationnel (en terme de situation par rapport à l'OT)

- BM se déplace avec la SM
  - donc réfléchit en terme de configuration (dans l'espace articulaire)

> Il faut donc un pont/changement de base entre l'espace opérationnel et l'espace articulaire

- On doit donc faire le lien entre $(q,\dot q, \ddot q)$ et $(x,\dot x,\ddot x)$
- On parle alors de 3 modèles:
  - $q$ --> $x$ modèle géométrique (MG)
  - $\dot q$ --> $\dot x$ modèle cinématique (MC)
  - $\ddot q$ --> $\ddot x$ modèle d'accélération (MA)
  - MGD: Modele Geo Directe quand on va de $q$ vers $x$
  - MGI: Modele Geo Inverse quand on va de $x$ vers $q$
  - Idem pour les autres modèles


![](/assets/images/VIRCRV.SlideIntro.19.png)

- ACT: Actionneur -> toute la partie automatique
- ROB: strucuture mécanique

> La robotique en général nécessite trois comptétences:
1. Déterminer/représenter la situation (e.g. le $X_{but}
2. Gérer les changements de repère
3. Gérer les changements de modèle

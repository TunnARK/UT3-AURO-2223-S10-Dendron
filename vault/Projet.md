---
id: nlx0gy6bhqyjfi7s3w73huq
title: Projet
desc: ''
updated: 1665483718507
created: 1665403102621
nav_exclude_children: true
---

# Projet 1: Bloc 1 -> Bloc 2

## Modalités

- 3.5 semaines
- 2 servers
    - inca.(private).univ-tlse3.fr
    - azteca.(private).univ-tlse3.fr
- Implémenter un TP pour la première semaine
    - Suivie animaux marins
        - torture a cape constant avec des courants
        - mesurer sa vitesse
    - SLAM linéaire
        - robot qui tourne en rond
        - capteur qui bouge en translation rectiligne
        - fermeture de boucle et SLAM
- 2ème et 3ème semaine
    - 4 par 4
    - Pour les automaticiens -> Mission Appolo
        - navette en orbite lacher avec une certaines conditions initiales
        - position et orientation a estimer en regime libre
        - chaque 6min il y a reperage des etoiles pour la mesure des amères
        - il y a un papier de la NASA pour l'utilisation de kalman pour localiser la capsule
        - Faire ces calculs
    - Pour les roboticiens Localisation et Navigation probabiliste
        - Landmark Base SLAM
        - Robot dans une salle carree remplit d'objet
        - SLAM Actif / Range & Bearing / Filtre kalman en melange de gausienne
- Utiliser Jupyter Notebook
- Vacances administratives du 10/31 au 11/04 -> fac fermée probablement du coup pb de salle

## À Faire

1. Etudier les videos
    - [Lecture 11 Probability Review, Bayes Filters, Gaussians -- CS287-FA19 Advanced Robotics](https://www.youtube.com/watch?v=xamzdNUN1o0)
    - [Lecture 12 Kalman Filters -- CS287-FA19 Advanced Robotics at UC Berkeley](https://www.youtube.com/watch?v=eCjffhEeQyw)
    - [Lecture 14 Particle Filters -- CS287-FA19 Advanced Robotics at UC Berkeley](https://www.youtube.com/watch?v=8k--yWn8_ds&list=PLwRJQ4m4UJjNBPJdt8WamRAt4XKc639wF&index=15)
    - Preparation pour les videos: revoir la partie II de [RMN.SLAM.CM.Poly.20220923.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/RMN.SLAM.CM.Poly.20220923.pdf)
2. Deadline 10/21
    - avoir compris le filtre de kalman (et le filtrage particulère)
    - finir le TP
3. Deadline 11/07
    - Presentation des projets

## Objectifs

- **Estimation stochastique**
- **Filtrage de Kalman** (linéaire + extensions)
    - EKF
    - UKF
- **Filtrage particulaire**
    - estimateur
    - mesures ne sont pas jeter dans un jeux d'equations
    - contruire la loi posterieur
        - placer des objets
        - et garder le nuages de particule credible


# Projet 2 - Autom

- Commande de système hybirde (commutation entre dynamique et statique)

# Projet 3 - Mapping ?

...
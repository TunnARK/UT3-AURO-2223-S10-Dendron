---
id: jx6726lv37ujozp7zraqfhc
title: '2022-09-02'
desc: ''
updated: 1662143674097
created: 1662098138857
traitIds:
  - journalNote
publishing: private
---

Aspect Organisation et Humains

- P. FILLATREAU ens. cher. en vision robotique

AOH.Slide1.0


Usine du future
  - connectée (data)
    - piloté par les données
  - intelligente
  - cobot (cohabitation/collabore)
  - verte
  - centrée humaine (hergonomie)
    - Kaysen/Kaizen [mot japonais] (amélioration qualité)
  - Aero Space Valley end 2030


Deux types d'industrie
  - celle qui produit
  - celle qui innove


Innovation Durable
  - censé respecté l'environnment 
  - parfois compris comme profit durable

- pixel mort
  - pixel éteint ou qui reste rouge

- Responsable de Réception
  - Audit au moment de délivrer les produits aux clients

- edream
  - batiment du LAAS
  - avec capteurs de présence

- domotique
  - capteurs de présence pour prédire
    - l'heizammer
    - les chutes

- Robot Sofia
  - humanoid
  - essais de donné une citoyenneté à ce robot 

AOH.Slide1.03.Summary

AOH.Slide1.04

- Math pure avec option phisic
- Electrotechnic & Automatic au N7
  - ces deux domaines sont ensemble car historiquement on cherché à commander des machines électriques
- Fait une thèse en robotique visuelle au LAAS en détaché de A?
  - thèse interrempue par service militaire à MATRA (Airbus Défense)
  - à MATAR il fait sa première expérience de projet avec le devel en V

Dev. avec le Cycle en V
1. CdC
  - parfois appele STB "Specificite technique des besoins" ?
  - Connaitre le client et comprendre son problème p.r.à ses clients
  - exemple 1: Fromagerie BEL son client c'est la distribution donc son problème c'est pas le produit mais la qualité des lots distribuer
  - exemple 2: Mesure
2. Spec/Req **WHAT**
3. Conception/Design **HOW**
4. Dev
5. Validation du design/Verification
6. Reception/Acceptance
7. Garantie/Maintenance


> Codage: Nom de variable préfixé par quatre lettres pour indiquer son type 

> **Equation de la chaleur** est utile au traitement d'image car un pixel seul n'a pas d'intéret mais un pixel avec son entourage est bcp plus utile du coup on s'interesse à la relation entre pixel

- sphéricité des graines de betterave réalisé par un labo
- Monsato veut trier les parasites de tournesol
  - 1000 graines/sec
  - à l'époque 10 image par sec donc un facteur 100
    - semble impossible mais au lieu de dire que c'est impossible va verifier si il y a meilleure façon de faire des calculs -> VHDL
  - mais personne ne veut acheter la cam qui trie
  - du coup plan B utiliser la cam chez ESA pour trier les infos utiles lors de l'observation de la terre (où les oceans et les nuages noient l'info utiles)
  - mais 0 vendus
  - Plan C Siemens Automotive a besoin de calculateur petit et rapide pour analyser les images d'une voiture à 130km/h

- mangrador pays bas espagnol industrie cooperative

- indicateur pour nos projets uni
  - retard
  - repartition des taches (pie charts)

 Project Management

![](/assets/images/AOH.SlidePoly.01.TableOfContent.png)

- Plannification : Chap 1 à Chap 6
- Monitoring : Chap 7 et plus

# Introduction

![](/assets/images/AOH.SlidePoly.02.Introduction.png)

- ici pas de pratique pour le moment

# Chap 1 - Definition of a Project

![](/assets/images/AOH.SlidePoly.03.TitleDefProject.png)

## Definition

![](/assets/images/AOH.SlidePoly.04.DefProject.png)

- specifique
- process progressif ! et avec méthode
- future réalité sans equivalent exact
- accomplissant des objectifs technique et economic
- à un début et une fin

- possède un aspect innovative

> Tout devrer être un projet car tout devrer être organisé

> **La gestion de projet est un _outils_ !!!**

![](/assets/images/AOH.SlidePoly.05.DefProject.png)

## Application

![](/assets/images/AOH.SlidePoly.06.Application.png)

- **Strategic Direction**
- exemple: developement web et bonne utilisation des emails


## Importance

![](/assets/images/AOH.SlidePoly.07.Importance.png)

- Project Managment Institute
  - Chapitre = représentant dans un pays

## Timeline

![](/assets/images/AOH.SlidePoly.08.DiagDefProject.png)

- **Indicators**
  - données **mesurables**
  - pour permettre de comparer avec les objectifs

- Développer **modulairement** pour backup/reuse et ainsi garantir/optimiser l'utilité du travail

- Identification strength/weakness
  - **SWOT Analysis** [Strengths/Weaknesses/Opportunities/Threats]

- Pendant le projet on planifie chaque tâches qui seront chacunes traiter comme un 'mini-projet' avec **un** responsable

## Objectives

![](/assets/images/AOH.SlidePoly.09.Objectives.png)

> Importance to satisfy both the client and the team for max success

### Magic Triangle

Quality vs Time vs Cost

- JURAN 1er à chercher à définir la qualité
  - "Qualité = Aptitude à l'usage" -> Client Satisfaction
  - Aujourd'hui Norme ISO 9001
- Qualité = 100% de satisfaction de la Specs


### Client Statisfaction

![](/assets/images/AOH.SlidePoly.10.ClientSatisfaction.png)

- Milestones = Jalons en français
- Stakeholders = acteurs
- Minutes of Meetings = Notes des meetings/Comptes Rendus

### Team Satisfaction

#### Herzberg/Maslow - Hierarchy of Needs
![](/assets/images/AOH.SlidePoly.11.TeamSatisfaction.png)


### Success Factors

![](/assets/images/AOH.SlidePoly.12.SuccessFactor.png)

- 3 types de Ressources
  - matérielles
  - humaines
  - financières

- Structure de découpage du projet
  > WBS = Work Breakdown Structure 

- Leadership a été définie initialement par la qualité
  - Leadership = "la direction a une vision" (Top/Down)

### Changing Environments

![](/assets/images/AOH.SlidePoly.13.ChangingEnvironments.png)

> Satisfaire les besoins explicites ET implicites

- Implicites => poser les questions et ne pas assumer du non dit

> **Project Management est bcp plus transverse que hierarchique**

### Bilan

![](/assets/images/AOH.SlidePoly.14.Bilan.png)

> **ATTENTION:** Il NE faut PAS surpasser les besoins ! Les atteindres est le plus important !

# Chap 2 - Life Cycle

![](/assets/images/AOH.SlidePoly.15.TitleLifeCycle.png)

## Definition Life Cycle

![](/assets/images/AOH.SlidePoly.16.DefLifeCycle.png)

> Simplistic View ! Car il manque l'organisation du projet qui se fait en amant.

## Phases Life Cycle

![](/assets/images/AOH.SlidePoly.17.PhaseLifeCycle.png)

- Bleu = Gestion de projet
- Jaune = Aspect Technique


- Selon la litérature, on peut décomposer un projet en 4 ou 5 phases

- Attention:
  - Bouclé un process demande  quand meme que la boucle sâche quand finir et ne pas s'éterniser
  - Ne pas backler la finalisation d'une phase avant de passer à une autre

- Plannifier en même temps que la définition à lieu car on peut tj 

- Completion = finaliser les rapports donc ne pas commencer à la fin d'écrire la doc ni trop temps mais progressivment


## Type of Process

![](/assets/images/AOH.SlidePoly.18.TypeProcess.png)

### Structure

![](/assets/images/AOH.SlidePoly.19.Structure.png)

### 5 Process Types

![](/assets/images/AOH.SlidePoly.20.5Process.png)

# Chap 3 - Scope

![](/assets/images/AOH.SlidePoly.21.TitleScope.png)

> **Nécessaire pour définir la Specs**

## Process Overview : Diagramme de GANTT

![](/assets/images/AOH.SlidePoly.22.ProcessOverview.png)

- Diagramme de Gantt = Répartition des tâches dans le temps
- Priority Matrix
- Network Logic
- PERT

## SMART Objectives

![](/assets/images/AOH.SlidePoly.23.SMART.png)

- S: Specific
- **M**: **Measurable**
- A: Attrative/Attainable
- **R**: **Reachable**/Reasonable
- **T**: **Temporal**

Les exemples donnés ne sont pas 

> Finir une tâche dans un état **stable** et **finalisé**


Précision métrique: mieux entre tech optic et mechanique ?
  - la méca est plus précise en métrologie
  - la précision optic est relative au champ de vision
    - cam de tel à 16M est précise pour scanner une feuille mais pas pour prendre en photo les alpes


## Client/Stakeholders

![](/assets/images/AOH.SlidePoly.24.ClientStakeholders.png)

- Liste de questions non exaustive !

## Deliverables

![](/assets/images/AOH.SlidePoly.25.DeliverablesMilestones.png)

- Lottisement:
  - Software.Doc + Hardware.Doc
  - Hardware + Software.Doc

> **Deliverables = Name VS Task = Action (so verb)**

## Requirements & Exclusions

> Supprimer _Technical_ et le remplacer par _projet_

![](/assets/images/AOH.SlidePoly.26.RequirementsExclusions.png)

Exemple:
- Système de métrologie en centrale nucléaire en mouvement
- comme mouvement nécessité d'un arret d'urgence
- client n'a pas le budget 
- donc indique dans le contrat:
  
  > "À la demande du client, le bouton d'arrêt d'urgence pourra être dans un autre projet future"


## Risks (5M) & Review

![](/assets/images/AOH.SlidePoly.27.5M.png)

![](/assets/images/AOH.SlidePoly.28.5MReview.png)

## Priority Matrix

![](/assets/images/AOH.SlidePoly.29.PriorityMatrix.png)

# Chap 4 - Project Planning

![](/assets/images/AOH.SlidePoly.30.TitleProjectPlanning.png)

## WBS

![](/assets/images/AOH.SlidePoly.31.WBS.png)

> **WBS** = Convertir a list of deliverables into a list of tasks

> **Critical Step of a project**

- On s'arrête à un sous-livrable lorsque ce sous-livrable possède un agent spécifique

![](/assets/images/AOH.TemplateSignatureDoc.png)

### Project Structure

![](/assets/images/AOH.SlidePoly.32.Structure.png)

### Exemple: Laptop

![](/assets/images/AOH.SlidePoly.33.WBSExempleLaptop.png)

### Work Packages

![](/assets/images/AOH.SlidePoly.34.WBSWorkPackages.png)

### RAM Responsability Assignment Matrix

![](/assets/images/AOH.SlidePoly.35.RAM.png)

> Cost Center = Où il faut suivre le cout car les membres ont été assigné et donc les couts suivent

## Estimating Duration

![](/assets/images/AOH.SlidePoly.36.EstimateDuration.png)


- Exemple:
  - Workload : 10j
  - Disponibility: 100%
  - Delay: best case 12j (depends on working days and holidays)


- L'important est de chiffré le worklaod
  - si en interne alors c'est à **travail-fixe**
  - si en externe alors on chiffre en **durée-fixe** (delay and cost)

## Cost/Time Relation

> **!!! Missing CURVE !!!**

![](/assets/images/AOH.SlidePoly.37.CostTime.png)

> **!!! Missing CURVE !!!**

# Chap 5 - Time Managment Tools

![](/assets/images/AOH.SlidePoly.38.TimeManagTools.png)

## Precedence Table

![](/assets/images/AOH.SlidePoly.39.PrecedenceTable.png)

## Dependencies Types

![](/assets/images/AOH.SlidePoly.40.DependenciesTypes.png)

> **IMPORTANT: Finish to Start / Start to Finish / Start to Start / Finish to Finish / Start to Delayed Start**

## Logical Network

![](/assets/images/AOH.SlidePoly.41.LogicalNetwork.png)

## Temporal Network

> Slide modified -> Check Polycope V11

![](/assets/images/AOH.SlidePoly.42.TemporalNetwork.png)

## Critical Path

![](/assets/images/AOH.SlidePoly.43.CriticalPath.png)

- On est dans un Critical Path dès lors qu'une tache retardé retard tout le projet

## Temporal Network

![](/assets/images/AOH.SlidePoly.44.TemporalNetwork.png)

## Potential Methods

### Exemple 1

![](/assets/images/AOH.SlidePoly.45.PotentialMethods1.png)


### Exemple 2

![](/assets/images/AOH.SlidePoly.46.PotentialMethods2.png)

### Solution Exemple 1

![](/assets/images/AOH.SlidePoly.47.PotentialMethods3.png)

### More Examples

![](/assets/images/AOH.SlidePoly.48.png)

![](/assets/images/AOH.SlidePoly.49.png)

![](/assets/images/AOH.SlidePoly.50.png)

![](/assets/images/AOH.SlidePoly.51.png)

![](/assets/images/AOH.SlidePoly.52.png)

## Gantt Chart

### Principle
![](/assets/images/AOH.SlidePoly.53.GanttChartPrinciple.png)

### Types

![](/assets/images/AOH.SlidePoly.54.GanttChartTypes.png)

### Setting Milestones

![](/assets/images/AOH.SlidePoly.55.GanttChartMilestones.png)

### Man Power

![](/assets/images/AOH.SlidePoly.56.GanttChartManPower.png)

### Monitoring

![](/assets/images/AOH.SlidePoly.57.GanntChartMonitoring.png)


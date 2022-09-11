---
id: p85rbwnti1ba3v7wlx9ae6w
title: Code Management
desc: ''
updated: 1662938431060
created: 1662938135263
---


> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par G. Saurel

Support de cours :
- [Lien vers les slides](https://homepages.laas.fr/matthieu/talks/git.pdf)

Lien utile :
- [Bac à Sable pour apprendre Git](https://learngitbranching.js.org/)

---


> Notes du 2022/09/08 - Start

# Code Management

![](/assets/images/COOSTAR.SlideCodeMgmt.01.png)
> git a été developpe pour le noyau linux


![](/assets/images/COOSTAR.SlideCodeMgmt.02.png)

## Agenda
![](/assets/images/COOSTAR.SlideCodeMgmt.03.png)

## Introduction
![](/assets/images/COOSTAR.SlideCodeMgmt.04.png)

![](/assets/images/COOSTAR.SlideCodeMgmt.05.png)

### Version Control Concepts
![](/assets/images/COOSTAR.SlideCodeMgmt.06.png)

- un commit = un freeze de l'état d'un dossier
  - prend la version parent
  - regarde ce qui est nouveau
  - en fait un hash
  - lors de la creation avec `git init` on cree un revision parente ici A puis chaque commit donne l'etat B puis C
  

![](/assets/images/COOSTAR.SlideCodeMgmt.07.png)

- possibilité de revenir sur un parent et faire une nouvelle branche
- historiquement la branche principale en Forge était appelé `master` puis elle a été corrigé à `main`
- dans projet on essais d'éviter de créer trop de branches

### Handling branches

![](/assets/images/COOSTAR.SlideCodeMgmt.08.png)

### Working in teams

![](/assets/images/COOSTAR.SlideCodeMgmt.09.png)

### Centralized model

![](/assets/images/COOSTAR.SlideCodeMgmt.10.png)

### Distributed model

![](/assets/images/COOSTAR.SlideCodeMgmt.11.png)

- Advantage plus besoin d'etre directement connecter au serveur (donc transfert de fichier plus rapide)

## Git Concepts

![](/assets/images/COOSTAR.SlideCodeMgmt.12.png)

**Def:** Repository / diff or patch / commit (verb and noun) / branch / tag 

![](/assets/images/COOSTAR.SlideCodeMgmt.13.png)

- tag reste à jamais sur un commit alors que la branch change à chaque commit
  - interface tig
    - `[]` branches du pc local (en bold pour la branch current)
    - `{}` branches sur le serveur

**Def:** Working Tree / Index / Blob

![](/assets/images/COOSTAR.SlideCodeMgmt.14.png)

### Git Interfaces

![](/assets/images/COOSTAR.SlideCodeMgmt.15.png)

Autre interface: `git gui`

### Git Forges

![](/assets/images/COOSTAR.SlideCodeMgmt.16.png)

### Initial Setup

![](/assets/images/COOSTAR.SlideCodeMgmt.17.png)

- `--global` configuration appliquée sur le pc
- set favorite editor: `git config --global --add core.editor emacs -nw`
- configuration stockée dans `~/.gitconfig`

## Individual Developper

![](/assets/images/COOSTAR.SlideCodeMgmt.18.png)

### Creating repository

![](/assets/images/COOSTAR.SlideCodeMgmt.19.png)

### Adding files

![](/assets/images/COOSTAR.SlideCodeMgmt.20.png)

### Querying Status

![](/assets/images/COOSTAR.SlideCodeMgmt.21.png)

> Pour montrer le status du dossier

### Committing changes

![](/assets/images/COOSTAR.SlideCodeMgmt.22.png)

- `git commit -a` réalise un `add` et puis `commit` en une seule ligne
- `-m` pour attacher un message au commit

### Git Index

![](/assets/images/COOSTAR.SlideCodeMgmt.23.png)

### Commits

![](/assets/images/COOSTAR.SlideCodeMgmt.24.png)

- digital signature
  - permet de comparer un clone en l'identifier avec une cle

### Interactive add

![](/assets/images/COOSTAR.SlideCodeMgmt.25.png)

- `-i` permet de visualiser quels fichiers selectionner pour le commit

### Looking Back

![](/assets/images/COOSTAR.SlideCodeMgmt.26.png)

- `index 6bd8f3c..c0ee9ab 100644` indique qu'on compare commit 6bd8f3c avec c0ee9ab et donne l'attribut de c0ee9ab avec 100644 pour indiquer si les permissions sont read/write/exe

### Examining Changes

![](/assets/images/COOSTAR.SlideCodeMgmt.27.png)

### Marking a version

![](/assets/images/COOSTAR.SlideCodeMgmt.28.png)

### Fixing mistakes

![](/assets/images/COOSTAR.SlideCodeMgmt.29.png)

## Using Branches

![](/assets/images/COOSTAR.SlideCodeMgmt.30.png)

### Branches

![](/assets/images/COOSTAR.SlideCodeMgmt.31.png)

### Switching branches

![](/assets/images/COOSTAR.SlideCodeMgmt.32.png)

### Listing available branches

![](/assets/images/COOSTAR.SlideCodeMgmt.33.png)

### Merging changes from another branche

![](/assets/images/COOSTAR.SlideCodeMgmt.34.png)

- fast forward vs normal merge
- software meld montre bien le principe des "3 way merge"

### Handling conflicts

![](/assets/images/COOSTAR.SlideCodeMgmt.35.png)

### Tools to help with merge

![](/assets/images/COOSTAR.SlideCodeMgmt.36.png)

### Picking individual changes

![](/assets/images/COOSTAR.SlideCodeMgmt.37.png)

- cherry-pick

### Replaying changes from a branch

![](/assets/images/COOSTAR.SlideCodeMgmt.38.png)

### Rebase

![](/assets/images/COOSTAR.SlideCodeMgmt.39.png)

### Interactive Rebase

![](/assets/images/COOSTAR.SlideCodeMgmt.40.png)

> DON'T USE after pushing ! Why ?

## Working together

![](/assets/images/COOSTAR.SlideCodeMgmt.41.png)

### Copying a repository

![](/assets/images/COOSTAR.SlideCodeMgmt.42.png)

### Remote repository

![](/assets/images/COOSTAR.SlideCodeMgmt.43.png)

> La remote s'appelle par défaut `origin`

### Updating from a repository

![](/assets/images/COOSTAR.SlideCodeMgmt.44.png)

### Remote branches

![](/assets/images/COOSTAR.SlideCodeMgmt.45.png)





> Notes du 2022/09/08 - End

---

> Notes du 2022/09/? - Start





###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.

###

COOSTAR.SlideCodeMgmt.




> Notes du 2022/09/? - End

---
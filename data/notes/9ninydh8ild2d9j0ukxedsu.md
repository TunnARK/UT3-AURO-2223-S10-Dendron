
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par M. Thaix

Support de cours :
- [OE.TP1.Sujet.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/OE.TP1.Sujet.pdf)
- [GitHub Repository](https://github.com/TunnARK/UT3-AURO-2223-S10-Coding/tree/master/OE-TP1-MGI)
- [Documentation scipy.optimize](https://docs.scipy.org/doc/scipy/tutorial/optimize.html)

Fonction utile sur python:
- `np.dot()` produit matricielle
- `np.linalg.inv()` inversion matricielle
- `np.linalg.norm()` norme d'un vecteur
- `Jt=J.transpose()` transposer une matrice
- `list.append()` ajout élément dans une liste

---

# Calcul numérique du MGI d’un RRR par PNL

![](/assets/images/OE.TP1.Sujet-01.png)
![](/assets/images/OE.TP1.Sujet-02.png)
![](/assets/images/OE.TP1.Sujet-03.png)

<!--
## Notes Présentation TP

- incrémentation vs solution directe
- mgd nécessaire pour avoir $X_k$ 
    - idée est que X_k = X_0
    - mgd donné et jacobienne donnée
    - $\dot X = J \dot q$ donnée
- Newton
    - au lieu de calculer la hessiene
    - on va calculer le zero de $H(q)$

- Gradient
    - singularite = det de la jaco à 0
        - attention sbras tendu det de J est 0
    - afficher l'erreur et espére que l'erreur converge vers 0
    - attention gradient sensible p.r. au pas

- scipy
    - ici on cherche le modele alors qu'avant on nous l'a donné et il fallait faire l'algo (ici l'algo est donné)
-->

## 1. Méthode de Newton

> ![](/assets/images/OE.TP1.Sujet-04.png)

### A) Montrer que $direction = J(q)^{-1} \cdot (X_d - f(q)$


D'après le slide 56 du cours, nous avons l'équation pour le modèle linéaire en multi-dimensionnel avec une fonction linéaire $H(q)$:

$$
\begin{matrix}
q_{k+1} &=& q_k + \nabla\Big(H(q)\Big)^{-t} \cdot \Big(H(q)\Big)\\[0.2cm]
q_{k+1} &=& q_k + \nabla\Big(X_d - f(q)\Big)^{-t} \cdot \Big(X_d - f(q)\Big)\\[0.2cm]
&=&  \\[0.2cm]
&=& q_k + J(q)^{-1} \cdot H(q)\\
\end{matrix}
$$

### B) Implémentation

#### Initialisation

Pour l'implémentation de la méthode de Newton, nous avons commencé par initialiser `qinit` et fixer le _pas_ et l'_erreur tolérée_ $\epsilon$.

Par défaut, on a fixé le _pas_ à 0.1 et _epsilon à 0.001_.

La partie d'initialisation se termine avec la saisie par l'utilisateur du nombre maximum d'itération (utile pour stopper l'algorithm une fois ce nombre atteint).

#### Iterations

La boucle d'iterartion est structuré comme suit :
```python
while(Hnorm>eps and i<NbIter) :
    # Jacobienne
    J = jacobienne(q)
    # Calcul de l'inverse
    Jinv=np.linalg.inv(J)
    # Calcul de l ecart entre le Xbut et le Xc actuel
    H=(Xbut-mgd(q))
    # Iteration
    q=q+pas*np.dot(Jinv,H)
    # Calcul de l erreur avec norme euclidienne
    Hnorm=np.linalg.norm(H)
    # Remplissage du vecteur avec la norme
    Hq.append(Hnorm)
    i=i+1
```

La boucle se lance si la métrique choisie (ici on a considéré la norme euclidienne) est supérieure à l'erreur tolérée $\epsilon$

## 2. Méthode du Gradient

> ![](/assets/images/OE.TP1.Sujet-05.png)

..

## 3. Utilisation de scipy.optimize

> ![](/assets/images/OE.TP1.Sujet-06.png)
[Documentation scipy.optimize](https://docs.scipy.org/doc/scipy/tutorial/optimize.html)


## 4. Optimisation sous contrainte

### 4.1 Contrainte de butée

> ![](/assets/images/OE.TP1.Sujet-07.png)

..

### 4.2 Contrainte sur la solution

> ![](/assets/images/OE.TP1.Sujet-08.png)

..

## 5. Travail à rendre en fin de séance

> ![](/assets/images/OE.TP1.Sujet-09.png)

..

## Code Fourni

```python
#############
# Code à utiliser pour débuter votre TP
#################
import matplotlib.pyplot as plt
import numpy as np
import time

#################################################
# Calcul du MGD du robot RRR
# INPUT: q = vecteur de configuration (radian, radian, radian)
# OUTPUT: Xc = vecteur de situation = (x,y, theta)
# x,y en mètre et theta en radian
def mgd(qrad):
#### Paramètres du robot
    l=[1,1,1]
    c1= np.cos(qrad[0])
    s1=np.sin(qrad[0])
    c12= np.cos(qrad[0]+qrad[1])
    s12=np.sin(qrad[0]+qrad[1])
    theta= qrad[0]+qrad[1]+qrad[2]
    c123=np.cos(theta)
    s123=np.sin(theta)
    x=l[0]*c1 + l[1]*c12 +l[2]*c123
    y=l[0]*s1 + l[1]*s12 +l[2]*s123
    Xd=[x,y,theta]
    return Xd
#################################################
# test de validation du MGD
##### INPUT de q en degré ###
qdeg = [90, -90, 0]
qr = np.radians(qdeg)
Xd= mgd(qr)
print("X=", Xd[0], "Y = ", Xd[1], "Theta (deg)= ", np.degrees(Xd[2]))

#################################################
# Calcul de J(q) du robot RRR
# INPUT: q = vecteur de configuration (radian, radian, radian)
# OUTPUT: jacobienne(q) analytique
def jacobienne(qrad):
#### Paramètres du robot
    l=[1,1,1]
    c1= np.cos(qrad[0])
    s1= np.sin(qrad[0])
    c12= np.cos(qrad[0]+qrad[1])
    s12=np.sin(qrad[0]+qrad[1])
    theta= qrad[0]+qrad[1]+qrad[2]
    theta= np.fmod(theta,2*np.pi)
    c123=np.cos(theta)
    s123=np.sin(theta)
    Ja=np.array([[-(l[0]*s1 + l[1]*s12 +l[2]*s123), -(l[1]*s12 +l[2]*s123), -(l[2]*s123)], [(l[0]*c1 + l[1]*c12 +l[2]*c123), (l[1]*c12 +l[2]*c123), (l[2]*c123)], [1, 1, 1]])
    return Ja

###################################################################################
# Afin de donner une situation atteignable pour le robot,
# vous pouvez utiliser le mgd pour définir Xbut à partir d’une configuration en q
###################################################################################
## qbut est donné en degré
qbutdeg= np.asarray([45, 45, -60.])
## Calcul Xbut à partir de qbut
Xbut= np.asarray(mgd(np.radians(qbutdeg)))
print("Xbut=", Xbut[0], "Ybut = ", Xbut[1], "Theta but (deg)= ", np.degrees(Xbut[2]))

############################################
## Fct d’affichage 2D du robot dans le plan
def dessinRRR(q) :
xA, yA = (0, 0)
xB, yB = (np.cos(q[0]), np.sin(q[0]))
xC, yC = (np.cos(q[0]) + np.cos(q[0]+q[1])), (np.sin(q[0]) + np.sin(q[0]+q[1]))
xD, yD = (np.cos(q[0]) + np.cos(q[0]+q[1]) + np.cos(q[0]+q[1]+q[2])),(np.sin(q[0]) + np
X=[xA, xB,xC,xD]
Y=[yA,yB,yC,yD]
plt.plot(X,Y, color="orange", lw=10, alpha=0.5, marker="o", markersize=20, mfc="red")
plt.axis(’equal’)
plt.axis(’off’)
plt.show()
################################################
############ Exemple d’affichage
dessinRRR(np.radians(qbutdeg))

########################################
######
###### Boucle principale de calcul du MGI
######################################
####
#### Définition de Xbut à partir de qbutdeg en degré
qbutdeg= np.asarray([45.,45.,-60])
qbut = np.radians(qbutdeg)
Xbut= np.asarray(mgd(qbut))
dessinRRR(qbut)
#### Définition de qinit
qinitdeg=np.asarray([120., 25, 45.])
qinit= np.radians(qinitdeg)
Xinit=np.asarray(mgd(qinit))
print("Xinit = ",Xinit)

##### A CODER
##q= qinit
##i=0
##
##
##nbpas= ???
##epsx= ???
## erx = valeur initale de du critère qu’on cherche à minimiser
##list_erreur = [erx] #
##start_time = time.process_time()
##while (????):
## direction = ???
## pas= ???
## ...
## ...
## list_erreur.append(erx) # Stocker la valeur du critère dans une liste
## i=i+1
##print("--- %s seconds ---" % round(time.process_time() - start_time,6))
### Visualisation des résultats
##print("Valeur finale du critère =",??," après ",i," itérations")
##print("qinit en deg =", qinitdeg)
##print("qcfinal en deg", np.degrees(qc))
##X= mgd(qc)
##print("Xinit =",Xinit, type(Xinit))
##print("Xfinal avec qfinal = ",X)
##print("Xbut à atteindre =", Xbut, type(Xbut))
##Xer= Xbut -X
##erx=np.linalg.norm(Xer)
##print("Erreur finale=",erx)
##abs = np.linspace(0,len(list_erreur)-1,(len(list_erreur)))
##plt.plot(abs,list_erreur,’k’)
##plt.show(block=True)
##
##dessinRRR(qc)
```
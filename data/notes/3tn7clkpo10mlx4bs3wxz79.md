
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par S. Durola

---

> Notes RKA du 2023/02/01 - Start




# Modèle d'ordre 4

![](/assets/images/B3.CCTR.TP2.BB20230201-01.png)

# Réduction d'ordre

## Réduction sur $i_2(t)$

![](/assets/images/B3.CCTR.TP2.BB20230201-02.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-03.png)

## Réduction sur $i_1(t)$

### Méthode 1

![](/assets/images/B3.CCTR.TP2.BB20230201-04.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-05.png)

### Méthode 2

![](/assets/images/B3.CCTR.TP2.BB20230201-06.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-07.png)

# Objectifs

![](/assets/images/B3.CCTR.TP2.BB20230201-08.png)

# Observateur Identité

![](/assets/images/B3.CCTR.TP2.BB20230201-09.png)

Le bouclage ne pourra modifier les modes de l'obs car un obs est concu expres avec des modes non-commandables

**Quelle est la dynamique de l'intégrateur sur la partie obs ?**
- Il y a deux boucles celle liée à $\hat A$ et celle venant de l'observateur $-GC$
- C'est pourquoi $F=A-GC$ !
- Au final un obs identité (et ceci n'est applicable que pour l'identité) revient à simuler le système réel et étudier l'erreur sur la sortie réelle et la simulé pour la réinjecter avec un gain $G$

# Effet Intégral et Retour d'État

Pour l'effet intégral:
- on mesure l'erreur sur la sortie
- on insert l'intégrateur sur l'erreur

Pour le retour d'état:
- on boucle sur la sortie de l'obs
- en ajoutant les précompensateurs sur la sortie et sur $x_i$

![](/assets/images/B3.CCTR.TP2.BB20230201-10.png)

# Calcul de retour d'état

![](/assets/images/B3.CCTR.TP2.BB20230201-11.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-12.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-13.png)

Il ne reste plus qu'à utiliser matlab pour trouver $K_a$ avec `Ka = acker(Aa, Ba, poles_des)`.

# Calcul de l'observateur

![](/assets/images/B3.CCTR.TP2.BB20230201-14.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-15.png)

On trouve $G$ avec `G = acker(A2', C2', poles_des)`.


# Exprimer les etats

![](/assets/images/B3.CCTR.TP2.BB20230201-16.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-17.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-18.png)

## 1) Expression de $x_2$

![](/assets/images/B3.CCTR.TP2.BB20230201-19.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-20.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-21.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-22.png)
![](/assets/images/B3.CCTR.TP2.BB20230201-23.png)

On vérifie bien que les modes du retour d'état s'appliquent sur le etats et pas l'erreur. La séparation est bien respectée (i.e. les bons modes désirés sont appliqués).

Et de plus la dynamique est bien autonome.

# Discretisation

## Thm de Shanon

![](/assets/images/B3.CCTR.TP2.BB20230201-24.png)

On perd de l'information lorsque le signal périodisé se superpose sur le signal. Ceci n'est jamais le cas uniquement lorsque le signal est **borné**. Dans ce cas, il faut prendre une période au moins doublement supérieure à la borne max du signal.

![](/assets/images/B3.CCTR.TP2.BB20230201-25.png)




> Notes RKA du 2023/02/01 - End

---
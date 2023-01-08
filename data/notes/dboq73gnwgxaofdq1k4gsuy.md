
# 1 - Mise en place de l'environnement

![](/assets/images/B1.P3D.TP1.Sujet.Part1.png)

# 2 - Vision Monoculaire

## 2-1. Calibration

![](/assets/images/B1.P3D.TP1.Sujet.Part2.Q1.png)

La mire est composée d'une grille de taille 4x11 contenant des cercles noirs sur un fond blanc.

Cette mire est asymmétrique ce qui apporte l'advantage d'éviter l'indétermination liée à une rotation de 180 degrés.

Il nous faut donc implémenter la fonction `findCirclesGrid`:


1. Dans `Calibration.py`, utiliser la [docs d'opencv](https://docs.opencv.org/3.4/) pour implémenter les fonctions prédéfinies comme `findCirclesGrid`
2. Dans `MonoMain.py`, instancier un objet de la class `MonoCalibration` en utilisant le constructeur
3. Dans `MonoMain.py`, lancer la fonction `acquire`
4. Prélever plusieurs perceptives de la mire en appuyant sur `espace`

![](/assets/images/B1.P3D.TP1.Sujet.Part2.Q2.png)

La variable `objectPoints` correspond à la position réelle/monde des cercles en $x,y,z$ tandis que la variable `imgPoints` elle correspond aux coordonnées des cercles dans le plan image en $u,v$.

1. Dans `Calibrate.py`, utiliser la [doc d'opencv](https://docs.opencv.org/3.4/) pour implémenter les fonctions prédéfinies `cv.calibrateCameraExtended`
2. Dans `MonoMain.py`, lancer la fonction `calibrate`

> Attention: attribut sans `self.`
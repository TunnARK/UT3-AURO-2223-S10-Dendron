---
id: w3jfkbcn4yh96zthrn6txqr
title: TP2
desc: ''
updated: 1664811127094
created: 1664796890101
---

---


> **Avertissement:** Cette page peut contenir des fautes ! Envoyez-moi un message sur `#UT3-AURO-M2-2223-Request:matrix.org` si vous en trouvez, merci.

> Cours donné par Olivier

---

# Comments

- postit (topics) pour faire
- bus logiciel
    - entrer avec un annuaire d'objet (roscore)
    - les nodes communiquent via cette annuaire
- rappel ROS 1 n'est pas sécurisé
- toute les unités sont

# Command Lines

1. `env | grep ROS`
    verifier le `_MASTER_URI`
2. `roscore` (dans un autre terminal a ne pas fermer)
3. `rosrun turtlesim turtlesim_node __name:=my_turtle`
4. `rosrun rqt_graph rqt_graph`
5. `rosnode info /my_turtle`
6. `rostopic echo /turtle1/pose`
7. `rostopic pub /turtle1/cmd_vel geometry msgs/Twist "linear: x:...y:...z:... angular: x:...y:...z:..." -r 1`
    Makes the turtle turn in circle over the z axis with 1 rad/s with a rate of 1 Hz
8. se connecter sur le reseau du robot `TIAGO_155` ou `PalRobotics` (mode passe admin `palroot` mode passe reseau `P@L-R0b0t1cs`)
9. `env | grep ROS`
10. `rosnode list`
11. `export ROS_MASTER_URI=http://10.68.0.1:1131`
12. `env | grep ROS`
13. `rostopic list | grep cmd_devel` chercher mobile base controller sans out
14. `export ROS_IP=10.68.0.131`

# Workspace

1. `mkdir workspaceroot`
2. `cd workspaceroot`
3. `mkdir src`
4. `catkin_init_workspace`
5. `catkin_create_pkg begin_tutorials std_msg rospy roscp`
6. `cd ./begin_tutorials`
7. `mkdir launch`
8. `cd ./launch`
9. `nano mimic.launch` and copy paste
    ```xml
    <launch>
        <group ns="turtlesim1">
         <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
        </group>
        
        <group ns="turtlesim2">
         <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
        </group>
        
        <node pkg="turtlesim" name="mimic" type="mimic">
         <remap from="input" to="turtlesim1/turtle1"/>
         <remap from="output" to="turtlesim2/turtle1"/>
        </node>
    </launch>
    ```
10. `cd ../..` pour se remettre sur le root du workspace
11. `catkin_make`
12. `source ./devel/setup.bash` verifier avant et apres les modifs appliquées avec `env | grep ROS`
13. `roslaunch begin_tutorial mimic.launch`
14. Check graph with `rosrun rqt_graph rqt_graph` 

Si le `bashrc` est 'corrompu' appliquer la séquence suivante :
1. Comment source de trop dans `~/.bashrc`
2. Se mettre sur root workspace et supprimer le build et le devel avec ``

# Message

1. `roscd beginner_tutorials`
2. `mkdir msg`
3 echo "int64 num" > msg/Num.msg`
 
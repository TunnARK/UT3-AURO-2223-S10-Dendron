
> **Avertissement:**
Cette page peut contenir des fautes ! Envoyez-moi un message sur [`#UT3-AURO-M2-2223-Request:matrix.org`](https://matrix.to/#/#UT3-AURO-M2-2223-Request:matrix.org) si vous en trouvez, merci.

> Cours donné par G. Saurel

Sources :
- [GodBolt (Compiler Explorer)](https://godbolt.org/)
- [Mark Theis (Documentation Assembleur RISCV)](https://mark.theis.site/riscv/)
- [Cliffle's Blog (for the code example)](http://cliffle.com/blog/not-thread-safe/#the-bank-account-example)

---

Un manageur nous demande de travailler sur un nouveau software pour retirer du cash dans un bancomat (voir [Cliffle's Blog](http://cliffle.com/blog/not-thread-safe/#the-bank-account-example) pour plus d'informations). 

# Partie 1 - Vérification des conditions

Il n'a pas eu le temps de compléter le tableau suivant :

![](/assets/images/B2.SATR.TD1.BB20221125-01.png)

Mais il nous demande quand même de trouver en fonction de $x$ :
1. la condition nécessaire d'ordonnançabilité ; ainsi que 
2. la condition suffisante pour RMA ; et
3. la condition suffisante pour EDF.

## Condition Nécessaire

![](/assets/images/B2.SATR.TD1.BB20221125-02.png)

Donc on sait que si $x>44$ cela ne servira à rien de continuer sur ce projet car il ne sera pas temps réel.

## Condition Suffisante

### RMA

![](/assets/images/B2.SATR.TD1.BB20221125-03.png)

### EDF

![](/assets/images/B2.SATR.TD1.BB20221125-04.png)

## Conclusion

- Si $\;x\leq16\;$, ce sera plus efficace de prendre l'algo EDF.
- Si $\;16<x\leq22\;$, on utilisera RMA.
- Si $\;22<x\leq44\;$, on ne saura pas l'efficacité a priori donc il faudra essayer.

# Partie 2 - Estimation du $x$

On reçoit plus de détails du manageur qui a écrit un code pour calculer/estimer ce $x$.

```c++
/*
 * Stores information about a bank account.
 */
struct bank_account {
    /* How much money is in the account. */
    int balance; /* never use floats for managing money (too much approximation) */
};

/*
 * Deposits 'amt' into the 'account' and returns the new balance.
 */
float deposit(struct bank_account *account, int amt) {
    account->balance += amt;
    return account->balance;
}

/*
 * Tries to withdraw 'amt' from the account. Returns 'true' if it
 * succeeded, 'false' if the account didn't contain enough.
 */
bool withdraw(struct bank_account *account, int amt) {
    if (account->balance >= amt) {
        account->balance -= amt;
        return true;
    } else {
        return false;
    }
}

```

On travaille mtnt sur le _Compiler Explorer_ [GodBolt (Compiler Explorer)](https://godbolt.org/) pour continuer la programmation avec l'architecture de jeux d'instructions (_redus instruction set_ = coeur de calcul) `RISC-V rv32gc clang 15.0.0`.

> Si besoin de voir la doc pour retrouver les acronymes des fonctions en assembleur, une option est [Mark Theis (Documentation Assembleur RISCV)](https://mark.theis.site/riscv/)


On va utiliser cette explorer pour compter le nombre d'instructions et ainsi mesurer le temps d'execution.

On obtient deux cas:

1. Si on suit la branche `withdraw>LBB1_1>LBB1_3`, on obtient **24 instructions**.

    $\longrightarrow$ Du coup, on ne peut que tester sans RMA et sans EDF.

2. Si on suit la branche `withdraw>LBB1_2>LBB1_3`, on obtient **18 instructions**.

    $\longrightarrow$ Du coup, dans ce cas, on sait qu'utiliser RMA sera plus efficace.

**Remarque :**
- On pourrait changer de compilateur pour vérifier si on trouve un meilleur nombre d'instructions.
- Par exemple, `RISC-V rv32gc gcc 12.1.0` semble plus perfomant pour cette fonction.
- On peut aussi demander d'optimiser le code en ajoutant `-O0` ou `-O1` max `-O2`.
    - Aller plus haut en optimisation risque de rendre les calculs trop imprécis.
    - Le cas où une optimisation rajoute un beug est plus rare.

# Partie 3 - Choix d'un RR de Période 10

Le manageur a l'intuition que passer en `RR de période 10` serait une bonne idée, vérifions :

Assumons qu'il y a 100 euros dans le compte et que les taches suivantes sont appelées : $\;T_1(100)\;$ [`withdraw`], $\;T_2(100)\;$ [`deposit`] et $\;T_3\;$ [`balance`].

Nous obtenons la séquence d'éxecution de période suivante :
![](/assets/images/B2.SATR.TD1.BB20221125-05.png)


---
title: Soluzioni esercizio indecibilita'
author: Giulio Umbrella
---

# Ex 1

Dimostrare che il seguente linguaggio e' indecidibile $L_R = {M,w | M accetta la stringa ww^{R}$}

*Soluzione*

Per dimostrare che $L_{R}$ e' indecidibile dimostriamo che esiste una riduzione $A_{TM} \le_{m} L_R$. La funzione f opera nel seguente modo:

F = su input *M*,*w* dove *M* e' una TM e w una stringa:

1. Costruisci la seguente $M_R$:  
    $M_R$ su input x:      
    1. se $x \ne ww^R$ accetta.
    2. Se $w = w^R$, esegue M su input w.
    3. Se *M* accetta, *accetta*
    4. Se *M* rifiuta, *rifiuta*
2. Restituisci $M_R,w$:  


Dimostriamo che f e' una riduzione valida:

1. Se $(M,w) \in A_{TM}$ allora la TM *M* accetta *w*. Quindi la macchina $M_R$ costruita accetta la parola $ww^{R}$. Quindi f(M,w) = $M_R \in L_R$
1. Se $(M,w) \notin A_{TM}$ allora la TM *M* non accetta *w*. Quindi la macchina $M_R$ costruita non accetta la parola $ww^{R}$. Quindi f(M,w) = $M_R \notin L_R$

## Che cosa rappresenta x?

La variabile x rappresenta l'input della TM $M_R$ quando viene messa in esecuzione. E' importante sottolineare cha il parametro x **non** viene dato in input alla funzione F; gli input di F sono infatti la TM e la stringa w. Dobbiamo specificare il valore x per indicare il comportamento di $M_R$. $M_R$ e' una TM e per funzionare ha bisogno di un input. Il restanti passaggi spiegano cosa fa $M_R$ una volta che riceve un input, ma quella e' una computazione a se stante che non viene eseguita da F.

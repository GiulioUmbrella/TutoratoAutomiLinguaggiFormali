---
title: Soluzioni Tutorato 08
author: Giulio Umbrella
geometry: margin=2cm
---

# Ex 1

Dimostrare che il seguente linguaggio e' indecidibile $L_R$ = (M,w | M accetta la stringa $ww^{R}$)

*Soluzione*

Per dimostrare che $L_{R}$ e' indecidibile dimostriamo che esiste una riduzione $A_{TM} \le_{m} L_R$. La funzione f opera nel seguente modo:

F = su input *M*,*w* dove *M* e' una TM e w una stringa:

1. Costruisci la seguente $M_R$:  
    $M_R$ su input x:      
    1. se $x \ne ww^R$ accetta.
    2. Se $x = ww^R$, esegue M su input w.
    3. Se *M* accetta, *accetta*
    4. Se *M* rifiuta, *rifiuta*
2. Restituisci $M_R,w$:  


Dimostriamo che f e' una riduzione valida:

1. Se $(M,w) \in A_{TM}$ allora la TM *M* accetta *w*. Quindi la macchina $M_R$ costruita accetta la parola $ww^{R}$. Quindi f(M,w) = $M_R \in L_R$
1. Se $(M,w) \notin A_{TM}$ allora la TM *M* non accetta *w*. Quindi la macchina $M_R$ costruita non accetta la parola $ww^{R}$. Quindi f(M,w) = $M_R \notin L_R$

## Che cosa rappresenta x?

La variabile x rappresenta l'input della TM $M_R$ quando viene messa in esecuzione. E' importante sottolineare cha la variabile x **non** viene dato in input alla funzione F; gli input di F sono infatti la TM e la stringa w. Dobbiamo specificare il valore x per indicare il comportamento di $M_R$. $M_R$ e' una TM e per funzionare ha bisogno di un input. Il restanti passaggi spiegano cosa fa $M_R$ una volta che riceve un input, ma quella e' una computazione a se stante che non viene eseguita da F.


# Ex 2

Pebbling e' un solitario giocato su un grafo non orientato G, in cui ogni vertice ha zero o piu' ciottoli. Una mossa del gioco consiste nel rimuovere due ciottoli da un vertice v e aggiungere un ciottolo ad un vertice u adiacente a v (il vertice v deve avere almeno due ciottoli all’inizio della mossa). Il problema PebbleDestruction chiede, dato un grafo G = (V,E) ed un numero di ciottoli p(v) per ogni vertice v, di determinare se esiste una sequenza di mosse che rimuove tutti i sassolini tranne uno.


Dimostra che PebbleDestruction e' **NP-hard** usando il problema del Circuito Ha- miltoniano come problema NP-hard noto (un circuito Hamiltoniano e' un ciclo che attraversa ogni vertice di G esattamente una volta).

*Soluzione*

Per dimostrare che un problema X e' NP-Hard dobbiamo prendere un problema Y che sappiamo essere NP-Hard A noto e dimostrare che si puo' effettuare una riduzione in tempo polinomiale.

La soluzione generale di un esercizio di riduzione a partire da un linguaggio NP-Hard e' composta da tre sotto punti:


1. Descrivere un algoritmo che prende una **qualsiasi** istanza di X e la trasforma in un'istanza **speciale** di Y
2. Dimostrare che una buona istanza di X e' convertita in una buona istanza di Y
3. Dimostrare che una buona istanza di Y e' convertita in una buona istanza di X

L'algoritmo di conversione e' generale, ma la dimostrazione verte su istanze particolari del problema.

- Dato un certificato di X, dobbiamo dimostrae

## Algoritmo Conversione

Dato i nodi del grafo, trasformiamo i nodi aggiungendo un'informazione nel seguente modo:   

1. Dato un vertice  il valore 2 - rappresenta due sassolini
2. In tutti i nodi tranne l'ultimo, inseriamo il valore 1 - rappresenta un sassolino
3. Nell'ultimo nodo inseriamo il valore 0 - nessun sassolino
4. Rimuoviamo le direzioni dagli archi.

## Dimostrazione Hamilton $\rightarrow$ PebbleDestruction

Se abbiamo una soluzione per un cammino sul grafo orientato, abbiamo una dimostrazione per il PebbleDestruction.

Nel grafo che otteniamo possiamo rimuovere tutti i sassolini tranne uno partendo dal nodo con due sassolini, rimuovendo i due sassolini e aggiungendone uno al nodo successivo del circuito. L'ultimo nodo non ha sassolini e ne riceve uno per via della mossa precedente.

La dimostrazione verte sul fatto che il certificato che abbiamo contiene un circuito Hamiltoniano, quindi possiamo seguirne i vertici seguendo le regole del gioco.

## Dimostrazione PebbleDestruction $\rightarrow$ Hamilton

In questo caso il certificato di partenza e' un circuito Hamiltoniano, a cui aggiungiamo i ciottoli. La sequenza parte necessariamente dal vertice con due sassolini - per le condizioni del gioco - e prosegue visitando gli altri vertici. Dato che una volta che visito un vertice non posso piu' visitarlo - non ci sono ciottoli con cui fare una mossa - e dal momento che li visito tutti ottengono una soluzione per il ciclo Hamiltoniano.

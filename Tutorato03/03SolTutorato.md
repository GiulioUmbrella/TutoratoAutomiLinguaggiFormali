w# Tutorato 03
Giulio Umbrella
03 Aprile 2022

## Ex 1 Linguaggi regolari

### Ex 1.1

Per una stringa w = $w_{1}w_{2}...w_{n}$, l'inversa e' la stringa $w^{R}=w_{n}, \cdots, w_{2}, w_{1}$. Per ogni linguaggio regolare A, sia $A^{R}=\{w^{R}|w \in A\}$. Mostrare che se A e' regolare, allora lo e' anche $A^{R}$.

Questo esercizio e' diverso da quelli visti in precedenza; dato un linguaggio regolare, ci viene chiesto di dimostare che con una modifica possiamo ottenere un altro linguaggio regolare. Dobbiamo percio' ragionare in modo piu' generico, senza produrre un automa specifico. Una soluzione informale e' la seguente

1. Dato il linguaggio A, produco un $NFA_1$ che lo riconosce A.
2. Per produrre l'automa che riconoscere il linguaggio $A^{R}$, posso modificare $NFA_1$ in $NFA_2$
   1. Inverto la direzione delle transizioni
   2. Lo stato iniziale di $NFA^{1}$ diventa accettante
   3. Lo stato accettante di $NFA^{2}$ diventa iniziale
3. Se $NFA^{1}$ ha piu' di uno stato accettante, aggiungo uno nuovo stato iniziale e una epsilon transizione pverso tutti gli ex-stati accettanti.

Per questo esercizio e' necessario partire da un NFA in modo da avere un solo percorso da stato iniziale ad accettante e poter seguire l'automa in senso inverso.


### Ex 1.2

Sia A/b = $\{w | wb \in A\}$. Mostrare che se A e' un linguaggio regolare e $b \in \sigma$, allora A/b e' regolare.

Come in Ex1.1 partiamo da un automa che riconosce il linguaggio regolare A e produciamo l'automa che riconosce A/b. Modifichiamo l'automa spostando lo stato accettante allo stato precendente a quello in cui viene riconosciuta la parola che termina per b (ed eliminiamo la transione associata).

## 2 Pumping Lemma

Dimostrare che i seguenti linguaggi non sono regolari


### Ex 2.1

$\{0^{n} 1^{m} 0^{n} |  m,n \ge 0 \}$

Per dimostrare che il linguaggio non e' regolare procediamo per contraddizione, ossia ipotiziamo che il linguaggio sia regolare e dimostriamo che questo porta ad una contraddizione, l'obbiettivo e' trovare una parola che rispetti le condizioni del pumping lemma che una volta pompata produca una parola non appartenente al linguaggio.  

Il pumping lemma infatti deve valere per tutte le parole che ne rispettano i requisiti; basta trovare una singola parola che viola la condizione per falsificarlo

**Passo 1 Scelta dimostrazione**: la tecnica che usiamo e' la contraddizione - assumiamo che il linguaggio sia regolare e che rispetti il pumping lemma. Esiste quindi una costante k che rappresenta la lunghezza minima della parola.  

NB: stiamo ipotizzando solo che k esista, non stiamo effettivamente scegliendo un valore.

**Passo 2 Scelta parola**: sappiamo che il pumping lemma deve valere per tutte le parole di lunghezza almeno k, quindi scegliamo una parola che rispecchi tale condizione. Una possibile scelta e' $w=0^{k}1^{k}0{k}$, dato che soddisfa automaticamente la condizione di lunghezza minima.

**Passo 3 Suddivisione parola**: ora dobbiamo spezzare la parole in tre componenti x, y e z. Il teorema ci dice che $|xy| \leq0$ e $|y| >0$. La scelta della parola $w=0^{k}1^{k}0{k}$ ci garantisce in modo automatico la struttura di xy e y, dato che i suoi primi k caratteri sono tutti zero.

Possiamo quindi scrivere che

- $y = 0^{p}$, con $p>0$
- $xy = 0^{k-p}$
- z e' uguale al resto della parola

**Passo 4 Scelta i**: i passi da 1 a 3 sono funzionali al passo quattro; ora dobbiamo usare quanto fatto prima per dimostrare che la parola pompata non appartine al linguaggio. Quindi con $w'= xy^{i}z$ se scegliamo i = 0otteniamo $xy^{0}z = 0^{k-p}1^{k}0{k}$.

La parola w' non appartiene al linguaggio, e quindi le condizioni del pumping lemma sono violate. L'ipotesi iniziale mi porta ad una contraddizione e quindi il linguaggio non puo' essere regolare.

### Ex 2.2

$\{w \in \{0,1\}^{\*} \mid  w e' palindroma\}$

Per dimostrare che il linguaggio non e' regolare, procediamo come nel precedente esercizio.

1. Assumiamo che il linguaggio sia regolare e che esista un costante k
2. Scegliamo una parola w che appartiene al linguaggio con $|w| > k$, ad esempio $w = 0^{k}0^{k}$
3. Suddividiamo la parola in xyz
- $y =0^{p}, p>0$
- $x =0^{k-p}$
- z tutto il resto
4. Dimostriamo che esiste un i per cui la parola $xy^{i}z$ non appartiene al linguaggio. Ad esempio con i = 0 otteniamo che $xy^{0}z=0^{k-p}0^{k}$ ossia una parola non palindroma.

NB: sia per Ex 2.1 che 2.2 abbiamo scelto i=0 per trovare un controesempio, ma non e' l'unico possibile. Qual'e' il solo valore che non puo' essere scelto?


### EX 2.3

Per questo esercizio possiamo utilizzare il risultato dell'Ex 2.2. Sappiamo infatti che il complementare di linguaggio regolare e' regolare, e ragionare per assurdo.

1. Assumiamo che il linguaggio delle parole non palindrome sia regolare.
2. Dal punto 1, sappiamo che il linguaggio complementare composto dalle parole palindrome e' regolare
3. Il punto 2 ci porta ad una contraddizione, perche' abbiamo dimostrato che il linguaggio delle parole palindrome non puo' essere regolare.

### Ex 2.4

Questo esercizio puo' essere risolto come l'esercizio 2.3 utilizzando la non regolarita' del linguaggio complementare. Dal momento che sia p che q sono strettamente maggiori di zero, il linguaggio e' formato da parole di lunghezza composta. Il linguaggio di parole di lunghezza pari a numeri primi non e' regolare (vedi Slide) e quindi il linguaggio non e' regolare.

### Ex 2.5

5. $\{0^{n}1^{m}0^{m+n} n,m \in \mathbb{N}  \}$

La soluzione di questo esercizio e' simile agli esercizi Ex 1 e Ex 2.


### Ex 2.6

$\{0^{n}0^{2^{n}} n,m \in \mathbb{N}  \}$

Questo esercizio verra' svolto nel prossimo tutorato [se non fosse possibile, aggiornero' le soluzioni].

## Ex 3 Lunghezza minima pumping

Per ognuno dei seguenti linguaggi, dare la lunghezza minima del pumping e giustificare la risposta.

L'esercizio chiede di identificare una lunghezza minima in modo da poter applicare il pumping lemma. In altri termini, dobbiamo indentificare la lunghezza per cui non e' possibile in alcun modo applicare il pumping lemma.

NB: le soluzioni degli altri punti verrano caricate prossimamente.

### Ex 3.1

$0001^{\star}$

Per questo linguaggio, possiamo vedere che e' impossibile applicare il pumping lemma per parole piu' corte di tre. Infatti pompando una parola come 000 otterremmo una parola con piu' di tre zeri, che non viene riconosciuta dal linguaggio. La lunghezza minima e' quattro, infatti data la parola 0001 possiamo impostare xy = 0001, y = 1 e z = $\epsilon$ e pompare la parola per ogni i.

### Ex 3.3
1011

Il linguaggio e' composta da una sola parola. Qualsiasi suddivisone in xyz ci darebbe la possibilita' di pompare la parola aggiungendo o togliendo caratteri. La lunghezza minima e' quindi 5.

NB: se utilizzassimo i=0 otterremo parole appartenti al linguaggi perche' la parola non viene modificata, ma il nostro obbiettivo e' trovare una lunghezza che funzioni per ogni $i \geq 0$

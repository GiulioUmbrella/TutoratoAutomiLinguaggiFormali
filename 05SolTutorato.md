---
title: Soluzioni Tutorato 5
author: Giulio Umbrella
---

# Ex 1

Dimostrare che il seguente linguaggio A = $\{ 0^{n} | n = 2^{k}, k \in \mathbb{N} \}$ non e' regolare.

Per dimostare l'affermazione procediamo per assurdo usando il Pumping Lemma; cioe' dimostriamo che esiste una parola che una volta pompata non appartiene al linguaggio.

Il procedimento e' simile a quanto visto in precedenza

1. Assumiamo che il linguaggio sia regolare
2. Scegliamo una parola che rispetti la lunghezza minima
3. Suddividiamo la parola in xyz
4. Troviamo i tale che $xy{i}z$ non appartiene al linguaggio

Per questo esercizio, la suddivisione della parola e' immediata, dato un qualsiasi k ottengo $w=0^{k}$ e quindi ottengo automaticamente che 

- $y = 0^{b}, b > 0$
- $x = 0^{a}, a + b \leq k$
- z e' formata solo zeri

Applicando il pumping lemma con i = 0 otteniamo $xy^{0}z = xz = 0^{2^{k} -b}$

Il problema e' nella scelta del valore da dare ad i. Per alcuni tipi di esercizi, la scelta di i e' molto semplice, ad esempio per il linguaggi delle parole palindrome abbiamo che se $w=0^{k}0^{k}$, basta impostare i = 0 per ridurre la lunghezza della prima meta' e ottere una parola che non appartiene al linguaggi.

In questo esercizio invece dobbiamo prestare piu' attenzione. Esistono infatti dei valori di i che possono produrre una parola che appartiene al linguaggio. Ad esempio, $2^{6}-32 = 32 = 2^{5}$ e quindi la parola appartiene al linguaggio.

Quindi non basta ridurre il numero di simboli, dobbiamo dimostare che la parola che si ottiene non appartiene al linguaggio. Nella dimostrazione assumiamo che il lunguaggio sia regolare e che esista la costante del pumping lemma k. La dimostrazione deve quindi basarsi sua un generico valore.

Una possibile dimostrazione e' la seguente:

- $w = 0^{2^{k}}$
- $x=\epsilon$
- $y = 0^{p}, 0 < p < k$
- $z = 0^{2^{k}-p}$

Possiamo considerare le potenze di due come $2^{2},2^{3},\dots,2^{k},2^{k+1},\dots$, se riusciamo a pompare una parole per produrne una di lunghezza compresa fra $2^{k}$e $2^{k+1}$, abbiamo produtto una parola che non appartiene al linguaggio.

Se prendiamo i = 2, $xy^{2}z = (0^{p})^{2}0^{2^{k}-p} = (0^{2p})0^{2^{k}-p} = 0^{2^{k}} 0^{p}$

Ora dobbiamo dimostare che la parola non puo' appartenere al linguaggio. Se prendiamo la parola appartenente al linguaggio successiva $0{2^{k+1}}$ la possiamo scomporre come $0^{2^{k+1}} =0^{2^{k} 2} = 0^{2^{k}+2^{k}} =  0^{2^{k}} 0^{2^{k}}$ 

Dato che p e' sicuramente minore di $2^{k}$, la parola non appartiene al linguaggio


# Ex 2

Dati due linguaggi A e B definiamo lo shuffle dei due linguaggi come $\{w | w = a_{1}b_{1},\dots,a_{k}b_{k}, \textrm{ con } ,   a_{1},\dots,a_{k} \in A,  b_{1},\dots,b_{k} \in B \textrm{ con } a_{i}, b_{i} \in \Sigma   \}$.

Dimostrare che se A e B sono regolari, lo shuffle di A e B e' un linguaggio regolare.

## Dimostrazione informale

Per dimostrare che un linguaggio e' regolare, basta produrre un automa a stati finiti. A differenza di altri esercizi in cui abbiamo una precisa definizione del linguaggio (ad esempio stringhe binarie di lunghezza pari), in questo contesto sappiamo solo che il linguaggi e' derivato da altri linguaggi. 

Questo esercizio va percio' affrontato in modo generale; sappiamo infatti solo che A e B sono regolari, ma non abbiamo indicazioni di nessun tipo sulla loro struttura. Dobbiamo costruire una dimostrazione di carattere generale che funziona per ogni linguaggio regolare A e B.

Sappiamo che A e B sono due linguaggi regolari quindi sappiamo che esistono due automi a stati finiti che li rappresentano. Attenzione, sappiamo che i due automi esistono, ma non abbiamo informazioni su cosa contengono.

Dati i due automi DA e DB definiamo 

- DA = (QA, ,A ,qA,FA)
- DB = (QB, ,B ,qB,FB)

Utilizzando questi automi, costruiamo un automa DS che riconosce le parole composte dallo shuffle di due parole di A e B. Possiamo pensare che DS ha a disposizione DA e DB, quindi l'automa puo' richiamarne le funzioni di transizione. Sappiamo che nell'input i caratteri sono alternati fra la parola in A e quella in B.

L'ordine delle operazioni e' il seguente:

1. 1L'automa DS parte dallo stato iniziale di A e B
2. L'automa DS legge il primo input e richiama le funzioni di transizioni di DA e aggiorna lo stato, infatti sappiamo che il primo simbolo appartiene al linguaggio A ; in questa fase DB rimane allo stato iniziale
3. Il secondo input per costruzione appartiene al linguaggio B; l'automa DS lascia DA immutato e aggiorna DB.
4. La procedura riparte aggiornando DA

In questo modo, le due parole di A e B vengono processate in parallelo ma in modo asincrono.  

## Dimostrazione formale

Per la dimostrazione formale dobbiamo define i cinque elementi di un automa a stati finito. Possiamo assumere che l'alfabeto sia 

### Funzione di transizione
La funzione di transione e' definita nel seguente modo

((x,y,A),a) = ((x,a),y,B)

**Input**: la funzione prende input una tupla di tre valori e l'input corrent

- x stato corrente di DA
- y stato corrente di DB
- A flag per indicare che l'input a deve essere processato usando DA

**Output**: la funzione produce in output una tupla di tre elementi
- (x,a) nuovo stato di DA a partire da x con input a
- y stato corrente di DB
- B flag per indicare che l'input deve essere processato usando l'automa DB

Definiam poi una funzione simile per 

Possiamo notare i seguenti punti:

- La procedura aggiorna DA ma lascia immutato DB.
- Il flag A viene cambiato in B per indicare che il prossimo input deve essere processato usando DB.
- Il meccanismo della funzione di transione di DS e ' sempre lo stesso: la funzione prende in input uno stato  e simbolo e produce in output uno stato.
- Gli stati di DS sono identificati da tuple di 3 elementi

### Insieme di stati

Per completare l'automa, dobbiamo definirne gli stati in input:

QS = QA x QB x {A,B}

**NB**: X e' il prodotto cartesiano fra insiemi, ossia l'insieme prodotto da tutte le coppie di singoli elementi. Ad esempio {a,b} X {c,d} = {{a,c), (a,d), (b,c), (b,d)}


### Stato iniziale 

q = $(q_{A}, q_{B}, A), ossia gli automi vengono processati a partire dai loro rispetti stati iniziali, e il primo automa ad essere processato e' A. 

### Stato accettante

F = FA x FB x {A}, l'automa accetta se entrambi gli stati sono accettanti; il flag A serve ad indicare che il prossimo input e' dal linguaggio A, e quindi l'input letto in precedenza era da B. 




Ora dobbiamo a


# Ex 3

# Ex 4
 


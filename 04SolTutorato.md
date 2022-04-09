---
title: Soluzioni Tutorato 4
author: Giulio Umbrella
---

## [Opzionale]

1. a elevvanto alla n quaddro
2. 

# Ex 1 Grammatiche libere da contesto

Definire delle gramatiche libere da contesto per i seguenti linguaggi

## Ex 1.1

$\{ w \mid  w = w^{R} \textrm{ ,w e' palindroma}\}$

Per ogni produzione, dobbiamo aggiungere lo stesso carattere a destra e a sinistra. Quindi definima una singola variabile che aggiunga lo stesso simbolo ogni volta che viene invocata. Aggiungiamo inoltre due produzioni in piu con terminali 0 e 1, in modo da produrre anche stringhe di lunghezza 1 (sono palindrome) e stringhe palindrome di lunghezza pari. Le regole per la grammatica sono le seguenti.

$R\rightarrow 0R0|1R1|1|0| \epsilon$

## Ex 1.2

$\{ w\#x \mid w^{R} \textrm{ e' una sottostringa di x }  \}$

In maniera informale possiamo rappresentare il linguaggio nel seguente modo $\{w \# \{0+1\}^{\star} w^{R} \{0+1\}^{\star} \}$ (NB la precedente rappresentazione **non** vuole essere una espressione regolare, ma un modo schematico di capire la struttura delle stringe)

Possiamo individuare due componenti

1. L'insieme di tutte le stringhe formate da 0,1
2. Le stringhe palindrome - possiamo infatti pensare alle stringhe palindrome come alla contatenzione di una parola w con la sua opposta.

Fatto questo, scriviamo delle regole per i due casi

1. $X\rightarrow 0X|1X|\epsilon$
2. $T\rightarrow 0T0 | 1T1$

Il problema adesso e' come combinare le due regole? Per farlo, possiamo pensare che le variabili possono essere chiamate in qualsiasi ordine, non necessariamente da destra a sinistra. Possiamo modificare la prima regola nel seguente modo $T\rightarrow 0T0|1T1|\#X$. Tornando al nostro esempio informale, abbiamo una regola che ci permette di produrre stringhe del tipo $\{w\# X w^{R} \}$. Adesso possiamo usare la regola su X per aggiungere qualsiasi stringa.


L'ultimo passaggio e' capire come aggiungere la parte finale della stringa. Per farlo aggiungiamo una nuova regola per inserire immediatamente X a destra di T, $S \rightarrow T|X$

La grammatica che otteniamo e' la seguente:

$S \rightarrow T|X$  
$T \rightarrow 0T0 | 1T1 |\# X$  
$X \rightarrow 0X| 1X| \epsilon$  



## Ex 1.3

$\{ x\#y \mid x,y \in \{0,1\}^{\star}, x \neq y \}$

# Ex 2 Grammatiche ambigue


# Ex 3 Forma normali

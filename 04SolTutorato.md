---
title: Soluzioni Tutorato 4
author: Giulio Umbrella
---

# Ex 1 Grammatiche libere da contesto

Definire delle gramatiche libere da contesto per i seguenti linguaggi

## Ex 1.1

\{ w | la lunghezza di w e' dispari con all'interno il simbolo zero\}

Data la parola w, possiamo dividerla nella concatenazione di tre componentti, w = Sx 0 Dx. 

Per la somma di numeri pari e dispari sappiamo che valgono i seguenti

- Pari + Pari = Pari
- Dispari + Dispari = Pari
- Pari + Dispari = Dispari

Possiamo verificare se w e' pari o dispari sulla base della lunghezza delle tre componenti.

|  \|Sx\| |  \|0\|  |  \|Dx\| | Dispari? |
|:-------:|:-------:|:-------:|----------|
| Pari    | Dispari | Pari    |     S    |
| Pari    | Dispari | Dispari |     N    |
| Dispari | Dispari | Pari    |     N    |
| Dispari | Dispari | Dispari |     S    |

Quindi vogliamo che a destra e a sinistra le stringhe siano entrambe di lunghezza pari o entrambe di lunghezza dispari.

Le produzioni sono le seguenti:

$S\rightarrow$ PSP | DSD| 0  
$P\rightarrow 00|01|10|11|\epsilon$  
$D\rightarrow 0|1|0P|1P$  

## Ex 1.2

$\{ w \mid  w = w^{R} \textrm{ ,w e' palindroma}\}$

Per ogni produzione, dobbiamo aggiungere lo stesso carattere a destra e a sinistra. Quindi definima una singola variabile che aggiunga lo stesso simbolo ogni volta che viene invocata. Aggiungiamo inoltre due produzioni in piu con terminali 0 e 1, in modo da produrre anche stringhe di lunghezza 1 (sono palindrome) e stringhe palindrome di lunghezza pari. Le regole per la grammatica sono le seguenti.

$R\rightarrow 0R0|1R1|1|0| \epsilon$

## Ex 1.3

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



## Ex 1.4

$\{ x\#y \mid x,y \in \{0,1\}^{\star}, x \neq y \}$

# Ex 2 Grammatiche ambigue

Considerate la seguente grammatica

S $\rightarrow$ A | If-then | If-then-else  
If-then $\rightarrow$ if cond then S  
If-then-else $\rightarrow$ if cond then S else  
A $\rightarrow$ a:=1  

**Ex1** Dimostrare che la grammatica e' ambigua  
**Ex2** Modificare la grammatica per rimuovere l'ambiguita'  

## Ex 2.1 Dimostrare che la grammatica e' ambigua

Per dimostrare chw una grammatica e' sufficiente tovar due derivazioni a sinistra che producono la stessa parola. Un possibile esempio e' il seguente:

S $\rightarrow$ If-then $\rightarrow$ If cond then S $\rightarrow$ If cond then It-then-else $\rightarrow$  
If cond then If cond then S else S

S $\rightarrow$ If-then-else $\rightarrow$ If cond then S else S $\rightarrow$ If cond then If-then else S $\rightarrow$  
If cond then If cond then S else S

Per completare entrambe le derivazioni, sostituiamo S con A e poi inseriamo il terminale a:=1

Per illustrare il problema, possiamoo vedere che le due derivazioni possono essere interpreatate in due modi diversi:

if (conditionA) {  
	if (conditionB) statementA; else statementB;  
}  

oppure

if (conditionA) {   
	if (conditionB) statementA;  
}  
else statementB;   

## Ex 2.2 Rimuovere ambiguita' da grammatica

Per rimuovere l'ambiguita', dobbiamo modificarne le regole. Introduciamo quindi due diverse variabili che definiamo Open e Closed con le seguenti caratteristiche:

- **Open**: puo' produre un if senza corrispettivo else 
- **Closed**: non ha nessun if oppure tutti gli if hanno un corrispettivo else

Quindi modifichiamo le regole come segue:

S $\rightarrow$ | Open | Closed  
Open $\rightarrow$ if cond then S | if cond then Closed else Open  
Closed $\rightarrow$ A |  if cond then Closed else Closed  
A $\rightarrow$ a:=1   

Possiamo vedere che tra un if e un else, possiamo aggiungere un if solo se aggiungiamo un corrispettivo else.

Possiamo controllare la derivazione ottenuta in precedenza:

S $\rightarrow$ Open $\rightarrow$ If cond then S $\rightarrow$ if cond then Closed $\rightarrow$ If cond then If cond then Closed If cond Closed $\rightarrow$ If cond if Cond A if cond Closed $\rightarrow$ If cond if Cond A if cond A

# Ex 3 Forma normali

Convertire in forma normale la seguente grammatica

A -> BAB|B|$\epsilon$
B -> 00|$\epsilon$

**Passo 1** Aggiungere variabile inizale
La variabile iniziale A e' presente anche a destra, quindi dobbiamo aggiungere una nuova variable iniziale.

S -> A
A -> BAB|B|$\epsilon$
B -> 00|$\epsilon$

NB

**Passo 2** Rimuovere regole $\epsilon$ 

A -> $\epsilon$

Aggiungiamo la produzione $\epsilon$ alla variabile iniziale S. Possiamo farlo perche' la forma normale di Chomsky ammetta la $\epsilon$ per la variabile iniziale.

S -> A|$\epsilon$
A -> BAB|B|
B -> 00|$\epsilon$


B -> $\epsilon$

Ora rimuoviamo la $\epsilon$ per la B. Dato che abbiamo la produzione BAB, dobbiamo considerare tre possibili casi, BA, AB, A.

S -> A|$\epsilon$
A -> BAB|B|BA|AB|A
B -> 00

Attenzione! Abbiamo eliminato la produzione A -> $\epsilon$ al passo precedente, quindi **non** dobbiamo aggiungerla.

**Passo 3** Rimuovere regole unitarie

Abbiamo tre regole unitarie da eliminiare

Possiamo eliminiare A-> A perche' e' una regola ciclica (non produce nulla) e sostituiamo 00 al posto di B nella produzione di A. Fatto questo, rimuoviamo la regola unitaria da S.

S -> BAB|00|BA|AB|$\epsilon$  
A -> BAB|00|BA|AB  
B -> 00  


**Passo 4** Conversione regole finali

Abbiamo una produzione con tre variabili a destra della freccia, introduciamo una nuova produzione per avere solo due variabli a destra.

S -> CB|00|BA|AB|$\epsilon$  
A -> CB|00|BA|AB  
B -> 00  
C -> BA








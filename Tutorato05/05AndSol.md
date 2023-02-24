---
title: Soluzione esercizi aggiuntivi
author: Giulio Umbrella
---

# Ex 1

Dimostrare che il linguaggio $\{ 0^{m}1^{n} | \textrm{n/m e' un numero intero} \}$ non e' regolare

# Soluzione

Dimostriamo che il linguaggio non e' regolare per assurdo; 

- k lunghezza del pumping lemma
- scegliamo la parola $w= 0^{k+1}1^{k+1}$, che soddisfa la lunghezza minima e appartiene al linguaggio.

Ora suddividiamo la parola w in xyz con $|xy| < k$ e $y \neq \epsilon$

Data la lunghezza della parola e i requisti del pumping lemma sappiamo che xy e formata interameente da 0, e quindi abbiamo 

- $x =\epsilon$
- $y =0^{p}, p > 0$
- $z =0^{k+1 -p }1^{k+1}$

Consideriamo l'esponente i = 2 e otteniamo la parola $xy^{2}z = 0^{2p}0^{k+1-p}1^{k+1} = 0^{k+1+p}1^{k+1}$.

Otteniamo un parola con n/m = (k+1)/(k+1+p), ossia un numero compreso fra 0 e 1. Il valore non e' intero e quindi la parola non appartiene al linguaggio. Il linguaggio quindi non e' regolare.





# Ex 2 
Siano L e M due linguaggi regolari su alfabeto {0,1}. Dimostare che il linguaggio L\&M = $\{x\&y | x \in L, y \in M, |x| = |y| \}$, dove x\&y e' l'and logic bit a bit. Per esempio, 101\&001 = 001.


# Soluzione

L'obiettivo e' costruire un automa $D_{S}$ che riconosca le stringhe composte dall'and logico delle stringhe ricosciute da $D_{A}$ e $D_{B}$. Data una stringa in input, vogliamo che sia riconosciuta dal linguaggio se entrambi gli automi la riconoscono.

I linguaggi sono regolari, quindi abbiamo a disposizione due automi:

- $D_{A}$ = ($Q_{A}$, $\Sigma$ ,$\delta_{A}$ ,$q_{A}$,$F_{A}$)
- $D_{B}$ = ($Q_{B}$, $\Sigma$ ,$\delta_{B}$ ,$q_{B}$,$F_{B}$)


Per decidere se accettare o meno, l'automa $D_{S}$ ha a disposizione gli automi dei due linguaggi; per ogni simbolo in output, $D_{S}$ fornisce il simbolo sia a $D_{A}$ che $D_{rBA}$. Se entrambi gli automi accettano la parola, l'automa $D_{S}$ accetta a sua volta. 

Il punto e' capire che tipo di input fornire ai due automi. Per capire meglio cosa fare, usiamo la tabella logica dell'operazione And: 


| A | B | A & B |
|---|---|:-----:|
| 1 | 1 |   1   |
| 1 | 0 |   0   |
| 0 | 1 |   0   |
| 0 | 0 |   0   |

Possiamo dedurre il seguente comportamento:

- Quando l'input e' 1 sappiamo che gli automi stanno processando entrambi il valore 1.
- Se il simbolo e' 0, non sappiamo di preciso quale sia il valore processato - infatti a 0 corrispondono tre coppie di valori.

Definiamo x e y come gli stati attuali di $D_{A}$ e $D_{B}$ e definiamo la funzione di transizione come segue.

- $\delta((x,y),1) = (\delta(x,1),\delta(y,1))$ 
- $\delta((x,y),0) = ((\delta(x,1),\delta(y,0)),(\delta(x,0),\delta(y,1)),(\delta(x,0),\delta(y,0))$ 

Quindi se abbiamo il simbolo 1 facciamo avanzare entrambi gli automi; se invece abbiamo zero, dobbiamo tentare tutte le possibili strade. In questo modo stiamo costruendo un NFA per coprire tutti i possibili percorsi.

Se $D_{A}$ automa accetta la parola, esistera' un percorso che porta ad uno stato accettante (stessa cosa per $D_{B}$).


Per completare l'automa, dobbiamo definirne le altre componenti:

- $\Sigma = \{0,1\}$
- $Q_{S}$ = $Q_{A}$ x $Q_{B}$ 
- q = $(q_{A}, q_{B})$
- F = $F_{A}$ x $F_{B}$ 

# Ex 3

Variante dell'esercizio 3

# Ex 4



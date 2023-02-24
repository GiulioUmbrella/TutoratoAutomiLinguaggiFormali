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

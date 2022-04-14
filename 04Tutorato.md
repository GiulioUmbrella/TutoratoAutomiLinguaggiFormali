---
title: Tutorato 4
author: Giulio Umbrella
---

# Ex 1 Grammatiche libere da contesto

Definire delle gramatiche libere da contesto per i seguenti linguaggi

## Ex 1.1

\{ w | la lunghezza di w e' dispari con all'interno il simbolo zero\}

## Ex 1.2

$\{ w \mid  w = w^{R} \textrm{ ,w e' palindroma}\}$

## Ex 1.3

$\{ w\#x \mid w^{R} \textrm{ e' una sottostringa di x }  \}$

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

# Ex 3 Forma normali

Convertire in forma normale la seguente grammatica

A $\rightarrow$ BAB|B|$\epsilon$  
B $\rightarrow$ 00|$\epsilon$  


## Ex 4 Esercizi aggiuntivi

Convertire in forma normale le seguenti grammatiche

### Ex 4.1

S $\rightarrow$ aXbX  
X $\rightarrow$ aY|bY$\epsilon$  
Y $\rightarrow$ X|c  

### Ex 4.2

S $\rightarrow$ AbA  
A $\rightarrow$ Aa|$\epsilon$




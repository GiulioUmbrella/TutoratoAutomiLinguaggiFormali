
---
title: Soluzioni Tutorato 5
author: Giulio Umbrella
---

# Ex 1

Dimostrare che il seguente linguaggio A = $\{ 0^{n} | n = 2^{k}, k \in \mathbb{N} \}$ non e' regolare.


# Ex 2

Dati due linguaggi A e B definiamo lo shuffle dei due linguaggi come $\{w | w = a_{1}b_{1},\dots,a_{k}b_{k}, \textrm{ con } ,   a_{1},\dots,a_{k} \in A,  b_{1},\dots,b_{k} \in B \textrm{ con } a_{i}, b_{i} \in \Sigma   \}$.

Dimostrare che se A e B sono regolari, lo shuffle di A e B e' un linguaggio regolare.

# Ex 3

Sia L un linguaggio regolare su un alfabeto $\Sigma$ con $\# \in \Sigma$ e sia dehash(w) la funzione che rimuove il simbolo hash dalla stringa. Ad esempio dehash(1#1) = 11, dehash(0#10#) = 010. Dimostrare che il linguaggio dehash(L) = $\{dehash(w): w \in L \}$ e' regolare.

# Ex 4

Sia L un linguaggio regolare su un alfabeto $\Sigma$. Dimostrare che il linguaggio suffixes(L) = $\{ y | xy \in L \textrm{per qualche stringa x} \in \Sigma^{\ast}  \}$ e' regolare.


# Esercizi aggiuntivi

1. Dimostrare che il linguaggio $\{ 0^{m}1^{n} | \textrm{n/m e' un numero intero} \}$ non e' regolare
2. Siano L e M due linguaggi regolari su alfabeto {0,1}. Dimostare che il linguaggio L\&M = $\{x\&y | x \in L, y \in M, |x| = |y| \}$, dove x\&y e' l'and logic bit a bit. Per esempio, 101\&001 = 001.
3. Siano L e M due linguaggi regolari su alfabeto {0,1}. Dimostare che il linguaggio $L XOR M = \{xXORy | x \in L, y \in M, |x| = |y| \}$, dove $xXOR y$ e' l'and logic bit a bit. Per esempio,$101XOR001 = 100$.
4. Dimostrare che il linguaggio $\{ 0^{m}1^{n} | m = n^{3} \}$ non e' regolare.

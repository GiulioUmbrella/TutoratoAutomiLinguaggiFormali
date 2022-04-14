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

Il perfect shuffle fra due linguaggi e' dato da $\{ \}$, dimostrare che se A e B sono due linguaggi regolari, allora il perfect shuffle e' regolare. 

# Ex 3

# Ex 4



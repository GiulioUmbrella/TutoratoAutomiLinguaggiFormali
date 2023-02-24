---
title: Soluzioni tutorato 07
author: Giulio Umbrella
---

# Ex 1

Mostrare che se A e' Turing-Riconoscibile e $A \le_m A^C$ allora A e' Turing decidibile.

*Soluzione*

Per la dimostrazione mettiamo assieme i seguenti risultati:

1. $A \le_m A^C$ quindi abbiamo che $A^C \le_m A$ tramite la stessa riduzione
2. A e' Turing recognizable e quindi da $A^C \le_m A$ concludiamo che anche $A^C$ e' Turing recognizable.
3. Sia A che $A^C$ sono Turing recognizable e quindi A e' decidibile.

# Ex 2


Dimostriamo per assurdo cche HALT_TM non puo' essere un linguaggio regolare

Sia R la Turing Machine per il linguaggio $HALT_TM$; data una coppia M,w, possiamo eseguire M,w su R e quindi sappiamo se la computazione termina o meno in un numero finito di passi. Se R da reject vuol dire che M non accetta w e quindi possiamo rifiutare. Se invece R accetta, vuol dire che la computazione di M su w termina sempre. Dato che non sappiamo se terminera' con accettazione o rifiuto, facciamo girare w su M e restituiamo lo stesso risultato.

Ora, facciamo la stessa cosa ma tramite riduzione


**Riduzione**: una funzione che permette di trasformare un problema in un altro problema.
La funzione e' un se e solo se, possiamo tradurre la cosa in questo modo

A $\le_m$ B, se *esiste* una funzione tale che $w \in A$ **SSE** $f(w) \in B$

Con la riduzione posso prendere un problema e trasformarlo in un altro problema equivalente.

E' tutto molto interessante, ma a cosa ci serve la riduzione?
1. Thm 5.22 (ok fin qui tutto abbastanza regionevole)
2. Corolary 5.23 (e qui le cose iniziano a farsi complicate)

Ora dimostriamo che HALT_TM e' irriducibile tramite Riduzione

Riduzione da $A_TM$ a $HALT_TM$

    <!-- F = On input (M, w):
        1. Construct the following machine $M^{\*}$
        $M^{\*}$ = On input x:
            1. Run M on x.
            2. If M accepts, accept.
            3. If M rejects, enters a loop.
        2. Output⟨$M^{\*}$,w⟩.” -->


Aggiungiamo il pezzo che ci serve per gli esercizi, cioe' dimostriamo la riduzione

*KP* che cosa vuol dire la condizione se e solo se?

Stando alla definizione di riduzione, dovremmo dimostrare due passaggi

1. $w \in A \rightarrow f(w) \in B$
2. $f(w) \in B \rightarrow w \in A$

In alternativa, si puo' dimostrare che la dimostazione se e solo se puo' essere trasformata nel seguente modo:

1. $w \in A  \rightarrow f(w) \in B$
2. $w \notin A  \rightarrow f(w) \notin B$

Con questo possiamo dimostrare che la riduzione di $HALT_TM$ e' corretta.

$M,w \in A_TM$ e quindi per costruzione accetta, quindi la computazione termina.
$M,w \notin A_TM$ ci sono due casi
    1. Se M rifiuta, allora $M^*$ entra in loop.
    2. Se M entra in loop, anche $M^*$ entra in loop e di conseguenza non accetta

COMMENTO
1. In alcuni casi (come $HALT_TM$) e' semplice capire costruire una TM che dimostri la contraddizione, in altri come vedremo nei prossimi esercizi, no
2. Attenzione al caso di Loop! Ricordate che se una TM entra in loop equivalente al rifiuto della parola.


# Ex 210617_seconda_parte_soluzione

$A_{1010}$ = {M | M e' una TM tale che 1010 $\in$ L(M)}.

Per questo esercizio procediamo per riduzione

Dimostrazione riduzione
1.
2.

Perche' funziona? In caso di loop anche $M_w$ va in loop
A cosa serva il controllo x != 1010?

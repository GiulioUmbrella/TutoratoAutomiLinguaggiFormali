---
title: Soluzioni Tutorato 6
author: Giulio Umbrella
---

# Ex 1

Sia $ALL_{DFA}$ = {<A> | A e' un DFA che e L(A) = $\sum^{\star}$ }. Mostrare che $ALL_{DFA}$ e' decidibile.

*Soluzione*

Per questo esercizio possiamo usare una TM che simuli il funzionamento del DFA come visto a lezione.

*Opz1* Come primo tentativo, possiamo considerare tutte le stringhe in $sigma$ e verificare se l'automa le accetta oppure no. Se una stringa non appartiene al linguaggio, l'automa la rifiuta e la computazione si blocca. Il problema e' che questa soluzione potrebbe non terminare mai se l'automa A accetta tutte le stringe, mentre il testo ci chiede di dimostrare che il linguaggio e' decidibile, ossia la computazione si interrompe sicuramente.

*Opz2* In alternativa, possiamo usare i risultati visti a lezione sui linguaggi decidibili. Sappiamo infatti che il determinare se un automa accetta il linguaggio vuoto e' un problema decidibile.

Sulla base di questo, possiamo convertire $ALL_{DFA}$ nel suo complementare, ossia il linguaggio che ha come

Costruiamo una TM che agisce nel seguente modo:

1. Convertire il DFA nel suo complementare
2. Verificare che il linguaggio accettato dal complementare sia il vuoto
3. Se la TM accetta il complementare, allora accettiamo l'automa di partenza.

# Ex 2

Sia $S{REX}$ = {<R,S> | R e S sono espressioni regolari tali che L(R) e' un sottoinsieme di L(S)}. Mostrare che $S{REX}$ e' decidibile.

Anche per questo caso potremmo verificare se una stringa del linguaggio appartiene a L(R) ma non L(S), ma andremmo incontro allo stesso problema dell'EX1; se L(R) e' effettivamente un sottoinsieme di L(S), la computazione non terminera' mai, violando la consegna.


Come per EX 1, facciamo riferimento a risultati noti.

1. Per prima cosa ricordiamo la seguente proprieta' degli insiemi: se A e' sotto insieme di B, l'intersezione fra A e B e' uguale all'insieme A, $A \subset B \rightarrow A \cap B = A$.
2. Convertire un'espressione regolare nel suo corrispettivo DFA e' un problema decidibile; piu' precisamente la concatenazione di due operazioni decidibili, il passaggio da RE a NFA e da NFA a RE.
3. Verificare se due DFA riconoscono lo stesso linguaggio e' un problema decidibile.
4. L'intersezione fra due linguaggi regolari e' un linguaggio regolare (proprrieta' di chiusura)

Costruiamo quindi un automa che opera nel modo seguente:

1. Dato l'input con le due espressioni regolari, produce per ciascuno di essi i rispettivi DFA, denominati A e B
2. Costruiamo il DFA che riconosce l'intersezione di A e B
3. Verifichiamo che $L(A) \cap L(B) = L(A)$.

Se la TM accetta la stringa, L(R) e' sottoinsieme di L(S).

# Ex 3

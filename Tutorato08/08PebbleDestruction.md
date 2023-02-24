---
title: Soluzione Pebble Destruction
author: Giulio Umbrella
---


**Goal** Dimostrare la riduzione da Hamilton a PebbleDestruction

# Algoritmo Conversione

Dato i nodi del grafo, trasformiamo i nodi aggiungendo un'informazione nel seguente modo:   

1. Nel primo nodo inseriamo il valore 2 - rappresenta due sassolini
2. In tutti i nodi tranne l'ultimo, inseriamo il valore 1 - rappresenta un sassolino
3. Nell'ultimo nodo inseriamo il valore 0 - nessun sassolino
4. Rimuoviamo le direzioni dagli archi.

# Dimostrazione Hamilton -> PebbleDestruction

Se abbiamo una soluzione per un cammino sul grafo orientato, abbiamo una dimostrazione per il PebbleDestruction.

Nel grafo che otteniamo possiamo rimuovere tutti i sassolini tranne uno partendo dal primo node, rimuovendo i due sassolini e aggiungendone uno al nodo successivo. L'ultimo nodo non ha sassolini e ne riceve uno per via della mossa precedente.

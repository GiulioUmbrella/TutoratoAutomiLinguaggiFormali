\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{tikz}
\usetikzlibrary{automata, positioning, arrows}

\tikzset{
        ->,
        >=stealth',
        node distance=2cm,
        every state/.style={thick, fill=gray!10}
        }


\title{Tutorato 02 Soluzioni Esercizi}
\author{Giulio Umbrella }
\date{03 Aprile 2022}


\begin{document}

\maketitle
\section{Espressioni regolari}

\subsection{Ex1}
Scrivere l'espressione regolare per i seguenti linguaggi.\par
\begin{enumerate}
  \item 1(0+1)*1
  \item ((0+1)(0+1))*
  \item ((0+1)(0+1))*(0+1)
  \item (0+1)*00
  \item (0+1)(0+1)(0+1)0(0+1)
  \item (1 + 01 + 0011)*(0+e)
  \item (0+1)*00 + 0
  \item (0+1)(0+1)
  \item 01 + 10 + 11
\end{enumerate}

\subsection{Ex2}
Dire se le seguenti affermazioni sono vere o false.\par
\begin{enumerate}
    \item Falso
    \item Vero
    \item Devo controllare l'ordine di applicazione delle parentesi, aggiornero' il prima possibile.
\end{enumerate}

\section{Conversione da RE a FA}
Convertire le seguenti espressioni regolari in FA 

Per la soluzione applicare quanto riportato nelle slide


\section{Conversion da FA a RE}

\subsection{Ex1}
Fornire un FA per i seguenti linguaggi e convertire l'automa in una espressione regolare.

\subsubsection{Ex1}
Stringhe binarie di lunghezza pari. \\

Per prima cosa, costruiamo l'automa che riconosce le stringhe binarie di lunghezza pari, Figura \ref{fig:Ex3.1} \\

Prima di procedere, dobbiamo verificare se dobbiamo modifiare l'automa. Le etichette che contengono la virgola $0,1$ vengono modificate in somme $0+1$ come vediamo in \ref{fig:Ex3.2}. L'automa ha un solo stato accettante, quindi possiamo applicare l'algoritmo.  \\

Abbiamo un solo stato da rimuovere $q_1$, quindi procediamo come indicato dall'algoritmo. Il percorso da eliminare e' $q_0 \rightarrow q_0$, quindi facciamo la concatenazione delle espressioni regolari lungo il percorso - senza includere self loop perche' asssenti in $q_1$. Notare che il punto di partenza e di arrivo conicidono ma la tecnica da applicare e' la stessa. L'espressione regolare ottenuta viene aggiunta come self loop su $q_1$, Figura \ref{fig:Ex3.3} \\

In Figura \ref{fig:Ex3.3} vediamo che lo stato iniziale e finale coincidono, quindi possiamo ricavare l'espressione regolare come $((0+1)(0+1))^{\star}$. \\

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state, right of =q0]  (q1) {$q_1$};          
    
        \draw (q0) edge[bend left, above] node{0,1} (q1)
              (q1) edge[bend left, below] node{0,1} (q0);

    \end{tikzpicture}
    \caption{Automa di partenza}
    \label{fig:Ex3.1}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state, right of =q0]  (q1) {$q_1$};          
    
        \draw (q0) edge[bend left, above] node{0+1} (q1)
              (q1) edge[bend left, below] node{0+1} (q0);

    \end{tikzpicture}
    \caption{Sostituzione con espressoni regolari}
    \label{fig:Ex3.2}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \draw (q0) edge[loop above] node{(0+1)(0+1)} (q1);
             
    \end{tikzpicture}
    \caption{Rimozione stato q1}
    \label{fig:Ex3.3}
\end{figure}

 


\subsubsection{Ex2}

Strighe binarie in cui il simbolo 1 e' ripetuto al piu' una volta sola \\

Anche in questo esercizio, il primo passaggio e' rappresentare l'automa che riconosce il linguaggio (Figura \ref{fig:Ex4.1}).  \\

Rispetto all'esercizio precedente, l'automa ha bisogno di una modifica in piu'. Oltre a trasformare le etichette in espressioni regolari, dobbiamo ricavare un automa con un solo stato accettante. Per farlo e' sufficiente:
\begin{enumerate}
    \item Aggiungere un nuovo stato accettante
    \item Aggiungere una epsilon transizione da ciascuno stato accettante al nuovo stato accettante
    \item Gli stati accettanti nell'automa di partenza diventano stati ordinari. 
\end{enumerate}

Il risultato e' in Figura \ref{fig:Ex4.2} \\

Ora possiamo procedere ed eliminiamo lo stato $q_1$. Osservando le frecce in ingresso ed in uscita, vediamo che lo stato ha un precedessore e due successori, quindi dobbiamo modificare due percorsi $q_0 \rightarrow q_3$ e $q_0 \rightarrow q_2$. \\

Per il percorso $q_0 \rightarrow q_2$ concateniamo le espressioni regolari lungo il percorso e inseriamo in mezzo il self-loop su $q_1$ e otteniamo l'espressione regolare $10^{\star}1$. Notiamo che non ci sono percorsi diretti fra $_0$ e $q_2$, quindi non dobbiamo aggiunggere altri percorsi. Il risultato e' in \ref{fig:Ex4.3}. \\

Per il percorso $q_0 \rightarrow q_3$ dobbiamo fare piu' attenzione. Abbiamo un percorso rappresentato da $10^{\star}\epsilon$ e un percorso diretto rappresentato da $\epsilon$, quindi sappiamo che dobbiamo unire le due espressioni regolare tramite il $+$. Qui e' bene fermarsi un attimo e ragionare su cosa stiamo facendo; mentre nella concatenazione il simbolo $\epsilon$ puo' essere rimosso, nell'unione dobbiamo convervarlo, come si vede in Figura \ref{fig:Ex4.3}. \\

Il motivo e' che nella concatenazione stiamo aggiungendo il simbolo vuoto all'espressione regolare $10^{\star}\epsilon$ e quindi lasciamo il risultato immutanto. Nell'unione $10^{\star}\epsilon + \epsilon$ invece stiamo aggiungendo il simbolo vuoto all'espressione regolare, dandoli la possibilita' di accettare la parola vuota. In altri termini, scrivere $10^{\star}$ e' errato perche' stiamo lasciando fuori una parola, quella vuota. \\

La rimozione di $q_1$ da come risultato l'automa di Figura \ref{fig:Ex4.3}. Per prima cosa osserviamo che lo stato $q_2$ non ha alcuna transione verso $q_3$. Infatti, il percorso da $q_0$ a $q_2$ contiene tutte le stringhe non accettate dal linguaggio, ossia quelle in cui il simbolo 1 e' ripetuto piu' di una volta. Lo stato $q_2$ rappresenta una sorta di "cestino" o vicolo cieco; una volta entrati non e' piu' possibili arrivare in uno stato accettante. Per proseguire possiamo semplicemente rimuoverlo, ottenendo l'automa in Figura \ref{fig:Ex4.4}. \\

Abbiamo due stati, quindi terminiamo come suggerito dall'algoritmo e otteniamo l'espressione regolare $0^{\star}10^{\star} + \epsilon$. \\

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state,accepting,right of =q0] (q1) {$q_1$};
        \node[state, right of =q1] (q2)  {$q_2$};          
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[above] node{1} (q1)
              (q1) edge[loop above] node{0} (q1)
              (q1) edge[above] node{1} (q2)
              (q2) edge[loop above] node{0,1} (q2);

    \end{tikzpicture}
    \caption{Automa di partenza Step 1}
    \label{fig:Ex4.1}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state, initial, ] (q0) {$q_0$};
        \node[state, right of =q0] (q1) {$q_1$};
        \node[state, right of =q1] (q2)  {$q_2$};          
        \node[state, accepting] at (1,-2) (q3)  {$q_3$};
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[above] node{1} (q1)
              (q0) edge[above] node{$\epsilon$} (q3)
              (q1) edge[loop above] node{0} (q1)
              (q1) edge[above] node{1} (q2)
              (q1) edge[above] node{$\epsilon$} (q3)
              (q2) edge[loop above] node{0+1} (q2);

    \end{tikzpicture}
    \caption{Aggiunta nuovo stato finale q3 }
    \label{fig:Ex4.2}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state, initial, ] (q0) {$q_0$};
        \node[state, right of =q1] (q2)  {$q_2$};          
        \node[state, accepting] at (0,-2) (q3)  {$q_3$};
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[above] node{10*1} (q2)
              (q0) edge[right] node{$10^{\star} + \epsilon$} (q3)
              (q2) edge[loop above] node{0+1} (q2);

    \end{tikzpicture}
    \caption{Rimozione stato q1 }
    \label{fig:Ex4.3}
\end{figure}


\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state, initial, ] (q0) {$q_0$};
        \node[state, accepting] at (0,-2) (q3)  {$q_3$};
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[right] node{$10^{\star} + \epsilon$} (q3);

    \end{tikzpicture}
    \caption{Rimozione stato q2 }
    \label{fig:Ex4.4}
\end{figure}


\subsubsection{Ex3}
Stringhe binarie che non comprendono la stringa 101.

Questo linguaggio presenta una complicazione, infatti richiede di ottenere tutte le stringhe che non rispettano una condizione. Anziche' ragionare su questo automa, possiamo ragionare in due passaggi: \\

\begin{enumerate}
    \item Costruiamo il DFA che accetta il linguaggio complementare.
    \item Invertiamo il DFA per ottenere il linguaggio di interesse.
\end{enumerate}

L'operazione complemento infatti e' chiusa per la classe dei linguaggi regolari; se applichiamo il complemento ad un linguaggio regolare, otteniamo un linguaggio regolare.

Per poter ottenere l'inverso, scegliamo di costruire un DFA che accetta il linguaggio complementare (Figura \ref{fig:Ex5.1}). Infatti, sappiamo che DFA e NFA sono equivalenti, ma come avete visto in classe, possiamo ottenere il linguaggio complementare da un DFA in modo piu' agevole, invertendo gli stati (Figura \ref{fig:Ex5.2}). \\


Una volta ottenuto l'automa, come primo step lo modifichiamo per ottenere un automa su cui applicare l'algoritmo di conversione, il risultato e' in Figura \ref{fig:Ex5.3}. Anche per questo esercizio, abbiamo uno stato che porta a parole non accettate dal linguaggio, lo stato $q_3$. Possiamo quindi rimuovere questo stato e procedere come l'algoritmo. 

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial] (q0) {$q_0$};
        \node[state,right of =q0] (q1) {$q_1$};
        \node[state,right of =q1] (q2) {$q_2$};
        \node[state, accepting, right of =q2] (q3) {$q_3$};
       
        \draw (q0) edge[loop above]  node{0} (q0)
              (q0) edge[above] node{1} (q1)
              (q1) edge[loop above] node{1} (q1)
              (q1) edge[above] node{0} (q2)
              (q2) edge[bend left, below] node{0} (q0)
              (q2) edge[above] node{1} (q3)
              (q3) edge[loop above] node{0,1} (q2);

    \end{tikzpicture}
    \caption{DFA linguaggio complementare}
    \label{fig:Ex5.1}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state,accepting,right of =q0] (q1) {$q_1$};
        \node[state,accepting,right of =q1] (q2) {$q_2$};
        \node[state, right of =q2] (q3) {$q_3$};
       
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[above] node{1} (q1)
              (q1) edge[loop above] node{1} (q1)
              (q1) edge[above] node{0} (q2)
              (q2) edge[bend left, below] node{0} (q0)
              (q2) edge[above] node{1} (q3)
              (q3) edge[loop above] node{0,1} (q2);

    \end{tikzpicture}
    \caption{DFA inverso per lingugaggio di partenza}
    \label{fig:Ex5.2}
\end{figure}

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state, accepting] at (1,2) (q4) {$q_4$};
        \node[state, initial] (q0) {$q_0$};
        \node[state, right of =q0] (q1) {$q_1$};
        \node[state, right of =q1] (q2) {$q_2$};
        \node[state, right of =q2] (q3) {$q_3$};
       
        \draw (q0) edge[loop above] node{0} (q0)
              (q0) edge[above] node{1} (q1)
              (q1) edge[loop above] node{1} (q1)
              (q1) edge[above] node{0} (q2)
              (q2) edge[bend left, below] node{0} (q0)
              (q2) edge[above] node{1} (q3)
              (q3) edge[loop above] node{0+1} (q2)
              (q0) edge[above] node{$\epsilon$} (q4)
              (q1) edge[above] node{$\epsilon$} (q4)
              (q2) edge[above] node{$\epsilon$} (q4);

    \end{tikzpicture}
    \caption{NFA}
    \label{fig:Ex5.3}
\end{figure}


\subsection{Ex2}

Convertire in RE il seguente automa (Figura) \ref{fig:Ex2.1}). \\

Per procedere rimuoviamo lo stato $q_1$ (Figura \ref{fig:Ex2.2} e ricaviamo l'espressione regolare $1+01^{\star}0(0+1)^{\star}$

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial] (q0) {$q_0$};
        \node[state] at (3,0) (q1) {$q_1$};
        \node[state,accepting] at (2,-2) (q2) {$q_2$};          
        
        
        \draw (q0) edge[above] node{0} (q1)
              (q0) edge[above] node{1} (q2)
              (q1) edge[above] node{0} (q2)
              (q1) edge[loop above] node{1} (q1)
              (q2) edge[loop below] node{0,1} (q2);

    \end{tikzpicture}
    \caption{Automa di partenza}
    \label{fig:Ex2.1}
\end{figure}



\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial] (q0) {$q_0$};
        \node[state,accepting] at (3,0) (q2) {$q_2$};          
        
        \draw 
              (q0) edge[above] node{$1+01^{\star}0$} (q2)
              (q2) edge[loop above] node{$0+1$} (q2);

    \end{tikzpicture}
    \caption{Rimozione stato $q_1$}
    \label{fig:Ex2.2}
\end{figure}
\end{document}

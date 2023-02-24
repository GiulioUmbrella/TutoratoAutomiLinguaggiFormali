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


\title{Tutorato 01}
\author{Giulio Umbrella }
\date{14 March 2022}


\begin{document}

\maketitle

\textbf{Nota} questa versione delle soluzioni e' una bozza e puo' essere soggetta a modifiche 


\section{DFA}
\subsection{Ex 1}
{$w \in \sum | |w| = 2$}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    % \centering % centers the figure
    \begin{tikzpicture}
        \node[state,initial] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state, accepting, right of=q1] (q2) {$q_2$};
        \node[state, right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[above] node{0,1} (q1)
              (q1) edge[above] node{0,1} (q2)
              (q2) edge[above] node{0,1} (q3)
              (q3) edge[loop above] node{0,1} (q3);

    \end{tikzpicture}
    \caption{Esercizio 01}
    \label{fig:Ex1}
\end{figure}

\subsection{Ex 2}
{$w \in \sum | |w| <= 2$}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    % \centering % centers the figure
    \begin{tikzpicture}
        \node[state, accepting,initial] (q0) {$q_0$};
        \node[state, accepting,right of=q0] (q1) {$q_1$};
        \node[state, accepting, right of=q1] (q2) {$q_2$};
        \node[state, right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[above] node{0,1} (q1)
              (q1) edge[above] node{0,1} (q2)
              (q2) edge[above] node{0,1} (q3)
              (q3) edge[loop above] node{0,1} (q3);

    \end{tikzpicture}
    \caption{Esercizio 02}
    \label{fig:Ex1}
\end{figure}

\subsection{Ex 3}
{$w \in \sum | |w| mod 2 = 0$}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state,right of=q0] (q1) {$q_1$};
      
        \draw (q0) edge[bend left, above] node{0,1} (q1)
              (q1) edge[bend left, below] node{0,1} (q0);

    \end{tikzpicture}
    \caption{Esercizio 03}
    \label{fig:Ex3}
\end{figure}



\subsection{Ex 4}
{$w \in \sum | ogni 0 e' seguito da 11 $}
\begin{figure}[h] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state] at (3,-2) (q4) {$q_4$};          
        \node[state, right of=q1] (q2) {$q_2$};
        \node[state, accepting,right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[loop above] node{1} (q0)
              (q0) edge[above] node{0} (q1)
              (q1) edge[above] node{1} (q2)
              (q2) edge[above] node{1} (q3)
              (q3) edge[loop above] node{1} (q3)
              (q3) edge[bend right, above] node{0} (q1)
              (q1) edge[below] node{0} (q4)
              (q2) edge[below] node{0} (q4)
              (q4) edge[loop below] node{0,1} (q4);

    \end{tikzpicture}
    \caption{Esercizio 04}
    \label{fig:Ex4}
\end{figure}

\subsection{Ex 5}
{$w \in \sum | contiene 000 come sottostringa $}
\begin{figure}[h] 
    % \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state, right of=q1] (q2) {$q_2$};
        \node[state, accepting,right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[loop above] node{1} (q0)
              (q0) edge[above] node{0} (q1)
              (q1) edge[above] node{0} (q2)
              (q2) edge[above] node{0} (q3)
              (q1) edge[bend left, below] node{1} (q0)
              (q2) edge[bend left, below] node{1} (q0)
              (q3) edge[loop above] node{0,1} (q3);
                  
    \end{tikzpicture}
    \caption{Esercizio 05}
    \label{fig:Ex5}
\end{figure}

\subsection{Ex 6}
{$w \in \sum | |w| mod 3 = 0$}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    % \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state, right of=q1] (q2) {$q_2$};
        
        \draw (q0) edge[above] node{0,1} (q1)
              (q1) edge[above] node{0,1} (q2)
              (q2) edge[bend left, below] node{0,1} (q0);
                  

    \end{tikzpicture}
    \caption{Esercizio 06}
    \label{fig:Ex6}
\end{figure}

\subsection{Ex 7}
{$w \in \sum | |w| mod 3 = 1$}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    % \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial ] (q0) {$q_0$};
        \node[state, accepting, right of=q0] (q1) {$q_1$};
        \node[state, right of=q1] (q2) {$q_2$};
        
        \draw (q0) edge[above] node{0,1} (q1)
              (q1) edge[above] node{0,1} (q2)
              (q2) edge[bend left, below] node{0,1} (q0);
                  

    \end{tikzpicture}
    \caption{Esercizio 07}
    \label{fig:Ex7}
\end{figure}

\section{NFA $\epsilon$ -NFA}

\subsection{Ex 1}
{$w \in {a,b,c}| \textrm{ non compaiono tutti i simboli} $}
\begin{figure}[h] 
    % \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state, accepting] at (2,2) (q1) {$q_1$};
        \node[state, accepting] at (2,0) (q2) {$q_2$};
        \node[state, accepting] at (2,-2)(q3) {$q_3$};
        
        \draw (q0) edge[above] node{b,c} (q1)
              (q1) edge[loop above] node{b,c} (q1)
              (q0) edge[above] node{a,c} (q2)
              (q2) edge[loop above] node{a,c} (q2)
              (q0) edge[above] node{a,b} (q3)
              (q3) edge[loop above] node{a,b} (q3);
                  
    \end{tikzpicture}
    \caption{Esercizio 02}
    \label{fig:Ex2.2}
\end{figure}


\subsection{Ex 2}
{$w \in {0,1}_*| \textrm{ contiene tre zero consecutivi}$}
\begin{figure}[h] 
    % \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state, right of=q1] (q2) {$q_2$};
        \node[state, accepting, right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[loop above] node{0,1} (q0)
              (q0) edge[above] node{0} (q1)
              (q1) edge[above] node{0} (q2)
              (q2) edge[above] node{0} (q3)
              (q3) edge[loop above] node{0,1} (q0);
                  
    \end{tikzpicture}
    \caption{Esercizio 02}
    \label{fig:Ex2.2}
\end{figure}


\subsection{Ex 3}
{$w \in {0,1}_*| \textrm{ contiene al suo interno la stringa 11 oppure 101}  $}
\begin{figure}[h] % ’ht’ tells LaTeX to place the figure ’here’ or at the top of the page
    \centering % centers the figure
    \begin{tikzpicture}

        \node[state,initial] (q0) {$q_0$};
        \node[state, right of=q0] (q1) {$q_1$};
        \node[state, right of=q1] (q2) {$q_2$};
        \node[state, accepting, right of=q2] (q3) {$q_3$};
        
        \draw (q0) edge[loop above] node{0,1} (q0)
              (q0) edge[above] node{1} (q1)
              (q1) edge[above] node{0,$\epsilon$} (q2)
              (q2) edge[above] node{1} (q3)
              (q3) edge[loop above] node{0,1} (q0);
                  

    \end{tikzpicture}
    \caption{Esercizio 03}
    \label{fig:Ex2.3}
\end{figure}


\section{Conversione NFA $\rightarrow$ DFA}
\subsection{Ex 1}

\begin{center}
\begin{tabular}{ c| c | c }
\hline
& 0 & 1 \\
\hline
$\emptyset$ & $\emptyset$ & $\emptyset$ \\ 
 \rightarrow \ast \{q0,q1,q3\} & \{q1,q3\} &\{q2,q4\} \\  
 \{q1,q3\} & \{q1,q3\} & \{q2,q4\} \\ 
 \ast \{q2,q4\} & \{q2,q5\} & $\emptyset$ \\  
 \ast \{q2,q5\} & \{q2\} & \{q4\} \\ 
 \ast \{q2\} & \{q2\} & $\emptyset$ \\ 
 \ast \{q4\} & \{q5\} & $\emptyset$ \\  
 \{q5\} & $\emptyset$ & \{q4\} \\ 
\end{tabular}
\end{center}

\end{document}

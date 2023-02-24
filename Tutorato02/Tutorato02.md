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


\title{Tutorato 02}
\author{Giulio Umbrella }
\date{21 March 2022}


\begin{document}

\maketitle
\section{Espressioni regolari}

\subsection{Ex1}
Scrivere l'espressione regolare per i seguenti linguaggi.\par
\begin{enumerate}
  \item Stringhe binarie che iniziano e finiscono con 1
  \item Stringhe binarie di lunghezza pari
  \item Stringhe binarie di lunghezza dispari
  \item Stringhe binarie che terminano con 00
  \item Stringhe binarie in cui il quarto simbolo e' uno zero
  \item Stringhe binarie in cui ciascuna coppia di zeri e' seguita da una coppia di uno
  \item Stringhe binarie divisibili per quattro
  \item tutte le rappresentazione di interni binari compresi fra zero e due
   \item le rappresentazione di interni binari compresi fra uno e due
\end{enumerate}

\subsection{Ex2}
Dire se le seguenti affermazioni sono vere o false.\par
\begin{enumerate}
    \item L({$\emptyset$*}) = $\emptyset$ 
    \item La stringa 'baa' appartiene al linguaggio L(a*b*a*b*) 
    \item L((a+b)*) = L((a*b*)*)
\end{enumerate}

\section{Conversione da RE a FA}
Convertire le seguenti espressioni regolari in FA 
\begin{enumerate}
    \item a(a* + b*) + c
    \item (ab + a)*
\end{enumerate}

\section{Conversione da FA a RE}
\subsection{Ex1}

Fornire un FA per i seguenti linguaggi e convertire l'automa in una espressione regolare.

\begin{enumerate}
    \item Stringhe binarie di lunghezza pari
    \item Strighe binarie in cui il simbolo 1 e' ripetuto al piu' una volta sola
    \item Stringhe binarie che non comprendono la stringa 101

\end{enumerate}

\subsection{Ex2}
Convertire in RE il seguente automa

\begin{figure}[h!] 
    % \centering % centers the figure
    \begin{tikzpicture}
        
        \node[state,initial, accepting] (q0) {$q_0$};
        \node[state] at (3,0) (q1) {$q_1$};
        \node[state,accepting] at (2,-2) (q2) {$q_2$};          
        
        
        \draw (q0) edge[above] node{0} (q1)
              (q0) edge[above] node{1} (q2)
              (q1) edge[above] node{0} (q2)
              (q1) edge[loop above] node{1} (q1)
              (q2) edge[loop below] node{0,1} (q2);


    \end{tikzpicture}
    % \label{fig:Ex4}
\end{figure}


\subsection{Esercizi aggiuntivi}

% \subsubsection{Ex1}
% Convertire in RE il seguente automa

% \begin{figure}[t] 
%     % \centering % centers the figure
%     \begin{tikzpicture}
        
%         % \node[state,initial, accepting] (q0) {$q_0$};
%         % \node[state] at (3,0) (q1) {$q_1$};
%         % \node[state,accepting] at (2,-2) (q2) {$q_2$};          
        
        
%         % \draw (q0) edge[above] node{0} (q1)
%         %       (q0) edge[above] node{1} (q2)
%         %       (q1) edge[above] node{0} (q2)
%         %       (q1) edge[loop above] node{1} (q1)
%         %       (q2) edge[loop below] node{0,1} (q2);


%     \end{tikzpicture}
%     % \label{fig:Ex4}
% \end{figure}




\subsubsection{Ex1}
Scrivere l'espressione regolare per i seguenti linguaggi.
\begin{enumerate}
    \item tutte le rappresentazione di interni binari compresi fra zero e otto
    \item tutte le rappresentazione di interni binari compresi fra uno e otto
\end{enumerate}

\end{document}

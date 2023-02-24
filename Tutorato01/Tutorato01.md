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



    \section{DFA}
    \begin{enumerate}
        \item {$w \in \sum | \mid w \mid  = 2$}
        \item {$w \in \sum | |w| <= 2$}
        \item {$w \in \sum  \mid w\mid| mod 2 = 0$}
        \item {$w \in \sum | \textrm{ ogni 0 e' seguito da 11} $}
        \item {$w \in \sum | \textrm{ contiene 000 come sottostringa} $}
        \item {$w \in \sum | \mid w\mid| mod 3 = 0$}
        \item {$w \in \sum | \mid w\mid| mod 3 = 1$}
    \end{enumerate}


\section{NFA $\epsilon$ -NFA}

\begin{enumerate}
    \item {$w \in {a,b,c}| \textrm{ non compaiono tutti i simboli} $}
    \item {$w \in {0,1}^*| \textrm{ contiene tre zero consecutivi}$}
    \item {$w \in {0,1}^*| \textrm{ contiene al suo interno la stringa 11 oppure 101}  $}
\end{enumerate}






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

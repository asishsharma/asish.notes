
snippet found on the internet
```tikz
\documentclass{article}
\usepackage{tikz}
\usetikzlibrary{shapes.geometric, arrows}

\tikzstyle{startstop} = [rectangle, rounded corners, 
minimum width=3cm, 
minimum height=1cm,
text centered, 
draw=black, 
fill=red!30]

\tikzstyle{io} = [trapezium, 
trapezium stretches=true, % A later addition
trapezium left angle=70, 
trapezium right angle=110, 
minimum width=3cm, 
minimum height=1cm, text centered, 
draw=black, fill=blue!30]

\tikzstyle{process} = [rectangle, 
minimum width=3cm, 
minimum height=1cm, 
text centered, 
text width=3cm, 
draw=black, 
fill=orange!30]

\tikzstyle{decision} = [diamond, 
minimum width=3cm, 
minimum height=1cm, 
text centered, 
draw=black, 
fill=green!30]
\tikzstyle{arrow} = [thick,->,>=stealth]
\begin{document}

\begin{tikzpicture}[node distance=2cm]

\node (start) [startstop] {Start};
\node (in1) [io, below of=start] {Input};
\node (pro1) [process, below of=in1] {Process 1};
\node (dec1) [decision, below of=pro1, yshift=-0.5cm] {Decision 1};

\node (pro2a) [process, below of=dec1, yshift=-0.5cm] {Process 2a
text text text text
text text text 
text text text};

\node (pro2b) [process, right of=dec1, xshift=2cm] {Process 2b};
\node (out1) [io, below of=pro2a] {Output};
\node (stop) [startstop, below of=out1] {Stop};

\draw [arrow] (start) -- (in1);
\draw [arrow] (in1) -- (pro1);
\draw [arrow] (pro1) -- (dec1);
\draw [arrow] (dec1) -- node[anchor=east] {yes} (pro2a);
\draw [arrow] (dec1) -- node[anchor=south] {no} (pro2b);
\draw [arrow] (pro2b) |- (pro1);
\draw [arrow] (pro2a) -- (out1);
\draw [arrow] (out1) -- (stop);

\end{tikzpicture}
\end{document}
```


```tikz
\usepackage{tikz-cd} 
\begin{document} 
\begin{tikzcd}     
T     
\arrow[drr, bend left, "x"]     
\arrow[ddr, bend right, "y"]     
\arrow[dr, dotted, "{(x,y)}" description] & & \\     K & X \times_Z Y \arrow[r, "p"] \arrow[d, "q"]     & X \arrow[d, "f"] \\     & Y \arrow[r, "g"]     & Z \end{tikzcd} \quad \quad \begin{tikzcd}[row sep=2.5em] A' \arrow[rr,"f'"] \arrow[dr,swap,"a"] \arrow[dd,swap,"g'"] &&   B' \arrow[dd,swap,"h'" near start] \arrow[dr,"b"] \\ & A \arrow[rr,crossing over,"f" near start] &&   B \arrow[dd,"h"] \\ C' \arrow[rr,"k'" near end] \arrow[dr,swap,"c"] && D' \arrow[dr,swap,"d"] \\ & C \arrow[rr,"k"] \arrow[uu,<-,crossing over,"g" near end]&& D \end{tikzcd} \end{document}
```


```tikz
\begin{document} \begin{tikzpicture}[domain=0:4] \draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9); \draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$}; \draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$}; \draw[color=red] plot (\x,\x) node[right] {$f(x) =x$}; \draw[color=blue] plot (\x,{sin(\x r)}) node[right] {$f(x) = \sin x$}; \draw[color=orange] plot (\x,{0.05*exp(\x)}) node[right] {$f(x) = \frac{1}{20} \mathrm e^x$}; \end{tikzpicture} \end{document}
```

```tikz
\usepackage{circuitikz} \begin{document} \begin{circuitikz}[american, voltage shift=0.5] \draw (0,0) to[isource, l=$I_0$, v=$V_0$] (0,3) to[short, -*, i=$I_0$] (2,3) to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0); \draw (2,3) -- (4,3) to[R=$R_2$, i>_=$i_2$] (4,0) to[short, -*] (2,0); \end{circuitikz} \end{document}
```

```tikz
\usepackage{pgfplots} \pgfplotsset{compat=1.16} \begin{document} \begin{tikzpicture} \begin{axis}[colormap/viridis] \addplot3[ surf, samples=18, domain=-3:3 ] {exp(-x^2-y^2)*x}; \end{axis} \end{tikzpicture} \end{document}
```

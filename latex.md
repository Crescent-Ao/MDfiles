下式\ref{sampeltable}和注释为上面程序的效果，数学符号可以自行百度，或者在这\url{http://www.mohu.org/info/symbols/symbols.htm}上面寻找，几乎包含了基本上要用的数学符号。
\begin{equation}\label{SampleEquation}
  \equationskipfrac
  \begin{split}
  \bm{x_}k&=\bm{\Phi}_{k,k-1}\bm{x}_{k-1}+\bm{\Gamma}_{k-1}\bm{w}_{k-1}\\
  \bm{z}_k&=\bm{H}_k\bm{x}_k+\bm{v}_k
  \end{split}
\end{equation}
式中：

\begin{tabular}{r@{---}l}
  $\bm{x}_k$  & The state variable of the $k^{th}$ step;\\
  $\bm{z}_k$  & The observation of the $k^{th}$ step; \\
  $\bm{\Phi}_{k,k-1}$ & The transition matrix of the $(k-1)^{th}$ to $k^{th}$ step; \\
  $\bm{\Gamma}_{k-1}$  & The measurement noise driving matrix of the $k^{th}$ step; \\
  %$\bm{H}_k$  & The measurement matrix of the $k^{th}$ step;\\
  %$\bm{w}_{k-1}$ & The systematic noise of the $(k-1)^{th}$ step ,$\bm{w}_{k-1}\sim N(0,\bm{Q}_{k-1})$;\\
  $\bm{v}_k$ & The measurement noise of the $k^{th}$ step,$\bm{v_k}\sim N(0,\bm{R}_k)$.
\end{tabular}

\newpage
\section{枚举格式}
官方模板未对枚举格式做出规定。但为了方便使用，本模板参考了大部分中文期刊的排版，对枚举格式做出了设置。枚举使用\fbox{$\setminus$begin\{enumerate\}}环境，编号为带有括号的数字，每个item的首行开头缩进两个字符，其余行不缩进。考虑到美观，不建议在item内部进行分段。示例如下：

\vspace{-4ex}
\begin{lstlisting}
\begin{enumerate}
	\item 内容一，内容一，内容一，内容一……
	\item 内容二，内容二，内容二，内容二……
	\item 内容三，内容三，内容三，内容三……
\end{enumerate}
\end{lstlisting}
\vspace{-1ex}

\begin{enumerate}
	\item 内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一，内容一。
	\item 内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二，内容二。
	\item 内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三，内容三。
\end{enumerate}

\section{参考文献}
参考文献在ThesisReference中\fbox{$\setminus$begin\{thebibliography\}}环境中进行填写，具体格式规范查阅参考文献标注国家标准GB/T~7714——2015。按照官方模板的要求，编号和参考文献内容分别左对齐。本模板使用box对编号的位置进行约束\fbox{$\setminus$makebox[1.5em][l]\{[\#1]\}}，设定宽度为1.5em，该值适用于一位和两位的编号，若编号达到三位数，则需要自行调整宽度。

模板参考文献使用下面文本框中方法，该方法比较业余，不便于大量参考文献的管理，并且需要手动输入书目信息。专业的方法是使用BibTeX，使用方法自行百度，BibTeX可以在Google scholar、百度学术上直接导入。

\vspace{-4ex}
\begin{lstlisting}
\begin{thebibliography}
\bibitem author,article, year, vol,
\end{thebibliography}
\end{lstlisting}

正文需要引用文献，使用\fbox{$\setminus$cite\{\}}即可。

\section{代码插入}
考虑到大多数同学的代码应该是MATLAB，在ThesisAppendix文件中将语言设置m语言，可以根据自身需要进行改变。网上的Mcode包编译效果非常不错，这里就直接拿来，做一回拿来主义。

Mcode包效果在附录B MATLAB Code中看到，其能较好地还原MATLAB本身的编程风格。程序代码需放到\fbox{$\setminus$begin\{lstlisting\}}环境中。

由于某些未知的原因，如果\fbox{$\setminus$begin\{lstlisting\}}环境跨页，可能会导致页眉出现乱码，所以使用时请注意代码的长度和放置的位置。

建议在\fbox{$\setminus$begin\{lstlisting\}}环境开始前用\fbox{$\setminus$vspace\{-4ex\}}，结束后用\fbox{$\setminus$vspace\{-1.5ex\}}来减少代码和上下文之间的距离，具体数值需要按照实际情况调整。

\end{spacing}
}
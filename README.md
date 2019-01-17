# This notebook defines <em>M&m</em> Sequences, and creates a function that can be used to apply the <em>M&m</em> Sequence Algorithm to any starting sequence.

# Unless otherwise noted- Source: Schultz, Harris, and Shiﬂett, Ray M&m Sequences. The College Mathematics Journal 36.3 (2005): 191-98. Web.

# 1. Billstein, Rick, Johnny W. Lott, and Libeskind Shlomo. A ProblemSolvingApproach to Mathematics for Elementary School Teachers. N.p.: GregTobin,2007. Print.

<hr style="height:3px">

### A sequence is an ordered arrangement of numbers, figures, or objects.$^1$
### Define $S_n$ as a sequence with $n$ terms. 
### Define $x_n$ as the $n^{th}$ term of the sequence $S_n$.
<hr>

For an example, let $S_3$ = 6, 78, 46.

We want to progress to the next sequence $S_4$; that is, we want to add another term to this sequence.  We must follow a specific algorithm though; we want the that the median of $S_3$ is equal to the mean of $S_4$.

Let then mean($S_n$) be the mean of $S_n$, and let median($S_n$) be the median of $S_n$.

In this case, we want that median($S_3$) = mean($S_4$).

We will recall that $S_3$ = 6, 78, 46.  To find the median of this sequence, we will first list each term in increasing order, and get 6, 46, 78.  From here we can see that median($S_3$) = 46.  Therefore we want that mean($S_4$) = 46.

We know that the mean of a sequence of numbers is the sum of each number in the sequence, divided by the amount of numbers in said sequence.  Recall that $x_n$ is the $n^{th}$ term of the sequence.

Hence we have that mean($S_4$) =  $ \frac{6+78+46+x_4}{4}$ =  46.

From here we can proceed to solve for the next term $x_4$:

$\frac{6+78+46+s_4}{4}$ =  46.

$\rightarrow \frac{6+78+46+s_4}{4} \times$ 4 =  46 $\times$ 4<br>
$\rightarrow$ 6 + 78 + 46 + $s_4$ = 184<br>
$\rightarrow$ 6 + 78 + 46 + $s_4$ - (6 + 78 + 46) = 184 -(6 + 78 +46)<br>
$\rightarrow s_4$ = 54

Therefore, $S_4$ = 6, 78, 46, 54.

Recall that a sequence is an ordered arrangement; The sequence 6, 78, 46, 54 is not the same as the sequence 6, 46, 54, 78.  If we apply this same algorithm again, we will get that $S_5$ = 6, 78, 46, 54, 66.  If we continue to apply this algorithm we will see that:


$S_{15}$ = 6, 78, 46, 54, 66, 74, 96, 108, 102, 110, 96, 100, 195, 213, 96<br>
$S_{16}$ = 6, 78, 46, 54, 66, 74, 96, 108, 102, 110, 96, 100, 195, 213, 96, 96<br>
$S_{17}$ = 6, 78, 46, 54, 66, 74, 96, 108, 102, 110, 96, 100, 195, 213, 96, 96, 96

We have reached a point where continue to append the same number to our sequence.  We wonder if this is just a coincidence, and try the algorithm with a new sequence.

$S_3$ = 13, 41, 53<br>
$S_{13}$  = 13, 41, 53, 57, 71, 83, 67, 71, 102, 112, 89, 93, 71<br>
$S_{14}$  = 13, 41, 53, 57, 71, 83, 67, 71, 102, 112, 89, 93, 71, 71<br>
$S_{15}$  = 13, 41, 53, 57, 71, 83, 67, 71, 102, 112, 89, 93, 71, 71, 71

Again, we continue to append the same number to our sequence.

Given three real numbers then, $x_1$, $x_2$, $x_3$, define the recursive sequence $\langle x_n \rangle$ by the algorithm: $x_{n+1}$ is the number such that mean($S_{n+1}$) = median($S_n$).  We will call such a sequence an $M\&m$ Sequence- or <em>Mean and Median</em> Sequence.

A $M\&m$ Sequence is <strong>stable</strong> if it eventually becomes constant, or if we can find a $k$ for which $x_n$ = $x_k$ for all $n \geq k$.

We will define $k$ as the <strong>length</strong> of the sequence, and $x_k$ as the <strong>stable value</strong>.

If we return to our original sequence:

$S_3$ =6, 78, 46<br>
$S_{17}$ = $\underbrace{6, 78, 46, 54, 66, 74, 96, 108, 102, 110, 96, 100, 195, 213, 96}_\text{15 terms}$, 96, 96

The <strong>stable value</strong> of this sequence is 96, and the first repeating 96 is the 15$^{th}$ term of the sequence; hence this sequence has a <strong>length</strong> of 15.  We should point out that $x_7$ = 96; however, $x_8$ =  108; hence the 96 at $x_7$ is irrelevant.  We are only concerned with repeating values once they become consecutive.

If we look at our second sequence:

$S_3$ = 13, 41, 53<br>
$S_{15}$ = $\underbrace{13, 41, 53, 57, 71, 83, 67, 71, 102, 112, 89, 93, 71}_\text{13 terms}$, 71, 71

$k$ = 13<br>
$x_k$=71

This brings us to the $M\&m$ Conjecture: Every $M\&m$ Sequence is stable.

As of the time this notebook was written, this conjecture is yet to be proven.  No matter what sequence you begin with, it seems to always stabilize.  This is an ongoing problem in Mathematics, and in this notebook we create a function which will take a list of numbers, and apply the aforementioned algorithm until 3 consecutive values are appeneded to our list; we assume that the sequence has stabilized at this point.
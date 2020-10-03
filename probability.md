# Probability


## What is probability theory
* In most narraw view, probability theory is just a branch of mathematics. We start with some axioms, we consider models that satisfy these axioms and we establish some consequences, which are the theorems of this theory.
* Probability can be interpreted as:
    * Frequencies: fraction of heads when coin tossed infinite number times
    * Describing belief: President can be reelected with probability 0.7; numeric guidance of how should I place my bets.
* Gives us some rules for thinking systematically about uncertain situation.
* If our probability model has some relationship with real world, then probability theory can be a very useful tool for making predictions and decisions that apply to the real world. Whether your prediction is good depends on the quality of the model. Field of statistics complements probability theory by using data to come up with good models.
* Relationship between real world, statistics and probability:
<img src="https://i.imgur.com/eZyQME1.png" alt="drawing" width="400" style="display: block;margin-left: auto; margin-right: auto;"/>

# Sample space
* Set of possible outcomes
    * Collective exhaustive
    * Mutually exclusive

# Probability Axioms
* Probability is assigned to events, which are subsets of a sample space($\Omega$)
    * Event can occur or did not occur; we either observe it or did not observe it

## Axioms
* Non-negativity: probability will always be non-negative number $$P(A)\geq0$$
* Normaliztion: probability of entire sample space should be 1 $$P(\Omega)=1$$
* Finite additivity: If $A\cap B=\emptyset$, then $P(A\cup B)=P(A)+P(B)$
* Countable additivity: If $A_1,A_2,...$ is an infinite **sequence** of disjoint events, then $P(A_1\cup A_2\cup...)=P(A_1)+P(A_2)+...$


### Consequences
$P(A)\leq 1$
> $1=P(\Omega)=P(A\cup A^c)=P(A)+P(A^c)$
> $P(A)=1-P(A^c)$

$P(\emptyset)=0$
> $1=P(\Omega)+P(\Omega^c)$
> $1=1+P(\emptyset)$
> $P(\emptyset)=0$

$P(A\cup B\cup C)$
> $P(A\cup B\cup C)=P((A\cup B)\cup C)=P(A\cup B)+P(C)=P(A)+P(B)+P(C)$

$P(\{s_1,s_2,...,s_k\})$
> $P(\{s_1,s_2,...,s_k\})=P(\{s_1\}\cup\{s_2\}\cup...\cup\{s_k\})=P(s_1)+P(s_2)+...+P(s_k)$

If $A\subset B$, then $P(A)\leq P(B)$
> $B=A\cup(B\cap A^c)$
> $P(B)=P(A)+P(B\cap A^c)\geq P(A)$

$P(A\cup B)=P(A)+P(B)-P(A\cap B)$
> $P(A\cup B)=P(A\cap B^c)+P(A\cap B)+P(B\cap A^c)$
> $P(A)=P(A\cap B^c)+P(A\cap B)$
> $P(B)=P(A\cap B)+P(B\cap A^c)$
We also derived **UNION BOUND**: $P(A)+P(B)\geq P(A\cup B)$

$P(A\cup B\cup C)=P(A)+P(A^c\cap B)+P(A^c\cap B^c \cap C)$
> Obvious from venn diagram; three sets are disjoint

Benferroni inequality
$P(A_1\cap A_2)\geq P(A_1)+P(A_2)-1$
> Using De Morgan's Law, $(A_1\cap A_2)^c=A_1^c\cup A_2^c$
> $P((A_1\cap A_2)^c)=P(A_1^c\cup A_2^c)\leq P(A_1^c)+P(A_2^c)$
> $1-P(A_1\cap A_2)\leq 1-P(A_1)+1-P(A_2)$

# Conditioning and independence
Probability is introduced as the way of describing our beliefs about the likelihood that a given event will occur. Our belief in general depends on the **given information** that we have.

Conditioning leads to revised probabilities that take into account **partial information** on the outcome of a probablistic experiment. Conditioning is a very useful tool that allow us to "divide and conquer" complex problems. They are also the foundation of inference.

Independence is used to model situations involving non-interacting probablistic phenomena and also plays an important role in building complex model from more elementary ones. Complex system is ususally made up by several components that are affected by unrelated, that is, **independent sources of randomness**.

## Conditional probability
$P(A|B)=\frac{P(A\cap B)}{P(B)}$
defined if only $P(B)>0$
This is just a definition, **motivated by the need to update belief based on partial given information**, it is not a theorem. It is very helpful to visualize as a venn diagram.

Conditional probability satifies all the axioms for ordinary probabilities. All theorems that we derive for ordinary probabilities will remain true for conditional probability as well.

$P(A|B)\geq0$ assuming $P(B)>0$

$P(\Omega|B)=\frac{P(\Omega\cap B)}{P(B)}=1$

$P(B|B)=\frac{P(B\cap B)}{P(B)}=1$

If $A\cap C=\emptyset$, then $P(A\cup C|B)=P(A|B)+P(C|B)$
> $P(A\cup C|B)=\frac{P((A\cup C)\cap B)}{P(B)}=\frac{P((A\cap B)\cup (C\cap B))}{P(B)}=\frac{P(A\cap B)}{P(B)}+\frac{P(C\cap B)}{P(B)}=P(A|B)+P(C|B)$

### Multiplication Rule
Follows from the definition of conditional probability
$P(A\cap B)=P(A)\times P(B|A)=P(B)\times P(A|B)$

$P(A\cap B \cap C)=P((A\cap B) \cap C) = P(A\cap B)*P(C|A\cap B)=P(A)*P(B|A)*P(C|A\cap B)$

## Total probability
$P(B)=\sum_{i}P(A_i)P(B|A_i)$
> $P(B)=P(A_1\cap B)+P(A_2\cap B)+...=P(A_1)\times P(B|A_1)+P(A_2)\times P(B|A_2)$

## Bayes rule
Partition sample space into $A_1, A_2, A_3$
We think of $P(A_1), P(A_2), P(A_3)$ as some sort of initial belief. They believe how likely we believe each scenairo to be.

Under each scenario, we also have the probability that an event of interest, B, occurs. 

Perhaps we observe that event B did indeed occur. Once that happens, maybe this should cause us to revise our beliefs about the likelihood of the different scenarios.

$P(A_i|B)=\frac{P(A_i\cap B)}{P(B)}$ by definition of conditional probability
$=\frac{P(A_i)*P(B|A_i)}{\sum_jP(A_j)*{P(B|A_j)}}$ by definition of multiplication rule and total probability

Can also be viewed as updating branches in the garden of folking data and then perform normalization to bring new sample space sum to 1.

## Independence
Intuitive definition: $P(A|B)=P(A)$
Knowing occurrence of B provides no information on A.

Formal definition:
$P(A\cap B)=P(A)*P(B)$
Symmetric with respect to A and B
applies even if P(B)=0

### Independence of event complements
If $A$ and $B$ are independent, then $A$ and $B^c$ are independent.

Proof:
$P(A)=P(A\cap B)+P(A\cap B^c)=P(A)*P(B)+P(A\cap B^c)$
$P(A\cap B^c)=P(A)-P(A)*P(B)=P(A)*(1-P(B))=P(A)*P(B^c)$

### Conditional independence
$P(A\cap B|C)=P(A|C)*P(B|C)$
Independence does **not** imply conditional independence

### Independence over collection of events
=pairwise independece+triplet independence+four-tuple independence+....

Three events can be pairwise independent but not independent when we consider the triplet

# Counting
In many problems, the calculation of probabilities reduce to counting. Counting the number of elements of various sets.

### The counting principle: a multistage process
If each stage is indepedent, we can select one stage and then select another stage. We can use product of the number of options in the two stages to note all possibilities.

In general, if there are $r$ stages and $n_i$ options at stage $i$, then we have a total of $n_1*n_2*n_3*...*n_r$ possibilities.

Permutation can be thought of a multistage process.
Number of ways to order N elements: $n!$
Number of subsets of {1..n} is $2^n$

## Combination
Can be derived with permutation and then undo ordering for the selected k elements.
${n \choose{k}}=\frac{n!}{(n-k)!k!}$

$\sum_{k=0}^{n}{n \choose k}=2^n$ = #Number of all subsets

## Binominal distribution
**Indepedence** between events is assumed
P(particular sequence)=$p^{head}(1-p)^{tails}$

**Any particular k head sequence has equal probabilities**

P(k heads)=$p^{head}(1-p)^{tails}$*# k-head sequences

Binomial coefficient: $\frac{n!}{k!(n-k)!}$

## Partitioning
The number of ways that we can partition a given set into subsets of prescribed sizes.
number of partitions = $\frac{n!}{n_1!n_2!...n_r!}$
This is called multinomial coefficient
It is a generalization of binomial coefficient

# Discrete Random Variable
A random variable is numeric quantity whose value is determined by the outcome of a probablistic experiment. The weight of randomly selected student is one example. 

Can be thought of as a function $X$. Input: outcome of an experiment,
Output: numeric value $x$

A random variable associates a number to every possible outcome

### Probability mass function
It is the "probability law" or "probability distribution" of discrete random variable.
<img src="https://i.imgur.com/ZCKtjJz.png" alt="drawing" width="200" style="display: block;margin-left: auto; margin-right: auto;"/>

$X=5$ means {$w:X(w)=5$} = {$a, b$}

$p_X(x)=P(X=x)=P(\{w\in\Omega \;s.t.\; X(w)=x \})$
$p_X(5)=1/2$

Properties: 
$p_X(x)>0$
$\sum_xp_X(x)=1$

### Bernoulli and indicator random variable
Models a trial that results in success/failure, head/tails, etc
Can also be indicator of r.v. if event A occurs

### Discrete uniform random variable
Models complete ignorance of some variable over a range of values

### Binomial random variable
Can be represented as a binary tree of possiblities
Define random variable which is number of heads observed

Can be used to model: number of successes in a given number of independent trials
<img src="https://i.imgur.com/CRa91j8.png" alt="drawing" width="300" style="display: block;margin-left: auto; margin-right: auto;"/>

### Geometric random variable
Models the situation where we are waiting for something to happen. Keep doing trails under success and counting number of trails before success.

$p_X(k)=p(X=k)=P(T^{k-1}H)=(1-p)^kp \;\; for \; k=1,2,3,4,5$

### Expectation/Mean of random variable
$E[X]=\sum_{x}xp_X(x)$

$E[I_A]=P(A)$

#### Elementary properties
If $a\leq X\leq b$, then $a\leq E[X] \leq b$
Proof:
$E[x]=\sum_{x}xp_X(x)\geq \sum_{x}ap_X(x)=a\sum_xp_X(x)=a$
Use symmetric argument to proof b as well.

If c is a constant, $E[c]=c$

#### The expected value rule
Let $X$ be a r.v. and let $Y = g(X)$

$E[Y]=\sum_yyp_Y(y)$

Expected value rule only involves PMF of the original random varialbe
$E[Y]=E[g(x)]=\sum_xg(x)p_X(x)$ 
<img src="https://i.imgur.com/O5HrKHH.png" alt="drawing" width="300" style="display: block;margin-left: auto; margin-right: auto;"/>


$E[X^2]=\sum_xx^2p_X(x)$
In general, $E[x^2]\neq((E[x])^2)$

#### Linearity of expectation
$E[ax+b]=aE[x]+b$

$E[ax+b]=\sum_x(ax+b)p_X(x)=a\sum_x(x)p_X(x)+b=aE[x]+b$

$E(g(x))=g(E[x])$ for linear functions

### Variance
Variance is a quantity that measures the amount of spread, or the dispersion of a probability mass function. In some sense, it quantifies the randomness that is present.

Variance:
$var(X)=E[(X-u)^2]$
$var(X)=\sum_x(x-u)^2p_X(x)$

$\sigma_X=\sqrt{var(X)}$
Standard deviation has the same units as the random variable and captures the width of the distribution.

Properties of the variance
$var(aX+b)=a^2var(X)$
proof:
$var(aX+b)=E[(aX+b-(a\mu+b))^2]=E[(aX-a\mu)^2]=E[a^2(X-\mu)^2]$
$=a^2E[(X-\mu)^2]=a^2var(X)$


$var(X)=E[X^2]-(E[X])^2$
proof:
$var(X)=E[(X-\mu)^2]=E[X^2-2\mu X+\mu^2]=E[X^2]-2\mu E[X]+\mu^2$
$=E[X^2]-2E[X]E[X]+E[X]E[X]=E[X^2]-(E[X])^2$

#### Variance of the Bernoulli and the uniform
Bernoulli:
$var(X)=\sum_x(x-E[x])^2p_X(x)=(1-p)^2p+(0-p)^2(1-p)=p(1-p)$
$var(X)=E[X^2]-(E[X])^2=p-p^2=p(1-p)$

Uniform:
$var(x)=E[x^2]-(E[x])^2=\frac{1}{n+1}(0^2+1^2+...+n^2)-(\frac{n}{2})^2$
$=\frac{1}{12}n*(n+2)$

### Conditional PMF and expectation
There is nothing really different when we deal with conditional PMFs, expectations and variances, except that we have to use the conditional probabilities throughout instead of the original probabilities.
$p_{X|A}(x)=P(X=x|A)$
$\sum_xp_{X|A}(x)=1$
$E[X|A]=\sum_xxp_{X|A}(x)$
$E[g(X)|A]=\sum_xg(x)p_{X|A}(x)$

### Total expectation theorem
$p_X(x)=P(A_1)*p_{X|A_1}(x)+...+P(A_n)*p{X|A_n}(x)$
From total probabilities therem, which states that:
$P(B)=P(A_1)P(B|A_1)+...+P(A_n)*P(B|A_n)$
and event B is $B=\{X=x\}$

We can time x on both sides for all x and get:
$\sum_xxp_X(x)=P(A_1)\sum_xxp_{X|A_1}(x)+...$
$E(x)=P(A_1)E(X|A_1)+...+P(A_n)E(X|A_n)$

### Geometric Random variable
$P_{x-n|x>n}(k)=P_X(k)$
$E[x]=\frac{1}{p}$
proof:
$E[X]=1+E[X-1]=1+(1-p)E[X]$

### Joint PMFs and the expected value rule
P(X=Y) cannot be answered if only know individual PMFs. In order to answer a question of this type, we will need information that tells us what values of X tend to occur with what values of Y. And this information is captured in the so-called joint PMF.

$p_{X,Y}(x,y)=P(X=x\; and\; Y=y)$
$\sum_x\sum_yp_{X,Y}(x,y)=1$

$P_X(x)=\sum_yp_{X,Y}(x,y)$ sum over y

Expected value rule
$E[g(X,Y)]=\sum_x\sum_yg(x,y)p_{X,Y}(x,y)$

### Linearity of expectation
$E[X+Y]=E[X]+E[Y]$
proof:
$E[X+Y]=E[g(x,y)]=\sum_x\sum_y(x+y)p_{X,Y}(x,y)$
$=\sum_x\sum_yxp_{X,Y}(x,y)+\sum_x\sum_yyp_{X,Y}(x,y)$
$=\sum_xx\sum_yp_{X,Y}(x,y)+\sum_yy\sum_xp_{X,Y}(x,y)$
$=\sum_xxp(x)+\sum_yyp(y)$

For binomial variable
the expected value is formally:
$E[X]=\sum_{k=0}^nk{n \choose{k}}p^k(1-p)^{n-k}$
We can use linearity of expection and indicator variable where:
$X_i=1$ if $i$th trial is success
$X=X_1+X_2+...+X_n$
$E[X]=E[X_1]+...+E[X_n]=np$

### Conditioning on a random variable; Indepedence of r.v.'s
$P_{X|Y}(x|y)=P(X=x|Y=y)=\frac{P(X=x,Y=y)}{P(Y=y)}$
defined only for y such that $p_Y(y)>0$

Note that if we change the value of little y, we will, of course, get a different conditional PMF.

Pictorially, the conditional PMF has the same form as the
corresponding slice of the joint PMF, except, again, that
the entries of that slice are renormalized so that the
entries add to 1.

### Conditional expectations
$E[X|Y=Y]=\sum_xxp_{X|Y}(x|y)$

$E[g(X)|Y=y]=\sum_xg(x)p_{X|Y}(x|y)$

Total probability theorem:
$p_X(x)=\sum_yp_Y(y)p_{X|Y}(x|y)$

Total expectation theorem:
$E[X]=\sum_yp_Y(y)E[X|Y=y]$

### Independence of random variable for all x
For random variable and an event
Intuitively, if I tell you that A occurred, this is not
going to change the distribution of the random
variable x. And this has to be true for all values of little x.
$P(A|X=x)=P(A) for all x

For two random variables:
$P_{X|Y}(x|y)=P_X(x) for all y$
$P_{Y|X}(y|x)=P_Y(y) for all x$
or
$P_{X,Y}(x,y)=P_X(x)P_Y(y) for all x,y$

### Independence and expectations
If X,Y are indepedent:
$E[XY]=E[X]E[Y]$
proof:
$E[g(x,y)]=\sum_x\sum_yxyp_{X,Y}(x,y)$
$=\sum_x\sum_yxyp(x)p(y)$
$=\sum_xxp(x)\sum_yyp(y)$

More general fact:
$E[g(X)h(Y)]=E[g(X)]E[h(y)]$ if g(x) and h(y) are independent

### Indepedence, variance and binominal variance
When X,Y are independent,
$var(X+Y)=var(X)+var(Y)$
proof:
var(𝑋+𝑌)
=E[(𝑋+𝑌−E[𝑋+𝑌])2]
=E[(𝑋−E[𝑋]+𝑌−E[𝑌])2]
=E[(𝑋−E[𝑋])2+2(𝑋−E[𝑋])(𝑌−E[𝑌])+(𝑌−E[𝑌])2]
=E[(𝑋−E[𝑋])2]+2E[(𝑋−E[𝑋])(𝑌−E[𝑌])]+E[(𝑌−E[𝑌])2]
=var(𝑋)+2E[(𝑋−E[𝑋])]E[(𝑌−E[𝑌])]+var(𝑌)
=var(𝑋)+var(𝑌).

\begin{align*}
E[X-E[X]] &= \sum_x (x - E[X]) p_X(x) \\
&= \sum_x (x p_X(x) - p_X(x) E[X] ) \\
&= \sum_x x p_X(x) - \sum_x p_X(x) E[X] \\
&= E[X] - E[X] \sum_x p_X(x) \\
&= 0.
\end{align*}


variance of binomial:
$var(X)=var(X_1)+var(X_2)+...=np(1-p)$

### Variance of geometric PMF
$E[X|X>1]=1+E[X]$
$E[X^2|X>1]=E[(X+1)^2]$

$E[X^2]=P(X=1)E[X^2|X=1]+P(X>1)E[X^2|X>1]$
$=p*1+(1-p)(E[X^2]+2E[X]+1)$

With same albegra
$E[X^2]=\frac{2}{p^2}-\frac{1}{p}$

$Var[X]=E[X^2]-(E[X])^2=\frac{1-p}{p^2}$

### Independence of random variable vs independence of events
Events A and B
Let $X=I_A$, $Y=I_B$

X and Y are indepedent if and only if A and B are independent

$P_{X,Y}(1,1)=P_X(1)P_Y(1)\iff P(A\cap B)=P(A)P(B)$
$P_{X,Y}(1,0)=P_X(1)P_Y(0)\iff P(A\cap B^c)=P(A)P(B)^c$
$P_{X,Y}(0,1)=P_X(0)P_Y(1)$
$P_{X,Y}(0,0)=P_X(0)P_Y(0)$

If $A$ and $B$ are indepedent, $A$ and $B^c$ must also be independent.
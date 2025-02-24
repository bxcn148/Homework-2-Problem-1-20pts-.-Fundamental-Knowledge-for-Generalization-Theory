Download link :https://programming.engineering/product/homework-2-problem-1-20pts-fundamental-knowledge-for-generalization-theory/


# Homework-2-Problem-1-20pts-.-Fundamental-Knowledge-for-Generalization-Theory
Homework 2 Problem 1 (20pts). Fundamental Knowledge for Generalization Theory
When the random variables can have negative values, the Markov inequality may fail. Give an example.

How will sample size and variance in uence concentration? Explain it using Chebyshev’s inequality.

Suppose X1; X2; ; Xn are i.i.d sub-Gaussian random variables with bounded variance, then we can apply both Chebyshev’s inequality and Hoe ding’s inequality. Discuss which bound is tighter.

Explain why i.i.d. sampling assumption is important for generalization theory.

Suppose all training data points are from distribution D in an i.i.d. manner. If we increse the number of training data points, will the generalization error increase or decrease?

Given a hypothesis class H with f 1; +1g-valued hypotheses. Consider the empirical Rademacher

complexity de ned in page 47 of lecture slides 4. When = 1, what is ^S( )? When

jHj R H

n ^

jHj = 2 , what is RS(H)?

(7) By generalization theorey, explain how to make out-of-sample error small through .


Problem 2 (20pts).

Suppose f 2 H maps sample space X to f0; 1g. The Rademacher complexity bound derived in our lecture is by applying McDiarmid’s inequality to

h(S) = sup [Erout(f) Erin(f)]

2H

Try to obtain a generalization bound in terms of the empirical Rademacher complexity RbS(H) by applying McDiarmid’s inequality to

(S) = sup [Erout(f) Erin(f) RbS(H)]

2H

Hint: You can follow the analysis in slides4 page 56-57 and use directly the result in slides6 page 58-60 that E[h(S)] R(H).

Problem 3 (40pts). Over tting

Toy polynomial regression using ‘2-regularization and cross-validation. Suppose that we have the underlying model

y = x2 + “:

(1)

We collect n = 10 data points f(xi; yi)gni=1; see the visualization in Figure 1. You can download the data from blackboard.



Figure 1: visualization of data

Now, suppose we are going to t all the data using 8-th order polynomials:

y = 0 + 1x + 2x2 + 3x3 + : : : + 8x8:

(2)

(a1) [2 points] Denote the = ( 0; : : : ; 8) 2 R9 as the parameter. We have the following linear model

y = X :

Specify y and X using the training data f(xi; yi)gni=1.

(a2) [5 points] Furthermore, we can formulate the following least squares

b =

argmin

2

kX yk2

:

(3)

2R9

Calculate b de ned in (3) and plot the tted curve in Figure 1 (limit x-axis from -1.5 to 1.5 and limit y-axis from -0.5 to 2.5). You can download the code used to generate Figure 1 from blackboard.

(a3) [3 points] Using the test data set, calculate the test error

k

X

y

testk2

of de ned in

(3).

testb

b

(b1) [20 points] Since we know that the underlying model in (1) is quadratic, while the tting model in (2) is polynomial of order 8, we must have over tting, which you can see from question (a2) and (a3). One way to prevent over tting is regularization. Instead of using (3), we formulate the following ‘2-regularized least squares

b =

argmin

2

2

kX yk2

+ k k2

:

(4)

2R9

However, one di culty to implementing (4) is determining the regularization parameter . A too large leads to under tting, while a too small (e.g. = 0) results in over tting. Suppose we set the set of candidates of as

[10 510 410 310 210 10:30:50:812510152050100]

using 5-fold cross-validation to select the regularization parameter , and plot the valida-tion error versus the value of , where error is the y-axis and is the x-axis (set the x-axis to log-scale).

(b2) [5 points] Based on the result in (b1), set = 0:01, 0:1, 0:8, and 5 in (4) and solve for the corresponding b, respectively. Plot the tted curve using the former four choices of in Figure 1, you have to draw four gures separately (limit x-axis from -1.5 to 1.5 and limit y-axis from -0.5 to 2.5).

(b3) [5 points] Using the test data set, calculate the test error

k

X

y

testk2

of each of

obtained in (b2).

testb

b


Problem 4 (40pts). Multinomial and Ordinal Logistic Regression

In this problem we are going to use logistic regression to solve the Mobile Price Classi cation task. In particular, we are given a certain group of features for a phone, such as battery power, RAM, clock speed, etc. Our objective is to predict the price range of the phone, which can be viewed as a classi cation problem.

The data format is a csv le. The training data contains 1700 samples, and the test data contains 300 samples. The rst 20 columns are features and the last column is the label. You may check the le for more detail.

Note: You are not allowed to use any pre-built packages for auto-di erentiation.

[25 points] Multinomial Logistic Regression. Each class l = 1; ; K is assigned a weight vector l. The a-posterior of yi is modeled by

exp(h l; xii)

Pr[yi = lj ; xi] = PK exp(h j; xii):

j=1

The problem can be formulated as

1+e t

1

Algorithm 1 Accelerated Gradient Descent

Input: Observed data X; y and initialization parameter 0.

2: 1 = 0 rf(x0)

3:

for t = 1 to T

1 do

4:

yt = t +

t 1

( t t 1)

t+2

5:

t+1 = yt rf(yt)

end for

Return T

where we use h(t) := to represent the sigmoid function. Here, and zj are parameters

to be learned. Note we have only one for all class now. The probability of being class j can be calculated as

Pr[yi = jj ; xi] = Pr[yi jj ; xi] Pr[yi j 1j ; xi]

= h( T xi zj) h( T xi zj 1):

Therefore, the problem can be formulated as

1

n K

^ = argmin

XX

1yi=l log(h( T xi

zj) h( T xi zj 1)):

(6)

n

i=1 l=1

You are asked to solve (6) by following the same instruction as the multinomial logistic regres-sion. Compare the performance of two algorithms.

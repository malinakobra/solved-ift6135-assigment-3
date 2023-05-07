Download Link: https://assignmentchef.com/product/solved-ift6135-assigment-3
<br>
Question 1 (4-4-4-4). One way to enforce autoregressive conditioning is via masking the weight parameters.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> Consider a two-hidden-layer convolutional neural network without kernel flipping, with kernel size 3×3 and padding size 1 on each border (so that an input feature map of size 5×5 is convolved into a 5 × 5 output). Define mask of type A and mask of type B as

<table width="517">

 <tbody>

  <tr>

   <td width="116">1<em>A </em>(<em>M </em>)::<em>ij </em>:=            10</td>

   <td width="160">if <em>i </em>= 2 and <em>j &lt; </em>2 if <em>i </em>= 3elsewhere</td>

   <td width="121">1<em>B </em>(<em>M </em>)::<em>ij </em>:= 10</td>

   <td width="120">if <em>i </em>= 2 and <em>j </em>≤ 2 if <em>i </em>= 3elsewhere</td>

  </tr>

 </tbody>

</table>

where the index starts from 1. Masking is achieved by multiplying the kernel with the binary mask (elementwise). Specify the receptive field of the output pixel that corresponds to the third row and the fourth column (index 34 of Figure 1 (Left)) in each of the following 4 cases:

<table width="238">

 <tbody>

  <tr>

   <td width="19">11</td>

   <td width="19">12</td>

   <td width="19">13</td>

   <td width="19">14</td>

   <td width="19">15</td>

   <td rowspan="5" width="49"> </td>

   <td width="19">11</td>

   <td width="19">12</td>

   <td width="19">13</td>

   <td width="19">14</td>

   <td width="19">15</td>

  </tr>

  <tr>

   <td width="19">21</td>

   <td width="19">22</td>

   <td width="19">23</td>

   <td width="19">24</td>

   <td width="19">25</td>

   <td width="19">21</td>

   <td width="19">22</td>

   <td width="19">23</td>

   <td width="19">24</td>

   <td width="19">25</td>

  </tr>

  <tr>

   <td width="19">31</td>

   <td width="19">32</td>

   <td width="19">33</td>

   <td width="19">34</td>

   <td width="19">35</td>

   <td width="19">31</td>

   <td width="19">32</td>

   <td width="19">33</td>

   <td width="19">34</td>

   <td width="19">35</td>

  </tr>

  <tr>

   <td width="19">41</td>

   <td width="19">42</td>

   <td width="19">43</td>

   <td width="19">44</td>

   <td width="19">45</td>

   <td width="19">41</td>

   <td width="19">42</td>

   <td width="19">43</td>

   <td width="19">44</td>

   <td width="19">45</td>

  </tr>

  <tr>

   <td width="19">51</td>

   <td width="19">52</td>

   <td width="19">53</td>

   <td width="19">54</td>

   <td width="19">55</td>

   <td width="19">51</td>

   <td width="19">52</td>

   <td width="19">53</td>

   <td width="19">54</td>

   <td width="19">55</td>

  </tr>

 </tbody>

</table>

Figure 1 – (Left) 5 × 5 convolutional feature map. (Right) Template answer.

<ol>

 <li>If we use <em>M</em><em><sup>A </sup></em>for the first layer and <em>M</em><em><sup>A </sup></em>for the second layer.</li>

 <li>If we use <em>M</em><em><sup>A </sup></em>for the first layer and <em>M</em><em><sup>B </sup></em>for the second layer.</li>

 <li>If we use <em>M</em><em><sup>B </sup></em>for the first layer and <em>M</em><em><sup>A </sup></em>for the second layer.</li>

 <li>If we use <em>M</em><em><sup>B </sup></em>for the first layer and <em>M</em><em><sup>B </sup></em>for the second layer.</li>

</ol>

Your answer should look like Figure 1 (Right).

<a href="#_ftnref1" name="_ftn1">[1]</a> . An example of this is the use of masking in the Transformer architecture (Problem 3 of HW2 practical part).

Question 2 (6-3-6-3). Reparameterization trick is a standard technique that makes the samples of a random variable differentiable. The trick represents the random variable as a simple mapping from another random variable drawn from some simple distribution<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>. If the reparameterization is a bijective function, the induced density of the resulting random variable can be computed using the change-of-variable density formula, whose computation requires evaluating the determinant of the Jacobian of the mapping.

Consider a random vector <em>Z </em>∈ R<em><sup>K </sup></em>with a density function <em>q</em>(<em>z</em>;<em>φ</em>) and a random variable <em>Z</em><sub>0 </sub>∈ R<em><sup>K </sup></em>having a <em>φ</em>-independent density function <em>q</em>(<em>z</em><sub>0</sub>). We want to find a deterministic function <em>g </em>: R<em><sup>K </sup></em>→ R<em><sup>K </sup></em>that depends on <em>φ</em>, to transform <em>Z</em><sub>0</sub>, such that the induced distribution of the transformation has the same density as <em>Z</em>. Recall the change of density for a bijective, differentiable <em>g</em>:         (1)

<ol>

 <li>Assume <em>q</em>(<em>z</em><sub>0</sub>) = N(<strong>0</strong><em>,</em><em>I</em><em><sub>K</sub></em>) and <em>g</em>, where <em>µ </em>∈ R<em><sup>K </sup></em>and. Note that is element-wise product. Show that <em>g</em>(<em>z</em><sub>0</sub>) is distributed by N(<em>µ,</em>diag(<em>σ</em><sup>2</sup>)) using Equation (1).</li>

 <li>Compute the time complexity of evaluating |det<em>J<sub>z</sub></em><sub>0</sub><em>g</em>(<em>z</em><sub>0</sub>)| when <em>g</em>. Use the big O notation and expressive the time complexity as a function of <em>K</em>.</li>

 <li>Assume <em>g</em>(<em>z</em><sub>0</sub>) = <em>µ </em>+ <em>Sz</em><sub>0</sub>, where <em>S </em>is a non-singular <em>K </em>× <em>K </em> Derive the density of <em>g</em>(<em>z</em><sub>0</sub>) using Equation (1).</li>

 <li>The time complexity of the general Jacobian determinant is at least O(<em>K</em><sup>2<em>.</em>37<a href="#_ftn2" name="_ftnref2">[2]</a></sup>)<sup>3</sup>. Assume instead <em>g</em>(<em>z</em><sub>0</sub>) = <em>µ </em>+ <em>Sz</em><sub>0 </sub>with <em>S </em>being a <em>K </em>× <em>K </em>lower triangular matrix; i.e. <em>S</em><em><sub>ij </sub></em>= 0 for <em>j &gt; i</em>, and <em>S</em><em><sub>ii </sub></em><em>&gt; </em>0. What is the time complexity of evaluating |det<em>J<sub>z</sub></em><sub>0</sub><em>g</em>(<em>z</em><sub>0</sub>)|?</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> . More specifically, these mapping should be differentiable wrt the density function’s parameters.

<a href="#_ftnref2" name="_ftn2">[2]</a> . <a href="https://en.wikipedia.org/wiki/Computational_complexity_of_mathematical_operations">https://en.wikipedia.org/wiki/Computational_complexity_of_mathematical_operations</a>

Question 3 (5-5-6). Consider a latent variable model <em>p<sub>θ</sub></em>(<em>x</em>) = <sup>R </sup><em>p<sub>θ</sub></em>(<em>x</em>|<em>z</em>)<em>p</em>(<em>z</em>)<em>dz</em>, where <em>p</em>(<em>z</em>) = N(<strong>0</strong><em>,</em><em>I</em><em><sub>K</sub></em>) and <em>z </em>∈ R<em><sup>K</sup></em>.The encoder network (aka “recognition model”) of variational autoencoder, <em>q<sub>φ</sub></em>(<em>z</em>|<em>x</em>), is used to produce an approximate (variational) posterior distribution over latent variables <em>z </em>for any input datapoint <em>x</em>.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> This distribution is trained to match the true posterior by maximizing the evidence lower bound (ELBO):

L(<em>θ,φ</em>;<em>x</em>) = E<em>q<sub>φ</sub></em>[log<em>p<sub>θ</sub></em>(<em>x </em>| <em>z</em>)] − <em>D</em><sub>KL</sub>(<em>q<sub>φ</sub></em>(<em>z </em>| <em>x</em>)||<em>p</em>(<em>z</em>))

Let Q be the family of variational distributions with a feasible set of parameters P ; i.e. Q = {<em>q</em>(<em>z</em>;<em>π</em>) : <em>π </em>∈ P}; for example <em>π </em>can be mean and standard deviation of a normal distribution. We assume <em>q<sub>φ </sub></em>is parameterized by a neural network (with parameters <em>φ</em>) that outputs the parameters, <em>π<sub>φ</sub></em>(<em>x</em>), of the distribution <em>q </em>∈ Q, i.e. <em>q<sub>φ</sub></em>(<em>z</em>|<em>x</em>) := <em>q</em>(<em>z</em>;<em>π<sub>φ</sub></em>(<em>x</em>)).

<ol>

 <li>Show that maximizing the expected complete data log likelihood (ECLL)</li>

</ol>

E<em>q</em><sub>(<em>z</em></sub><sub>|<em>x</em></sub><sub>)</sub>[log<em>p<sub>θ</sub></em>(<em>x</em>|<em>z</em>)<em>p</em>(<em>z</em>)]

for a fixed <em>q</em>(<em>z</em>|<em>x</em>), wrt the model parameter <em>θ</em>, is equivalent to maximizing

log<em>p<sub>θ</sub></em>(<em>x</em>) − <em>D</em><sub>KL</sub>(<em>q</em>(<em>z</em>|<em>x</em>)||<em>p<sub>θ</sub></em>(<em>z</em>|<em>x</em>))

This means the maximizer of the ECLL coincides with that of the marginal likelihood only if <em>q</em>(<em>z</em>|<em>x</em>) perfectly matches <em>p</em>(<em>z</em>|<em>x</em>).

<ol start="2">

 <li>Consider a finite training set {<em>x</em><em><sub>i </sub></em>: <em>i </em>∈ {1<em>,…,n</em>}}, <em>n </em>being the size the training data. Let <em>φ</em><sup>∗ </sup>be the maximizer argmax In addition, for each <em>x</em><em><sub>i </sub></em>let <em>q<sub>i </sub></em>∈ Q be an “instance-dependent” variational distribution, and denote by the maximizer of the corresponding ELBO. Compare <em>D</em><sub>KL</sub>(<em>q<sub>φ</sub></em>∗(<em>z</em>|<em>x</em><em><sub>i</sub></em>)||<em>p<sub>θ</sub></em>(<em>z</em>|<em>x</em><em><sub>i</sub></em>)) and <em>D</em><sub>KL</sub>(<em>q<sub>i</sub></em><sup>∗</sup>(<em>z</em>)||<em>p<sub>θ</sub></em>(<em>z</em>|<em>x</em><em><sub>i</sub></em>)). Which one is bigger?</li>

 <li>Following the previous question, compare the two approaches in the second subquestion</li>

</ol>

(a) in terms of bias of estimating the marginal likelihood via the ELBO, in the best case scenario

(i.e. when both approaches are optimal within the respective families)

<ul>

 <li>from the computational point of view (efficiency)</li>

 <li>in terms of memory (storage of parameters)</li>

</ul>

<a href="#_ftnref1" name="_ftn1">[1]</a> . Using a recognition model in this way is known as “amortized inference” ; this can be contrasted with traditional variational inference approaches (see, e.g., Chapter 10 of Bishop’s <em>Pattern Recognition an Machine Learning</em>), which fit a variational posterior independently for each new datapoint.

<ul>

 <li>independent of size of the dataset.</li>

</ul>

Question 4 (8-8). Let <em>p</em>(<em>x,z</em>) be the joint probability of a latent variable model where <em>x </em>and <em>z </em>denote the observed and unobserved variables, respectively. Let <em>q</em>(<em>z</em>|<em>x</em>) be an auxiliary distribution which we call the <em>proposal</em>, and define<sup>5</sup>

We’ve seen in class that this objective is a tighter lower bound on log<em>p</em>(<em>x</em>) than the evidence lower bound (ELBO), which is equal to L<sub>1 </sub>; that is L<sub>1</sub>[<em>q</em>(<em>z</em>|<em>x</em>)] ≤ L<em><sub>K</sub></em>[<em>q</em>(<em>z</em>|<em>x</em>)] ≤ log<em>p</em>(<em>x</em>).

In fact, L<em><sub>K</sub></em>[<em>q</em>(<em>z</em>|<em>x</em>)] can be interpreted as the ELBO with a refined proposal distribution. For <em>z<sub>j </sub></em>drawn i.i.d. from <em>q</em>(<em>z</em>|<em>x</em>) with 2 ≤ <em>j </em>≤ <em>K</em>, define the <em>unnormalized </em>density

<em>(Hint: in what follows, you might need to use the fact that if </em><em>w</em><sub>1</sub><em>,…,w<sub>K </sub>are random variables that have the same distribution, then </em><em>K</em>E[<em>w</em><sub>1</sub>] = <sup>P</sup><em><sub>i </sub></em>E[<em>w<sub>i</sub></em>] = E[<sup>P</sup><em><sub>i </sub></em><em>w<sub>i</sub></em>]<em>. You need to identify such </em><em>w<sub>i</sub>’s before applying this fact for each subquestion. )</em>

<ol>

 <li>Show that L<em><sub>K</sub></em>[<em>q</em>(<em>z</em>|<em>x</em>)] = E<em>z</em><sub>2:<em>K</em></sub>[L<sub>1</sub>[<em>q</em>˜(<em>z</em>|<em>x,z</em><sub>2</sub><em>,…,z<sub>K</sub></em>)]]; that is, the importance-weighted lower bound with <em>K </em>samples is equal to the average ELBO with the unnormalized density as a refined proposal.</li>

 <li>Show that <em>q<sub>K</sub></em>(<em>z</em>|<em>x</em>) := E<em>z</em><sub>2:<em>K</em></sub>[<em>q</em>˜(<em>z</em>|<em>x,z</em><sub>2</sub><em>,…,z<sub>K</sub></em>)] is in fact a probability density function. Also, show that L<sub>1</sub>[<em>q<sub>K</sub></em>(<em>z</em>|<em>x</em>)] is an even tighter lower bound than L<em><sub>K</sub></em>[<em>q</em>(<em>z</em>|<em>x</em>)]. This implies <em>q<sub>K</sub></em>(<em>z</em>|<em>x</em>) is closer to the true posterior <em>p</em>(<em>z</em>|<em>x</em>) than <em>q</em>(<em>z</em>|<em>x</em>) due to resampling, since L<em><sub>K</sub></em>[<em>q</em>(<em>z</em>|<em>x</em>)] ≥ L<sub>1</sub>[<em>q</em>(<em>z</em>|<em>x</em>)]. (Hint: <em>f</em>(<em>x</em>) := −<em>x</em>log<em>x </em>is concave.)</li>

</ol>

Question 5 (5-5-5-6). Normalizing flows are expressive invertible transformations of probability distributions. In this exercise, we will see how to satisfy the invertibility constraint of some family of parameterizations. For the first 3 questions, we assume the function <em>g </em>: R → R maps from real space to real space.

<ol>

 <li>Let <em>g</em>(<em>z</em>) = <em>af </em>(<em>bz </em>+ <em>c</em>) where <em>f </em>is the ReLU activation function <em>f</em>(<em>x</em>) = max(0<em>,x</em>). Show that <em>g </em>is non-invertible.</li>

 <li>Let , where <sup>P</sup><em><sub>i </sub></em><em>w<sub>i </sub></em>= 1, <em>a<sub>i </sub>&gt; </em>0, and <em>σ</em>(<em>x</em>) =</li>

</ol>

1<em>/</em>(1 + exp(−<em>x</em>)) is the logistic sigmoid activation function and <em>σ</em><sup>−1 </sup>is its inverse. Show that <em>g </em>is <em>strictly monotonically increasing </em>on its domain (−∞<em>,</em>∞), which implies invertiblity.

<ol start="3">

 <li>Consider a residual function of the form <em>g</em>(<em>z</em>) = <em>z </em>+ <em>f</em>(<em>z</em>). Show that <em>df/dz &gt; </em>−1 implies <em>g </em>is invertible.</li>

 <li>Consider the following transformation:</li>

</ol>

<em>g</em>(<em>z</em>) = <em>z </em>+ <em>βh</em>(<em>α,r</em>)(<em>z </em>− <em>z</em><sub>0</sub>)                                                       (42)

where <em>z</em><sub>0 </sub>∈ R<em><sup>D</sup></em>, <em>α </em>∈ R<sup>+</sup>, <em>β </em>∈ R, and <em>r </em>= ||<em>z </em>− <em>z</em><sub>0</sub>||<sub>2</sub>, <em>h</em>(<em>α,r</em>) = 1<em>/</em>(<em>α </em>+ <em>r</em>). Consider the following decomposition of <em>z </em>= <em>z</em><sub>0 </sub>+<em>r</em><em>z</em>˜. (i) Given <em>y </em>= <em>g</em>(<em>z</em>), show that <em>β </em>≥ −<em>α </em>is a sufficient condition to derive the unique <em>r </em>from equation (42). (ii) Given <em>r </em>and <em>y</em>, show that equation (42) has a unique solution <em>z</em>˜.

Question 6 (4-3-6). In this question, we are concerned with analyzing the training dynamics of GANs. Consider the following value function

<em>V </em>(<em>d,g</em>) = <em>dg                                                                    </em>(43)

with <em>g </em>∈ R and <em>d </em>∈ R. We will use this simple example to study the training dynamics of GANs.

<ol>

 <li>Consider gradient descent/ascent with learning rate <em>α </em>as the optimization procedure to iteratively minimize <em>V </em>(<em>d,g</em>) r.t. <em>g </em>and maximize <em>V </em>(<em>d,g</em>) w.r.t. <em>d</em>. We will apply the gradient descent/ascent to update <em>g </em>and <em>d </em>simultaneously. What is the update rule of <em>g </em>and <em>d</em>? Write your answer in the following form</li>

</ol>

[<em>d</em><em>k</em>+1<em>,g</em><em>k</em>+1]&gt; = <em>A</em>[<em>d</em><em>k</em><em>,g</em><em>k</em>]&gt;

where <em>A </em>is a 2 × 2 matrix; i.e. specify the value of <em>A</em>.

<ol start="2">

 <li>The optimization procedure you found in 6.1 characterizes a map which has a stationary point<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>, what are the coordinates of the stationary points?</li>

 <li>Analyze the eigenvalues of A and predict what will happen to <em>d </em>and <em>g </em>as you update them jointly. In other word, predict the behaviour of <em>d<sub>k </sub></em>and <em>g<sub>k </sub></em>as <em>k </em>→ ∞.</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> . A stationary point is a point on the surface of the graph (of the function) where all its partial derivatives are zero (equivalently, the gradient is zero). Source: <a href="https://en.wikipedia.org/wiki/Stationary_point">https://en.wikipedia.org/wiki/Stationary_point</a>
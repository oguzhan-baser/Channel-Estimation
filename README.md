# Channel Estimation
Estimation of the channel coefficients is an important concept before equalizer design since the design depends on channel coefficients. As one can see from the figure below, the channel changes between each communication nodes and thus in each communication round, the estimation of the channel may be required for reliable communication. Representing the overall channel as a mathematical model in a finite length vector is quite fortunate for system design in digital communications because it makes almost any latter algorithm less complex, more accurate and more feasible in the run time. There are several channel estimation algorithms such as Least Mean Squares and Recursive Least Squares algorithms. For the sake of simplicity and conciseness, Maximum Likelihood Single Shot Estimation algorithm was chosen to be implemented in this project.

![](./figs/scheme.PNG)

## Maximum Likelihood Single Shot Estimation
During channel estimation , several pilot symbols known by both the receiver and the transmitter are sent through the channel through which the information will pass, and the unknown coefficients of channel are estimated by maximum log likelihood method
One can model the received pilots by the receiver as follows:

![](./figs/eqn1.PNG)

where y is incoming signal, h is channel vector, x is pilot symbol sequence and η is noise for that time instant. To utilize MATLAB’s fast matrix operations, one can represent the summation given above as a matrix multiplication between channel vector and sliding pilot symbols. One should note that sliding pilots should be in reverse order since channel vector is not flipped in the convolution as shown in the formula above. Say we send 3 known pilot symbols.

![](./figs/eqn2.PNG)

size of X is = (channel length+pilot numbers-1) x channel length

![](./figs/eqn3.PNG) | width=100

It is known fact that **η** vector is independent and identically distributed Gaussian random variable with μ = 0, σ². Since **𝑋**, **𝐻** vectors are deterministic, **𝑌** is also i.i.d. Gaussian random variable with mean vector **μ**= **𝐻**𝑥**𝑋**, σ².

![](./figs/eqn4.PNG)

This is the likelihood function. Then, one can take log likelihood by taking ln of this function owing to the monotonicity of log function following equation is got.

![](./figs/eqn5.PNG)

This is the likelihood function and one can maximize this function by optimizing over channel coefficients as the following

![](./figs/eqn6.PNG)

This equation gives the channel coefficients that we are looking for the MMSE equalization. The formulation of the MMSE equalization can be directly got from the [book](https://books.google.com/books/about/Digital_Communications.html?id=HroiQAAACAAJ#:~:text=Digital%20Communications%20is%20a%20classic,depth%20to%20cover%20two%20semesters.), which is

![](./figs/eqn7.PNG)



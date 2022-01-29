# Channel Estimation
Estimation of the channel coefficients is an important concept before equalizer design since the design depends on channel coefficients. As one can see from the figure below, the channel changes between each communication nodes and thus in each communication round, the estimation of the channel may be required for reliable communication. Representing the overall channel as a mathematical model in a finite length vector is quite fortunate for system design in digital communications because it makes almost any latter algorithm less complex, more accurate and more feasible in the run time. There are several channel estimation algorithms such as Least Mean Squares and Recursive Least Squares algorithms. For the sake of simplicity and conciseness, Maximum Likelihood Single Shot Estimation algorithm was chosen to be implemented in this project.

![](./figs/scheme.PNG)

## Maximum Likelihood Single Shot Estimation
During channel estimation , several pilot symbols known by both the receiver and the transmitter are sent through the channel through which the information will pass, and the unknown coefficients of channel are estimated by maximum log likelihood method
One can model the received pilots by the receiver as follows:

figs/eqn1.png

where y is incoming signal, h is channel vector, x is pilot symbol sequence and η is noise for that time instant. To utilize MATLAB’s fast matrix operations, one can represent the summation given above as a matrix multiplication between channel vector and sliding pilot symbols. One should note that sliding pilots should be in reverse order since channel vector is not flipped in the convolution as shown in the formula above. Say we send 3 known pilot symbols.

figs/eqn2.png
figs/eqn3.png

size of X is = (channel length+pilot numbers-1) x channel length

figs/eqn4.png
figs/eqn5.png

It is known fact that η⃗⃗ is independent and identically distributed Gaussian random variable with μ = 0, σ2. Since 𝑋⃗, 𝐻⃗⃗ are deterministic, 𝑌⃗⃗ is also i.i.d. Gaussian random variable with μ⃗⃗ = 𝐻⃗⃗𝑥𝑋⃗, σ2

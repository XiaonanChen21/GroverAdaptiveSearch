In this file we implement ''Grover Adaptive Search for Constrained Polynomial Binary Optimization''. We have a Qiskit function that takes three inputs:
*   a pseudo-boolean function $f: \mathbb{F}_2^n\to \mathbb{Z}$
*   a threshold, $t\in \mathbb{Z}$
*   a constraint function $C: \mathbb{F}_2^n\to \mathbb{Z}$

and outputs marker oracle $U_{f,t,C}$ such that $$U_{f,t,C}|x⟩_n|y⟩_1=\begin{cases}|x⟩_n|y\oplus 1⟩_1, \; \mathrm{if}\; f(x)>t \; \mathrm{ and } \; C(x)\ge 0 \\|x⟩_n|y⟩_1, \; \mathrm{otherwise.}
\end{cases}$$

We implement GAS by the following steps:
*   Realize function $f$ and $C$ by circuits (For simplicity, assume $f,C$ are polynomials)
*   Implement the oracle $U_{f,t,C}$, seting the constraints to be $f>t \,\wedge\,C\ge 0$.
*   Apply Grover and measure to find a candidate $x^{(0)}$.
*   Recursively run Grover with updated $t=f(x^{(0)})$.


# Matrices
Topic: 
Date: 2022-06-27

---

## Summary
What it is about very briefly

## Notes
- Matrices are defined with round brackets $\large \begin{pmatrix} 2 & 4 \\ 3 & 8\end{pmatrix}$
- The key to solving *simultanious equation* $$\begin{align*} &2a + 3b = 8 \\ &10a + 1b = 13\end{align*}$$ is appreciating how *vectors* are transformed by *matrices*, aka the heart of *linear algebra*.
- Applying one matrix and the another is called *composition* or *combination of matrix transformations*
- Different types of *matrix transformation* :
	- A matrix that doesn't change the vector, it's a matrix of the *basis vector* of the space $\begin{pmatrix} 1 & 0 \\ 0 & 1\end{pmatrix}$ . This one's called *IDENTITY MATRIX* OR $I$
	- Matrices that *increases* $\large \begin{pmatrix} 3 & 0 \\ 0 & 2\end{pmatrix}$ or *squishes* $\large \begin{pmatrix} \frac{1}{3} & 0 \\ 0 & \frac{1}{2}\end{pmatrix}$ the basis vectors.
	- Matrices that *flip around one of the axis*, $\large \begin{pmatrix} -1 & 0 \\ 0 & 2\end{pmatrix}$ or *inverts* everything $\large \begin{pmatrix} -1 & 0 \\ 0 & -2\end{pmatrix}$
	- Matrices that shears one of the vectors $\large \begin{pmatrix} 1 & 1 \\  0 & 1\end{pmatrix}$, this one keeps X where it is and shears Y (from $\begin{bmatrix} 0 \\ 1\end{bmatrix}$).
- Matrix multiplicatin *IS ASSOCIATITIVE* but *IS NOT COMMUTATIVE*
- The *Inverse* matrix of *A* is *A^-1*, aka a matrix that *A^-1* reverses what *A* does and gives me the *Identity matrix*. In the expression $$\Large  A r = s$$
where $A$ = Matrix, $r$ = the vector that the matrix operates on and $s$ = the resulting vector and $\large r$ is unknown, i can multiply both end by the inverse matrix $$\large A^{-1} A r = A^{-1} s  $$ where $\large A^{-1} A = I$ identity matrix and $\large I * r = r$, i need to find the *inverse of A* to be able to solve my problem.

- Too long to describe but useful to check, are some operation you can do like:
	- [Elimination](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/0903b4b404284cd14b66ecccea103fd4_MIT18_06SCF11_Ses1.2sum.pdf) and also [here](https://www.math.utah.edu/~zwick/Classes/Fall2012_2270/Lectures/Lecture7.pdf) to get a [Upper Triangular Matrix](https://en.wikipedia.org//wiki/Triangular_matrix).
	- [Back Substitution](https://www.math.usm.edu/lambers/mat610/sum10/lecture4.pdf) 
	At the end of these two, i'd have transformed *A* into the *Identity Matrix*, which for a matrix like $\begin{pmatrix} 1 & 1 & 3 \\ 1 & 2 & 4 \\ 1 & 1 & 2\end{pmatrix}$ is $\begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1\end{pmatrix}$
- They way to find the *inverse* of a matrix $A$, let's call it $B$, in the equation $$A B = I$$
Is to get the *Identity matrix* for *A* and the *indentity Matrix I* will be transformed into the *inverse of A, aka B*. Probably slightly different from what you'd learn in school but it's the fastest/easist way (*Elimination + back substitution*) when done computationally.
This is called [Decomposition Process, Matrix Decomposition or Factorization](https://en.wikipedia.org/wiki/Matrix_decomposition)


## Questions
- Item




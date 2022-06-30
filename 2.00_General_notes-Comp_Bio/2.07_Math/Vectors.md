
# Vectors
Topic: #Matrix #Vector
Date: 2022-06-03

---

## Summary
Notes Vectors. Starts here at [[Linear_algebra_lesson]]. This is the first lesson where it introduces what is linear algebra and how matrix multiplication happens, or matrix vector multiplication.

## Vector
- Vectors are not just geometric objects in the physical space but they can described directions along any sort of axes, if we think about them like these, than are just lists. 
- Doing vector addition is just the sum of each compenent of the ijth element of the vector, something like a = $\begin{bmatrix}2 \\ 3\end{bmatrix}$ and b = $\begin{bmatrix}-1 \\ 4\end{bmatrix}$, a + b = $\begin{bmatrix}1 \\ 7\end{bmatrix}$. Vector addition, since it's done component by component it's called *associative*. Associatives means that (r + s) + t is equal to r + (s + t) like with normal numbers.
- Multiplication by a scalar is just multiplication of a number for each component of the vector, a = $\begin{bmatrix}2 \\ 3\end{bmatrix}$, a * 2 = $\begin{bmatrix}4 \\ 6\end{bmatrix}$
- *Length* of a vector = *size* of a vector. The *size* of a vector is defined as the sum of the squares of its compenent all square rooted. Given vector  `r`  = $\begin{bmatrix}a \\ b\end{bmatrix}$,  $|r|$ aka the `size of vector r` = $\sqrt[2](a^2 + b^2)$.
- *dot product*  of a vector = *inner scalar* or *projection product*. The *dot product* gives us a single number so if, a = $\begin{bmatrix}3 \\ 2\end{bmatrix}$ and b = $\begin{bmatrix}-1 \\ 2\end{bmatrix}$, the dot product *a. b* is equal to = 3 * -1 + 2 * 2 = 1
- *dot product* properties:
	- is *commutative*, *r.s* = *s.r*
	- is *distributed over addition*, *r.(s + t)* = *r.s + r.t*
	- is *associative over scalar distribution*, *r.(as)* = *a * (r.s)* where a is a scalar number 
- Link between dot product and length/modulus of a vector, the dot product of a vector by itself *r.r* i get the sum of the squares of it's components and it's the same as the square of it's *size or modulus*. To get it, simply take the square root of the dot product of the vector with itself
- Using the *cosine rule*, we can derive that 
	r.s = $|r|$ $|s|$ * $\cos\theta$ . 
	if two vectors are orthogonal, $\theta$ betwenn them is 90 degrees and cosin is 0, the dot product is zero. If they go in the same direction and $\theta$ = 0 degrees, then cosin is 1 and it's just $|r| |s|$. If $\theta$ = 180, cosin is -1, and the dot product is - $|r| |s|$.
- *Projection* is the "shadow" of one vector onto the other as if i have a triangle and one side falls at 90 degrees onto the other one. In the dot product r.s = $|r|$ $|s|$ * $\cos\theta$ the projection of *s* on *r* is $|s|$ * $\cos\theta$ , so now r.s = $|r|$ * projection of s. $|s|$ * $\cos\theta$ gives me a number, a scalar projection and that's why the dot product it's also called the *projection product* because it takes the projection of one vector onto another.
- *Vector projection* is defined as the dot product divided by mod r squared and all multiplied by vector r       $r * \frac{r\cdot s}{|r|^2}$ 
- *Basis vectors* are the vectors used to define the coordinate space in which we work. Given a vector r and basis vectors ei and ej, we can describe the vector r using the dot product with a new set of basis vector, bi and bj, only if those are orthogonals ($\theta$ = 90 degrees) to each other. Otherwise i'd need a matrix to do *transformation of axes*.
- *Basis* is a set of *n* vectors:
	- are not liner combinations of each other (aka *linearly independent*)
	- span the space they describe
	- the space is n-dimentional
Use as much as possible *orthonormal basis vector sets* aka at 90 degrees and of length 1 (unit)

# Other

### Find the product of two square matrices (Strassen Algorithm)

The Strassen Algorithm for matrix multiplication is not the fastest known algorithm, but most faster algorithms are very complex and derived from the Strassen one, so it's worth knowing nonetheless.

The standard way of multiplying two 4x4 matrices, A and B (\\( A_{1,2} \\) corresponds to matrix A, row 1, column 2), is as follows:
- \\( C_{1,1} = A_{1,1}B_{1,1} + A_{1,2}B_{2,1} \\)
- \\( C_{1,2} = A_{1,1}B_{1,2} + A_{1,2}B_{2,2} \\)
- \\( C_{2,1} = A_{2,1}B_{1,1} + A_{2,2}B_{2,1} \\)
- \\( C_{2,2} = A_{2,1}B_{1,2} + A_{2,2}B_{2,2} \\)

This method requires 8 multiplications. The Strassen algorithm takes advantage of the fact that there are shared multiplications among the 8, and it can be narrowed down to 7:
- \\( M_1 = (A_{1,1} + A_{2,2})(B_{1,1} + B_{2,2}) \\)
- \\( M_1 = (A_{2,1} + A_{2,2})B_{1,1} \\)
- \\( M_1 = A_{1,1}(B_{1,2} - B_{2,2}) \\)
- \\( M_1 = A_{2,2}(B_{2,1} - B_{1,1}) \\)
- \\( M_1 = (A_{1,1} + A_{1,2})B_{2,2} \\)
- \\( M_1 = (A_{2,1} - A_{1,1})(B_{1,1} + B_{1,2}) \\)
- \\( M_1 = (A_{1,2} - A_{2,2})(B_{2,1} + B_{2,2}) \\)

Which are used as follows:
- \\( C_{1,1} = M_1 + M_4 - M_5 + M_7 \\)
- \\( C_{1,2} = M_3 + M_5 \\)
- \\( C_{2,1} = M_2 + M_4 \\)
- \\( C_{2,2} = M_1 - M_2 + M_3 + M_6 \\)

To calculate the product of 2 matrices of size NxN where N 2 1, the Strassen algorithm divides each matrix into a 2x2 matrix of submatrices. In the case of odd N, there may be some 1x1 submatrices. The submatrices are multiplied recursively and so on until the result of the base matrix is produced.

It excels in multiplying matrices where \\( N = 2^i \\) for some integer _i_. It runs in \\( O(N^{2.8074...}) \\) time, but that's probably not worth memorizing.

### Apply a Fourier Transform (Cooley-Turkey Algorithm, Fast Fourier Transform)

A Fourier transform has many uses in the real world, but it is a complex thing. The Fast Fourier Transform is an optimal way to derive a Fourier transform, and the Cooley-Turkey algorithm is an algorithm that uses that method. More info [here](https://en.wikipedia.org/wiki/Cooley%E2%80%93Tukey_FFT_algorithm).

### Given the feedback history of a function, a current value, and a desired value, determine what new value applied to the function will likely yield the desired value (PID Controller)

As the section title suggests, PID controllers estimate what input to a function will yield the desired output based on the history of the function's inputs and outputs, and which state the context is in.

Another complex operation involving math principles. More info [here](https://en.wikipedia.org/wiki/PID_controller).

### Factor an integer (General Number Field Sieve)

The General Number Field Sieve is a classical way of factoring integers. Another complex operation involving math principles. More info [here](https://en.wikipedia.org/wiki/General_number_field_sieve).
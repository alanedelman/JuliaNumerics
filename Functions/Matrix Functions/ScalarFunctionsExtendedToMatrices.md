# Scalar Functions extended to Matrix functions of Matrices:
**Wikipedia Definition:**
http://en.wikipedia.org/wiki/Matrix_function#Extending_scalar_functions_to_matrix_functions

**Notation:** f(M)

**Ambiguities:** (other reasonable definitions of f(M)) 

1. Pointwise application of f. . 
2. Cholesky Decoposition when f(x)=sqrt(x). (another generalization
   of scalar sqrt)
3. Scalar Functions of Matrix Argument (this page covers matrix functions of matrix argument)

 

**Numerical Conditioning Issues:**  The Mathematical Definition, while easy to implement, 
      can be highly ill-conditioned, especially when the eigenvector matrix itself
      is ill-conditioned.  The Schur decomposition (available in Lapack) can ameliorate this.

**Branch Cuts:**  The issue of the proper handling of branch cuts for scalar functions
              is tricky enough.  It has been virtually ignored for matrix functions.
               Very likely different software packages will make different choices.

**Extra Accuracy:**  Many of the most common elementary functions
such as sqrt (required by IEEE) and sine (if the right libraries are used) can be accurate to
                the last bit, even when ill-conditioned.  This may be beyond
                 reach, and anyway has not been carefully studied.

**References:** van Loan, Higham ....  (especially Higham's book)

**Embelishments for efficiency and accuracy:**  
 `f(M,v) = f(M)*v` (computed more efficiently).  For example, if
f(x)=1/x, `f(M,v)=M\v`.

 
                      


Common Cases:                Julia  MATLAB            Mathematica            Maple([LinearAlgebra] package)

Powers                               M^p              MatrixPower            MatrixPower
Inverses                             inv(M),M^(-1)    Inverse                MatrixInverse
Matrix Exponential                   expm             MatrixExp              MatrixExponential
Matrix Logarithm                     logm             MatrixLog              use MatrixFunction
Matrix Sqrt                          sqrtm,M^(.5)     MatrixPower[M,0,5]     use MatrixPower
General Functions                    funm             MatrixFunction         MatrixFunction

Additions that might make sense:

1.  A page for separate matrix functions
2.  Completion and Annotation of Reference List
3.  R, Python Syntax
4.  Numerical comparison of good test cases

would be good to add R and python and point out exactly the places where there are interesting numerical differencs.

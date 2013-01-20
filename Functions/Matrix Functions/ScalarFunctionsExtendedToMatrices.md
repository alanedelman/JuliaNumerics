# Scalar Functions extended to Matrices:
*Wikipedia Definition:*
http://en.wikipedia.org/wiki/Matrix_function#Extending_scalar_functions_to_matrix_functions

Notation: f(M)

Syntax Ambiguities:  One can apply f to each element pointwise. 
                     The cholesky factor is sometimes called a matrix sqrt,
                           since when n=1 it is the ordinary sqrt.
                     Symmetric functions of the eigenvalues such as
                         orthogonal polynomials of matrix argument and hypergeometrics
                         of matrix argument.

Numerical Conditioning Issues: The Mathematical Definition, while easy to implement, 
      can be highly ill-conditioned, especially when the eigenvector matrix itself
      is ill-conditioned.  The Schur decomposition (available in Lapack) can ameliorate this.

Branch Cuts:  The issue of the proper handling of branch cuts for scalar functions
              is tricky enough.  It has been virtually ignored for matrix functions.
               Very likely different software packages will make different choices.

Extra Accuracy:  Many of the most common elementary functions can be accurate to
                the last bit, even when ill-conditioned.  This may be beyond
                 reach, and anyway has not been carefully studied.

References: van Loan, Higham ....  (especially Higham's book)

Variations:  a blackbox sending v-->f(M)*v can be more useful as in M\v
             and can take advantage of so much
 
                      


Common Cases:                Julia  MATLAB            Mathematica            Maple([LinearAlgebra] package)

Powers                               M^p              MatrixPower            MatrixPower
Inverses                             inv(M),M^(-1)    Inverse                MatrixInverse
Matrix Exponential                   expm             MatrixExp              MatrixExponential
Matrix Logarithm                     logm             MatrixLog              use MatrixFunction
Matrix Sqrt                          sqrtm,M^(.5)     MatrixPower[M,0,5]     use MatrixPower
General Functions                    funm             MatrixFunction         MatrixFunction

would be good to add R and python and point out exactly the places where there are interesting
numerical differencs.

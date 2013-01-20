# Scalar Functions extended to Matrix functions of Matrices:
**Wikipedia Definition:**
http://en.wikipedia.org/wiki/Matrix_function#Extending_scalar_functions_to_matrix_functions

**Notation:** f(M)

**Ambiguities:** (other reasonable definitions of f(M)) 

1. Pointwise application of f. . 
2. Cholesky Decoposition when f(x)=sqrt(x). (another generalization
   of scalar sqrt)
3. Less well known: Scalar Functions extended to *scalar* functions of Matrix Argument (this page covers scalar functions extended to  *matrix* functions of matrix argument)

 

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

 
                      
<table>
<tr>
<th> Function:    </th><th>   Julia </th><th>  MATLAB </th><th>            Mathematica     </th><th>       Maple ([LinearAlgebra] package) </th>
<tr><th> Powers  </th><th>M^p</th><th> M^p </th><th>   MatrixPower </th><th>     MatrixPower </tr>
<tr><th> Inverses </th><th></th></th> inv(M),M^(-1) </th><th> Inverse </th><th>                MatrixInverse </th></tr>
<tr><th>Matrix Exponential </th>     <th>expm</th><th>   expm </th>            <th> MatrixExp </th><th>    MatrixExponential </th>
Matrix Logarithm                     logm             MatrixLog              use MatrixFunction
<tr><th>Matrix Sqrt</th> <th>M^(0.5)</th>                        sqrtm,M^(.5)     MatrixPower[M,0,5]     use MatrixPower
</tr>
<tr>
<th>General Functions </th>                    funm             MatrixFunction         MatrixFunction
</table>


Additions that might make sense:

1.  A page for separate matrix functions
2.  Completion and Annotation of Reference List
3.  R, Python Syntax
4.  Numerical comparison of good test cases

would be good to add R and python and point out exactly the places where there are interesting numerical differencs.

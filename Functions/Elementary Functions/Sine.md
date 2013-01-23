# Sine
**Wikipedia Definition:**
http://en.wikipedia.org/wiki/Sine


**Condition Number**
`abs(x/tan(x))`

The sine function is ill-conditioned for very large arguments and near the zeros (non-zero integer multiples of π)) .

**Desirable Features**
1. Least possible forward error: This means that sin(x) computes the 
correctly rounded theoretical value of the sine of the machine number x
2. Monotonicity: This means that for real x, at least, the computed sin(x) is monotonic where the underlying theoretical function is. 
3. Performance: May be (?) at odds with number 1, which would then require settling merely for a good backward error. 


**Julia Discussions**

`sin(2.0^64)` and `sin(pi)` are discussed: 
https://github.com/JuliaLang/julia/issues/1768#issuecomment-12505531

**Complex Identity**

sin(x+iy)=sin x cosh y + i cos x sinhy

**Ill Conditioned Case study:sin(2^64)**

Answers you may see. (In Numerical Order)

1.  0.0235 Best Answer (seen on all platforms using the fdlibm library)
2.  0.2472  Commonly seen on 32 bit windows not using fdlibm
3.  0.3128 Commonly seen on 32 bit linux not using fdlibm
4.  0.8281 Seen on maple which first rounds 2^64 to be 18446744070000000000 and then takes the sin.  (2^64=18446744073709551616).

The open source library fdlibm (Freely Distributable Library-Math) was developed at SUN Microsystem (when?) by (among others, I'd bet, good folks trained by Kahan???? history missing!)  It contains in particular
a higly accurate `modhalfpi` function 
<a href="http://www.netlib.org/fdlibm/e_rem_pio2.c">
e_rem_pio2.c </a>.  Where a quick click reveals π/2 and 2/π in hex to many digits.

I think I once heard that it was msvcrt.dll (the microsoft c runtime library) that was giving the often seen windows answer of 0.2472....  This is not confirmed.

Also the julia thread https://github.com/JuliaLang/julia/issues/1768#issuecomment-12505531 has Viral reporting that Hari Koduvely saw the 0.3128... number on windows on a very old version of julia.  It might
be good to double check if that wasn't linux.

<table>
**Julia (pre 0.1)**
<table>
<tr>
<td> sin(2.0^64) </td>
<td> 0.023598509904439558 </td>
<td> num2hex(sin(2.0^64)) </td>
<td> 3f982a353118793d</td>
<tr>
</tr>
</table>


**MATLAB (R2010b**
<table>
<tr>
<td> sin(2^64) </td>
<td> 0.023598509904440 </td>
<td> format(hex);sin(2^64) </td>
<td>  3f982a353118793d </td>
</tr>
</table>

**R 2.10.1 (windows vista)**
<table>
<tr>
<td>
format(sin(2^64),digits=20)
</td>
<td>
[1] "0.2472606463094177"
</td>
</tr>
</table>

**Mathematica 7 (Windows Vista)**
<table>
<tr>
<td>
N[Sin[2^64]]
</td>
<td>
0.247261
</td>
<td>
N[Sin[2^64],20]
</td>
<td>
 0.023598509904439558634
</td>
</tr>
</table>
</table>

**Ill Conditioned Case study:sin(pi)**

It is useful to understand the difference between π and pi.
(See https://github.com/alanedelman/JuliaNumerics/blob/master/Constants/Pi.md)


<table>
<tr>
<td> sin(π) </td> <td> 0 </td>
</tr>
<tr>
<td> sin(pi) </td> <td> very close to π-pi. </td><td> 1.224646799147353e-016 </td>
</table>

# Sine
**Wikipedia Definition:**
http://en.wikipedia.org/wiki/Sine


**Condition Number**
`abs(x/tan(x))`

The sine function is ill-conditioned for very large arguments and near the zeros (integer multiples of π) .


**Julia Discussions**

`sin(2.0^64)` and `sin(pi)` are discussed: 
https://github.com/JuliaLang/julia/issues/1768#issuecomment-12505531

**Complex Identity**

sin(x+iy)=sin x cosh y + i cos x sinhy

**Ill Conditioned Case study:sin(2^64)**

<table>
<tr>
Julia (pre 0.1) 
</tr>
<tr>
<td> sin(2.0^64) </td>
<td> 0.023598509904439558 </td>
<td> num2hex(sin(2.0^64)) </td>
<td> “3f982a353118793d” </td>
<tr>
</tr>
<tr>
MATLAB
</tr>


</table>

**Ill Conditioned Case study:sin(pi)**

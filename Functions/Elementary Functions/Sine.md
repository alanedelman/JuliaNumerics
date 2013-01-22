# Sine
**Wikipedia Definition:**
http://en.wikipedia.org/wiki/Sine


**Condition Number**
`abs(x/tan(x))`

The sine function is ill-conditioned for very large arguments and near the zeros.



My favorite example of this is sin(2.0^64) as I have seen many
different answers even from the same technical computing software
on different platforms. 

(See the discussion on whether whether there even is one "right" answer
 in the context of floating point.)

sin(2.0^64)  0.023598509904440  3f982a353118793d

**Julia Discussions**

`sin(2.0^64)` and `sin(pi)` are discussed: 
https://github.com/JuliaLang/julia/issues/1768#issuecomment-12505531

**Complex Numbers**

sin(x+iy)=sin x cosh y + i cos x sinhy
## Shintani domains for totally complex quartic number fields 

Here we give an algorithm (in PARI GP) to obtain a fundamental domain for totally complex quartic number fields $k$ hosted in the file [ShintaniDomainK41.gp](https://github.com/acapunay-math/ShintaniK41/blob/main/Algorithm/ShintaniDomainK41.gp). By [Shintani's unit theorem](https://en.wikipedia.org/wiki/Shintani%27s_unit_theorem) such domain is a finite union of polyhedral cones with generators in $k$. 

This implementation is based on the manuscript (abbreviated MS)

[ATTRACTOR-REPELLER CONSTRUCTION OF SHINTANI DOMAINS FOR TOTALLY COMPLEX QUARTIC FIELDS](https://www.sciencedirect.com/science/article/pii/S0022314X23002299) 

by A. CAPUÑAY, M. ESPINOZA AND E. FRIEDMAN, Journal of Number Theory, Volume 258, May 2024, Pages 146-172.

## Execution

$(I).$ After uploading the file `ShintaniDomainK41.gp` in Pari GP, using an irreducible polynomial $p$ (which defines a complex quartic number field), then you can use the command

 ```bash
 F=FDK41(p);
 ```

This returns a list $F:=[F1,F2,F3,F4]$ asociated to a Shintani domain interpreted as follows


1. The first entry $F1$ (i.e., $F[1]$) has the form 

      $$[t,p,reg,disc,E,r,T]$$

with 

$t =$  real computation time for $F$ in milliseconds

$p =$  quartic irreducible polynomial defining a totally complex number field $k:= \text{the quotient ring } \mathbb{Q}[X]/(p)$ 

$reg =$  Regulator of $k$ to $19$ decimals

$disc =$ Discriminant of $k$

$E =$  fundamental unit of $k$. The Shintani domain corresponds to the action on $(\mathbb{C}^{\ast})\times(\mathbb{C}^{\ast})$ of the 
       group generated by $E$. The  unit $E$, like all other elements of $k$ below, is given as a polynomial $g$ in $\mathbb{Q}[X]$ 
       of degree at most $3$. The associated element of $k$ is the class of $g$ in $\mathbb{Q}[X]/(p)$
       
$r =$  minimal positive integer with $|E_1|^{2r} < 0.184$ as in display $(34)$ of Ms. Here $E_1$ is an embedding of $E$ in $\mathbb{C}$
   
$T =$    number of 4-cones in the Shintani domain constructed 

  
2. The second entry $F2$ of $F$ (i.e., $F[2]$) has the form  

      $$[\tilde{e}_1,\tilde{e}_2,\tilde{e}_3,\tilde{e}_4]$$

where $\tilde{e}_j$ (for $1\leq j\leq 4$) is an element of $k$ approximating the $j-th$ element of the standard basis of $\mathbb{R}^4 = \mathbb{C}^2$, wherein $k$ is embedded. The elements $\tilde{e}_j$ are mentioned at the beginning of the proof of the Main Theorem in section 5 of the Ms. The error bound ($\varepsilon$ in the Ms) used was $1/150$. 


3. The third entry $F3$ of $F$ (i.e., $F[3]$) has the form  

      $$[C_1,C_2,...,C_T]$$

which is a list of the $T$ (semi-closed) cones in the Shintani domain, where $T = F[1][7]$ was described above. Each cone $C_j$ is given by $m$ linear inequalities ($m$ depending on the cone) giving $m$ closed or open half-spaces whose intersection is $Cj$. Thus, each $Cj$ has the form  

  $$[v_1,v_2,...,v_m]$$

where $v_i=[w,1]$ or $[w,-1]$ and $w$ is an element of $k$ (depending on $i$ and $j$). If $w$ is followed by $1$, then the corresponding (closed) half-space is the set of elements $x$ of $\mathbb{R}^4$ with $\text{Trace}(xw) \geq 0$. If $w$ is followed by $-1$, then the corresponding (open) half-space is given by $\text{Trace}(xw) > 0$. Here Trace is the extension to $\mathbb{R}^4$ of the trace map from $k$ to $\mathbb{Q}$.

4. The fourth entry $F4$ of $F$ (i.e., $F[4]$) has the form  

      $$[CC_1,CC_2,...,CC_T]$$

where $CC_j$ is the closure in $\mathbb{R}^4$ of the cone $C_j$ in $F3$. Each closed cone $CC_j$ is given here by a list of generators in $k$.
             



$(II).$ If you want to obtain Shintani domains for a list of (totally complex quartic) polynomials `L`, you can use the command

  ```bash
  ShintaniExamplesK41(L)
  ```

This creates a file with Shintani domains via the command `FDK41(p)` for each polynomial `p` of the list `L`

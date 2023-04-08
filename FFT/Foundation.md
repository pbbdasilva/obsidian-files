
### Problem expl

Compute $C(x)$ = $A(x) * B(x)$  in $O(nlogn)$

### Naive solution (DFT)

- A and B deg n => we need n+1 points in the graph to determine the coefcs of each polynom
- $C(x)$ is deg $2n$ => needs 2n+1 points

Let $A(x)$ = $\sum_{0}^{n-1} a_{i} * x_{i}$
Let the set of points {{$x_{i}$,$y_{i}$ }} for i $\in$ [0,n-1] all distinct
![[Pasted image 20230213084731.png]]

This is equivalent as:
![[Pasted image 20230213090302.png]]

This matrix always has an inverse? (Vandermonde)
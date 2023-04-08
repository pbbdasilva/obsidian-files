
Given array X, compute the DFT $$Y[k] = \sum_{j=0}^{N-1} X[k] * w^{jk}_{n}\tag{1}$$
where $$w^{jk}_{N} = cis(\frac{2\pi jk}{N}) = e^{\frac{2\pi jki}{N}}\tag{2}$$
 FFT => Compute DFT in $O(NlogN)$

Cooley-Tukey: Split (1) into smaller DFTs
$t = 0,1,2,...$

$$Y[k] = \sum_{t=0}^{N-1} X[2t] e^{\frac{2\pi 2tki}{N}} + \sum_{t=0}^{N-1} X[2t+1] e^{\frac{2\pi (2t+1)ki}{N}}$$
$$Y[k] = \sum_{t=0}^{N-1} X[2t] e^{\frac{2\pi tk}{N/2}} + e^{\frac{2\pi ki}{N/2}}\sum_{t=0}^{N-1} X[2t+1] e^{\frac{2\pi (t)k}{N/2}}$$
$$FFT_{N} = FFT^{even}_{N/2} + CTE * FFT^{odd}_{N/2}$$
Radix-2 split

Can be done with other factors, composite N, $N = N_{1}N_{2}$ we can compute N2 FFT's of size N1

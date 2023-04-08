
Dada uma mensagem, $(n,e)$ é a chave pública e $d$ a chave privada

$n$ precisa ser um número tal que $n = pq$ , p e q primos grandes
de modo que criptografar uma mensagem é fazer 

b : bloco
$C(b) = b^e$ mod n

Para descriptografar
$D(b) = b^{ed}$ mod n
d sendo inverso mult de e modulo $\phi(n)$
assim, $ed = 1 + k\phi(n)$
$D(b) =b.b^{k\phi(n)}$
por euler-fermat
$D(b) = b.1$

### CRT

Dada um sistema linear de equações modulares de k primos entre si (i.e. $gcd(n_{i}, n_{j})$), a solução do sistema é determinada e tem fórmula fechada

Ex:

$x = 2$ mod 11
$x = 4$ mod 12
$x = 5$ mod 13

$x = \sum_{j=1}^{k} a_jN_ju_j$ mod N
$N = \prod_{j=1}^{k} n_j$
onde $N_j = N/u_j$ e $u_j = N_j^{-1}$ mod $n_j$

### Uso
alguns sistemas existem (como escolher o N, o e), e usamos o CRT pra resolver

#### Elgamal
Literalmente resolver discrete log
$y = g^x$ mod p
publica [y, g, p]

o cara vai te dar 2 contas escolhendo um k positivo menor que p-2
onde $m$ é a mensagem
$b = my^k$
$a = g^k$

Dai pra decifrar basta fazer $\frac{b}{a^x}$

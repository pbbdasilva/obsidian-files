
### Cifra de Cesar
transpor todas as letras do alfabeto de um valor cte

### Transposicao vs Substituicao
transposicao => gera difusao => permutar as letras, gerar anagramas (dissipa a estrutura estatística da mensagem)
substituicao => gera confusao => o texto é substituido por novos simbolos mas a ordem é mantida (torna a relação entre a mensagem e o criptograma complexas)

### Cifra de Vigenere
![[Pasted image 20230312103310.png]]

Varias chaves (offsets)
$f_i(a) = a + K_i$ mod n

### Criptografia Chave Pública
![[Pasted image 20230312104329.png]]

### Teste de kasiski
- Descobrir o comprimento da chave
Analisar distancia entre simbolos iguais
Se S ocorreu nas posicoes x e x+d, d divide o comprimento da chave

### Teste de Fridman
- Determinar a probabilidade de um criptograma ter sido gerado por um processo mono ou polialfabético
	Índice de Coincidência := $\frac{1}{N(N-1)} * \sum_{i=1}^{n} F_i(F_i - 1)$
onde Fi é a ocorrência do i-ésimo símbolo de um alfabeto de n símbolos e N é a quantidade de símbolos no texto.

Cada alfabeto possui um IC
nao entendi legal como usar


### Cifra de Hill
Converte letras em números, agrupa os números n a n e multiplica-se mod 26 cada bloco por uma matriz nxn invertível. Após isso, volta os números para letras.

O processo inverso é basicamente usar a matriz inversa


### Bayes
$P(x|y) = \frac{P(x)P(y|x)}{P(y)}$

### Sigilo Perfeito

- $Pr[Y = y] = \sum Pr[K = k] Pr[x = d_k(y)]$
- $Pr[Y = y | X = x] = \sum Pr[K = k]$
Usar Bayes para ter $Pr[X = x | Y = y]$

Um sistema de sigilo perfeito ocorre quando
$Pr[X = x | Y = y] = Pr[X = x]$ 

### Entropia
$H(X) = - \sum_{x \in X} Pr[x]\log_2(Pr[x])$
medida em bits,

### Entropia Condicional
$H(X | Y) = - \sum_{x \in X} \sum_{y \in Y} Pr[Y = y]Pr[X = x | Y = y]\log_2(Pr[X = x | Y = y])$

A entropia condicional mede a quantidade média de informações sobre X não
revelada por Y.
$H(X,Y) = H(X|Y) + H(Y)$

### Entropia condional da chave 
$H(K|C)$ é usada para mensurar a incerteza restante da chave dado que o texto cifrado é conhecido

$H(K|C) = H(K) + H(P) - H(C)$

### Coisas de Shannon
- Para uma dada linguagem, considerando todas as mensagens de length N
a taxa da linguagem $r = \frac{H(M)}{N}$ é a quantidade média de bits de informação por caractere

- A taxa absoluta da linguagem $R = \log2(L)$ com L sendo a quantidade de caracteres na linguagem.

- A redundância se dá por $D = R - r$

- A quantidade de textos cifrados necessários para um oponente decifrar a chave é $\frac{H(K)}{D}$


![[Pasted image 20230312235742.png]]








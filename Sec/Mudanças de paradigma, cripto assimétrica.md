### Ideia inicial

Encontrar duas funções $f_{k1}$ e $f_{k2}$ comutáveis

de forma que:
$$f_{k2}(f_{k1}(x)) = f_{k1}(f_{k2}(x)) \tag{1}$$

isso é util pois:

- A encripta $m$ e envia
- B recepe $f_{1}(m)$
- B envia $f_{2}(f_{1}(m))$
- A desencripta usando $f_{1}^{-1}(m)$
fazendo $f_{1}^{-1}(f_{2}(f_{1}(m))) = f_{1}^{-1}(f_{1}(f_{2}(m))) = f_{2}(m)$
- Assim B pode desencriptar e receber $m$

#### Chave pública

![[Pasted image 20230227085413.png]]


### Diffie Hellman Algorithm
Mascarar problema da sequencia supercrescente em mochila

### Discrete log
resolver problema $y^x = p$ mod N
encontrar x que atenda equação


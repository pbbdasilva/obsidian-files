
Difusão => Permutação das letras (variação da posição)
Substituição => Substitui os símbolos


ECB -> cifra os caras em blocos, mas tem o problema de cifras blocos iguais acaba por não cifrar de fato a msg

![[Pasted image 20230223103559.png]]

CBC -> utiliza da cifra anterior para usar como chave para cifrar os blocos, resolvendo o problema anterior, contudo, isso traz uma dependência de dados nas cifras, dificultando a velocidade da encriptação

![[Pasted image 20230223103813.png]]

CTR -> um método parecido com CBC mas que permite paralelismo

Cifra de Feistel -> Utiliza o mesmo algoritmo para cifrar de decifrar a mensagem


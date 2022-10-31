# Flip Flops🩴?

## 1. Visão geral 

Flip flop é um componente usado para armazenar um bit de dado e um circuito de flip flops é responsável por armazenar vários bits (conjuntos de 0 e 1) nos nossos dispositivos. Então como você deve imaginar, esses dispositivos são usados em memórias e suas saídas podem mudar já que dependem de suas entradas. Para lembrar disso basta pensar em como você manda salvar informações no seu dispositivo, sua ação é parte da entrada e a saída seria os bits que foram armazenados. 

Podemos dizer então que os flip-flops seguem uma lógica sequencial na qual a sua saída futura depende das duas saídas anteriores + as suas entradas. 

> The term flip – flop is used as they can switch between the states under the influence of a control signal (clock or enable) i.e. they can ‘flip’ to one state and ‘flop’ back to other state.

## 2. Flip Flop JK

O Flip Flop JK veio para solucionar um problema do Flip Flop RS. Mas que problema era esse?
Para descobrir o problema, vamos primeiro ver um pouco do funcionamento do RS, que deu base ao JK.

### 2.1. Entendendo primeiro o flip flop RS 

<p align="center" width="100%">
  <img src="https://www.electronicshub.org/wp-content/uploads/2015/06/SR-flip-flop-symbol.jpg">
</p>

SET: Liga a saída Q -> 1, consequentemente ~Q -> 0</br>
RESET: Desliga a saída Q -> 0, consequentemente ~Q -> 1

Vamos analisar todas as combinações possíveis através da tabela-verdade? (Desconsiderando o clock por enquanto)<br>
Qa = Q anterior<br>
Qf = Q futuro 

| R | S | Qa | Qf| ~Qf|
| :-|:-:|:-:| :-:| :-:|
| 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 |Inválido| 
| 1 | 1 | 1 |Inválido| 

Podemos simplificar a tabela de modo que: 
| R | S | Q |
|:-:|:-:|:-:|
| 0 | 0 | Qa|
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 |nválido|

Note que:
<ul>
  <li>Quando R e S forem 0, nada é mandado pra saída Q, portanto ela permanecerá no seu estado anterior (Qa)</li>
  <li>Quando somente S for 1, ele mandará 1 para saída Q</li>
  <li>Quando somente R for 1, ele mandará 0 para saída Q</li>
  <li>No entanto, R e S não podem estar ligados ao mesmo tempo</li>
</ul>

Neste último caso, a opção é contraditória já que não tem como você ligar e desligar a saída ao mesmo tempo. Além disso, o flip flop RS não possui nenhum tipo de tratamento para essa possibilidade, é por esse motivo que o flip flop JK se faz presente.
Vamos ver isso mais a fundo de modo que a figura a seguir representa a lógica do RS através de portas lógicas já estudadas anteriormente: 

<p align="center" width="100%">
  <img src="https://www.estudegratis.com.br/images/questoes/a8cd88d3243adf244148.gif">
</p>

Pegue um papel e uma caneta, desenhe o circuito e faça o fluxo do circuito considerando que R e S são iguais a 1 (sim, os dois). (Faça isso com todas as possibilidades também, se possível.)
<ol>
  <li>S é 1, ao ser negado, valerá 0.</li>
  <li>0 e qualquer outra coisa vale 0 também. ao ser negado, a saída Q valerá 1</li>
  <li>R é 1, ao ser negado, valerá 0.</li>
  <li>0 e qualquer outra coisa vale 0 também. ao ser negado, a saída ~Q valerá 1</li>
</ol>

Entende como isso é contraditório? Q e ~Q deveriam apresentar valores opostos!

### 2.2. Agora sim o JK

A estrutura do JK é bem parecida com a do RS, sendo as 3 entradas respctivamente J, clock e K. Já as saídas não se diferem, sendo denominadas aqui de Q e ~Q.
<p align="center" width="100%">
  <img src="https://w7.pngwing.com/pngs/936/789/png-transparent-jk-flip-flop-digital-electronics-electronic-symbol-others-miscellaneous-angle-white-thumbnail.png">
</p>

Aqui o J funciona como o S (set) e o K como o R (reset). Desse modo J muda a saída para 1 e K para 0. Analise a tabela-verdade: 

| J | K | Q | ~Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | Qa| ~Qa| 
| 0 | 1 | 0 | 1 | 
| 1 | 0 | 1 | 0 |
| 1 | 1 |~Qa| Qa|

A tabela-verdade do RS e do JK são bem parecidas, no entanto, na última linha se nota um diferencial. Ao setar as entradas J e K para 1 ao mesmo tempo, as saídas ficará fazendo "trocas" e entrará no seu estado de comutação. Para entender como isso acontece, veremos o flip flop JK representado por portas NAND.

<p align="center" width="100&">
  <img src="https://ajpeletroinfo.com.br/wp-content/uploads/2020/01/flip-3.png">
</p>

Perceba que o JK são duas portas NAND acopladas em um flip-flop RS. Ainda não percebeu? <a href="https://prnt.sc/x6mG8FwyZz2P" target="_blank" rel="external">Veja aqui</a>

Vamos fazer a possibilidade de J=1 e K=1 para entender como é possível:
<ol>
  <li>Fazer o NAND entre J e CLK e ~Q => Q</li>
  <li>Fazer o NAND entre Q e ~Q = > 1</li>
  <li>Fazer o NAND entre K e CLK e Q => ~Q</li>
  <li>Fazer o NAND entre Q e ~Q => 1</li>
 </ol>
 
 Até o momento temos isso: <a href="https://prnt.sc/eJ07irffNO-4">Veja aqui</a>
 
 A partir disso, o ciclo irá se realimentar e as saídas com os resultados 1 irá fazer o <a href="https://prnt.sc/pVhuGPnNInUp">seguinte percurso</a>, portanto, 1 será uma das entradas dos NANDs. Desse modo:
 
 <ol>
  <li>Fazer NAND entre Q e 1 => Q</li>
  <li>Fazer NAND entre ~Q e 1 => ~Q</li>
 </ol>
 
 Desta forma, é possível compreender que não há contradição nesse tipo de flip-flop quando J e K são ambos 1.


### 2.3. E o clock? 🕓
O sinal de clock é composto por ondas quadradas de 0s e 1s sendo esses variados de forma rítmica. Quando essas ondas estão em 1, é indicado a possibilidade de troca de estado das saídas. 

A frequência indica quantas vezes em um determinado intervalo de tempo o circuito pode fazer uma troca, então quanto maior a frequência, maior a velocidade das trocas.
<p align="center" width="100%">
  <img src="https://th.bing.com/th/id/R.75a1fb268ccfe118b66cf3390fedb3e0?rik=NfU%2bL1fmJaRugg&riu=http%3a%2f%2fwiki.foz.ifpr.edu.br%2fwiki%2fimages%2fc%2fcb%2fPulsosClock.png&ehk=pNhb%2bGuETn%2b0EkcNUrXveL7a74T6Zo0qciC28bQWA4s%3d&risl=&pid=ImgRaw&r=0">
</p> 


## 3. Exemplo
Vamos fazer um breve exemplo de um contador de 3 até 1 para que você perceba a utilidade do flip flop JK. 

O primeiro passo para fazer isso seria se perguntar quantos bits são necessários para contar até 3. Para isso você pode pensar que o número 3 em binário é igual a 11 que por sua vez, possui dois dígitos. Outra possibilidade seria pensar que 2 elevado a 2 é igual a 4, ou seja, 4 possibilidades incluindo o zero, sendo elas 0, 1, 2 e 3. 

Sabendo disso, temos apenas as saídas pois sabemos que queremos contar de 1 até 3, mas como descobrimos as entradas a partir das saídas? 
Há uma tabela de auxílio para isso, mas vamos nos perguntar de onde ela veio. Veja:
| Q | Q+1 | J | K |
|:-:| :-: |:-:|:-:|
| 0 |  0  | 0 | X |
| 0 |  1  | 1 | X |
| 1 |  0  | X | 1 |
| 1 |  1  | X | 0 |

Por favor, não decore essa tabela mas aprenda a chegar nela. 
Veja que 0 (Q anterior = Q) deve continuar a ser 0 (Q futuro = Q+1), 0 deve passar a ser 1, 1 deve passar a ser 0 e 1 deve continuar a ser 1. Visto essas possibilidades de transição, vamos inserir as entradas, J e K com o auxílio da tabela-verdade do flip flop JK. 

0 -> 0 (basta observar nas linhas 1 e 2, o que elas tem em comum? J = 0)<br>
  <ol>
    <li>Olhe na coluna Q e veja as possibilidades de Q ser igual a 0</li>
    <li>Perceba que há 3 possibilidades, linha 1 e 2.</li>
    <li>A linha 4 será desconsiderada, pois o Qa = 0 e como ele deve ser negado, a saída de Q passará a ser 1.</li>
  </ol>
0 -> 1 (basta observar nas linhas 3 e 4, o que elas tem em comum? J = 1)<br>
1 -> 0 (basta observar nas linhas 2 e 4, o que elas tem em comum? K = 1)<br>
1 -> 1 (basta observar nas linhas 1 e 3, o que elas tem em comum? K = 0)<br>

| J | K | Q |  |
|:-:|:-:|:-:| :-: |
| 0 | 0 | Qa| -> Linha 1 |
| 0 | 1 | 0 | -> Linha 2 |
| 1 | 0 | 1 | -> Linha 3 |
| 1 | 1 |~Qa| -> Linha 4 |


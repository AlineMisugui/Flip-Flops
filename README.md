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

Vamos analisar todas as combinações possíveis através da tabela-verdade? (Desconsiderando o clock por enquanto)

| R | S | Q | ~Q|
| :-|:-:|:-:| :-:| 
| 0 | 0 | Qa| Qa| 
| 0 | 1 | 1 | 0 | 
| 1 | 0 | 0 | 1 |
| 1 | 1 |Inválido|Inválido|

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
| 0 | 1 | 1 | 0 | 
| 1 | 0 | 0 | 1 |
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

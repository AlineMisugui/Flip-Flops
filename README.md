# Flip Flops🩴?

## 1. Visão geral 

Flip flop é um componente usado para armazenar um bit de dado e um circuito de flip flops é responsável por armazenar vários bits (conjuntos de 0 e 1) nos nossos dispositivos. Então como você deve imaginar, esses dispositivos são usados em memórias e suas saídas podem mudar já que dependem de suas entradas. Para lembrar disso basta pensar em como você manda salvar informações no seu dispositivo, sua ação é parte da entrada e a saída seria os bits que foram armazenados. 

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


### 2.2. Agora sim o JK
aaa

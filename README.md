# Flip Flops🩴?

## 1. Visão geral 

Flip flop é um componente usado para armazenar um bit de dado e um circuito de flip flops é responsável por armazenar vários bits (conjuntos de 0 e 1) nos nossos dispositivos. Então como você deve imaginar, esses dispositivos são usados em memórias e suas saídas podem mudar já que dependem de suas entradas. Para lembrar disso basta pensar em como você manda salvar informações no seu dispositivo, sua ação é parte da entrada e a saída seria os bits que foram armazenados. 

> The term flip – flop is used as they can switch between the states under the influence of a control signal (clock or enable) i.e. they can ‘flip’ to one state and ‘flop’ back to other state.

## 2. Flip Flop JK

O Flip Flop JK veio para solucionar um problema do Flip Flop RS. Mas que problema era esse?

### 2.1. Pega a visão do RS 

<p align="center" width="100%">
  <img src="https://www.electronicshub.org/wp-content/uploads/2015/06/SR-flip-flop-symbol.jpg">
</p>

SET: Liga a saída Q -> 1, consequentemente ~Q -> 0</br>
RESET: Desliga a saída Q -> 0, consequentemente ~Q -> 1

Vamos analisar todas as combinações possíveis através da tabela-verdade? (Desconsiderando o clock por enquanto)


| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |

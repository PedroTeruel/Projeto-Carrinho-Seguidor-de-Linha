# Como Construir um Carrinho Seguidor de Linha: Guia Passo a Passo

## Introdução

Como um dos projetos mais clássicos para introdução a engenharia, a construção de um carrinho seguidor de linha: um robô autônomo capaz de detectar e seguir uma trilha no chão, permite aplicar conhecimentos teóricos de forma pratica, estimulando raciocínio logico e solução de problemas.

Este artigo apresenta um passo a passo completo para criar um projeto funcional de carrinho seguidor de linha, desde a construção do circuito eletrônico até a montagem mecânica do robô. O projeto foi construído por mim no 1º semestre da engenharia de computação do Senac São Paulo e aborda conhecimentos de eletrônica, soldagem, modelagem 3D, lógica de sensores e controle de motores.

O principal objetivo foi a construção de um carrinho seguidor de linha que funciona como um robô autônomo capaz de identificar e seguir uma trilha contínua através de sensores infravermelhos, interpretando os dados em tempo real para corrigir sua trajetória e manter o movimento sobre a trilha.

Veja nos vídeos dos links abaixo o funcionamento do carrinho que você irá aprender a construir nesse artigo:
- 🔗 [Vídeo 1 – Funcionamento do Carrinho](https://www.youtube.com/watch?v=o5KDZBv2Lis)
- 🔗 [Vídeo 2 – Detalhes do Circuito](https://www.youtube.com/shorts/yLg4nNAEKBg)

## Materiais Necessários
![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img2.png?raw=true)
## Circuito lógico
![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img3.png)

O circuito é composto por dois blocos simétricos, um para o controle do motor esquerdo e outro para o direito. Cada bloco utiliza um LED emissor infravermelho (D1/D4 – TIL32) e um fototransistor (D2/D5 – TIL78) para detectar a linha preta sobre o chão. O LED emite luz infravermelha constantemente, e o fototransistor detecta a luz refletida: superfícies claras refletem mais luz, e superfícies escuras (como a linha preta) refletem menos.

Quando o sensor (D2/D5) recebe a luz refletida, ele conduz corrente para a base do transistor NPN Q1/Q3 (BC547) por meio do resistor R2/R7 (10kΩ). Isso faz com que o transistor (Q1/Q3) conduza, permitindo que sua saída vá para o GND. Essa saída está conectada à base do segundo transistor, um PNP TIP127 (Q2/Q4), por meio de R3/R8 (4k7Ω). Quando a base do TIP127 é puxada para o GND, ele conduz, ligando o motor M1/M2 e acendendo o LED indicador D7/D8, indicando que o motor está em funcionamento.

O resistor R1/R6 (330Ω) está em série com o LED emissor (D1/D4) para limitar a corrente, enquanto R5/R10 (330Ω) protege os LEDs indicadores (D7/D8). Os diodos D3/D6 (1N4001) são colocados em paralelo com os motores para proteger o circuito de picos de tensão.

Por fim, os capacitores C1 (220µF) e C2 (100nF), ligados à alimentação vinda da bateria de 6V (BT1), são usados para estabilizar a tensão, filtrando ruídos e evitando oscilações no funcionamento do circuito. 

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img4.png)

Esse circuito, gerará a placa abaixo, que será construída no decorrer desse projeto.

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img5.png)
![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img6.png)

Convenção comum em PCBs: 
  Ilha quadrada → Positivo (+) 
  Ilha circular → Negativo (–)

## Etapas do Projeto
###   1. Desenvolvimento da placa de circuito
1- Na placa de cobre, desenhe as trilhas com base no circuito logico utilizando um lápis para esboço, depois passe a caneta permanente. Lembre-se de desenhar as ilhas de solda grandes o suficiente para os furos dos componentes.

2- Corte a placa no tamanho adequado e realizamos os furos para as ilhas de solda.

3- Mergulhe a placa no percloreto de ferro por 30 minutos, até que o cobre excedente seja corroído.

4- Após a corrosão, lave a placa com água para remover o excesso de percloreto, limpe a tinta da caneta com álcool e utilize borracha para finalizar a limpeza.

Obs: Descarte o percloreto usado em local apropriado. Nunca jogue na pia.

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img7.png)

### 2. Perfuração e Soldagem dos Componentes

Fure a placa nos pontos adequados usando uma furadeira ou ferramenta manual e solde os componentes na seguinte ordem:

1- Resistores e capacitores (R1-R10 e C1-C2)

2- Diodos e transistores (D3, D6 e Q1-Q4)

3- Sensores TIL32 e TIL78 (D1, D2 e D4, D5) (**Obs: Os Sensores devem ser soldados no lado das trilhas da placa, pois eles que identificarão a linha a ser seguida) (Não solde os sensores colados na 4- plaquinha, deixe uma sobra na perna para ajustes futuros**)4

5- LEDs (D7-D8)

6- Motores e suporte de pilhas (BT1, M1 e M2)

7- **Os fios são ligados da seguinte maneira: Os fios que saem de M1 da placa ligam direto no motor, e o mesmo vale para M2. Para BT1, o fio que sai do positivo liga no interruptor, e o fio que sai do negativo liga direto na bateria. Para finalizar, o positivo da bateria liga no outro ponto do interruptor.**

Obs: Certifique-se de que os motores estejam girando para o lado certo (com as ligações apontando para dentro).

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img8.png)
![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img9.png)
![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img10.png)

### 3. Construção do Chassi

O chassi do carrinho foi construído com base no modelo 3D utilizando o SolidWorks. Em uma placa de MDF, foi cortado e furado a laser para maior precisão, porém, é possível construí-lo manualmente ou utilizando uma impressora 3D.

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img11.png)

### 4. Montagem

-Fixe os motores DC com rodas nas laterais do chassi, deixando espaço entre eles para a placa de circuito.

-Na parte inferior dianteira, coloque o circuito, com os sensores infravermelhos voltados para o chão.

-Conecte o suporte de pilhas e a chave liga/desliga de forma acessível.

-Prenda tudo com parafusos ou cola quente, conforme o material do chassi.

![Clique para ver o vídeo do circuito](https://github.com/PedroTeruel/Projeto-Carrinho-Seguidor-de-Linha/blob/main/Imagens/img12.png)

## Funcionamento e lógica de controle

O carrinho funciona de maneira autônoma, sem a necessidade de um microcontrolador simulando aplicações reais da automação. No circuito, o LED infravermelho emite sinal constantemente, enquanto o fototransistor detecta a reflexão da superfície. Quando o carrinho passa por uma linha preta, o fototransistor não recebe o sinal pois ele não é refletido de volta, assim, essa variação de sinal controla os transistores que ligam ou desligam os motores.

-Se o sensor esquerdo não recebe o sinal → motor esquerdo é desativado → o carrinho vira para a esquerda.

-Se o sensor direito não recebe o sinal→ motor direito é ativado → o carrinho vira para a direita.

-Se ambos detectam branco → ambos os motores funcionam → o carrinho segue reto.

## Testes e ajustes

Os ajustes são essenciais para o bom funcionamento do carrinho, principalmente nos sensores.   Caso o carrinho não esteja detectando uma curva, é necessário regular a altura dos sensores para melhor leitura. Além disso, os sensores devem estar em “V” para que o sinal retorne para o receptor, dessa forma é preciso regular até achar a posição ideal dos sensores.

Caso o carrinho esteja muito rápido, é necessário ajustar a velocidade para que o carrinho passe mais devagar na curva e os sensores possam detectar e desligar o motor a tempo. A velocidade pode ser reduzida utilizando pilhas menos carregadas, alterando as resistências, ou retirando uma das pilhas e fechando o circuito da caixa de bateria.

## Pontos de Atenção Observados

-Em curvas muito fechadas, o carrinho tem dificuldade de se manter na linha, devido ao espaçamento entre os sensores.

-É necessário ajustar a altura dos sensores para melhorar a sensibilidade na detecção da linha.

-A potência dos motores tem impacto direto na estabilidade: velocidades mais altas dificultaram o controle do carrinho.

## Conclusão

A construção do carrinho seguidor de linha é uma boa introdução à engenharia e automação. Com esse projeto é possível aprender conceitos fundamentais como sensores, transistores, controle de motores e montagem de circuitos. Além disso, estimula habilidades manuais e de resolução de problemas. Esse artigo mostra que, com dedicação, mesmo utilizando materiais simples e de baixo custo, é possível desenvolver um robô funcional, que exemplifica de forma clara o funcionamento de sistemas autônomos no mundo real.

## LinkedIn

Você pode acessar informações sobre esse projeto no meu linkedin clicando nesse link 

- [Como Construir um Carrinho Seguidor de Linha – Guia Passo a Passo (LinkedIn)](https://www.linkedin.com/pulse/como-construir-um-carrinho-seguidor-de-linha-guia-passo-teruel-rvckc)



## ELA I: Circuito de Teclado Musical com Transistores

Este projeto detalha a construção de um teclado musical de duas oitavas, concebido como parte da disciplina de Eletrônica Analógica Experimental 1. O circuito é composto por três estágios principais: um oscilador de relaxação, um amplificador de pequenos sinais e um amplificador de potência classe B em configuração push-pull.

### Etapas do Circuito

1.  **Oscilador de Relaxação:**
    O coração do teclado é um oscilador de relaxação que utiliza um transistor de unijunção (UTJ). A função deste estágio é gerar um sinal periódico (onda dente de serra) cuja frequência é determinada pela carga e descarga de um capacitor através de um resistor. A frequência do sinal, que corresponde às notas musicais, pode ser ajustada e é calculada teoricamente pela equação:

    $f_o \approx \frac{1.218}{RC}$

    Para a montagem, foi utilizado o transistor JFET modelo 2N2646.

2.  **Amplificador de Pequenos Sinais:**
    O sinal gerado pelo oscilador é então enviado para um amplificador de pequenos sinais. Este estágio emprega um transistor bipolar de junção (TBJ) com polarização por divisor de tensão. Sua finalidade é aumentar a tensão do sinal de entrada para que ele possa excitar o próximo estágio de forma adequada.

3.  **Amplificador de Potência (Push-Pull):**
    A etapa final consiste em um amplificador classe B, responsável por fornecer a corrente necessária para alimentar um alto-falante. Este amplificador é montado em uma configuração *push-pull*, com dois transistores (Q1 e Q2) que operam em seções simétricas para amplificar as partes positiva e negativa da onda do sinal de forma separada. Quando a tensão de entrada é positiva, o transistor Q1 conduz, enquanto o Q2 permanece em corte, e o inverso ocorre para tensões de entrada negativas. Os transistores utilizados nesta etapa são o BC337 (Q1) e o BC327 (Q2).

### Componentes Utilizados

| Estágio | Componente | Valor/Modelo |
| :--- | :--- | :--- |
| **Oscilador** | Transistor | JFET 2N2646 |
| | Capacitor (C) | 100 nF |
| | Resistores (RB1, RB2) | 1000 Ω, 100 Ω |
| **Amplificador de Pequenos Sinais** | Resistor (R1) | 5.6 kΩ |
| | Resistor (R2) | 1500 Ω |
| | Resistor (RC) | 330 Ω |
| | Resistor (RE) | 100 Ω |
| | Capacitor (C1) | 10 µF |
| | Capacitor (CE) | 10 µF |
| **Amplificador Push-Pull** | Transistor (Q1) | BC337 |
| | Transistor (Q2) | BC327 |
| | Diodos | IN4148 |
| | Resistor (R) | 4.7 kΩ |
| | Capacitor (CC) | 10 µF |

### Desenvolvimento da PCB e Montagem

Os esquemas elétricos e o layout da placa de circuito impresso (PCI) foram desenvolvidos com o software KiCad. A PCI foi confeccionada pelo método de termotransferência e corrosão com percloreto de ferro. A estrutura física do teclado, incluindo a *case* e as teclas, foi modelada em 3D com o software Tinkercad e impressa em uma impressora 3D. A alimentação do circuito é de 5V, podendo ser fornecida por um *power bank* ou uma fonte DC.

<div>
  align="center"

<img src="https://github.com/user-attachments/assets/edd3df49-5a7d-437c-b2a0-a598a5d566ce"
     alt="image"
     style="width:70%; height:auto;" />

![SDLAKS](https://github.com/user-attachments/assets/8946a344-4def-4d9c-b5c6-ba1beb4de862)
</div>

---

## ELA II: Amplificador Somador de Áudio com Reforçador de Corrente

Este projeto detalha a construção de um circuito eletrônico para mixagem e amplificação de dois canais de áudio (direito e esquerdo). O sistema utiliza um amplificador operacional na configuração de somador, seguido por um estágio reforçador de corrente para alimentar um alto-falante.

### Etapas do Circuito

1.  **Estágio de Entrada e Mixagem (Amplificador Somador):**
    O coração do circuito é o amplificador operacional NE5532 (U1), configurado como um amplificador somador inversor. Os sinais de áudio dos canais esquerdo (S) e direito (R), provenientes de um adaptador Bluetooth (J5), passam por capacitores de acoplamento (C3 e C4) para remover qualquer componente DC. Em seguida, os sinais são combinados nos resistores R1 e R2 e aplicados à entrada inversora (pino 2) do amplificador operacional. O resistor de feedback R3, em conjunto com R1 e R2, define o ganho de tensão do estágio. A entrada não-inversora (pino 3) é aterrada.

2.  **Estágio de Saída (Reforçador de Corrente Push-Pull):**
    O sinal amplificado na saída do NE5532 (pino 6) é enviado para um estágio de reforço de corrente. Este estágio utiliza um par de transistores de junção bipolar (BJT) em uma configuração *push-pull* classe B, composta por um transistor NPN (Q1) e um PNP (Q2). A função desta etapa é fornecer a corrente necessária para alimentar uma carga de baixa impedância, como o alto-falante (J3), sem sobrecarregar a saída do amplificador operacional. O transistor NPN amplifica o semiciclo positivo do sinal, enquanto o transistor PNP amplifica o semiciclo negativo.

3.  **Fonte de Alimentação:**
    O circuito é alimentado por uma fonte de +5V, conectada através de uma porta USB_A (J4). Essa tensão de entrada (+VCC) é então estabilizada pelo regulador de tensão U3. Os capacitores C1 e C2 são utilizados para filtrar ruídos na entrada e na saída do regulador, garantindo uma tensão de +5V estável para o circuito. As tensões de alimentação simétricas de +15V e -15V, indicadas no esquemático para alimentar o amplificador operacional, são representativas do modo de operação ideal do componente, mas o funcionamento prático do circuito depende da fonte conectada.

### Componentes Principais

| Componente | Referência | Função |
| :--- | :--- | :--- |
| Amplificador Operacional | U1 (NE5532) | Somar e amplificar os sinais de áudio de entrada. |
| Transistor NPN | Q1 | Amplificar o semiciclo positivo do sinal de áudio. |
| Transistor PNP | Q2 | Amplificar o semiciclo negativo do sinal de áudio. |
| Regulador de Tensão | U3 | Estabilizar a tensão de alimentação em +5V. |
| Conector de Entrada | J5 | Interface para o adaptador Bluetooth. |
| Conector de Saída | J3 | Conexão para o alto-falante. |
| Conector de Alimentação | J4 (USB_A) | Ponto de entrada da alimentação de +5V. |
| Resistores | R1, R2 (10kΩ) | Resistores de entrada do somador. |
| Resistor | R3 (10kΩ) | Resistor de feedback, define o ganho. |
| Capacitores | C3, C4 (10µF) | Capacitores de acoplamento para os canais de áudio. |
| Capacitores | C1, C2 (100µF) | Capacitores de filtro para o regulador de tensão. |


<img src="https://github.com/user-attachments/assets/1e7293e1-5c7d-4e56-b1ab-3feed9f472a0"
     alt="image"
     style="width:40%; height:auto;" />

# Cálculo Numérico 
# Método da Bissecção: Cálculo de Resistência em Circuito RLC 

Este projeto implementa um algoritmo numérico em Python para solucionar um problema de engenharia elétrica referente a circuitos RLC transientes. O objetivo é determinar o valor exato de um resistor ($R$) necessário para dissipar uma carga específica em um determinado tempo, utilizando o **Método da Bissecção**.

## 📄 Descrição do Problema

O problema baseia-se no comportamento transiente de um circuito contendo um Resistor, um Indutor e um Capacitor (RLC) após o fechamento de uma chave. A variação da carga no capacitor em função do tempo é descrita pela seguinte equação diferencial linear de segunda ordem:

$$q(t) = q_{0}e^{-Rt/(2L)}\cos\left[\left(\sqrt{\frac{1}{LC}-\left(\frac{R}{2L}\right)^{2}}\right)\cdot t\right]$$

Onde:
* **$q(t)$**: Carga no tempo $t$.
* **$q_0$**: Carga inicial ($V_0C$).
* **$R$**: Resistência (a variável desconhecida).
* **$L$**: Indutância.
* **$C$**: Capacitância.

### Parâmetros do Projeto
O objetivo é encontrar o valor de **$R$** tal que a carga seja dissipada para **1% do seu valor original** ($q/q_0 = 0.01$) no tempo $t = 0.05s$.

Os valores utilizados na simulação são:
* **Indutância ($L$):** $5$ H
* **Capacitância ($C$):** $10^{-4}$ F
* **Tempo alvo ($t$):** $0.05$ s
* **Razão alvo ($q/q_0$):** $0.01$

---

## 🧮 Metodologia Numérica

Para encontrar o valor de $R$, o problema foi modelado como uma busca de raízes (zeros) de uma função não linear $f(R) = 0$.

Utilizou-se o **Método da Bissecção** devido à sua robustez e garantia de convergência para funções contínuas em intervalos com troca de sinal. O método de Newton-Raphson foi descartado neste contexto devido à complexidade algébrica de derivar a equação de carga em relação a $R$.

### Definição da Função $f(R)$
Para aplicar o método numérico, a equação original foi manipulada para a forma $f(R) = 0$:

$$f(R) = \left( e^{-Rt/(2L)}\cos\left[\left(\sqrt{\frac{1}{LC}-\left(\frac{R}{2L}\right)^{2}}\right)\cdot t\right] \right) - 0.01$$

### Critérios de Parada
O algoritmo encerra a busca quando uma das seguintes condições é atendida:
1.  **Tolerância do Intervalo:** O erro estimado `(b - a) / 2` é menor que a tolerância definida.
2.  **Raiz Exata:** O valor de $f(R)$ é exatamente $0$.

---

## 🚀 Como Executar

### Pré-requisitos
* Python 3.x
* Biblioteca padrão `math` (não é necessária instalação externa).

### Passos
1.  Clone este repositório:
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    ```
2.  Navegue até a pasta do projeto e execute o script:
    ```bash
    python main.py
    ```
3.  O terminal exibirá o progresso das iterações, mostrando o estreitamento do intervalo até a convergência final.

---

## 🔍 Exemplo de Saída

```text
Iniciando Metodo da Bissecção para o circuito RLC
=========================================
Iteração 1
Intervalo R: [0.000000, 400.000000]
Ponto Médio (R): 200.000000
...
--- RESULTADO FINAL ---
O valor do resistor R é: 328.XXXXXX Ohms
Valor da função na raiz: 0.000XXX

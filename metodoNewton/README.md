Video sobre o método: https://www.youtube.com/watch?v=l5NE-2k8T8Y

## Método de Newton-Raphson: Fundamentação e Implementação

O Método de Newton-Raphson é uma técnica iterativa de **método aberto** utilizada para encontrar aproximações das raízes (ou zeros) de uma função real ($f(x) = 0$). É reconhecido por sua **convergência quadrática**, o que o torna um dos métodos mais rápidos na área de cálculo numérico, desde que o chute inicial seja bem escolhido.

---

### 1. Princípio Geométrico: A Reta Tangente

A base do método reside na geometria:
1.  Começamos com um chute inicial ($x_i$).
2.  No ponto $(x_i, f(x_i))$, traçamos a **reta tangente** à curva da função.
3.  O próximo palpite, $x_{i+1}$, é o ponto onde essa reta tangente intercepta o eixo horizontal ($X$).



[Image of Newton-Raphson method geometric interpretation showing tangent line approximation]


Essa aproximação linear (a reta tangente) nos guia rapidamente para a raiz.

---

### 2. Fórmula de Iteração

A fórmula é derivada da definição de inclinação ($f'(x)$), que é a derivada da função no ponto $x_i$.

A fórmula para calcular o próximo ponto é:

$$x_{i+1} = x_i - \frac{f(x_i)}{f'(x_i)}$$

O termo $\frac{f(x_i)}{f'(x_i)}$ representa o **ajuste horizontal** necessário para mover-se de $x_i$ para $x_{i+1}$.

---

### 3. Estrutura do Código

O código implementado busca a raiz da função **$f(x) = x^2 - 2$** (cuja raiz positiva é $\sqrt{2}$).

#### a. Funções Requeridas

O Método de Newton-Raphson exige duas funções para serem definidas:
* **`f(x)`:** A função original, $x^2 - 2$.
* **`df(x)`:** A derivada da função, $2x$.

#### b. Critério de Parada (Convergência)

O loop se encerra quando a **diferença absoluta** entre o novo e o antigo valor de $x$ for menor que a tolerância definida (`tolerancia`).

O critério de parada implementado é:

```python
if abs(x_novo - x_atual) < tolerancia:
    return x_novo

```

Isso garante que a mudança na estimativa (o erro estimado) seja menor que o erro máximo permitido, confirmando a convergência.

### Considerações Importantes

- Chute Inicial (x_0): O sucesso do Método de Newton-Raphson depende de um bom chute inicial. Um chute ruim pode levar à divergência ou à convergência para uma raiz diferente da desejada.
- Derivada Zero: Se em algum ponto f′(x_i)=0, o método falha, pois a reta tangente é horizontal e não cruza o eixo X.
- Vantagem: Sua convergência quadrática significa que o número de dígitos corretos na raiz se duplica aproximadamente a cada iteração, tornando-o extremamente eficiente.

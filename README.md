# 📚 Métodos Numéricos Essenciais (Bissecção & Newton-Raphson)

Este repositório contém a implementação em Python de dois algoritmos fundamentais de Cálculo Numérico utilizados para encontrar as raízes (zeros) de funções: o Método da Bissecção e o Método de Newton-Raphson.

---

## Estrutura do Repositório

O conteúdo deste repositório está organizado em duas pastas principais, cada uma dedicada a um método específico e contendo seus respectivos arquivos de código (`.py`) e documentação (como exemplos de uso ou relatórios):

| Pasta | Conteúdo Principal |
| :--- | :--- |
| **`01-Metodo_Bisseccao`** | Implementação do método de Bissecção. |
| **`02-Metodo_Newton_Raphson`** | Implementação do método de Newton-Raphson. |

---

## Métodos Implementados (Breve Resumo)

### 1. Método da Bissecção

O Método da Bissecção é um **método fechado** que garante a convergência, desde que a raiz esteja cercada por um intervalo inicial $[a, b]$ onde a função $f(x)$ troca de sinal (Teorema de Bolzano).

* **Princípio:** Reduz o intervalo de busca pela metade a cada iteração, garantindo que o erro máximo diminua linearmente.
* **Vantagem:** Extrema robustez e garantia de sucesso.
* **Desvantagem:** Lento.

### 2. Método de Newton-Raphson

O Método de Newton-Raphson é um **método aberto** que utiliza a derivada ($f'(x)$) para determinar a inclinação da reta tangente em um ponto, mirando diretamente na raiz.

* **Princípio:** Usa a reta tangente para iterar o chute $x_{i+1} = x_i - \frac{f(x_i)}{f'(x_i)}$.
* **Vantagem:** Convergência quadrática (extremamente rápido, se convergente).
* **Desvantagem:** Requer o cálculo da derivada e pode divergir se o chute inicial for ruim.

---

## Requisitos de Execução

Os algoritmos são implementados puramente em Python 3 e utilizam apenas bibliotecas padrão, como `math` (quando necessário para funções complexas).

**Autor:** [George Henrique]

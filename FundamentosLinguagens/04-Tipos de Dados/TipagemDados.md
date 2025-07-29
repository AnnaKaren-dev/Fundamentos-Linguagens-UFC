# Comparação de Tipagem: Python, C e JavaScript

As linguagens de programação lidam com tipos de dados de formas diferentes. Essa diferença afeta diretamente a forma como declaramos, usamos e manipulamos variáveis.

comparação Python, C e JavaScript em tre̊s aspectos:
-Tipagem dinâmica x estática
-Tipagem fraca x forte
-Declaração de variáveis com tipos

---

## Python – Tipagem Dinâmica e Forte

- **Dinâmica**: o tipo é determinado em tempo de execução.
- **Forte**: não permite operações inválidas entre tipos.

```python
# Python infere o tipo da variável automaticamente
x = 10         # x é um inteiro
x = "dez"      # agora x é uma string

# Tipagem forte: erro ao somar inteiro com string
y = 5 + "2"     # TypeError: unsupported operand type(s)
```

**Observação**:

- Não precisa declarar tipos.
- Trocar o tipo da variável é permitido.
- Tipagem forte evita combinações sem sentido, como somar número e string.

## C – Tipagem Estática e Forte

- **Estática**: tipos definidos em tempo de compilação.
- **Forte**: erros de tipo são detectados na compilação.

```c
#include <stdio.h>

int main() {
    int x = 10;      // tipo fixo: inteiro
    x = "dez";       // Erro: tipo inválido

    int y = 5 + 2;    // ok
    char* z = "teste";
    // printf("%d\n", y + z); // Erro: soma inválida entre int e ponteiro

    return 0;
}
```

**Observação**:

- Deve declarar o tipo da variável.
- O tipo não pode mudar depois.
- Compilador verifica tipos antes de executar.

## JavaScript – Tipagem Dinâmica e Fraca

- **Dinâmica**: tipo é definido em tempo de execução.
- **Fraca**: converte tipos automaticamente (coerção implícita).

```javascript
let x = 10; // x é number
x = "dez"; // agora x é string

let y = 5 + "2"; // Resultado: "52" (number + string → string)

let z = "5" - 1; // Resultado: 4 (string → number automaticamente)
```

**Observação**:

- Pode mudar o tipo da variável a qualquer momento.
- Permite misturar tipos com conversão automática.
- Pode causar erros sutis e comportamentos inesperados.

---

## Tabela Comparativa

| Linguagem  | Tipagem          | Declaração Tipo | Conversão Implícita | Segurança  |
| ---------- | ---------------- | --------------- | ------------------- | ---------- |
| Python     | Dinâmica + Forte | Não obrigatória | Não                 | Alta       |
| C          | Estática + Forte | Obrigatória     | Não                 | Muito alta |
| JavaScript | Dinâmica + Fraca | Não obrigatória | Sim                 | Baixa      |

---

## Conclusão

- **Python**: seguro e flexível, mas erros de tipo só aparecem em tempo de execução.
- **C**: rigoroso e eficiente, ideal para controle de memória e desempenho.
- **JavaScript**: flexível, mas propenso a erros silenciosos por conversões implícitas.

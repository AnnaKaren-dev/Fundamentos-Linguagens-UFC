# Exemplo Recursivo de uma Pilha

## Objetivo

Demonstrar o funcionamento da recursão utilizando como exemplo a soma dos `n` primeiros números naturais com base na pilha de chamadas da função.

## Lógica Recursiva

A função recursiva `sumNaturals(n)` soma todos os números de `n` até `0`, utilizando o conceito de recursão com um **caso base** bem definido.

### Código-fonte

```python

def sumNaturals(n):
    if n == 0:
        return 0
    else:
        return n + sumNaturals(n - 1)

print(sumNaturals(4))

```

## Etapas da Recursão

Durante a chamada de `sumNaturals(4)`, a função realiza as seguintes chamadas recursivas:

- `sumNaturals(4)` chama `sumNaturals(3)`
- `sumNaturals(3)` chama `sumNaturals(2)`
- `sumNaturals(2)` chama `sumNaturals(1)`
- `sumNaturals(1)` chama `sumNaturals(0)`
- `sumNaturals(0)` retorna `0` → caso base

### Retorno das chamadas

- `sumNaturals(1)` retorna `1 + 0 = 1`
- `sumNaturals(2)` retorna `2 + 1 = 3`
- `sumNaturals(3)` retorna `3 + 3 = 6`
- `sumNaturals(4)` retorna `4 + 6 = 10`

---

## Representação da Pilha de Chamadas

Durante a execução, as chamadas são empilhadas até o caso base, como representado abaixo:

```
Topo da pilha
-----------------------
sumNaturals(4)
-----------------------
sumNaturals(3)
-----------------------
sumNaturals(2)
-----------------------
sumNaturals(1)
-----------------------
sumNaturals(0)
-----------------------
Base da pilha
```

Conforme o retorno ocorre, a pilha é desempilhada.

---

## Conclusão

- Este exemplo evidencia o funcionamento da recursão com clareza:
- Cada chamada recursiva é empilhada até o caso base.
- A pilha de chamadas armazena o estado anterior de cada execução.
- O retorno ocorre em ordem reversa, utilizando os valores retornados para compor o resultado final.
- A função `sumNaturals(4)` retorna corretamente `10`, somando `4 + 3 + 2 + 1 + 0`.

# Programação Funcional em Python: Recursão e Funções de Alta Ordem

## Exemplo: Soma dos fatoriais dos números pares de uma lista

```python
from functools import reduce

# Função recursiva para calcular o fatorial
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n-1)

# Lista de números de exemplo
numbers = [1, 2, 3, 4, 5, 6]

# Filtra apenas os números pares (função de alta ordem: filter)
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Calcula o fatorial de cada número par (função de alta ordem: map)
factorials = list(map(factorial, evens))

# Soma todos os fatoriais (função de alta ordem: reduce)
sum_factorials = reduce(lambda x, y: x + y, factorials)

print("Números pares:", evens)
print("Fatoriais dos pares:", factorials)
print("Soma dos fatoriais dos pares:", sum_factorials)
```

**Explicação:**
- `factorial(n)`: função recursiva para calcular o fatorial de um número.
- `filter`: seleciona apenas os números pares da lista.
- `map`: aplica a função fatorial a cada número par.
- `reduce`: soma todos os fatoriais calculados.
# Passagem de Parâmetros: Por Valor e Por Referência (C e Python)

Neste documento, apresenta a diferença entre a **passagem de parâmetros por valor** e **por referência**, com exemplos em **C** e **Python**.

---

## Definição

- **Passagem por valor**: a função recebe **uma cópia** do valor original. Alterações não afetam o valor fora da função.
- **Passagem por referência**: a função recebe **o próprio endereço/memória** do valor. Alterações afetam o valor original.

---

## Em C

### Passagem por Valor

```c
#include <stdio.h>

void doubleValue(int x) {
    x = x * 2;  // Modifica apenas a cópia local
}

int main() {
    int number = 10;
    doubleValue(number);
    printf("Número após função: %d\n", number); // Saída: 10
    return 0;
}
```

###  Passagem por Referência (com ponteiros)

```c
#include <stdio.h>

void doubleValue(int *x) {
    *x = (*x) * 2;  // Modifica o valor original usando ponteiro
}

int main() {
    int number = 10;
    doubleValue(&number);
    printf("Número após função: %d\n", number); // Saída: 20
    return 0;
}
```

---

##  Em Python

Python não permite passagem por referência pura, mas objetos mutáveis (como listas, dicionários) se comportam como se fosse por referência.

###  Passagem por Valor (imutável)

```python
def doubleValue(x):
    x = x * 2  # Modifica a cópia local

number = 10
doubleValue(number)
print("Número após função:", number)  # Saída: 10
```

### ▶️ "Passagem por Referência" com lista (mutável)

```python
def doubleElement(lista):
    lista[0] = lista[0] * 2  # Modifica a lista original

values = [10, 20, 30]
doubleElement(values)
print("Lista após função:", values)  # Saída: [20, 20, 30]
```

---

##  Comparativo

| Linguagem | Valor (imutável)      | Referência (mutável ou ponteiro)  |
| --------- | --------------------- | --------------------------------- |
| C         | Inteiros, floats etc. | Ponteiros (`int*`, `float*` etc.) |
| Python    | `int`, `str`, `float` | `list`, `dict`, `set`, objetos    |

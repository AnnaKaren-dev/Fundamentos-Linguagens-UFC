# Programa com Estruturas de Controle em Python

Este documento apresenta um programa simples em Python que utiliza:

- **Estrutura de seleção**: `if`, `elif`, `else`
- **Estrutura de repetição**: `while`
- **Controle de fluxo**: `break`, `continue`

O exemplo simula um **jogo de adivinhação**, onde o usuário tenta descobrir um número aleatório.

---

## Código Python Comentado

```python
# Programa: Jogo de adivinhação
# Objetivo: O usuário deve adivinhar um número entre 1 e 10

import random

# Gera um número aleatório entre 1 e 10
secretNumber = random.randint(1, 10)
numberOfAttempts = 0

print("Adivinhe o número entre 1 e 10")

# Estrutura de repetição: laço que continua até o usuário acertar ou digitar 'sair'
while True:
    attempts = input("Digite seu palpite ou sair para encerrar: ")

    # Controle de fluxo: permite sair do loop se o usuário quiser
    if attempts.lower() == 'sair':
        print("Saindo do jogo. O número era:", secretNumber)
        break  #  Encerra o laço imediatamente

    # Estrutura de seleção: valida se o valor digitado é um número
    if not attempts.isdigit():
        print("Por favor, digite um número válido.")
        continue  # Pula o restante do laço e volta ao início

    # Converte a entrada para inteiro
    attempts = int(attempts)
    numberOfAttempts += 1

    # Estrutura de seleção com múltiplas condições
    if attempts < secretNumber:
        print("Muito baixo!")      # Executado se o palpite for menor
    elif attempts > secretNumber:
        print("Muito alto!")       # Executado se for maior
    else:
        print(f"Parabéns! Você acertou em {numberOfAttempts} tentativas.")
        break  # Encerra o laço pois o número foi adivinhado
```

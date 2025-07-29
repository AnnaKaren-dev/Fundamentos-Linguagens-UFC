# Concorrência em Python: Threads vs Processos

## Conceitos

###  Diferença entre _Threads_ e _Processos_

 **Processo** 
- Programa em execução com espaço de memória próprio.

- Possui memória isolada para cada processo.

- Comunicação entre processos é mais complexa (IPC - Inter Process Communication).

- Criação é mais cara em termos de recursos e tempo.

- Falhas em um processo não afetam outros.

**Thread** 

- Unidade de execução dentro de um processo, compartilhando memória.

- Memória é compartilhada entre as threads do mesmo processo.

- Comunicação é mais simples, pois compartilham memória.

- Criação é mais leve e rápida.

- Falhas podem afetar outras threads.

---

##  Exemplo de Concorrência com `threading`

Neste exemplo, utilizamos o módulo `threading` do Python para simular duas atividades concorrentes:

1. Leitura de dados
2. Processamento de dados

Ambas são executadas simultaneamente por meio de **threads**, aproveitando o tempo de espera de uma para executar a outra.

### 🔧 Código (`concorrencia_threads.py`)

```python
import threading
import time
import random

# Função que simula leitura de dados
def readData(nome_fonte):
    for i in range(3):
        tempo = random.uniform(0.5, 1.5)
        print(f"[{nome_fonte}] Lendo dado {i+1}... (aguardando {tempo:.2f}s)")
        time.sleep(tempo)
    print(f"[{nome_fonte}] Leitura finalizada.")

# Função que simula processamento de dados
def processData():
    for i in range(3):
        tempo = random.uniform(0.5, 1.0)
        print(f"[Processamento] Processando dado {i+1}... (aguardando {tempo:.2f}s)")
        time.sleep(tempo)
    print("[Processamento] Processamento finalizado.")

# Criando threads
thread_leitura = threading.Thread(target=readData, args=("Fonte A",))
thread_processamento = threading.Thread(target=processData)

# Iniciando threads
thread_leitura.start()
thread_processamento.start()

# Aguardando as threads terminarem
thread_leitura.join()
thread_processamento.join()

print("\n Programa finalizado.")
```

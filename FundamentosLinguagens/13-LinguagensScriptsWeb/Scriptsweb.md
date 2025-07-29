# Exemplos de Scripts para Automação e Web em Python

Este documento apresenta exemplos de automação e manipulação de dados usando Python, com os módulos `os`, `shutil` e `requests`.

---

## 1. Consultando uma API Pública (requests)

```python
import requests

# Consulta a API pública para previsão de idade pelo nome
url = 'https://api.gateway.io/?name=anna'
resposta = requests.get(url)

if resposta.status_code == 200:
    dados = resposta.json()
    print(f"Nome: {dados['name']}")
    print(f"Idade estimada: {dados['age']}")
    print(f"Ocorrências: {dados['count']}")
else:
    print('Erro ao acessar a API.')
```

---

## 2. Enviando E-mail Automaticamente (smtplib)

```python
import smtplib
from email.mime.text import MIMEText

# Configurações do e-mail
remetente = 'seuemail@exemplo.com'
destinatario = 'destino@exemplo.com'
mensagem = MIMEText('Olá! Este é um e-mail automático enviado por um script Python.')
mensagem['Subject'] = 'E-mail Automático'
mensagem['From'] = remetente
mensagem['To'] = destinatario

# Envia o e-mail (exemplo com servidor local)
try:
    with smtplib.SMTP('localhost') as servidor:
        servidor.send_message(mensagem)
    print('E-mail enviado com sucesso!')
except Exception as e:
    print('Erro ao enviar e-mail:', e)
```

---

## Exemplo: Consulta uma API e envia o resultado por e-mail

```python
import requests
import smtplib
from email.mime.text import MIMEText

# Consulta a API pública para previsão de idade pelo nome
url = 'https://api.agify.io/?name=lucas'
resposta = requests.get(url)

if resposta.status_code == 200:
    dados = resposta.json()
    conteudo_email = f"Nome: {dados['name']}\nIdade estimada: {dados['age']}\nOcorrências: {dados['count']}"
else:
    conteudo_email = 'Erro ao acessar a API.'

# Configurações do e-mail
remetente = 'seuemail@exemplo.com'
destinatario = 'destino@exemplo.com'
mensagem = MIMEText(conteudo_email)
mensagem['Subject'] = 'Resultado da consulta à API Agify'
mensagem['From'] = remetente
mensagem['To'] = destinatario

# Envia o e-mail (exemplo com servidor local)
try:
    with smtplib.SMTP('localhost') as servidor:
        servidor.send_message(mensagem)
    print('E-mail enviado com sucesso!')
except Exception as e:
    print('Erro ao enviar e-mail:', e)
```

---

Esses exemplos mostram como automatizar tarefas comuns de acesso à web e envio de e-mails usando Python, sem manipulação de arquivos locais.

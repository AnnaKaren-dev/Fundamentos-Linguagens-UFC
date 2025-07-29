#  Analisador Léxico Simples em Python

Este é um exemplo de analisador léxico (tokenizador) em Python para uma mini-gramática. O objetivo é reconhecer identificadores, números, operadores e palavras-chave de uma linguagem hipotética.

##  Mini-Gramática

### Tokens Suportados:
- **Identificadores**: letras seguidas de letras ou dígitos (ex: `x`, `soma1`)
- **Números**: sequências de dígitos (ex: `123`)
- **Operadores**: `+`, `-`, `*`, `/`
- **Palavras-chave**: `let`, `print`
- **Pontuação**: `=`, `;`

## Lógica do Tokenizador

```python
import re

# Expressões regulares para os tokens
token_spec = [
    ('NUMBER',     r'\d+'),
    ('ID',         r'[a-zA-Z_]\w*'),
    ('OP',         r'[+\-*/]'),
    ('ASSIGN',     r'='),
    ('END',        r';'),
    ('SKIP',       r'[ \t\n]+'),
    ('MISMATCH',   r'.'),
]

# Compilando todas em um regex único
tok_regex = '|'.join(f'(?P<{name}>{pattern})' for name, pattern in token_spec)
compiled_re = re.compile(tok_regex)

# Função de análise léxica
def lexer(code):
    tokens = []
    for match in compiled_re.finditer(code):
        kind = match.lastgroup
        value = match.group()
        if kind == 'SKIP':
            continue
        elif kind == 'MISMATCH':
            raise SyntaxError(f'Token inválido: {value}')
        else:
            tokens.append((kind, value))
    return tokens

# Código de exemplo
source_code = "let x = 10 + 20; print x;"

# Tokenizando
tokens = lexer(source_code)

# Mostrando os tokens
for token in tokens:
    print(token)

# Resultado 
('ID', 'let')
('ID', 'x')
('ASSIGN', '=')
('NUMBER', '10')
('OP', '+')
('NUMBER', '20')
('END', ';')
('ID', 'print')
('ID', 'x')
('END', ';')

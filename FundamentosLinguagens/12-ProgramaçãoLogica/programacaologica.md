# Exemplo de Programação Lógica: Genealogia em Prolog

Este exemplo modela relações familiares usando sintaxe em Prolog. Inclui fatos, regras e exemplos de consultas, com explicações.

---

## Fatos

```prolog
% pai(Pai, Filho): Pai é pai de Filho
pai(joao, maria).
pai(joao, jose).
pai(jose, ana).

% mae(Mae, Filho): Mae é mãe de Filho
mae(maria, pedro).
mae(ana, carla).
```

---

## Regras

```prolog
% aio(Pessoa, Filho): Pessoa é pai ou mãe de Filho (ancestral imediato)
aio(Pai, Filho) :- pai(Pai, Filho).
aio(Mae, Filho) :- mae(Mae, Filho).

% avo(Avo, Neto): Avo é avô ou avó de Neto
avo(Avo, Neto) :- pai(Avo, Pai), pai(Pai, Neto).
avo(Avo, Neto) :- pai(Avo, Mae), mae(Mae, Neto).
avo(Avo, Neto) :- mae(Avo, Pai), pai(Pai, Neto).
avo(Avo, Neto) :- mae(Avo, Mae), mae(Mae, Neto).
```

---

## Exemplos de Consultas

```prolog
% Quem é neto(a) de joao?
?- avo(joao, X).
% Resultado esperado: X = ana.

% Quem é ancestral imediato de pedro?
?- aio(X, pedro).
% Resultado esperado: X = maria.
```

---

## Explicação
- **Fatos**: Definem relações diretas de paternidade e maternidade.
- **Regras**: Permitem deduzir relações mais complexas, como ancestralidade (avô/avó).
- **Consultas**: Exemplos de perguntas que podem ser feitas ao sistema lógico.
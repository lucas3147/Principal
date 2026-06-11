# MENU

* [Dir](#dir)
* [Help](#help)

## Dir

A função `dir()` exibe os atributos e métodos disponíveis em um objeto.

### Comandos

* `dir(objeto)`: lista tudo que o objeto possui.
* `dir()`: lista os nomes disponíveis no escopo atual.

## Help

A função `help()` exibe a documentação de objetos, funções, classes e métodos.

### Comandos

* `help(objeto)`: mostra a documentação do objeto.
* `help(funcao)`: mostra como utilizar uma função.
* `help(classe.metodo)`: mostra detalhes de um método específico.

### Quando usar cada um

O fluxo mais comum é:

1. Descobrir os métodos com `dir()`.
2. Entender o funcionamento com `help()`.

### Exemplo

```python
lista = []

dir(lista)
help(lista.append)
```
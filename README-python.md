# MENU

* [Dir](#dir)
* [Help](#help)
* [Função `range()`](#funcao-range)
* [Conceito de Listas](#conceito-de-listas)
    * [Listas Dinâmicas](#listas-dinâmicas)
    * [Criação e Manipulação](#criação-e-manipulação)
    * [Métodos de Manipulação](#métodos-de-manipulação)
    * [Indexação](#indexação)
    * [Iteração e Entrada do Usuário](#iteração-e-entrada-do-usuário)
    * [Exemplos Práticos](#exemplos-práticos)
    * [Cópias de Listas](#cópias-de-listas)
* [Conceito de Tuplas](#conceito-de-tuplas)
    * [Criação de Tuplas](#criacao-de-tuplas)
    * [Acesso aos Elementos](#acesso-aos-elementos)
    * [Métodos das Tuplas](#metodos-das-tuplas)
    * [Conversão entre Lista e Tupla](#conversao-entre-lista-e-tupla)
    * [Desempacotamento](#desempacotamento)
    * [Comparação entre Listas e Tuplas](#comparacao-entre-listas-e-tuplas)
* [Funções Lambda](#funcoes-lambda)
    * [Sintaxe](#sintaxe)
    * [Comparação com `def`](#comparacao-com-def)
    * [Uso com funções embutidas](#uso-com-funcoes-embutidas)
    * [Limitações](#limitacoes)
    * [Quando usar](#quando-usar)
* [Condição ternária](#condicao-ternaria)
    * [Sintaxe](#sintaxe)
    * [Quando utilizar](#quando-utilizar)
    * [Exemplos](#exemplos)


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

## Função `range()`

A função `range()` gera uma sequência de números inteiros. Ela é muito utilizada em laços `for` para controlar quantas vezes um bloco de código será executado.

### Sintaxe

```python
range(início, fim, passo)
```

* `início`: onde a sequência começa (padrão `0`).
* `fim`: onde a sequência termina (**não é incluído**).
* `passo`: intervalo entre os números (padrão `1`).

### Exemplos

* `range(5)` → `0, 1, 2, 3, 4`
* `range(3, 8)` → `3, 4, 5, 6, 7`
* `range(0, 11, 2)` → `0, 2, 4, 6, 8, 10`
* `range(10, 0, -1)` → `10, 9, 8, ..., 1`

### Comandos

* `range(5)`: gera números de `0` até `4`.
* `range(2, 7)`: gera números de `2` até `6`.
* `range(0, 10, 2)`: gera números de `2` em `2`.
* `range(10, 0, -1)`: gera uma contagem regressiva.
* `list(range(...))`: converte o objeto `range` em uma lista.

## Conceito de Listas

Uma lista é uma estrutura de dados que armazena vários elementos em uma única variável. Ela pode conter diferentes tipos de dados, inclusive outras listas.

### Comandos

* `[]`: cria uma lista.
* `list()`: cria uma lista a partir de outro iterável.

### Listas Dinâmicas

As listas em Python possuem tamanho dinâmico, permitindo adicionar e remover elementos durante a execução do programa, diferentemente de arrays de tamanho fixo em muitas outras linguagens.

### Comandos

* `append(valor)`: adiciona um elemento ao final.
* `extend(iterável)`: adiciona vários elementos.

### Criação e Manipulação

As listas podem ser criadas vazias ou preenchidas e manipuladas por meio de métodos específicos.

### Comandos

* `append()`: adiciona um único elemento.
* `extend()`: adiciona vários elementos.
* `insert(indice, valor)`: insere um elemento em uma posição específica.

### Métodos de Manipulação

Os métodos permitem ordenar, remover, localizar e contar elementos.

### Comandos

* `sort()`: ordena a lista.
* `sort(reverse=True)`: ordena em ordem decrescente.
* `pop(indice)`: remove e retorna um elemento pelo índice.
* `remove(valor)`: remove a primeira ocorrência do valor.
* `count(valor)`: conta quantas vezes um valor aparece.
* `index(valor)`: retorna o índice da primeira ocorrência.

### Indexação

Cada elemento possui um índice positivo (começando em `0`) e um índice negativo (a partir de `-1`, do último elemento).

### Comandos

* `lista[0]`: primeiro elemento.
* `lista[-1]`: último elemento.
* `lista[inicio:fim]`: obtém uma fatia (*slice*) da lista.

### Iteração e Entrada do Usuário

É possível percorrer listas com `for` e construir listas usando dados fornecidos pelo usuário.

### Comandos

* `for item in lista`: percorre os elementos.
* `for i in range(len(lista))`: percorre pelos índices.
* `append()`: adiciona os valores informados.

### Exemplos Práticos

As listas podem ser utilizadas para somar valores, localizar elementos, criar cadastros simples e diversas outras tarefas.

### Comandos

* `sum(lista)`: soma os elementos numéricos.
* `in`: verifica se um elemento existe na lista.
* `index()`: encontra a posição de um elemento.

### Cópias de Listas

A atribuição (`=`) cria uma referência para a mesma lista. Para criar listas independentes, utilize cópias superficiais (`copy()` ou `[:]`) ou profundas (`copy.deepcopy()`).

### Comandos

* `copy()`: cria uma cópia superficial.
* `[:]`: outra forma de cópia superficial.
* `copy.deepcopy()`: cria uma cópia profunda de estruturas aninhadas.

## Conceito de Tuplas

Uma tupla é uma coleção ordenada e **imutável**, usada para armazenar dados que não devem ser modificados após sua criação.

#### Comandos

* `()`: cria uma tupla.
* `tuple(iterável)`: converte um iterável em uma tupla.

### Criação de Tuplas

As tuplas podem conter um ou vários elementos, inclusive de tipos diferentes. Para criar uma tupla com apenas um elemento, é necessário adicionar uma vírgula.

#### Comandos

* `(1, 2, 3)`: cria uma tupla com três elementos.
* `(10,)`: cria uma tupla com um único elemento.

### Acesso aos Elementos

Os elementos de uma tupla são acessados por índices positivos e negativos, da mesma forma que nas listas.

#### Comandos

* `tupla[0]`: primeiro elemento.
* `tupla[-1]`: último elemento.
* `tupla[inicio:fim]`: retorna uma fatia (*slice*) da tupla.

### Métodos das Tuplas

Como são imutáveis, as tuplas possuem apenas métodos para consulta.

#### Comandos

* `count(valor)`: conta quantas vezes um valor aparece.
* `index(valor)`: retorna o índice da primeira ocorrência.

### Conversão entre Lista e Tupla

É possível converter listas em tuplas e vice-versa quando necessário.

#### Comandos

* `tuple(lista)`: converte uma lista em tupla.
* `list(tupla)`: converte uma tupla em lista.

### Desempacotamento

O desempacotamento permite atribuir os elementos de uma tupla diretamente a várias variáveis.

#### Comandos

* `a, b, c = tupla`: atribui cada elemento da tupla a uma variável.

### Comparação entre Listas e Tuplas

* **Lista (`[]`)**: mutável, ideal para coleções que podem mudar.
* **Tupla (`()`)**: imutável, ideal para dados fixos e constantes.

## Funções Lambda

As funções `lambda` são **funções anônimas** (sem nome) usadas para criar funções simples e temporárias. Elas retornam automaticamente o resultado da única expressão que contêm.

### Comandos

* `lambda argumentos: expressão`: cria uma função anônima.

### Sintaxe

A sintaxe de uma função `lambda` é composta pela palavra-chave `lambda`, seguida pelos parâmetros e por uma única expressão. O valor dessa expressão é retornado automaticamente, sem necessidade de usar `return`.

### Comandos

* `lambda x: x * 2`: recebe um argumento e retorna seu dobro.
* `lambda a, b: a + b`: recebe dois argumentos e retorna a soma.
* `lambda: "Olá"`: função sem parâmetros.

### Comparação com `def`

Uma função criada com `lambda` pode substituir uma função simples criada com `def`. No entanto, `lambda` é indicada apenas para funções curtas, enquanto `def` é mais adequada para funções com múltiplas instruções ou reutilização.

### Comandos

* `def`: cria funções nomeadas, com múltiplas linhas e uso de `return`.
* `lambda`: cria funções anônimas com uma única expressão.

### Uso com funções embutidas

As funções `lambda` são frequentemente utilizadas como argumento de funções que esperam outra função, como `sorted()`, `map()`, `filter()` e `max()`.

### Comandos

* `sorted(iterável, key=lambda ...)`: define o critério de ordenação.
* `map(lambda ..., iterável)`: aplica uma transformação a cada elemento.
* `filter(lambda ..., iterável)`: filtra elementos conforme uma condição.
* `max(iterável, key=lambda ...)`: encontra o maior elemento com base em um critério.

### Limitações

Uma função `lambda` aceita apenas **uma única expressão**. Ela não permite múltiplas instruções, atribuições de variáveis (`=`), blocos de código ou o uso explícito de `return`.

### Quando usar

Utilize `lambda` para funções pequenas, temporárias e simples, principalmente quando forem usadas apenas uma vez. Para lógicas mais complexas, reutilização ou maior legibilidade, prefira criar funções com `def`.

## Condição ternária

A condição ternária é uma forma reduzida de escrever um `if...else` quando há apenas duas opções possíveis. Ela retorna um valor dependendo do resultado de uma condição.

### Sintaxe

```python
valor_se_verdadeiro if condição else valor_se_falso
```

### Exemplos

Verificar maioridade:

```python
status = "Maior de idade" if idade >= 18 else "Menor de idade"
```

Verificar número par:

```python
resultado = "Par" if numero % 2 == 0 else "Ímpar"
```

Escolher o maior número:

```python
maior = a if a > b else b
```

Imprimir diretamente:

```python
print("Aprovado" if nota >= 7 else "Reprovado")
```

### Quando utilizar

* Quando existem apenas **duas possibilidades**.
* Quando a expressão é simples e melhora a legibilidade.
* Evite encadear muitas condições ternárias; nesses casos, prefira `if/elif/else`.
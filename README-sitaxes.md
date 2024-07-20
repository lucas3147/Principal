# MENU

- [C#](#c)
    - [Utilizando records para representar DTOS](#utilizando-records-para-representar-dtos)
    - [Switch expression](#switch-expression)

## C#

### Utilizando records para representar DTOS

**Exemplo de uso:**

1. errado:

```c#
public class CLienteDTO
{
    public int Id { get; private set; }
    public string Nome { get; private set; }
    public string Email { get; private set; }

    public ClienteDto(int id, string nome, string email) {
        Id = id;
        Nome = nome;
        Email = email;
    }
}
```

2. certo:

```c#
public record ClienteDTO(int Id, string Nome, string Email);
```

**Características dos records:**

1. Desconstrução:

- Você pode desconstruir um record em suas propriedades, facilitando a manipulação dos dados.

```c#
var cliente = new ClienteDto(1, "João", "joao@example.com");
var (id, nome, email) = cliente;
```

2. Cópia com Modificação (With Expression):

- Você pode criar uma cópia de um record modificando algumas de suas propriedades.

```c#
var cliente2 = cliente with { Nome = "Maria" };
```

3. Herança:

- Os records suportam herança, mas diferentemente das classes normais, um record que herda de outro record cria um novo tipo de record.

## Switch expression

**Exemplo de uso**

1. errado:

```c#
switch (CodigoStatus)
{
    case 0:
        mensagem = "Em andamento";
        break;
    case 1:
        mensagem = "Entregue";
        break;
    default:
        mensagem = "Cancelado";
        break;
}
```

2. certo:

```c#
var mensagem = CodigoStatus switch
{
    false => "Em andamento",
    true => "Entregue",
    _ => "Cancelado"
}
```

**Como funciona:**

- Expressão de entrada: No switch expression, você avalia uma expressão (no exemplo, CodigoStatus).

- Padrões de correspondência: Cada caso é representado por um padrão de correspondência, seguido pelo operador => e o valor a ser retornado.

- Valor padrão: O padrão _ é utilizado como padrão para casos que não correspondem a nenhum dos anteriores, funcionando de forma semelhante ao default no switch tradicional.

**Vantagens:**

- Sintaxe concisa: Reduz a verbosidade do código.

- Imutabilidade: Switch expressions retornam um valor, incentivando o uso de variáveis imutáveis (readonly ou const).

- Legibilidade: Melhoram a legibilidade do código, tornando mais fácil entender a lógica de controle de fluxo.

## Evite os métodos ToUpper / ToLower ao comparar strings

**Exemplo de uso**

- errado:

```c#
public bool SaoIguaisIneficiente()
{
    return textol.ToUpper() == texto2.ToUpper();
}
```

- certo:

```c#
public bool SaoIguaisEficiente()
{
    return string.Equals(textol, texto2,StringComparison.OrdinalIgnareCase);
}
```

- Ultilizando benchmarking

<table>
  <thead>
    <tr>
      <th>Method</th>
      <th>Mean</th>
      <th>Error</th>
      <th>StuDev</th>
      <th>GenD</th>
      <th>Allocated</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>SaoIguaisIneficiente</td>
      <td>20.1993 ns</td>
      <td>0.0737 ns</td>
      <td>0.0616 ns</td>
      <td>0,0034</td>
      <td>64B</td>
    </tr>
    <tr>
      <td>SaoIguaisEficiente</td>
      <td>10.2963 ns</td>
      <td>0.0040 ns</td>
      <td>0.0043 na</td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
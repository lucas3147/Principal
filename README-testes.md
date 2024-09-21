# MENU

- [Padrões e Boas Práticas ao Usar o NUnit com Exemplos](#padrões-e-boas-práticas-ao-usar-o-nunit-com-exemplos)
    - [Organização de Testes](#1-organização-de-testes)
    - [AAA (Arrange, Act, Assert)](#2-aaa-arrange-act-assert)
    - [Isolamento dos Testes](#3-isolamento-dos-testes)
    - [Uso Correto das Asserções](#4-uso-correto-das-asserções)
    - [Testes Parametrizados](#5-testes-parametrizados)
    - [Mocks e Stubs](#6-mocks-e-stubs)
    - [Testes de Exceções](#7-testes-de-exceções)
    - [Organização de Testes em Categorias](#8-organização-de-testes-em-categorias)
    - [Evidência de Testes (Output)](#9-evidência-de-testes-output)
    - [Setup e Teardown Globais](#10-setup-e-teardown-globais)
    - [Testes Assíncronos](#11-testes-assíncronos)
    - [Evitar Dependências de Ambiente](#12-evitar-dependências-de-ambiente)

## Padrões e Boas Práticas ao Usar o NUnit com Exemplos

### 1. Organização de Testes

- **Nomeação Descritiva**: Nomeie seus testes de forma que descrevam o comportamento esperado.
  Exemplo: 
  ```csharp
  [Test]
  public void CalculateTotalPrice_ShouldReturnCorrectSum_WhenItemsAreValid() { }
  ```

- **Classe de Testes por Unidade de Lógica**: Cada classe de teste deve corresponder a uma funcionalidade.

### 2. AAA (Arrange, Act, Assert)

Este padrão divide os testes em três partes:
- **Arrange**: Configure o ambiente de teste.
- **Act**: Execute a ação.
- **Assert**: Verifique os resultados.

Exemplo:
```csharp
[Test]
public void AddItem_ShouldIncreaseItemCount() 
{
    // Arrange
    var cart = new ShoppingCart();
    var item = new Item("Apple", 1);

    // Act
    cart.AddItem(item);

    // Assert
    Assert.AreEqual(1, cart.TotalItems);
}
```

### 3. Isolamento dos Testes

Cada teste deve ser independente. Utilize `[SetUp]` e `[TearDown]` para configurar e limpar o ambiente.
Exemplo:
```csharp
[SetUp]
public void Setup() { /* Executado antes de cada teste */ }

[TearDown]
public void Teardown() { /* Executado após cada teste */ }
```

### 4. Uso Correto das Asserções

Utilize `Assert` de forma apropriada:
- `Assert.AreEqual(expected, actual)`
- `Assert.IsTrue(condition)`
- `Assert.Throws<T>(() => metodo())`

Exemplo:
```csharp
Assert.AreEqual(5, resultado);
Assert.IsTrue(cliente.Ativo);
Assert.Throws<ArgumentNullException>(() => servico.Calcular(null));
```

### 5. Testes Parametrizados

Use `[TestCase]` para fornecer diferentes conjuntos de dados.
Exemplo:
```csharp
[TestCase(1, 2, 3)]
[TestCase(2, 3, 5)]
public void Add_ShouldReturnCorrectSum(int a, int b, int expectedResult) 
{
    var result = calculator.Add(a, b);
    Assert.AreEqual(expectedResult, result);
}
```

### 6. Mocks e Stubs

Use mocks para simular dependências externas.
Exemplo:
```csharp
var mockService = new Mock<IUserService>();
mockService.Setup(service => service.GetUserById(It.IsAny<int>())).Returns(new User());
```

### 7. Testes de Exceções

Verifique se exceções são lançadas corretamente.
Exemplo:
```csharp
[Test]
public void DivideByZero_ShouldThrowException() 
{
    Assert.Throws<DivideByZeroException>(() => calculator.Divide(10, 0));
}
```

### 8. Organização de Testes em Categorias

Use `[Category]` para agrupar testes.
Exemplo:
```csharp
[Test, Category("Unit")]
public void TestMethod() { }
```

### 9. Evidência de Testes (Output)

Use `TestContext.WriteLine()` para imprimir mensagens úteis.
Exemplo:
```csharp
[Test]
public void TestMethod() 
{
    TestContext.WriteLine("Testando comportamento...");
    Assert.AreEqual(2, 1 + 1);
}
```

### 10. Setup e Teardown Globais

Use `[OneTimeSetUp]` e `[OneTimeTearDown]` para configuração global.
Exemplo:
```csharp
[OneTimeSetUp]
public void GlobalSetup() { /* Executado uma vez antes de todos os testes */ }

[OneTimeTearDown]
public void GlobalTeardown() { /* Executado uma vez após todos os testes */ }
```

### 11. Testes Assíncronos

Suporte para testes `async` com NUnit.
Exemplo:
```csharp
[Test]
public async Task GetData_ShouldReturnValidData() 
{
    var result = await service.GetDataAsync();
    Assert.IsNotNull(result);
}
```

### 12. Evitar Dependências de Ambiente

Certifique-se de que os testes não dependem de configurações locais.

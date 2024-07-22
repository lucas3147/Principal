# MENU

- [SQL SERVER / T-SQL](#sql-server--t-sql)
    - [Criação de script que identifica dados truncados](#criação-de-script-que-identifica-dados-truncados)
    - [Como consultar o script de exibições/procedures/functions](#como-consultar-o-script-de-exibiçõesproceduresfunctions)
    - [Renomeando colunas por script](#renomeando-colunas-por-script)
    - [Utilizando cursores para operações complexas](#utilizando-cursores-para-operações-complexas)
    - [Criação de tipos de tabelas no sql server](#criação-de-tipos-de-tabelas-no-sql-server)

## SQL SERVER / T-SQL

### Criação de script que identifica dados truncados

**Utilização:**

```sql
--Script verifica dado truncado

IF OBJECT_ID('tempdb..#TempTableTruncada') IS NOT NULL
    DROP TABLE #TempTableTruncada;

declare 
	@scriptVerificaValorTruncado NVARCHAR(MAX), 
	@colunas NVARCHAR(MAX);

--Sua consulta a inserir na tabela
--**IMPORTANTE: 
--cada coluna deve ter um alias correspondente, os espaços devem ser trocados por underline (_).
--Antes do from declare INTO # e o nome da tabela temporária**


----------------------------------

--Recebendo as colunas, os valores de cada linha é o tamanho dos caracteres
SELECT 
	@colunas = CONCAT(@colunas, 'ISNULL(LEN(',COLUMN_NAME,'), 0) AS ', COLUMN_NAME,', ')
FROM 
	tempdb.INFORMATION_SCHEMA.COLUMNS
WHERE 
	TABLE_NAME LIKE '%#TempTableTruncada%';

SET @colunas = LEFT(@colunas, LEN(@colunas) - 1);

SET @scriptVerificaValorTruncado = CONCAT('SELECT ', @colunas,' FROM #TempTableTruncada');

EXEC sp_executesql @scriptVerificaValorTruncado;
```

### Como consultar o script de exibições/procedures/functions

**Uitilização**

```sql
/* consulta de exibições */
SELECT definition
FROM sys.objects o
INNER JOIN sys.sql_modules m ON o.object_id = m.object_id
WHERE o.type = 'V'  /* V para Views */
AND o.name = 'Vw_Asp_Adm_Funcionarios_Ferias';

/* consulta de procedures e function */
SELECT definition
FROM sys.sql_modules
WHERE object_id = OBJECT_ID('sp_grava_data_adesao');

/* usando procedure interna: Exibições, procedures e functions */
EXEC sp_helptext 'Vw_Asp_Adm_Funcionarios_Ferias';
```

### Renomeando colunas por script

**Ultilização**

```sql
EXEC sp_rename 'dbo.ErrorLog.ErrorTime', 'ErrorDateTime', 'COLUMN';
```

### Utilizando cursores para operações complexas

**Ultilização**

``` sql
-- Lógica para a utilização

-- Declarar variável
declare @id_cliente numeric(18,0);

-- Declarar cursor
DECLARE cliente_cursor CURSOR FOR           
SELECT Id_cliente FROM Tlm_Importacao

-- Abrir cursor
OPEN cliente_cursor

-- Comecar a leitura dos dados do cursor
FETCH NEXT FROM cliente_cursor  
INTO @id_cliente

WHILE @@FETCH_STATUS = 0   
BEGIN

  /*
  Lógica aqui
  */

  -- Próximo item de dados
  FETCH NEXT FROM cliente_cursor  
  INTO @id_cliente
END

--Fechando cursor
CLOSE cliente_cursor;          
DEALLOCATE cliente_cursor;
```

### Criação de tipos de tabelas no sql server

É possível utilizar tipos de tabelas no sql server, para realizar scripts mais complexos e sofisticados, como por exemplo:

- Utilizar esses tipos de tabelas na passagem de parâmetros de procedures.
- Operações complexas que exigiriam scripts dinâmicos podem ser trocados por tipos de tabelas

**Utilização**

```sql

--Criação do tipo de tabela
CREATE TYPE TipoTabela AS TABLE
(
    Coluna1 INT,
    Coluna2 NVARCHAR(255)
);

--Utilização do tipo de tabela na passagem de parâmetro da procedure
CREATE PROCEDURE sp_ProcessarDados
    @dados TipoTabela READONLY
AS
BEGIN
    INSERT INTO TabelaDestino (Coluna1, Coluna2)
    SELECT Coluna1, Coluna2
    FROM @dados;
END
```
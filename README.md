# Sql-portfolio# SQL Portfolio

Este repositório contém exemplos de consultas SQL usando o banco de dados Northwind para demonstrar minhas habilidades e conhecimentos em SQL.

## Tópicos

1. [Consultas Básicas](#consultas-básicas)
2. [Consultas de Agregação](#consultas-de-agregação)
3. [Consultas com JOINs](#consultas-com-joins)
4. [Subconsultas](#subconsultas)
5. [Consultas de Manipulação de Dados](#consultas-de-manipulação-de-dados)

---

## Consultas Básicas

```sql
-- Selecionar todos os registros de uma tabela
SELECT * FROM Customers;

-- Selecionar colunas específicas
SELECT CustomerID, CompanyName, ContactName FROM Customers;

-- Filtrar registros com WHERE
SELECT * FROM Customers WHERE Country = 'Germany';

-- Contar o número de registros em uma tabela
SELECT COUNT(*) AS NumberOfCustomers FROM Customers;

-- Calcular a média de frete
SELECT AVG(Freight) AS AverageFreight FROM Orders;

-- Agrupar registros e calcular a soma
SELECT Country, SUM(Freight) AS TotalFreight 
FROM Orders 
GROUP BY Country;

-- Inner Join entre duas tabelas
SELECT Orders.OrderID, Customers.CompanyName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

-- Left Join
SELECT Orders.OrderID, Customers.CompanyName, Orders.OrderDate
FROM Orders
LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

-- Subconsulta para encontrar o maior valor de frete
SELECT * FROM Orders WHERE Freight = (SELECT MAX(Freight) FROM Orders);

-- Subconsulta em cláusula FROM
SELECT Country, AVG(Freight) AS AverageFreight
FROM (SELECT Country, Freight FROM Orders) AS CountryFreight
GROUP BY Country;

-- Inserir dados em uma tabela
INSERT INTO Customers (CustomerID, CompanyName, ContactName, Country)
VALUES ('ABCDE', 'New Company', 'John Doe', 'USA');

-- Atualizar dados em uma tabela
UPDATE Customers SET ContactName = 'Jane Doe' WHERE CustomerID = 'ABCDE';

-- Deletar dados de uma tabela
DELETE FROM Customers WHERE CustomerID = 'ABCDE';

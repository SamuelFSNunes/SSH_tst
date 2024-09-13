
# Comandos SQL

## 1. DDL (Data Definition Language)
Comandos usados para definir e modificar a estrutura do banco de dados.

- **`CREATE`**: Cria uma nova tabela, índice, ou outro objeto no banco de dados.
  ```sql
  CREATE TABLE table_name (column_name datatype, ...);
  ```

- **`ALTER`**: Modifica a estrutura de uma tabela existente.
  ```sql
  ALTER TABLE table_name ADD column_name datatype;
  ```

- **`DROP`**: Remove uma tabela ou outro objeto do banco de dados.
  ```sql
  DROP TABLE table_name;
  ```

- **`TRUNCATE`**: Remove todos os dados de uma tabela, mantendo sua estrutura.
  ```sql
  TRUNCATE TABLE table_name;
  ```

## 2. DML (Data Manipulation Language)
Comandos usados para gerenciar dados dentro das tabelas.

- **`SELECT`**: Consulta dados de uma ou mais tabelas.
  ```sql
  SELECT column_name FROM table_name;
  ```

- **`INSERT`**: Insere novos dados em uma tabela.
  ```sql
  INSERT INTO table_name (column_name1, column_name2, ...) VALUES (value1, value2, ...);
  ```

- **`UPDATE`**: Atualiza dados existentes em uma tabela.
  ```sql
  UPDATE table_name SET column_name = value WHERE condition;
  ```

- **`DELETE`**: Remove dados de uma tabela.
  ```sql
  DELETE FROM table_name WHERE condition;
  ```

## 3. DCL (Data Control Language)
Comandos usados para gerenciar permissões e controles de acesso.

- **`GRANT`**: Concede permissões a usuários.
  ```sql
  GRANT SELECT ON table_name TO user_name;
  ```

- **`REVOKE`**: Remove permissões de usuários.
  ```sql
  REVOKE SELECT ON table_name FROM user_name;
  ```

## 4. TCL (Transaction Control Language)
Comandos usados para gerenciar transações.

- **`COMMIT`**: Finaliza uma transação e salva as alterações.
  ```sql
  COMMIT;
  ```

- **`ROLLBACK`**: Desfaz as alterações feitas por uma transação.
  ```sql
  ROLLBACK;
  ```

- **`SAVEPOINT`**: Define um ponto de restauração dentro de uma transação.
  ```sql
  SAVEPOINT savepoint_name;
  ```

- **`SET TRANSACTION`**: Define características para uma transação.
  ```sql
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  ```

## 5. JOINs e Tipos de JOIN
Comandos para combinar registros de duas ou mais tabelas.

Para melhor entendimento desse assunto, consultar a seguinte [documentação](https://www.hashtagtreinamentos.com/join-no-sql?gad_source=1&gclid=CjwKCAjwxY-3BhAuEiwAu7Y6s-ApPDBXahynHGmljricVG81py8DZABd9b6sGD47eOybL5LJl9l9tRoCgRAQAvD_BwE)

- **`INNER JOIN`**: Retorna registros que têm correspondência nas duas tabelas.
  ```sql
  SELECT columns
  FROM table1
  INNER JOIN table2
  ON table1.common_column = table2.common_column;
  ```

- **`LEFT JOIN`**: Retorna todos os registros da tabela à esquerda e os correspondentes da direita.
  ```sql
  SELECT columns
  FROM table1
  LEFT JOIN table2
  ON table1.common_column = table2.common_column;
  ```

- **`RIGHT JOIN`**: Retorna todos os registros da tabela à direita e os correspondentes da esquerda.
  ```sql
  SELECT columns
  FROM table1
  RIGHT JOIN table2
  ON table1.common_column = table2.common_column;
  ```

- **`FULL JOIN`**: Retorna todos os registros de ambas as tabelas, correspondentes ou não.
  ```sql
  SELECT columns
  FROM table1
  FULL JOIN table2
  ON table1.common_column = table2.common_column;
  ```

## 6. GROUP BY e HAVING
Comandos para agrupar registros e aplicar filtros em grupos.

- **`GROUP BY`**: Agrupa registros com base em valores em colunas específicas.
  ```sql
  SELECT column_name, COUNT(*)
  FROM table_name
  GROUP BY column_name;
  ```

- **`HAVING`**: Filtra grupos após a agregação de resultados.
  ```sql
  SELECT column_name, COUNT(*)
  FROM table_name
  GROUP BY column_name
  HAVING COUNT(*) > 1;
  ```

## 7. ORDER BY
Comando para ordenar os resultados da consulta.

- **`ORDER BY`**: Ordena os resultados em ordem ascendente ou descendente.
  ```sql
  SELECT column_name
  FROM table_name
  ORDER BY column_name ASC;
  ```

## 8. UNION e UNION ALL
Comandos para combinar resultados de múltiplas consultas.

- **`UNION`**: Remove duplicatas ao combinar os resultados.
  ```sql
  SELECT column_name FROM table1
  UNION
  SELECT column_name FROM table2;
  ```

- **`UNION ALL`**: Mantém duplicatas ao combinar os resultados.
  ```sql
  SELECT column_name FROM table1
  UNION ALL
  SELECT column_name FROM table2;
  ```

## 9. DISTINCT
Comando para remover duplicatas nos resultados da consulta.

- **`DISTINCT`**: Retorna valores distintos de uma coluna.
  ```sql
  SELECT DISTINCT column_name
  FROM table_name;
  ```

## 10. LIMIT
Comando para limitar o número de registros retornados.

- **`LIMIT`**: Limita o número de registros retornados pela consulta.
  ```sql
  SELECT column_name
  FROM table_name
  LIMIT 10;
  ```

## 11. WHERE
Comando para filtrar registros com base em uma condição.

- **`WHERE`**: Filtra resultados que atendem a uma condição.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE condition;
  ```

## 12. BETWEEN, IN, e LIKE
Comandos para realizar comparações avançadas.

- **`BETWEEN`**: Seleciona valores dentro de um intervalo.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name BETWEEN value1 AND value2;
  ```

- **`IN`**: Seleciona valores que correspondem a uma lista de valores.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name IN (value1, value2, value3);
  ```

- **`LIKE`**: Pesquisa valores que correspondem a um padrão.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name LIKE 'pattern%';
  ```

## 13. IS NULL e IS NOT NULL
Comandos para verificar se os valores são `NULL` ou não.

- **`IS NULL`**: Seleciona registros onde o valor é `NULL`.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name IS NULL;
  ```

- **`IS NOT NULL`**: Seleciona registros onde o valor não é `NULL`.
  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name IS NOT NULL;
  ```

---

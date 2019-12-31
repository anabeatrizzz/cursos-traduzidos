Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Indice
- [WHERE](#where)
  - [Operadores do SQL](#operadores-do-sql)
  - [BETWEEN](#between)
  - [Valores textuais](#valores-textuais)
- [Filtrando com AND e OR](#filtrando-com-and-e-or)
  - [Operadores lógicos](#operadores-lógicos)
  - [OR](#or)
  - [Combinando AND e OR](#combinando-and-e-or)
- [IN e NOT IN](#in-e-not-in)
  - [IN](#in)
  - [NOT IN](#not-in)

# WHERE
#### [Voltar ao indice](#indice)
O `WHERE` é usado para mostrar apenas registros que preenchem um critério específico. 

A sintaxe do `WHERE`: 
```sql
SELECT lista_de_colunas
FROM nome_da_tabela
WHERE condição;
```
Considere a seguinte tabela:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
4|Emily|Adams|Houston
5|James|Roberts|Filadélfia
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago
9|Samuel|Clark|San Diego
10|Anthony|Young|Los Angeles

Na tabela, podemos selecionar um registro específico: 
```sql
SELECT * FROM clientes 
WHERE ID = 7;
```

ID|Nome|Sobrenome|Cidade
---|---|---|---
7|Daniel|Harris|Nova York

### Operadores do SQL
#### [Voltar ao indice](#indice)
Operadores de comparação e operadores lógicos são usados na afirmação `WHERE` para filtrar os dados a serem selecionados. 

Os seguintes operadores de comparação podem ser usados com a afirmação `WHERE`:

Operador|Descrição
---|---
`=`|Igual
`!=`|Não igual
`>`|Maior que
`<`|Menor que
`>=`|Maior ou igual a
`<=`|Menor ou igual a
`BETWEEN`|Entre um número e outro

Por exemplo, podemos mostrar todos os nomes listados em nossa tabela com excessão daquele que tem o ID 5.
```sql
SELECT * FROM clientes
WHERE ID != 5;
```
__Resultado:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
4|Emily|Adams|Houston
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago
9|Samuel|Clark|San Diego
10|Anthony|Young|Los Angeles

Como pode ver, o registro com o ID de número 5 está excluído da lista.

### BETWEEN
#### [Voltar ao indice](#indice)
O operador `BETWEEN` seleciona valores dentro de um intervalo. O primeiro valor deve ser o limite mínimo e o segundo valor, o limite máximo. 

A sintaxe do operador `BETWEEN` é a seguinte: 
```sql
SELECT nome(s)_da_coluna(s) 
FROM nome_da_tabela 
WHERE nome_da_coluna
BETWEEN valor1 AND valor2;
```
A seguinte afirmação SQL seleciona todos os registros com IDs que estão entre 3 e 7:
```sql
SELECT * FROM clientes
WHERE ID BETWEEN 3 AND 7;
```
__Resultado:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
3|Chloe|Anderson|Chicago
4|Emily|Adams|Houston
5|James|Roberts|Filadélfia
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York

Como pode ver, os valores mínimo e máximo são incluídos.
### Valores textuais
#### [Voltar ao indice](#indice)
Quando trabalhamos com colunas que contem textos, devemos colocar qualquer texto que apareça na afirmação entre __aspas simples (')__. 

A seguinte afirmação SQL seleciona todos os registros onde a coluna Cidade tem o valor 'Nova York'.
```sql
SELECT ID, Nome, Sobrenome, Cidade 
FROM clientes 
WHERE Cidade = 'Nova York';
```

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York

Se seu texto contem um apóstrofo, você deve usar duas aspas simples para que o apóstrofo apareça. Por exemplo: 'Can"t'

# Filtrando com AND e OR
#### [Voltar ao indice](#indice)
### Operadores lógicos
#### [Voltar ao indice](#indice)
Podem ser usados para combinar dois valores Boolean e retornar um resultado verdadeiro, falso ou nulo.<br>Os seguintes operadores podem ser usados:

Operador|Descrição
---|---
`AND`|Verdadeiro se ambas expressões forem verdadeiras.
`OR`|Verdadeiro se uma das expressões for verdadeira.
`IN`|Verdadeiro se o operando é igual a um de uma lista de expressões.
`NOT`|Retorna verdadeiro se a expressão não for verdadeira.

Quando mostramos dados usando a afirmação `SELECT`, usamos operadores lógicos na afirmação `WHERE` para combinar múltiplas condições. 

Se você quer selecionar linhas que satisfaçam todas as condições, use o operador lógico `AND`.

ID|Nome|Sobrenome|Idade
---|---|---|---
1|John|Smith|35
2|David|Williams|23
3|Chloe|Anderson|27
4|Emily|Adams|34
5|James|Roberts|31
6|Andrew|Thomas|45
7|Daniel|Harris|30

Para encontrar os nomes dos clientes que estão entre 30 a 40 anos de idade, escreva a seguinte consulta:
```sql
SELECT ID, Nome, Sobrenome, Idade
FROM clientes WHERE Idade >= 30 AND Idade <= 40;
```
Resultado:

ID|Nome|Sobrenome|Idade
---|---|---|---
1|John|Smith|35
4|Emily|Adams|34
5|James|Roberts|31
7|Daniel|Harris|30

Você pode combinar quantas condições quiser para que os resultados desejados sejam mostrados.
### OR
#### [Voltar ao indice](#indice)
Se você quer selecionar linhas que satisfaçam pelo menos uma das condições dadas, você pode usar o operador lógico `OR`. 

A seguinte tabela descreve como o operador lógico `OR` funciona:

Condicao1|Condicao2|Resultado
---|---|---
Verdadeira|Verdadeira|Verdadeiro
Verdadeira|Falsa|Verdadeiro
Falsa|Verdadeira|Verdadeiro
Falsa|Falsa|Falso

Por exemplo, se você quer encontrar os clientes que vivem em Nova York ou em Chicago, a consulta iria ser assim:
```sql
SELECT * FROM clientes
WHERE Cidade = 'Nova York' OR Cidade = 'Chicago';
```
__Resultado:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
3|Chloe|Anderson|Chicago
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago

Você pode usar `OR` com duas ou mais condições.

### Combinando AND e OR
#### [Voltar ao indice](#indice)
As condições `AND` e `OR` do SQL podem ser combinadas para testar múltiplas condições em uma consulta. Esses dois operadores são chamados de operadores conjuntivos.

Quando combinamos essas condições, é importante usar parênteses para ordenar, assim, se sabe a ordem para avaliar a condição.

Considere a seguinte tabela:

ID|Nome|Sobrenome|Cidade|Idade
---|---|---|---|---
1|John|Smith|Nova York|35
2|David|Williams|Los Angeles|23
3|Chloe|Anderson|Chicago|27
4|Emily|Adams|Houston|34
5|James|Roberts|Filadélfia|31
6|Andrew|Thomas|Nova York|45
7|Daniel|Harris|Nova York|30
8|Charlotte|Walker|Chicago|35
9|Samuel|Clark|San Diego|20
10|Anthony|Young|Los Angeles|33

A afirmação abaixo seleciona todos os clientes da cidade de Nova York E que tenham a idade igual a 30 OU 35:
```sql
SELECT * FROM clientes
WHERE Cidade = 'Nova York' AND (Idade = 30 OR Idade = 35);
```
__Resultado:__

ID|Nome|Sobrenome|Cidade|Idade
---|---|---|---|---
1|John|Smith|Nova York|35
7|Daniel|Harris|Nova York|30

Você pode aninhar quantas condições quiser. 

# IN e NOT IN
#### [Voltar ao indice](#indice)
### IN
#### [Voltar ao indice](#indice)
O operador `IN` é usado quando queremos comparar uma coluna com mais de um valor. 

Por exemplo, você talvez precise selecionar todos os clientes de Nova York, Los Angeles e Chicago.<br>Com a condição `OR`, nosso SQL iria ficar assim:
```sql
SELECT * FROM clientes
WHERE Cidade = 'Nova York'
OR Cidade = 'Los Angeles'
OR Cidade = 'Chicago';
```
__Resultado:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago
10|Anthony|Young|Los Angeles

Você pode conseguir o mesmo resultado com uma única condição `IN`, invés de múltiplas condições `OR`:
```sql
SELECT * FROM clientes
WHERE Cidade IN ('Nova York', 'Los Angeles', 'Chicago'); 
```
Isso iria produzir o mesmo resultado:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago
10|Anthony|Young|Los Angeles

Note o uso dos parênteses na sintaxe.

### NOT IN
#### [Voltar ao indice](#indice)
O operador `NOT IN` nos permite excluir uma lista de valores específicos de uma tabela-resultado.

Se adicionarmos `NOT` antes de `IN` na nossa consulta anterior, os clientes que vivem nessas cidades iriam ser excluídos:
```sql
SELECT * FROM clientes
WHERE Cidade NOT IN ('Nova York', 'Los Angeles', 'Chicago');
```
__Resultado:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
4|Emily|Adams|Houston
5|James|Roberts|Filadélfia
9|Samuel|Clark|San Diego

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).
Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Índice
- [Colunas customizadas](#colunas-customizadas)
  - [A função CONCAT](#a-função-concat)
  - [AS](#as)
  - [Operadores aritméticos](#operadores-aritméticos)
- [Funções](#funções)
  - [A função UPPER](#a-função-upper)
  - [SQRT e AVG](#sqrt-e-avg)
  - [A função SUM](#a-função-sum)
- [Sub consultas](#sub-consultas)

# [Colunas customizadas](#índice)
### [A função CONCAT](#índice)
A função `CONCAT` é usada para combinar dois ou mais valores textuais e retornar o texto combinado. 

Vamos combinar Nome com Cidade separando com vírgula:
```sql
SELECT CONCAT(Nome, ',', Cidade) FROM customers;
```
Resultado:

CONCAT(Nome, ' , ' , Cidade)|
---|
John, Nova York|
David, Los Angeles|
Chloe, Chicago|
Emily, Houston|
James, Filadélfia|
Andrew, Nova York|
Daniel, Nova York|
Charlotte, Chicago|
Samuel, San Diego|
Anthony, Los Angeles|

A função `CONCAT()` leva dois ou mais parâmetros.
### [AS](#índice)
Usar `CONCAT` resulta em uma nova coluna. Há um nome padrão para essa coluna-resultado. Você pode mudar o nome dela usando o comando `AS`:
```sql
SELECT CONCAT(Nome,', ', Cidade) AS nova_coluna
FROM clientes;
```
E quando você executar a consulta, o nome da coluna terá sido mudado:

nova_coluna|
---|
John, Nova York|
David, Los Angeles|
Chloe, Chicago|
Emily, Houston|
James, Filadélfia|
Andrew, Nova York|
Daniel, Nova York|
Charlotte, Chicago|
Samuel, San Diego|
Anthony, Los Angeles|

### [Operadores aritméticos](#índice)
Operadores aritméticos fazem operações aritméticas com operadores numéricos. Os operadores aritméticos incluem: adição (+), subtração (-), multiplicação (*) e divisão (/). 

A tabela __trabalhadores__ a seguir mostra nomes de trabalhadores e salários:

ID|Nome|Sobrenome|Salario
---|---|---|---
1|John|Smith|2000
2|David|Williams|1500
3|Chloe|Anderson|3000
4|Emily|Adams|4500
5|James|Roberts|2000
6|Andrew|Thomas|2500
7|Daniel|Harris|3000
8|Charlotte|Walker|3500
9|Samuel|Clark|4000
10|Anthony|Young|5000

O exemplo abaixo adiciona 500 a cada salário e seleciona o resultado:
```sql
SELECT ID, Nome, Sobrenome, Salario+500 AS Salario
FROM trabalhadores;
```
__Resultado:__

ID|Nome|Sobrenome|Salario
---|---|---|---
1|John|Smith|2500
2|David|Williams|2000
3|Chloe|Anderson|3500
4|Emily|Adams|5000
5|James|Roberts|2500
6|Andrew|Thomas|3000
7|Daniel|Harris|3500
8|Charlotte|Walker|4000
9|Samuel|Clark|4500
10|Anthony|Young|5500

Parênteses podem ser usados para indicar operações que precisam ser executadas primeiro. Também são usados para melhorar a leitura do código.
# [Funções](#índice)
### [A função UPPER](#índice)
A função `UPPER` converte todas as letras de um texto específico para letras maiúsculas.<br>A função `LOWER` converte o texto para letras minúsculas.

A seguinte consulta SQL coloca todos os Sobrenome em maiúsculo:
```sql
SELECT Nome, UPPER(Sobrenome) AS Sobrenome
FROM trabalhadores;
```
__Resultado:__

Nome|Sobrenome
---|---
John|SMITH
David|WILLIAMS
Chloe|ANDERSON
Emily|ADAMS
James|ROBERTS
Andrew|THOMAS
Daniel|HARRIS
Charlotte|WALKER
Samuel|CLARK
Anthony|YOUNG

Se há caracteres no texto que não são letras, essa função não terá efeito nelas. 

### [SQRT e AVG](#índice)
A função `SQRT` retorna a raiz quadrada de um valor passado como argumento. 

Vamos calcular a raiz quadrada de cada salário:
```sql
SELECT Salario, SQRT(Salario)
FROM trabalhadores;
```
__Resultado:__

Salario|SQRT(Salario)
---|---
2000|44.72
1500|38.72
3000|54.77
4500|67.08
2000|44.72
2500|50
3000|54.77
3500|59.16
4000|63.24
5000|70.71

De maneira similar, a função `AVG` retorna a média de uma coluna numérica:
```sql
SELECT AVG(Salario) FROM trabalhadores;
```
__Resultado:__

AVG(Salario)|
---|
3100.0000|

Outra maneira de fazer o `SQRT` é usar `POWER` com o expoente 1/2. Entretanto, `SQRT` parece executar mais rapidamente do que `POWER` neste caso.
### [A função SUM](#índice)
A função `SUM` é usada para calcular a soma dos valores de uma coluna. 

Por exemplo, para saber a soma de todos os salários da tabela trabalhadores, nossa consulta SQL ficaria assim:
```sql
SELECT SUM(Salario) FROM trabalhadores;
```
__Resultado:__

SUM(Salario)|
---|
31000|

A soma de todos os salários é 31000
# [Sub consultas](#índice)
Uma __subconsulta__ é uma consulta dentro de outra consulta. 

Se quisermos a lista de todos os empregados cuja os salários são __maiores__ do que a média, primeiro calculamos a média:
```sql
SELECT AVG(Salario) FROM trabalhadores;
```
Como já sabemos a média, podemos usar um simples `WHERE` para listar os salários que são maiores que esse número.
```sql
SELECT Nome, Salario FROM trabalhadores
WHERE Salario > 3100
ORDER BY Salario DESC;
```
__Resultado:__

Nome|Salario
---|---
Anthony|5000
Emily|4500
Samuel|4000
Charlotte|3500

O `DESC` classifica os resultados em ordem __decrescente__.<br>De maneira similar, o `ASC` classifica os resultados em ordem __crescente__. 

Uma única subconsulta retornará o mesmo resultado mais facilmente.
```sql
SELECT Nome, Salario FROM trabalhadores
WHERE Salario > (SELECT AVG(Salario) FROM trabalhadores)
ORDER BY Salario DESC;
```
O mesmo resultado será mostrado.

Nome|Salario
---|---
Anthony|5000
Emily|4500
Samuel|4000
Charlotte|3500

Coloque a subconsulta entre __parênteses__.<br>Note que não há ponto e vírgula no fim da subconsulta, pois é parte da nossa única consulta.

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

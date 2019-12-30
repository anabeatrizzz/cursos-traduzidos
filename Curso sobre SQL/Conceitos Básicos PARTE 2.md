Este curso é de propriedade do aplicativo SoloLearn e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

- [Selecionando múltiplas colunas](#selecionando-múltiplas-colunas)
  - [Selecionando todas as colunas](#selecionando-todas-as-colunas)
- [DISTINCT e LIMIT](#distinct-e-limit)
  - [O comando DISTINCT](#o-comando-distinct)
  - [O comando LIMIT](#o-comando-limit)
- [Classificando resultados](#classificando-resultados)
  - [Nome totalmente qualificado](#nome-totalmente-qualificado)
  - [ORDER BY](#order-by)
  - [Classificando múltiplas colunas](#classificando-múltiplas-colunas)

# Selecionando múltiplas colunas
#### [Voltar ao indice](#indice)
Como citado anteriormente, a afirmação SELECT do SQL retorna registros de tabelas no seu banco de dados SQL. 

Você pode selecionar múltiplas colunas de uma vez. Apenas liste os nomes das colunas separadas por vírgulas:

```sql
SELECT Nome, Sobrenome, Cidade
FROM clientes;
```
Resultado:

Nome | Sobrenome | Cidade
-|-|-|
John | Smith | Nova York
David | Williams | Los Angeles
Chloe | Anderson | Chicago
Emily | Adams | Houston
James | Roberts | Filadelfia

Não coloque uma vírgula depois do último nome da coluna. 
### Selecionando todas as colunas
#### [Voltar ao indice](#indice)
Para retornar toda a informação contida em sua tabela, coloque um asterisco depois do comando SELECT, invés de escrever cada nome das colunas separadamente.

A seguinte afirmação SQL seleciona todas as colunas da tabela clientes:

```sql
SELECT * FROM clientes;
```
Resultado:

ID | Nome | Sobrenome | Cidade | CodigoPostal
-|-|-|-|-
1 | John | Smith | Nova York | 10199
2 | David | Williams | Los Angeles | 90052
3 | Chloe | Anderson | Chicago | 60607
4 | Emily | Adams | Houston | 77201
5 | James | Roberts | Filadelfia | 19104

Em SQL, o asterisco significa "todos".
# DISTINCT e LIMIT
#### [Voltar ao indice](#indice)
### O comando DISTINCT
#### [Voltar ao indice](#indice)
Quando você tem registros duplicados em uma tabela, faz sentido mostrar apenas registros únicos, invés de mostrar os duplicados. 

O comando `DISTINCT` do SQL é usado em conjunto com o `SELECT` para eliminar todos os registros duplicados e mostrar apenas os registros únicos. 

A sintaxe básica do `DISTINCT` é a seguinte:

```sql
SELECT DISTINCT coluna1, coluna2
FROM tabela;
```
Veja a tabela clientes abaixo:

ID | Nome | Sobrenome | Cidade
-|-|-|-
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
4|Emily|Adams|Houston
5|James|Roberts|Filadelfia
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York
8|Charlotte|Walker|Chicago
9|Samuel|Clark|San Diego
10|Anthony|Young|Los Angeles

Veja que há nomes duplicados de cidade. A seguinte afirmação SQL seleciona apenas valores distintos da coluna Cidade:

```sql
SELECT DISTINCT Cidade FROM clientes;
```
Isso mostraria o seguinte resultado. Registros duplicados foram removidos.

Cidade|
-|
Nova York|
Los Angeles|
Chicago|
Houston|
Filadelfia|
San Diego|

O comando `DISTINCT` apenas busca por valores únicos.
### O comando LIMIT
#### [Voltar ao indice](#indice)
Por padrão, todos os resultados que satisfazem as condições especificadas na afirmação SQL são retornados. Entretanto, às vezes precisamos retornar apenas alguns registros. No MySQL, isso é feito usando o comando `LIMIT`. 

A sintaxe do `LIMIT` é a seguinte:

```sql
SELECT colunas
FROM tabela
LIMIT numero_de_registros;
```
Por exemplo, podemos retornar os primeiros cinco registros da tabela clientes.

```sql
SELECT ID, Nome, Sobrenome, Cidade
FROM clientes LIMIT 5;
```
Iríamos ter o seguinte resultado:

ID|Nome|Sobrenome|Cidade
-|-|-|-
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
4|Emily|Adams|Hoston
5|James|Roberts|Filadelfia

Você também pode escolher registros usando uma determinada ordem.
No exemplo a seguir, escolhemos quatro registros, começando da terceira posição:

```sql
SELECT ID, Nome, Sobrenome, Cidade
FROM clientes LIMIT 3, 4;
```
Retornado o seguinte resultado:

ID|Nome|Sobrenome|Cidade
-|-|-|-
4|Emily|Adams|Houston
5|James|Roberts|Filadelfia
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York

O motivo pelo qual é mostrado resultados a partir do ID número 4 (e não 3) é que o MySQL começa contando do zero, significando que a primeira Iinha começa do número 0 (e não 1).
# Classificando resultados
#### [Voltar ao indice](#indice)
### Nome totalmente qualificado
#### [Voltar ao indice](#indice)
Em SQL, você pode colocar o nome da tabela antes do nome da coluna fazendo a separação com um ponto final.
As seguintes afirmações são equivalentes:

```sql
SELECT Cidade FROM clientes;
```
```sql
SELECT clientes.Cidade FROM clientes;
```
O termo para a sintaxe mencionada acima é chamado de “nome totalmente qualificado" da coluna.

Essa forma de escrita é útil especialmente quando estamos trabalhando com múltiplas tabelas que podem ter mesmos nomes de colunas.

### ORDER BY
#### [Voltar ao indice](#indice)
É usado com o `SELECT` para classificar os dados retornados. 
O exemplo a seguir classifica nossa tabela clientes pela coluna Nome.

```sql
SELECT * FROM clientes
ORDER BY Nome;
```
Resultado:

ID | Nome | Sobrenome | Cidade
-|-|-|-
6|Andrew|Thomas|Nova York
10|Anthony|Young|Los Angeles
8|Charlotte|Walker|Chicago
3|Chloe|Anderson|Chicago
7|Daniel|Harris|Nova York
2|David|Williams|Los Angeles
4|Emily|Adams|Houston
5|James|Roberts|Filadelfia
1|John|Smith|Nova York
9|Samuel|Clark|San Diego

Como pode ver, as linhas estão ordenadas de maneira alfabética pela coluna Nome.

Por padrão, o comando `ORDER BY` classifica os resultados em ordem crescente.
### Classificando múltiplas colunas
#### [Voltar ao indice](#indice)
Quando estiver usando `ORDER BY` com mais de uma coluna, separe a lista de colunas com vírgulas. Aqui está a tabela clientes mostrando os seguintes registros:

ID | Nome | Sobrenome | Idade
-|-|-|-
1|John|Smith|35
2|David|Williams|23
3|Chloe|Anderson|27
4|Emily|Adams|34
5|James|Roberts|31
6|Andrew|Thomas|45
7|Daniel|Harris|30

Classificando por Sobrenome e Idade:

```sql
SELECT * FROM clientes
ORDER BY Sobrenome, Idade;
```
Essa afirmação `ORDER BY` retorna o seguinte resultado:

ID | Nome | Sobrenome | Idade
-|-|-|-
4|Emily|Adams|34
3|Chloe|Anderson|27
7|Daniel|Harris|30
5|James|Roberts|31
2|David|Williams|23
1|John|Smith|35
6|Andrew|Thomas|45

Como temos dois Smiths, eles irão ser ordenados pela coluna Idade em ordem crescente. 

O comando `ORDER BY` começa a classificar na sequência das colunas. Irá classificar pela primeira coluna listada e então pela segunda, assim em diante.

Este curso é de propriedade do aplicativo SoloLearn e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).
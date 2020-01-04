Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Indice
- [INSERT](#insert)
	- [Inserindo dados](#inserindo-dados)
- [UPDATE e DELETE](#update-e-delete)
	- [Atualizando dados](#atualizando-dados)
	- [Atualizando múltiplas colunas](#atualizando-múltiplas-colunas)
	- [Deletando dados](#deletando-dados)
- [Criando uma tabela](#criando-uma-tabela)
	- [Tabelas do SQL](#tabelas-do-sql)
	- [Tipos de dados](#tipos-de-dados)
	- [Chave primaria](#chave-primaria)

# [INSERT](#indice)
### [Inserindo dados](#indice)
As tabelas do SQL armazenam dados em linhas, uma embaixo da outra. A afirmação `INSERT INTO` é usada para adicionar novas linhas de dados a uma tabela do banco de dados.<br>A sintaxe do `INSERT INTO` é a seguinte:
```sql
INSERT INTO nome_da_tabela
VALUES (valor1, valor2, valor3,...);
```
Certifique-se que a ordem dos valores é a mesma que a ordem das colunas na tabela.

Veja a tabela __trabalhadores__ a seguir:

ID|Nome|Sobrenome|Idade
---|---|---|---
1|Emily|Adams|34
2|Chloe|Anderson|27
3|Daniel|Harris|30
4|James|Roberts|31
5|John|Smith|35
6|Andrew|Thomas|45
7|David|Williams|23

Use a seguinte afirmação SQL para inserir uma nova linha:
```sql
INSERT INTO trabalhadores
VALUES (8, 'Anthony', 'Young', 35);
```
Os valores são separados por vírgula e sua ordem corresponde as colunas na tabela.<br>__Resultado:__

ID|Nome|Sobrenome|Idade
---|---|---|---
1|Emily|Adams|34
2|Chloe|Anderson|27
3|Daniel|Harris|30
4|James|Roberts|31
5|John|Smith|35
6|Andrew|Thomas|45
7|David|Williams|23
8|Anthony|Young|35

Quando você coloca registros em uma tabela usando o `INSERT`, você deve fornecer um valor para cada coluna que não tem um valor padrão ou que não suporta valores nulos.

De modo alternativo, você pode especificar os nomes das colunas da tabela na afirmação `INSERT INTO`:
```sql
INSERT INTO nome_da_tabela(coluna1, coluna2, coluna3, ...,colunaN)
VALUES(valor1, valor2, valor3,...valorN);
```
coluna1, coluna2, ..., colunaN são os nomes das colunas onde você deseja colocar dados.
```sql
INSERT INTO trabalhadores(ID, Nome, Sobrenome, Idade)
VALUES(8, 'Anthony', 'Young', 35);
```
Isso irá inserir os dados dentro das colunas correspondentes:

ID|Nome|Sobrenome|Idade
---|---|---|---
1|Emily|Adams|34
2|Chloe|Anderson|27
3|Daniel|Harris|30
4|James|Roberts|31
5|John|Smith|35
6|Andrew|Thomas|45
7|David|Williams|23
8|Anthony|Young|35

Você pode colocar as colunas em qualquer ordem contanto que os valores estejam ordenados da mesma maneira.

Também é possível inserir dados em apenas colunas __específicas__.
```sql
INSERT INTO trabalhadores(ID, Nome, Sobrenome)
VALUES(9, 'Samuel', 'Clark');
```
__Resultado:__

ID|Nome|Sobrenome|Idade
---|---|---|---
1|Emily|Adams|34
2|Chloe|Anderson|27
3|Daniel|Harris|30
4|James|Roberts|31
5|John|Smith|35
6|Andrew|Thomas|45
7|David|Williams|23
8|Anthony|Young|35
9|Samuel|Clark|0

Na coluna Idade há o valor 0 pois, esse é o valor padrão. 

# [UPDATE e DELETE](#indice)
### [Atualizando dados](#indice)
A afirmação `UPDATE` nos permite alterar os dados em uma tabela. 

A sintaxe básica de um `UPDATE` com um `WHERE` é a seguinte:
```sql
UPDATE nome_da_tabela
SET colunal = valorl, coluna2 = valor2, ...
WHERE condition;
```
Você indica a coluna e seu novo valor em uma lista separada por vírgula depois de `SET`. 

Se você não escrever um `WHERE`, __todos__ os registros da tabela irão ser atualizados!

Veja a seguinte tabela chamada "trabalhadores":

ID|Nome|Sobrenome|Salario
---|---|---|---
1|John|Smith|2000
2|David|Williams|1500
3|Chloe|Anderson|3000
4|Emily|Adams|4500

Para atualizarmos o salário do John, podemos usar a seguinte consulta: 
```sql
UPDATE trabalhadores
SET Salario = 5000
WHERE ID = 1;
```
__Resultado:__

ID|Nome|Sobrenome|Salario
---|---|---|---
1|John|Smith|__5000__
2|David|Williams|1500
3|Chloe|Anderson|3000
4|Emily|Adams|4500

### [Atualizando múltiplas colunas](#indice)
Também é possível atualizar múltiplas colunas ao mesmo tempo as separando com vírgulas:
```sql
UPDATE trabalhadores
SET Salario = 5000, Nome = 'Robert'
WHERE ID = 1;
```

ID|Nome|Sobrenome|Salario
---|---|---|---
1|__Robert__|Smith|__5000__
2|David|Williams|1500
3|Chloe|Anderson|3000
4|Emily|Adams|4500

Você pode colocar a ordem que quiser no `SET`.

### [Deletando dados](#indice)
A afirmação `DELETE` é usada para remover dados de uma tabela. As consultas `DELETE` funciona do mesmo jeito que as consultas `UPDATE`.
```sql
DELETE FROM nome_da_tabela
WHERE condição;
```
Por exemplo, você pode excluir um empregado específico da tabela:
```sql
DELETE FROM trabalhadores
WHERE ID = 1;
```

ID|Nome|Sobrenome|Salario
---|---|---|---
2|David|Williams|1500
3|Chloe|Anderson|3000
4|Emily|Adams|4500

Se você não escrever um `WHERE`, __todos__ os registros da tabela irão ser apagados!<br>A afirmação `DELETE` remove os dados da tabela permanentemente.

# [Criando uma tabela](#indice)
### [Tabelas do SQL](#indice)
Um único banco de dados pode armazenar várias tabelas, cada uma tendo seu papel no esquema do banco de dados. 

As tabelas do SQL são compostas de linhas e colunas. As colunas das tabelas são responsáveis por armazenar muitos tipos de dados, incluindo números, textos, datas e até mesmo arquivos. 

A afirmação `CREATE TABLE` é usada para criar uma nova tabela. 

Para criar uma tabela, você precisa nomeá-la, definir suas colunas e definir cada tipo de dado.

A sintaxe básica da afirmação `CREATE TABLE` é a seguinte:
```sql
CREATE TABLE table_name (  
   nome_da_coluna1 tipo_de_dado(tamanho),  
   nome_da_coluna2 tipo_de_dado(tamanho),  
   nome_da_coluna3 tipo_de_dado(tamanho),  
   ....  
   nome_da_colunaN tipo_de_dado(tamanho)  
);
```
\- Os __nome_da_coluna__ indicam os nomes das colunas que queremos criar.<br>- O parâmetro __tipo_de_dado__ indica qual é o tipo de dado das tabelas. Por exemplo, use `int` se uma coluna apenas pode receber números inteiros.<br>- O parâmetro __tamanho__ indica o comprimento máximo da coluna da tabela. 

Note os __parênteses__ na sintaxe.

Suponhamos que você queira criar uma tabela chamada "usuarios" que consiste em quatro colunas: UsuariolD, Sobrenome, Nome e Cidade. 

Use a seguinte afirmação `CREATE TABLE`:
```sql
CREATE TABLE usuarios(  
   UsuarioID INT,  
   Nome VARCHAR(100),
   Sobrenome VARCHAR(100),
   Cidade VARCHAR(100)
);
```
`varchar` é o tipo de dado que armazena caracteres. Você indica o número de caracteres dentro de parênteses depois do tipo. No exemplo acima, as colunas podem conter um texto que tenha no máximo __100__ caracteres. 
### [Tipos de dados](#indice)
Especificam o tipo de dado de uma coluna. 

Se uma coluna chamada "Sobrenome" irá armazenar nomes, então o tipo de dado dessa coluna deve ser "varchar" (caractere de comprimento variável).

Os tipos de dados mais comuns:<br>__**Numéricos**__<br>`INT` - Um número inteiro de tamanho normal<br>`FLOAT`(M, D) - Um número com vírgula. Você pode definir o comprimento (M) e o número de decimais (D).<br>`DOUBLE`(M, D) - Um número com vírgula. Você pode definir o comprimento (M) e o número de decimais (D).

__**Data e hora**__<br>`DATE` - Uma data no formato AAAA-MM-DD. <br>`DATETIME` - Uma combinação de data e hora no formato AAAA-MM-DD HH:MM:SS.<br>`TIMESTAMP` - Um registro de data e hora, calculado a partir da meia-noite de 1° de janeiro de 1970.<br>`TIME` - Armazena horas no formato HH:MM:SS.

__**Texto**__<br>`CHAR`(M) - Texto de comprimento fixo. O tamanho é especificado em parênteses. Máximo de 255 bytes.<br>`VARCHAR`(M) - Texto de comprimento variável. O tamanho máximo é especificado em parênteses.<br>`BLOB` - São usados para armazenar grandes quantidades de dados binários, como imagens ou outros tipos de arquivos.<br>`TEXT` - Grandes quantidades de dados textuais. 

Escolher o tipo de dado correto para as colunas é a chave para o bom design do banco de dados.
### [Chave primaria](#indice)
O UsuariolD é a melhor opção de chave primária para nossa tabela usuarios.<br>Defina a chave primária durante a criação da tabela usando `PRIMARY KEY`.
```sql
CREATE TABLE Users(
   UsuarioID INT,
   Nome VARCHAR(100),
   Sobrenome VARCHAR(100),
   Cidade VARCHAR(100),
   PRIMARY KEY(UsuarioID)
);
```
Especifique o nome da coluna nos parênteses do `PRIMARY KEY`.

Quando executamos a consulta, nossa tabela irá ser criada no banco de dados.

UsuarioID|Nome|Sobrenome|Cidade
---|---|---|---
 | | | 
 | | | 
 | | | 

Agora você pode usar INSERT INTO's para inserir dados na tabela.

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

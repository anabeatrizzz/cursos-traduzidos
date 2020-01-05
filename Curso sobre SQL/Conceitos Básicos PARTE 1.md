Este curso é de propriedade do aplicativo SoloLearn e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Indice
- [Introdução ao banco de dados](#introdução-ao-banco-de-dados)
  - [Um banco de dados](#um-banco-de-dados)
  - [As tabelas do banco de dados](#as-tabelas-do-banco-de-dados)
  - [Chaves primárias](#chaves-primárias)
  - [O que é SQL?](#o-que-é-sql)
- [Comandos SQL: SELECT](#comandos-sql-select)
  - [Comandos básicos SQL](#comandos-básicos-sql)
  - [O comando SELECT](#o-comando-select)
- [Regras de sintaxe SQL](#regras-de-sintaxe-sql)
  - [Multiplas consultas](#multiplas-consultas)
  - [Sensibilidade](#sensibilidade)
  - [Regras de sintaxe](#regras-de-sintaxe)

# [Introdução ao banco de dados](#indice)
### [Um banco de dados](#indice)
Um banco de dados é uma coleção de dados que é organizada de uma maneira que facilita o acesso, o gerenciamento e a atualização.

Um banco de dados é feito de tabelas que armazenam informações relevantes.

Por exemplo, você usaria um banco de dados se você fosse criar um site como o YouTube, que contém várias informações como vídeos, nomes de usuário, senhas e comentários.

![Imagem da tabela](http://i.imgur.com/88mRdYa.png)

### [As tabelas do banco de dados](#indice)
Uma tabela armazena e mostra dados de forma estruturada por colunas e linhas, semelhante às planilhas do Excel.

Bancos de dados frequentemente contêm múltiplas tabelas, cada uma designada para um propósito. Por exemplo, imagine criar uma tabela que contenha nomes e números de telefone. 

Primeiro, iríamos criar colunas chamadas Nome, Sobrenome e Telefone. 

Cada tabela contém seus campos, baseado no que irá armazenar.

Nome | Sobrenome | Telefone
-----|-----------|---------
John | Smith | 13 9 7155-5512
David | Williams | 11 9 5691-9997
Chloe | Anderson | 12 9 2010-7777
Emily | Adams | 14 9 5663-3312
James | Roberts | 15 9 7637-7729

Uma tabela tem um número específico de colunas mas pode conter quantas linhas quiser.
### [Chaves primárias](#indice)
Uma chave primária é um campo na tabela que, unicamente, identifica os registros da tabela.

As principais características das chaves primárias são:
* Devem conter um valor único para cada linha.
* Não podem conter valores nulos.

Por exemplo, nossa tabela contém um registro para cada nome em uma lista telefônica. A coluna ID seria uma boa escolha de chave primária pois, há a chance de duas pessoas terem o mesmo nome.

ID | Nome | Sobrenome | Telefone
-|-|-|-
1 | John | Smith | 13 9 7155-5512
2 | David | Williams | 11 9 5691-9997
3 | Chloe | Anderson | 12 9 2010-7777
4 | Emily | Adams | 14 9 5663-3312
5 |James | Roberts | 15 9 7637-7729

* Cada tabela apenas pode ter UMA chave primária.
* O valor da chave primária deve ser diferente para cada linha.
### [O que é SQL?](#indice)
Quando você entende o que é um banco de dados, saber o que é SQL fica fácil. SQL significa Structured Query Language (Linguagem Estruturada para Consultas)

SQL é usado para acessar e manipular um banco de dados. MySQL é um programa que entende SQL.

O SQL pode:
* inserir, atualizar ou deletar registros em um banco de dados.
* criar novos bancos de dados, tabelas, procedimentos armazenados, views.
* recuperar dados do banco de dados, etc.

SQL é de padrão ANSI, mas há diferentes versões da linguagem SQL. A maioria dos programas de bancos de dados SQL tem suas próprias propriedades adicionadas, mas todas elas suportam os comandos principais.

# [Comandos SQL: SELECT](#indice)
### [Comandos básicos SQL](#indice)
A afirmação `SHOW` mostra informação que está no banco de dados e em suas tabelas. Essa ferramenta útil te deixa observar o conteúdo do seu banco de dados e te lembrar da estrutura de suas tabelas.
Por exemplo, o comando `SHOW DATABASES` lista os bancos de dados gerenciados pelo servidor.

O comando `SHOW TABLES` é usado para mostrar todas as tabelas no banco de dados MySQL selecionado.

`SHOW COLUMNS` mostra informação sobre as colunas de uma tabela específica.
O seguinte exemplo mostra as colunas em nossa tabela clientes:

Field | Type | Null | Key | Default | Extra
-|-|-|-|-|-
ID | int(11) | NO | PRI | NULL
Nome | varchar(60) | NO | |NULL
Sobrenome | varchar(60) | NO | | NULL
Cidade | varchar(30) | NO | | NULL
CodigoPostal | int(10) | NO | | NULL

`SHOW COLUMNS` mostra os seguintes valores para cada coluna da tabela: 

__Field__: nome da coluna.

__Type__: tipo de dado da coluna.

__Key__: indica se a coluna é indexada.

__Default__: valor padrão referido a coluna.

__Extra__: pode conter qualquer informação adicional disponível sobre uma coluna específica.
### [O comando SELECT](#indice)
É usado para selecionar dados de um banco de dados. O resultado é armazenado em uma tabela de resultados, que é chamada de result-set. 

Uma consulta pode recuperar informação de colunas selecionadas ou de todas as colunas da tabela. Para criar uma afirmação `SELECT` simples, especifique o(s) nome(s) da(s) coluna(s) que você precisa.

Sintaxe:

```sql
SELECT colunas
FROM tabela
```

- __colunas__ inclui uma ou mais colunas de cada dado recuperado
- __tabela__ é o nome de cada tabela de onde a informação é recuperada.

Abaixo está os dados da nossa tabela clientes:

ID | Nome | Sobrenome | Cidade | CodigoPostal
-|-|-|-|-
1 | John | Smith | Nova York | 10199
2 | David | Williams | Los Angeles | 90052
3 | Chloe | Anderson | Chicago | 60607
4 | Emily | Adams | Houston | 77201
5 | James | Roberts | Filadelfia | 19104

A seguinte afirmação SQL seleciona o Nome da tabela clientes:

```sql
SELECT Nome FROM clientes
```

Nome|
----|
John|
David|
Chloe|
Emily|
James|

Uma afirmação `SELECT` retorna zero ou mais linhas de uma ou mais tabelas do banco de dados.
# [Regras de sintaxe SQL](#indice)
### [Multiplas consultas](#indice)
SQL permite executar múltiplas consultas ou comandos ao mesmo tempo. 

A seguinte afirmação SQL seleciona as colunas Nome e Cidade da tabela clientes: 

```sql
SELECT Nome FROM clientes;
SELECT Cidade FROM clientes;
```
Resultado:

Nome|
----|
John|
David|
Chloe|
Emily|
James|

Cidade|
------|
Nova York|
Los Angeles|
Chicago|
Houston|
Filadelfia|

Lembre-se de terminar cada afirmação SQL com ponto e vírgula para indicar que a afirmação está completa e pronta para ser interpretada. Nesse tutorial, usaremos ponto e vírgula no fim de cada afirmação SQL.
### [Sensibilidade](#indice)
SQL não diferencia entre letras maiúsculas e minúsculas.
As seguintes afirmações são equivalentes e irão mostrar o mesmo resultado:

```sql
select Cidade from clientes;
SELECT Cidade FROM cleintes;
sElEct Cidade From clientes; 
```
É comum praticar a escrita de todos os comandos SQL em letras maiúsculas.
### [Regras de sintaxe](#indice)
Uma única afirmação SQL pode ser colocada em uma ou mais linhas. Além disso, múltiplas afirmações SQL podem ser combinadas em uma única linha. 

Espaços em branco e múltiplas linhas são ignoradas no SQL. Por exemplo, a consulta a seguir está absolutamente correta.

```sql
SELECT       Cidade
FROM clientes;
```
Entretanto, é recomendado evitar linhas e espaços em branco desnecessários.

Espaçamento apropriado e indentação separa os comandos fazendo com que suas afirmações SQL fiquem fáceis de ler e editar.

Este curso é de propriedade do aplicativo SoloLearn e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

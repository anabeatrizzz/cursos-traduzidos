Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# NOT NULL e AUTO_INCREMENT
### Restrições do SQL
As __restrições__ do SQL são usadas para especificar regras para os dados da tabela. 

As restrições mais comuns do SQL são as seguintes:<br>`NOT NULL` - Indica que uma coluna não pode conter qualquer valor nulo.<br>`UNIQUE` - Não permite inserir um valor duplicado em uma coluna. A limitação `UNIQUE` mantém a singularidade de uma coluna em uma tabela. Mais de uma coluna pode ter a limitação `UNIQUE` em uma tabela.<br>`PRIMARY KEY` - Força a tabela a aceitar dados únicos para uma coluna específica e essa limitação cria um índice único para acessar a tabela rapidamente.<br>`CHECK` - Determina se o valor de uma expressão lógica é válido ou não.<br>`DEFAULT` - Quando colocamos dados na tabela, se nenhum valor é fornecido para uma coluna, então a coluna tem o valor estabelecido como `DEFAULT`.

Por exemplo, o seguinte código diz que a coluna __nome__ não permite valores nulos.
```sql
nome VARCHAR(100) NOT NULL
```
Durante a criação da tabela, especifique as restrições das colunas depois do tipo de dado da coluna.
### AUTO INCREMENT
O incremento automático permite que um número único seja gerado quando um novo registro é inserido na tabela. 

Frequentemente, queremos que o valor da chave primária seja criado automaticamente cada vez que inserimos um novo registro. 

Por padrão, o valor de início do `AUTO_INCREMENT` é 1 e irá incrementar de um em um para cada novo registro.<br>Vamos estabelecer o campo UsuariolD como a chave primária que automaticamente gera um novo valor:
```sql
UsuarioID INT NOT NULL AUTO_INCREMENT,
PRIMARY KEY (UsuarioID)
```
### Usando restrições
O exemplo abaixo demonstra como criar uma tabela usando limitações.
```sql
CREATE TABLE Usuarios (
	id INT NOT NULL AUTO_INCREMENT,
	nome_de_usuario VARCHAR(40) NOT NULL,
	senha VARCHAR(10) NOT NULL,
	PRIMARY KEY(id) 
);
```
O seguinte SQL afirma que as colunas "id", "nome_de_usuario" e "senha" não aceitam valores nulos. Também definimos um auto incremento para o campo da chave primária.<br>__Aqui está o resultado:__

#|Coluna|Tipo|Nulo|Padrão|Extra
---|---|---|---|---|---
1|id|INT(11)|Não|Nenhum|AUTO_INCREMENT
2|nome_de_usuario|VARCHAR(40)|Não|Nenhum|
3|senha|VARCHAR(10)|Não|Nenhum|

Quando inserimos um novo registro na tabela usuarios, não é necessário especificar um valor para a coluna id; um valor único será adicionado automaticamente.
# Alternando, eliminando e renomeando uma tabela
### ALTER TABLE
O comando `ALTER TABLE` é usado para adicionar, deletar ou modificar colunas em uma tabela existente. Você também usaria o `ALTER TABLE` para adicionar várias limitações em uma tabela existente. 

Considere a seguinte tabela chamada __pessoas__:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago

O seguinte código SQL adiciona uma nova coluna chamada AnoDeNascimento:
```sql
ALTER TABLE pessoas ADD AnoDeNascimento date;
```

ID|Nome|Sobrenome|Cidade|AnoDeNascimento
---|---|---|---|---
1|John|Smith|Nova York|_NULL_
2|David|Williams|Los Angeles|_NULL_
3|Chloe|Anderson|Chicago|_NULL_

Todas as linhas tem o valor padrão na coluna nova adicionada, que, neste caso, é `NULL`.
### Eliminando
O código SQL a seguir demonstra como apagar a coluna chamada AnoDeNascimento da tabela pessoas.
```sql
ALTER TABLE pessoas
DROP COLUMN AnoDeNascimento;
```
A tabela pessoas irá ficar assim:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago

A coluna, junto com todos seus dados, irá ser completamente removida da tabela.

Para apagar a tabela inteira, use o comando `DROP TABLE`:
```sql
DROP TABLE pessoas;
```
Tenha cuidado ao apagar uma tabela. Apagar uma tabela resultará na perda total da informação armazenada na tabela!

### Renomeando
O comando `ALTER TABLE` também é usado para renomear colunas:
```sql
ALTER TABLE pessoas
CHANGE Nome name VARCHAR(100);
```
Essa consulta irá renomear a coluna chamada Nome para name.<br>__Resultado:__

ID|name|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago

Você pode renomear a tabela inteira usando o comando `RENAME`:
```sql
RENAME TABLE pessoas TO usuarios;
```
Isso renomeará a tabela pessoas para usuarios.
# Views
Em SQL, uma view é uma __tabela virtual__ que é baseada na tabela-resultado da afirmação SQL.

Uma view contem linhas e colunas, como uma tabela real. Os campos em uma view são campos de uma ou mais tabelas reais em um banco de dados.

As views nos permitem:<br>- Estruturar dados de uma maneira que usuários ou classes de usuários achem natural ou intuitiva.<br>- Restringir acesso aos dados de tal maneira que o usuário consiga ver e (às vezes) modificar exatamente o que eles precisam.<br>- Resumir dados de varias tabelas e usá-los para gerar relatórios. 

Para criar uma view:
```sql
CREATE VIEW nome_da_view AS
SELECT nome(s)_da(s)_coluna(s)
FROM nome_da_tabela
WHERE condição;
```
A consulta `SELECT` pode ser tão complexa quanto você quiser. Pode conter múltiplos JOINS e outros comandos.
### Criando views
Veja a tabela __trabalhadores__, que contém os seguintes registros:

ID|Nome|Sobrenome|Idade|Salario
---|---|---|---|---
1|Emily|Adams|34|5000
2|Chloe|Anderson|27|10000
3|Daniel|Harris|30|6500
4|James|Roberts|31|5500
5|John|Smith|35|4500
6|Andrew|Thomas|45|6000
7|David|Williams|23|3000

Vamos criar uma view que mostra o nome e o salário de cada trabalhador.
```sql
CREATE VIEW Lista AS
SELECT Nome, Salario
FROM trabalhadores;
```
Agora, você pode consultar a view __Lista__ como se fosse uma tabela de verdade.
```sql
SELECT * FROM Lista;
```
Resultado:

Nome|Salario
---|---
Emily|5000
Chloe|10000
Daniel|6500
James|5500
John|4500
Andrew|6000
David|3000

Uma view sempre mostra dados atualizados! O mecanismo do banco de dados usa a afirmação SQL da view para recriar os dados cada vez que um usuário consulta uma view.
### Atualizando uma view
Você pode atualizar uma view usando a seguinte sintaxe:
```sql
CREATE OR REPLACE VIEW view nome_da_view AS
SELECT nome(s)_da(s)_coluna(s)
FROM nome_da_tabela
WHERE condição;
```
O exemplo abaixo diz para nossa view Lista para incluir também o Sobrenome:
```sql
CREATE OR REPLACE VIEW Lista AS
SELECT Nome, Sobrenome, Salario
FROM trabalhadores;
```
__Resultado:__

Nome|Sobrenome|Salario
---|---|---
Emily|Adams|5000
Chloe|Anderson|10000
Daniel|Harris|6500
James|Roberts|5500
John|Smith|4500
Andrew|Thomas|6000
David|Williams|3000

Você pode apagar uma view com o comando `DROP VIEW`.
```sql
DROP VIEW Lista;
```
Às vezes é mais fácil apagar uma tabela e recriá-la invés de usar o `ALTER TABLE` para mudar a definição da tabela.

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Índice
- [Juntando tabelas](#juntando-tabelas)
- [Tipos de junção](#tipos-de-junção)
	- [Nomes customizados](#nomes-customizados)
	- [LEFT JOIN](#left-join)
	- [RIGHT JOIN](#right-join)
- [UNION](#union)
	- [Conjunto de operações](#conjunto-de-operações)
	- [UNION ALL](#union-all)

# [Juntando tabelas](#índice)
Todas as consultas mostradas até agora foram selecionadas de apenas uma tabela por vez. 

Uma das ferramentas mais benéficas do SQL é a habilidade de combinar dados de duas ou mais tabelas. 

Nas duas tabelas a seguir, a tabela chamada __clientes__ armazena informações sobre clientes:

ID|Nome|Cidade|Idade
---|---|---|---
1|John|Nova York|35
2|David|Los Angeles|23
3|Chloe|Chicago|27
4|Emily|Houston|34
5|James|Filadélfia|31

A tabela __pedidos__ armazena informação sobre pedidos individuais e sua quantidade:

ID|Nome|Cliente_ID|Quantidade
---|---|---|---
1|Livro|3|5000
2|Caixa|5|3000
3|Brinquedo|2|4500
4|Flores|4|1800
5|Bolo|1|6700

No SQL, __"juntar tabelas"__ significa combinar dados de duas ou mais tabelas. Juntar tabelas cria uma __tabela temporária__ mostrando os dados das tabelas que foram juntadas.

Invés de armazenar o nome do cliente em ambas tabelas, a tabela __pedidos__ contem uma referência ao __ID do cliente__ que aparece na tabela clientes. Essa abordagem é mais eficiente, ao invés de armazenar o mesmo valor textual em ambas tabelas.<br>Para selecionarmos os dados correspondentes de ambas tabelas, vamos precisar __juntá-las__ com base nessa condição.

Para juntar as duas tabelas, escreva o nome delas separando com vírgula usando `FROM`:
```sql
SELECT clientes.ID, clientes.Nome, pedidos.Nome, pedidos.Quantidade
FROM clientes, pedidos
WHERE clientes.ID = pedidos.Cliente_ID
ORDER BY clientes.ID;
```
Cada tabela contem as colunas "ID" e "Nome", para selecionarmos o Id e Nome corretos, __nomes totalmente qualificados__ são usados. 

Veja que o `WHERE` "junta" as tabelas por uma condição, o __ID__ da tabela __clientes__ deve ser igual ao __customer_ID__ da tabela __pedidos__.

__Resultado:__

ID|Nome|Nome|Quantidade
---|---|---|---
1|John|Bolo|6700
2|David|Brinquedo|4500
3|Chloe|Bolo|5000
4|Emily|Flores|1800
5|James|Caixa|3000

Os dados retornados mostram os pedidos dos clientes e sua quantidade. 

Indique múltiplas tabelas no `FROM` as separando com vírgulas.

# [Tipos de junção](#índice)
### [Nomes customizados](#índice)
Diferentes nomes podem ser usados para as tabelas também. Você pode encurtar a consulta usando "apelidos" para as tabelas:
```sql
SELECT clie.ID, clie.Nome, pedi.Nome, pedi.Quantidade
FROM clientes AS clie, pedidos AS pedi
WHERE clie.ID = pedi.Cliente_ID
ORDER BY clie.ID;
```
Como pode ver, usamos o apelido da tabela quando queremos indicá-la. 

Os tipos de junção do SQL são as seguintes:<br>- `INNER JOIN`<br>- `LEFT JOIN`<br>- `RIGHT JOIN`

`INNER JOIN` é o mesmo que `JOIN`. Retorna linhas quando há uma combinação entre as tabelas. 

__Sintaxe:__
```sql
SELECT nome(s)_da(s)_coluna(s)
FROM tabela1 INNER JOIN tabela2
ON tabela1.nome_da_coluna = tabela2.nome_da_coluna;
```
Veja que o `ON` específica a condição `INNER JOIN`.

A imagem abaixo demostra como o `INNER JOIN` funciona:

![INNERJOIN](https://i.imgur.com/nlCTPRm.png)

Apenas os registros que combinam com a condição `JOIN` são mostrados.
### [LEFT JOIN](#índice)
Retorna todas as linhas da tabela da esquerda, até mesmo se não há combinação na tabela da direita. 

Isso significa que se não há combinações usando o `ON` na tabela da direita, a junção ainda retornará as linhas da primeira tabela no resultado.

A sintaxe básica do `LEFT JOIN` é a seguinte:
```sql
SELECT tabelal.colunal, tabela2.coluna2...
FROM tabelal LEFT OUTER JOIN tabela2
ON tabelal.nome_da_coluna = tabela2.nome_da_coluna;
```
`OUTER` é opcional e pode ser pagado. 

A imagem a seguir mostra como o `LEFT JOIN` funciona:

![LEFTJOIN](https://i.imgur.com/qVWIxMa.png)

Veja as seguintes tabelas:<br>__clientes:__

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
3|Chloe|Anderson|Chicago
4|Emily|Adams|Houston
5|James|Roberts|Filadélfia
6|Andrew|Thomas|Nova York
7|Daniel|Harris|Nova York

__itens:__

ID|Nome|Custo|Vendedor_ID
---|---|---|---
39|Livro|5,09|1
24|Caixa|2,99|1
72|Brinquedo|23,07|2
36|Flores|50,75|2
18|Camiseta|22,05|3
16|Caderno|150,22|4
74|Perfume|90,09|6

A seguinte afirmação SQL retornará todos os __clientes__ e os __itens__ que talvez tenham:
```sql
SELECT clientes.Nome, itens.Nome
FROM clientes LEFT OUTER JOIN itens
ON clientes.ID = itens.Vendedor_ID;
```
__Resultado:__

Nome|Nome
---|---
John|Livro
John|Caixa
David|Brinquedo
David|Flores
Chloe|Camisa
Emily|Caderno
Andrew|Perfume
James|NULL
Daniel|NULL

A tabela-resultado contem todas as linhas da tabela da esquerda e os dados que combinam da tabela da direita. 

Se nenhuma combinação é encontrada para uma linha, `NULL` é mostrado.

### [RIGHT JOIN](#índice)
Retorna todas as linhas da tabela da direita até mesmo se não há combinações com a tabela da esquerda.

![RIGHTJOIN](https://i.imgur.com/4PJoGJy.png)

A sintaxe básica do `RIGHT JOIN` é a seguinte:
```sql
SELECT tabelal.colunal, tabela2.coluna2...
FROM tabelal RIGHT OUTER JOIN tabela2
ON tabelal.nome_da_coluna = tabela2.nome_da_coluna;
```
De novo, o `OUTER` é opcional e pode ser apagado.

Veja o mesmo exemplo sendo usado com RIGHT JOIN: 
```sql
SELECT clientes.Nome, itens.Nome FROM clientes
RIGHT JOIN itens ON clientes.ID = itens.Vendedor_ID;
```
__Resultado:__

Nome|Nome
---|---
John|Livro
John|Caixa
David|Brinquedo
David|Flores
Chloe|Camisa
Emily|Caderno
Andrew|Perfume

O `RIGHT JOIN` retorna todas as linhas da tabela da direita (itens), mesmo se não há combinações com a tabela da esquerda (clientes).

Há outros tipos de junção em SQL mas não são suportados pelo MySQL.

# [UNION](#índice)
### [Conjunto de operações](#índice)
Você talvez precise combinar dados de múltiplas tabelas formando um conjunto de dados. Podendo ser para tabelas com dados similares dentro do mesmo banco de dados ou talvez há a necessidade de combinar dados similares com outros bancos de dados ou até mesmo com outros servidores. 

Para isso, use os operadores `UNION` e `UNION ALL`.

`UNION` combina múltiplos conjuntos de dados em um único conjunto e remove o que é duplicado.<br>`UNION ALL` combina múltiplos conjuntos de dados em um único conjunto mas não remove linhas duplicadas.

`UNION ALL` é mais rápido do que `UNION` pois, ele não remove linhas duplicadas.

É usado para combinar as tabelas-resultado de duas ou mais afirmações `SELECT`.

Todas as afirmações `SELECT` dentro do `UNION` devem ter o mesmo número de colunas. As colunas devem ter os mesmos tipos de dados. As colunas em cada afirmação `SELECT` devem estar na mesma ordem.<br>A sintaxe do `UNION` é a seguinte:
```sql
SELECT nome(s)_da(s)_coluna(s) FROM tabelal
UNION
SELECT nome(s)_da(s)_coluna(s) FROM tabela2;
```
Aqui está a tabela __primeira__:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles

Aqui está a tabela __segunda__:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|James|Roberts|Filadélfia
2|David|Williams|Los Angeles

```sql
SELECT ID, Nome, Sobrenome, Cidade FROM primeira
UNION 
SELECT ID, Nome, Sobrenome, Cidade FROM segunda;
```
A tabela-resultado será esta:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
1|James|Roberts|Filadélfia

Como podemos ver, as linhas duplicadas foram removidas.

__DICA:__ Se suas colunas não corresponderem exatamente a todas as consultas, você poderá usar um valor NULL (ou qualquer outro), como:
```sql
SELECT Nome, Sobrenome, Empresa FROM contatosDeNegocio 
UNION
SELECT Nome, Sobrenome, NULL FROM outrosContatos;
```
### [UNION ALL](#índice)
Seleciona todas as linhas de cada tabela e as combina numa única tabela. 

A seguinte afirmação SQL usa o `UNION ALL` para selecionar dados das tabelas primeira e segunda:
```sql
SELECT ID, Nome, Sobrenome, Cidade FROM primeira
UNION ALL 
SELECT ID, Nome, Sobrenome, Cidade FROM segunda;
```
A tabela-resultado:

ID|Nome|Sobrenome|Cidade
---|---|---|---
1|John|Smith|Nova York
2|David|Williams|Los Angeles
1|James|Roberts|Filadélfia
2|David|Williams|Los Angeles

Como podemos ver, a tabela-resultado inclui as linhas duplicadas também.

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

# Indice
- [LIKE e MIN](#like-e-min)
  - [LIKE](#like)
  - [A função MIN](#a-função-min)

# [LIKE e MIN](#indice)
### [LIKE](#indice)
É útil quando estamos especificando uma __condição de pesquisa__ dentro de uma afirmação `WHERE`.
```sql
SELECT nome(s)_da(s)_coluna(s)
FROM nome_da_tabela
WHERE nome_da_coluna LIKE padrão;
```
O padrão de combinação do SQL permite que você use "_" para encontrar qualquer caractere e "%" para encontrar um número arbitrário de caracteres (incluindo nenhum caractere). 

Por exemplo, para selecionarmos trabalhadores cuja o primeiro nome comece com a letra __A__, usaríamos a seguinte consulta:
```sql
SELECT * FROM trabalhadores
WHERE Nome LIKE 'A%';
```
__Resultado:__

ID|Nome|Sobrenome|Salario
---|---|---|---
6|Andrew|Thomas|2500
10|Anthony|Young|5000

A seguinte consulta SQL seleciona todos os empregados com o sobrenome terminado em "s":
```sql
SELECT * FROM trabalhadores
WHERE Sobrenome LIKE '%s';
```
__Resultado:__

ID|Nome|Sobrenome|Salario
---|---|---|---
2|David|Williams|1500
4|Emily|Adams|4500
5|James|Roberts|2000
6|Andrew|Thomas|2500
7|Daniel|Harris|3000

O `%` pode ser usado __múltiplas__ vezes dentro do mesmo padrão.
### [A função MIN](#indice)
É usada para retornar o valor mínimo de uma expressão numa afirmação `SELECT`. 

Por exemplo, você talvez queira saber o salário mínimo dos trabalhadores.
```sql
SELECT MIN(Salario) AS Salario FROM trabalhadores;
```

Salario|
---|
1500|

Todas as funções SQL podem ser combinadas para se criar uma única expressão.

Este curso é de propriedade do aplicativo [SoloLearn](https://www.google.com/url?q=https://play.google.com/store/apps/details?id%3Dcom.sololearn&sa=D&ust=1576783845736000&usg=AFQjCNGtodbaSu06Z4kEDTksKn0tg7eK-w) e foi traduzido por [Ana Beatriz Augusto](https://www.linkedin.com/in/anabeatrizz/) usando os recursos [Reverso Context](https://context.reverso.net/translation/) e [Google Tradutor](https://translate.google.com.br/?hl=pt-BR).

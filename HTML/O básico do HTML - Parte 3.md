## Índice
1. [Elementos em bloco e em linha](#elementos-em-bloco-e-em-linha)

	1.1 [Tipos de elementos](#tipos-de-elementos)
2. [Formulários](#formulários)

	2.1 [O elemento `form`](#o-elemento-form)
	
	2.2 [Os atributos `method` e `name`](#os-atributos-method-e-name)
	
	2.3 [Elementos do formulário](#elementos-do-formulário)
3. [Projeto blog: Formulário de contato](#projeto-blog-formulário-de-contato)
4. [Cores no HTML](#cores-no-html)

	4.1 [Modelo de cor do HTML](#modelo-de-cor-do-html)
	
	4.2 [Valores das cores](#valores-das-cores)
	
	4.3 [Cores do fundo e da fonte](#cores-do-fundo-e-da-fonte)
5. [Frames](#frames)

	5.1 [A tag `frame`](#a-tag-frame)
	
	5.2 [Trabalhando com frames](#trabalhando-com-frames)
6. [Projeto blog: Juntando tudo](#projeto-blog-juntando-tudo)

### [Elementos em bloco e em linha](#índice)
#### [Tipos de elementos](#índice)
No HTML, a maioria dos elementos são definidos como __nível de bloco__ ou elementos __em linha__.<br>
Elementos de nível de bloco começam a partir de uma nova linha.<br>
__Por exemplo__: `<h1>`, `<form>`, `<li>`, `<ol>`, `<ul>`, `<p>`, `<pre>`, `<table>`, `<div>`, etc.

Elementos em linha são normalmente mostrados sem quebra de linha.<br>
__Por exemplo__: `<b>`, `<a>`, `<strong>`, `<img>`, `<input>`, `<em>`, `<span>`, etc.

O elemento `<div>` é um elemento nível de bloco que frequentemente é usado como __contêiner para outros elementos HTML__.<br>
Quando usado junto com alguns estilos CSS, o elemento `<div>` pode ser usado para estilizar blocos de conteúdo:

```html
<body>
  <div style="background-color: green; color: white; padding: 20px;">
    <p>Texto.</p>
    <p>Outro texto.</p>
  </div>
</body>
```

De modo parecido, o elemento em linha `<span>` frequentemente é usado como contêiner para textos.<br>
Quando usado com CSS, o elemento `<span>` pode ser usado para estilizar __partes do texto__:

```html
<body>
  <h2>
	  Uma mensagem <span style="color: red">importante</span>
  </h2>
</body>
```

> :information_source: __Resumo__<br>O elemento `<div>` define uma seção nível de bloco em um documento.<br>O elemento `<span>` define uma seção em linha em um documento.

Outros elementos podem ser usados como blocos ou em linha, como os seguintes elementos:<br>
`<applet>` - Applet Java embutido<br>
`<iframe>` - *Frame* em linha<br>
`<ins>` - Texto inserido<br>
`<map>` - Mapa de imagem<br>
`<object>` - Objeto embutido<br>
`<script>` - Script dentro de um documento HTML

Você pode inserir elementos em linha dentro de elementos de bloco. Por exemplo, você pode ter múltiplos elementos `<span>` dentro de um elemento `<div>`.

> :information_source: Elementos em linha __não podem__ conter nenhum elemento de bloco.

### [Formulários](#índice)
#### [O elemento `<form>`](#índice)
Os formulários do HTML são usados para coletar informações do usuário.<br>
Formulários são definidos usando o elemento `<form>` com as tags de abertura e fechamento:

```html
<body>
  <form></form>
</body>
```

Use o atributo `action` para indicar o site que carregará depois que o usuário enviar o formulário.

```html
<form action="https://www.sololearn.com"></form>
```

> :information_source: Geralmente o formulário é enviado para um site que está em um servidor.

#### [Os atributos `method` e `name`](#índice)
O atributo `method` especifica o método HTTP (__GET__ ou __POST__) a ser usado quando um formulário é enviado:

```html
<form action="url" method="GET">
```

```html
<form action="url" method="POST">
```

> :information_source: Quando usa-se __GET__, os dados do formulário estarão visíveis no endereço da página.<br><br>Use __POST__ se o formulário está atualizando dados ou incluí informações sensíveis (senhas).<br>`POST` oferece melhor segurança, pois os dados enviados não são visíveis no endereço da página.

Para usar o que o usuário enviou, você precisa dos elementos de formulário, como campos de textos. O elemento `<input>` tem muitas variações, dependendo do atributo `type`. Pode ser `text`, `password`, `radio`, `url`, `submit`, etc.

__O exemplo abaixo mostra um formulário requerindo nome de usuário e senha:__

```html
<form>
  <input
    type="text"
    name="nomeUsuario"
  />
  <br />
  <input
    type="password"
    name="senha"
  />
</form>
```

> :information_source: O atributo `name` especifica um nome para um formulário.

#### [Elementos do formulário](#índice)
Se mudarmos o tipo do input para `radio`, permitimos que o usuário selecione apenas uma opção dentre várias:

```html
<input
  type="radio"
  name="genero"
  value="masculino"
/> Masculino
<br />
<input
  type="radio"
  name="genero"
  value="feminino"
/> Feminino
```

O tipo `checkbox` permite que o usuário selecione mais do que uma opção:

```html
<input
  type="checkbox"
  name="genero"
  value="1"
/> Masculino
<br />
<input
  type="checkbox"
  name="genero"
  value="2"
/> Feminino
```

> :information_source: O elemento `input` não tem tem tag de fechamento.

O botão de tipo `submit` __envia um formulário__ para a url do atributo `action`.

```html
<input
  type="submit"
  value="Enviar"
/>
```

> :information_source: Depois que o formulário for enviado, os dados devem ser processados no servidor usando uma linguagem de programação, como PHP.

### [Projeto blog: Formulário de contato](#índice)
Em seguida, vamos criar um formulário de contato para o blog. O formulário conterá campos para nome, e-mail e mensagem. Também vamos adicionar um botão de envio.

O blog é apenas uma página estática, então não enviará o formulário realmente. Você teria que criar o código do lado do servidor para enviar um formulário de verdade e processar os dados. Para aprender como, [veja o curso sobre PHP do SoloLearn](https://www.sololearn.com/learning/1059) depois de ter concluído os cursos de [HTML](https://www.sololearn.com/learning/1014) e [CSS](https://www.sololearn.com/learning/1023).

> :information_source: __TAREFA__: Deixe o formulário do seu jeito!

### [Cores no HTML](#índice)
As cores no HTML são expressadas como valores hexadecimais.

__0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F__

> :information_source: Como podemos ver, há 16 valores, de 0 até F. O zero representa o menor valor e F representa o maior.

#### [Modelo de cor do HTML](#índice)
Cores são mostradas combinando luzes __vermelhas__, __verdes__ e __azuis__ (RGB).

Valores hexadecimais são escritos usando o símbolo de hashtag (#) seguidos por três ou seis caracteres hexadecimais. Como mostrado na foto abaixo, os círculos se sobrepõem, formando novas cores.

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=2467" />
</p>

> :information_source: Cores RGB são suportadas por todos os navegadores.

#### [Valores das cores](#índice)
O número de combinações de __vermelho__, __verde__ e __azul__ são aproximadamente 16 milhões.

__Algumas delas:__

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=2468" />
</p>

Podemos misturar as cores para formar novas cores:

__Laranja e vermelho:__

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=2469" />
</p>

> :information_source: Cores hexadecimais são suportadas por todos os navegadores.

#### [Cores do fundo e da fonte](#índice)
O atributo `bgcolor` pode ser usado para mudar a cor do fundo da página.

Esse exemplo deixa a página com fundo azul escuro e um texto em branco:

```html
<body bgcolor="#000099">
  <h1>
    <font color="#FFFFFF">Texto</font>
  </h1>
</body>
```

> :information_source: O atributo `color` especifica a cor do texto dentro do elemento <span title="Não suportado no HTML5"><u>`font`</u></span>

### [Frames](#índice)
#### [A tag `<frame>`](#índice)
Uma página pode ser dividida em *frames* usando um documento especial de *frame*.

A tag `<frame>` define uma janela específica (*frame*) dentro de um `<frameset>`. Cada `<frame>` dentro de um `<frameset>` pode ter diferentes atributos, como borda, rolagem, possibilidade de mudar o tamanho, etc.

O elemento `<frameset>` especifica o número de colunas ou linhas do frameset e também a porcentagem ou número de pixels que cada uma ocupa.

```html
<frameset cols="100, 25%, *"></frameset>

<frameset rows="100, 25%, *"></frameset>
```

> :information_source: A tag `<frameset>` não é suportada no HTML 5.

#### [Trabalhando com frames](#índice)
Use o atributo `noresize` para especificar que um usuário não pode mudar o tamanho de um elemento `<frame>`.

```html
<frame noresize="noresize">
```

O conteúdo de um *frame* deve ser definido usando o atributo `src`.

Por último, o elemento `<noframes>` fornece uma maneira pros navegadores que não suportam *frames* mostrarem a página. O elemento pode conter uma página alternativa, com uma tag `body` e qualquer outro elemento.

```html
<frameset cols="25%, 50%, 25%">
  <frame src="a.html" />
  <frame src="b.html" />
  <frame src="c.html" />
  <noframes>Frames não suportados!</noframes>
</frameset>
```

> :information_source: A tag `<frame>` não é suportada no HTML 5.

### [Projeto blog: Juntando tudo](#índice)
Para finalizar o blog, usaremos um *frame* para embutir um vídeo do YouTube. Também criaremos uma seção __Siga-me__ no fim da página incluindo links.

> :information_source: __TAREFA__:<br>1. Finalize a página do seu blog.<br>2. Compartilhe seu código!

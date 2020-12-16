# Índice
- [Desenvolvimento front-end](#desenvolvimento-front-end)
  - [O que é desenvolvimento front-end?](#o-que-é-desenvolvimento-front-end)
  - [Por que React?](#por-que-react)
- [Adicionando React em um site](#adicionando-react-em-um-site)
- [Create React App](#create-react-app)
  - [Estrutura do projeto](#estrutura-do-projeto)
  - [Fazendo mudanças](#fazendo-mudanças)
  - [StackBlitz](#stackblitz)
- [O projeto](#o-projeto)

### [Desenvolvimento front-end](#índice)
#### [O que é desenvolvimento front-end?](#índice)
Faz referência a o que o usuário final (também chamado de __cliente__) vê. Na forma mais básica, este desenvolvimento consiste de HTML, CSS e JavaScript.

Enquanto desenvolvedor, facilmente surgirá partes complexas no seu site. Resolver problemas fica difícil quando precisa-se passar por diversas linhas de código para encontrá-los.

Eventualmente, os desenvolvedores decidiram que deveria existir uma maneira melhor de gerenciar todo esse código, então criaram bibliotecas para ajudá-los. __React__ é uma dessas bibliotecas.

> :information_source: React foi criado pelo Facebook e divulgado ao público em maio de 2013 e tem sido constantemente mantido desde então.

#### [Por que React?](#índice)
__React__ é uma das bibliotecas JavaScript mais populares para aplicações web front-end.

Algumas vantagens do React:

__Velocidade__

Sites interativos precisam atualizar o DOM toda vez que uma mudança acontece. Este processo é geralmente lento.

Comparada com outras bibliotecas que manipulam o DOM, o React usa um DOM virtual, permitindo atualizar apenas as partes do site que mudaram. Isso aumenta muito a velocidade das atualizações, visto que sites modernos talvez contenham milhares de elementos.

__Facilidade__

O React permite que os desenvolvedores agrupem códigos relacionados, assim, deixando a construção e manutenção de aplicativos de larga escala menos complexas.

__Apoio__

O React tem uma grande e incrível comunidade e é de código aberto. É mantida pelo Facebook também.

### [Adicionando React em um site](#índice)
O React pode ser adicionado em um site sem qualquer instalação ou ferramenta especial.

Primeiramente, precisamos adicionar a biblioteca React usando duas tags `script` no `head` do documento HTML:

```html
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>

```

Agora, precisamos adicionar outra, para permitir o uso do JSX.

JSX é uma sintaxe JavaScript recomendada a ser usada com React.

Vamos aprender sobre JSX mais adiante, mas agora vamos adicionar mais uma tag `script`:

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

```

> :information_source: Essa abordagem apenas se encaixa em pequenas demonstrações. Vamos aprender a criar um projeto real pronto para produção mais adiante.

Depois de adicionar as tags `script`, podemos começar a construir nosso aplicativo React!

Adicionamos um contêiner, que será usado para mostrar algo usando React.

```html
<div id="container"></div>
```

> :information_source: Você pode usar qualquer __id__ para seu contêiner. Ele será usado pelo React para encontrar o contêiner e adicionar conteúdo nele.

Agora é hora para nosso primeiro código em React!
Vamos mostrar uma simples mensagem em um cabeçalho:

```html
<script type="text/babel">
  ReactDOM.render(<h1>Ola, React!</h1>, document.getElementById('container')
  )
</script>
```

O código encontra a `div container` e adiciona um `h1` nela.

### [Create React App](#índice)
Anteriormente, aprendemos como adicionar o React em um documento HTML simples usando as tags `script`.

Porém, sites reais têm uma escala diferente, contêm inúmeros arquivos, usam bibliotecas 3D, etc.

O Facebook criou uma ferramenta chamada [Create React App](https://create-react-app.dev/) que facilita a configuração de um projeto React usando apenas um comando!

Para começar, veja se você possui uma versão recente do [Node](https://nodejs.org/en/) instalado em seu computador.

Execute os seguintes comandos no terminal para criar e inicializar um aplicativo React chamado __meu-app__:

```
npx create-react-app meu-app
cd meu-app
npm start 

```

Todas as dependências serão instaladas, a configuração será feita e o projeto inicializará em __localhost:3000__.

Este é o resultado padrão do nosso projeto no navegador:

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=4380" />
</p>

> :information_source: __Create App React__ nos permite focar no código, do que ficar instalando e configurando diferentes ferramentas.

#### [Estrutura do projeto](#índice)
Vamos explorar a estrutura do nosso projeto abrindo-o usando um editor de código.

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=3940" />
</p>

A pasta __public__ contém arquivos relacionados a como a aplicação irá ser mostrada para o cliente, o mais importante deles é __index.html__, que é o modelo HTML da nossa página:

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=3941" />
</p>

A pasta __src__ contém os arquivos de JavaScript, CSS e imagens que serão compilados em um pacote e injetados em __index.html__

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=3942" />
</p>

Como o React é compilado em um pacote? Ele usa um "file loader". Neste caso, __Webpack__ é usado.

Webpack cria um pacote com o conteúdo de múltiplos arquivos que precisam ser empacotados juntos e são todos adicionados juntos em um único arquivo.

Ao invés de fazer o arquivo HTML procurar e encontrar múltiplos arquivos, o que pode pode causar lentidão, ele apenas precisa encontrar um.

> :information_source: Lembre-se, todos os arquivos CSS e JavaScript precisam ser adicionados na pasta __src__, se não o webpack não os verá.

Enquanto há outros arquivos na pasta __src__, os dois arquivos abaixo são os únicos críticos:

- __index.js__: Este arquivo é o ponto de entrada para nossa aplicação. No nosso código, um método chamado `ReactDOM.render()` é usado para encontrar um elemento com `id="root"` no HTML e adicionar nossa aplicação React dentro deste elemento.

- __App.js__: Este arquivo é o componente principal que irá ser renderizado no DOM, que atualmente inclui o logotipo do React e o texto padrão, mostrado anteriormente.

#### [Fazendo mudanças](#índice)
Agora que sabemos como criar e executar um projeto React, vamos mudar o resultado padrão para uma simples mensagem de olá.

Para isso, precisamos abrir __src/index.js__ e mudar o código para o seguinte:

```javascript
ReactDOM.render(
  <h1>Olá, React!</h1>,
  document.getElementById('root')
);

```

Isso irá mostrar a mensagem como um cabeçalho:

<p align="center">
  <img width="300" src="https://api.sololearn.com/DownloadFile?id=4388" />
</p>

> :information_source: Um recurso muito legal do Create React App é o __Carregamento Rápido__, que automaticamente mostra as mudanças feitas no código no navegador.

#### [StackBlitz](#índice)
Para facilitar, vamos estar usando StackBlitz para permitir a mudança e execução do código React.

O mesmo projeto no StackBlitz:

<p align="center">
  <img width="500" src="https://api.sololearn.com/DownloadFile?id=4389" />
</p>

[Veja no StackBlitz](https://stackblitz.com/edit/hello-react-example?file)

Foram removidos todos os arquivos extras, como os logotipos, para deixar a estrutura mais simples.

Agora temos os seguintes arquivos:

__index.html__: A página de modelo HTML.

__index.js__: O ponto de entrada do nosso aplicativo.

__style.css__: A estilização do nosso projeto.

__package.json__: Possui vários metadados sobre o projeto, como dependências.

### [O projeto](#índice)
Ao longo do curso, vamos te ajudar a praticar e criar seu próprio aplicativo de __Gerenciador de Contatos__ usando React, assim você irá fixar o que aprendeu e será capaz de colocar em prática.

Nosso gerenciador de contatos irá permitir ver a lista de contatos e adicionar novos na lista.

<p align="center">
  <img width="400" src="https://api.sololearn.com/DownloadFile?id=4390" />
</p>

Veja o aplicativo funcionando no [StackBlitz](https://stackblitz.com/edit/react-contact-manager-4)

> :information_source: Não fique com medo do código. Quando completar o curso, tudo irá fazer sentido. Garantimos!
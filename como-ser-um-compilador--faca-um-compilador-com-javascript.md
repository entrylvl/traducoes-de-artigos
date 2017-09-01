# Como ser* um compilador - Faça um compilador com JavaScript

## *Sim! Você deve ser um compilador. É muito legal.

Este post foi publicado sobre a licença [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).
Me avise caso você faça um tradução para outra língua, para ela poder ser adicionada na lista.

Um maravilhoso domingo em Bushwick, Brooklyn. Eu achei um livro chamado ["Design by Number"(Desenhe através de numeros) por John Maeda](https://mitpress.mit.edu/books/design-numbers) na minha livraria local. Nele tinha instruções passo a passo da [linguagem de programação DBN](http://dbn.media.mit.edu/) - uma linguagem de programação feita no fim dos anos 90 no laboratório de mídia do MIT, feito para introduzir programação de computadores com conceitos visuais.

![](http://i.imgur.com/ur3ls5B.png)
*Exemplo de código DNB http://dbn.media.mit.edu/introduction.html*

Eu imediatamente pensei em fazer SVG através do DBN e rodar em browser, seria um projeto interessante em 2016, melhor que instalar o ambiente Java para executar o código fonte original do DBN.
Eu percebi que teria que escrever um compilador de DBN para SVG, então a aventura de escrever um compilador começou. **"Fazendo um compilador" para muito como ciência da computação...mas eu nunca inverti nós de arvore em entrevistas de código, será que eu posso fazer um compilador?**

![](https://cdn-images-1.medium.com/max/960/1*mihwNKQqerkXUZ4GQhqgsg.png)
*Meu compilador imaginário, onde o código vai ser punido. Se o código é ruim, ele é capturado na mensagem de erro para sempre.*

## Vamos tentar sert um compilador primeiro

Compilador é um mecanismo que pega um pedaço de código e transforma em outras coisa. Vamos compilar um simples DBN em um desenho fisíco.
Existe três comandos nesse código DBN, "Paper" define a cor do papel, "Pen" define a cor da caneta, e "Line" que desenha uma linha. No parâmetro da cor, 100 significa preto ou rgb(0%, 0%, 0%) no CSS. A imagem produzida pelo DBN sempre é na escala do cinza. No DBN o papel sempre é 100x100, a largura da linha sempre é 1 e a linha é definida por coordenadas x e y do ponto de início até o ponto final contando a partir do canto inferior esquerdo.
Vamos ser o compilador nós mesmos. Pare agora, pegue papel e caneta, e vamos tentar compilar as seguintes linhas de código como desenho.

```
Paper 0
Pen 100
Line 0 0 100 50
```

Você desenhou uma linha preta no meio da esquerda para a direta? Parabéns!

Você acabou de se tornar um compilador.

![](https://cdn-images-1.medium.com/max/800/1*aDJskliFHSIIfYhr8aN3UA.png)*Resultado Compilado*

## Como um compilador funciona?

Vamos ver o que acabou de acontecer na nossa cabeça como um compilador.

### 1. Análise Léxica (tokenização)

A primeira coisa que nós fizemos foi separar cada palavra chave (chamadas de tokens) por um espaço em branco. Enquanto separavamos as palavras, nós também associamos tipos primitivos a cada token, como "palavra" ou "número".

![](http://i.imgur.com/Od8BBR6.png)

### 2. Parseamento (Análise Sintática)

Quando o bloco de texto é separado em tokens, nós analizamos cada um deles e tentamos encontrar a relação entre os tokens.
Nesse caso, nós agrupamos os números associados com os tokens de comando. Fazendo isso, nós começamos a ver a estrutura do código.

![](http://i.imgur.com/vqrhG77.png)

### 3. Transformação

Quando nós analisamos a sintaxe pelo parseamento, nós transformamos a estrutura em algo apropriado para o resultado final. Nesse caso, nós vamos desenhar a imagem, então nós estamos transformando isso em instruções passo a passo para seres humanos.


![](http://i.imgur.com/gMKP9rL.png)

### 4. Geração de código

Por último, nós fazemos do resultado compilado, um desenho. Nesse ponto, nós seguimos as instruções que fizemos no último passo para desenhar.

![](https://cdn-images-1.medium.com/max/800/1*250m-6zI6slTBirOxHX7kw.png)
*Geração de código*

E é isso que um compilador faz!

O desenho que nós fizemos é o resultado compilado (como um .exe quando compilamos um código em C). Nós podemos passar esse desenho para qualquer um ou qualquer dispositivo (scanner, câmera e etc) para "rodar" e todos verão uma linha preta no meio.


# Um compilador não deve usar recursão, busca em árvore e etc ?

Sim, e essas são ótimas técnicas para construir um compilador, não não significa que você tem que usá-las na primeira vez.

Eu comecei fazendo um compilador para uma pequena parte da linguagem DBN, uma parte bem limitada. Desde então, eu aumentei o escopo e agora planejo adicionar funcionalidades como variáveis, blocos e laços para este compilador. Seria uma ótima ideia usar estas técnicas agora, mas não é um requisito para começar.

# Vamos fazer um compilador

Agora que nós sabemos como um compilador funciona, vamos fazer um em JavaScript. Esse compilador recebe código DBN e tranforma em código SVG.

### 1. Função léxica

Assim como podemos dividir a frase inglesa "Eu tenho uma caneta" para [Eu, tenho, uma, caneta], o analisador léxico divide uma cadeia de código em pequenos pedaços (tokens). No DBN, cada token é delimitado por espaços em branco e classificado como "word" ou "number"

```javascript
function lexer (code) {
  return code.split(/\s+/)
          .filter(function (t) { return t.length > 0 })
          .map(function (t) {
            return isNaN(t)
                    ? {type: 'word', value: t}
                    : {type: 'number', value: t}
          })
}
```

```
entrada: "Paper 100"
saida:[
  { type: "word", value: "Paper" }, { type: "number", value: 100 }
]
```

### 2. Função Parser

O Parser passa por cada token, encontra informações sintáticas e cria um objeto chamado AST (Árvore de sintaxe abstrata ou Abstract Syntax Tree). Você pode pensar em AST como um mapa para o nosso código - uma maneira de entender como um pedaço de código está estruturado.
No nosso código, existem 2 tipos de sintaxe "NumberLiteral" e "CallExpression". NumberLiteral (Número literal) significa que o valor é um número. Ele é usado como argumento para CallExpression (Expressão de chamada).

```javascript

function parser (tokens) {
  var AST = {
    type: 'Drawing',
    body: []
  }
  // extrai um token por vez como current_token. Itera até que não haja mais tokens.
  while (tokens.length > 0){
    var current_token = tokens.shift()

    // Já que um token número não faz nada sozinho, nós só análisamos a sintaxe quando encontramos uma palavra.
    if (current_token.type === 'word') {
      switch (current_token.value) {
        case 'Paper' :
          var expression = {
            type: 'CallExpression',
            name: 'Paper',
            arguments: []
          }
          // se o token atual é uma "CallExpression" do tipo "Paper", o próximo token deve ser uma cor como argumento
          var argument = tokens.shift()
          if(argument.type === 'number') {
            expression.arguments.push({  // Adiciona o argumento ao objeto da expressão
              type: 'NumberLiteral',
              value: argument.value
            })
            AST.body.push(expression)    // Coloca o objeto da expressão no corpo da nossa AST
          } else {
            throw 'Paper command must be followed by a number.'
          }
          break
        case 'Pen' :
          ...
        case 'Line':
          ...
      }
    }
  }
  return AST
}
```

```
entrada: [
  { type: "word", value: "Paper" }, { type: "number", value: 100 }
]
saida: {
  "type": "Drawing",
  "body": [{
    "type": "CallExpression",
    "name": "Paper",
    "arguments": [{ "type": "NumberLiteral", "value": "100" }]
  }]
}
```

### 3. Função de transformação

A AST que criamos no passo anterior é boa para descrever o que está acontecendo no código, mas não é útil para criar o arquivo SVG.
Por exemplo. "Papel" é um conceito que só existe no paradigma DBN. No SVG, podemos usar o elemento <rect> para representar um papel. A função Transformer converte AST para outro AST que é compatível com SVG.

```javascript
function transformer (ast) {
  var svg_ast = {
    tag : 'svg',
    attr: {
      width: 100, height: 100, viewBox: '0 0 100 100',
      xmlns: 'http://www.w3.org/2000/svg', version: '1.1'
    },
    body:[]
  }

  var pen_color = 100 // cor padrão da caneta é preta

  // Extrai a expressão de chamada como `node`. Itera até que não haja mais expressões no body(corpo).
  while (ast.body.length > 0) {
    var node = ast.body.shift()
    switch (node.name) {
      case 'Paper' :
        var paper_color = 100 - node.arguments[0].value
        svg_ast.body.push({ // Adiciona o elemento rect e informações para o body(corpo) da AST do svg
          tag : 'rect',
          attr : {
            x: 0, y: 0,
            width: 100, height:100,
            fill: 'rgb(' + paper_color + '%,' + paper_color + '%,' + paper_color + '%)'
          }
        })
        break
      case 'Pen':
        pen_color = 100 - node.arguments[0].value // guarda a cor atual da caneta na variavel `pen_color`
        break
      case 'Line':
        ...
    }
  }
  return svg_ast
 }
```

```
entrada: {
  "type": "Drawing",
  "body": [{
    "type": "CallExpression",
    "name": "Paper",
    "arguments": [{ "type": "NumberLiteral", "value": "100" }]
  }]
}
saida: {
  "tag": "svg",
  "attr": {
    "width": 100,
    "height": 100,
    "viewBox": "0 0 100 100",
    "xmlns": "http://www.w3.org/2000/svg",
    "version": "1.1"
  },
  "body": [{
    "tag": "rect",
    "attr": {
      "x": 0,
      "y": 0,
      "width": 100,
      "height": 100,
      "fill": "rgb(0%, 0%, 0%)"
    }
  }]
}
```

### 4. Função geradora
Como última etapa deste compilador, a função geradora cria um código SVG baseado no novo AST que nós fizemos na etapa anterior.

```js
function generator (svg_ast) {

  // cria um atributo do tipo texto a partir do objeto attr
  // { "width": 100, "height": 100 } becomes 'width="100" height="100"'
  function createAttrString (attr) {
    return Object.keys(attr).map(function (key){
      return key + '="' + attr[key] + '"'
    }).join(' ')
  }

  // o primeiro atributo sempre é o <svg>. Cria um atributo do tipo string para a tag svg
  var svg_attr = createAttrString(svg_ast.attr)
  var svg_attr = createAttrString(svg_ast.attr)

  // para cada elemento no corpo do svg_ast, gera uma svg tag
  var elements = svg_ast.body.map(function (node) {
    return '<' + node.tag + ' ' + createAttrString(node.attr) + '></' + node.tag + '>'
  }).join('\n\t')

  // faz o empacotamento dos elementos com as tags de abrir e fechar o svg para completar o código SVG
  return '<svg '+ svg_attr +'>\n' + elements + '\n</svg>'
}
```

```
entrada: {
  "tag": "svg",
  "attr": {
    "width": 100,
    "height": 100,
    "viewBox": "0 0 100 100",
    "xmlns": "http://www.w3.org/2000/svg",
    "version": "1.1"
  },
  "body": [{
    "tag": "rect",
    "attr": {
      "x": 0,
      "y": 0,
      "width": 100,
      "height": 100,
      "fill": "rgb(0%, 0%, 0%)"
    }
  }]
}
```

```
saída:
<svg width="100" height="100" viewBox="0 0 100 100" version="1.1" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100" height="100" fill="rgb(0%, 0%, 0%)">
  </rect>
</svg>
```

### 5. Coloque tudo junto como um compilador
Vamos chamar esse compilador de "compilador sbn" (compilador SVG por números).
Nós criamos um objeto sbn com os métodos lexer, parser, transformer e generator. Então adicionamos o método compile que chama os outros quatro métodos encadeadamente.

Agora nós podemos passar um código em formato de texto para o compilador e obter o SVG como saída.

```js
var sbn = {}
sbn.VERSION = '0.0.1'
sbn.lexer = lexer
sbn.parser = parser
sbn.transformer = transformer
sbn.generator = generator

sbn.compile = function (code) {
  return this.generator(this.transformer(this.parser(this.lexer(code))))
}

// chama o compilador sbn
var code = 'Paper 0 Pen 100 Line 0 50 100 50'
var svg = sbn.compile(code)
document.body.innerHTML = svg
```

Eu fiz uma demonstração interativa que mostra os resultados de cada etapa desse compilador. O código do compilador sbn foi disponibilizado no github. Estou adicionando novas funcionalidades no compilador neste momento. Se você quer checar o compilador básico que eu fiz nesse artigo por favor verifique essa [versão simples](https://github.com/kosamari/sbn/tree/simple)


## Escrever um compilador é muito legal

Oque você pode fazer como compilador ? Talvez você possa fazer uma nova lingagem como JavaScript em Espanhol... que tal español script?

```
// ES (español script)
función () {
  si (verdadero) {
    return «¡Hola!»
  }
}
```

Exitem pessoas que fizeram linguagens de programação em [Emoji (Emojicode)](http://www.emojicode.org/) e em imagem colorida ([Linguagem programação Piet](http://www.dangermouse.net/esoteric/piet.html)). As possibilidades são infinitas!

## Aprendizados ao fazer um compilador

Fazer um compilador foi divertido, mas acima de tudo, me ensinou muito sobre desenvolvimento de software. Aqui estão algumas coisas que eu aprendi enquanto fazia meu compilador.

![](https://cdn-images-1.medium.com/max/960/1*AREFc7UVIAu_YIgk46EwaA.png)*Como eu imagino compulador depois de ter feito um*

### 1. Você não precisa conhecer tudo
Assim como o nosso analisador léxico, você não precisa saber tudo desde o início. Se você realmente não entender uma parte do código ou tecnologia, não hesite em dizer "Tem isso, e eu sei um pouco dela" e passar para o próximo passo. Não se estresse com isso, você ir'á entender eventualmente.

### 2. Não seja um babaca com mensagens de erro
O papel do analisado é seguir a regra e checar se as coisas foram escritas segundo ela. Muitas vezes erros acontecem. Então, tente enviar mensagens úteis e acolhedoras. É fácil falar "Isso não funciona desse jeito” (como "Token ILEGAL" ou "undefined não é uma função" erro no JavaScript) mas ao invés tento falar aos seus usuários o que deveria acontecer, o melhor que você conseguir.

Isso também se aplica a comunicação da equipe. Quando alguém está travado em uma questão, ao invés de dizer "isso não funciona", talvez você possa começar dizendo "Eu tentaria jogar no google palavras chaves como ___ and ___ ." ou “Eu recomendaria ler essa página na documentação.” Você não precisa fazer o trabalho por eles, mas você com certeza pode ajudar eles a fazer um trabalho melhor e mais rápido, apenas fornecendo um pouco mais de ajuda. Elm é uma linguagem de programação que [abraça esse método](http://http://elm-lang.org/blog/compiler-errors-for-humans). Ela usa "Talvez você quisesse tentar isso?" na mensagem de erro.

### 3. Contexto é tudo

Finalmente, como nosso transformador transformou um tipo de AST em outra mais apropriada para o resultado final, tudo é especifico do contexto.
Não existe uma maneira perfeita de fazer as coisas. Então não faça as coisas só porque é popular ou porque você fez antes, pense primeiro no contexto. Coisas que funcionam para um usuário podem ser um desastre para outro.
Tambem aprecie o trabalho que estas transformações fazem. Você pode conhecer um otimo transformador no seu time - alguem que é muito bom em aproximar distâncias.
O trabalho dessas transformadores podem não produzir código diretamente, mas é muito importante para produzir um produto de qualidade.

Espero que você tenha gostado deste artigo e eu espero que tenha te convencido sobre o quão legal é contruir e ser um compilador.
Esse é um excerto de uma palestra que eu ministrei na JSCong Colombia 2016 em Medellin, Colombia. Se quiser saber mais sobre esta a palestra veja os slides [aqui](https://kosamari.com/presentation/jsconfcolombia-2016/#0).

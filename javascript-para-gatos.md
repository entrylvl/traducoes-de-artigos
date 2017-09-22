## Uma introdução para novos programadores

### Tão fácil que seu companheiro humano também pode fazer!

JavaScript é uma lingugagem de programação ou, em outras palavras, uma maneira pela qual o computador é instruído a fazer coisas. Da mesma forma que um controla humanos com assobios e miados, um pode controlar computadores com instruções escritas em uma linguagem de programação. Todos os `web browsers` entendem JavaScript e você pode se beneficiar disso para que páginas `web` façam coisas malucas!

JavaScript começou como uma forma de tornar as páginas `web` mais interativas. Hoje em dia JavaScript roda em muitos lugares além dos `web browsers` - roda em servidores `web`, celulares e até robôs! Essa página irá te ensinar um pouco sobre o básico de JavaScript pra que você consiga começar agora mesmo*.

*  Tempo de leitura: Quase nada. Provavelmente uma hora ou duas. Aliás já que você é um gato, é mais provável que você fique deitado no sol por aí do que comece com isso agora.

### Tabela de conteúdo
* O console
* Strings
* Valores e variáveis
* Usando funções
* Funções embutidas no JS
* Download de novas funções JS
* Escrevendo novas funções
* Loops
* Arrays
* Objetos
* Callbacks
* Leitura recomendada

### Não seja um gato assustado

![](https://github.com/maxogden/javascript-for-cats/blob/master/images/yarnify.png)

Você sempre irá evoluir, mesmo com programação! Diferente de [dar patadas em um copo de água](https://github.com/maxogden/javascript-for-cats/blob/master/images/dealwithit.gif) sobre o seu laptop, nada nesses tutoriais irá danificar o seu computador de nenhuma forma, mesmo se você errar um comando ou clicar no botão errado. Assim como gatos, programas de computador erram o tempo todo: cometendo erros de ortografia, esquecendo aspas ou colchetes, e não lembrando sobre como funções básicas (como fio, lasers) funcionam. Programadores se preocupam mais em fazer as coisas funcionarem eventualmente do que com tentar que elas funcionem na primeira tentativa. O melhor jeito de aprender programação é cometendo erros.

### O básico
Existe JavaScript rodando nessa página agora mesmo. Vamos brincar com ele um pouco. Para o bem da simplicidade eu vou assumir que você está usando Google Chrome para ler essa página (se você não está é provavelmente mais simples para nós dois que você continue seguindo usando o Chrome).

Primeiro, clique com o botão direito em qualquer lugar na tela e selecione **Inspecionar Elemento**, então clique na aba **Console**. Você deve ver algo parecido com isso.

![](https://github.com/maxogden/javascript-for-cats/blob/master/images/console.gif)

Isso é um console, também conhecido como "linha de comando" ou "terminal". Basicamente é um jeito de digitar uma coisa por vez em um computador, e imediatamente receber a resposta do computador de volta. Eles são super úteis como ferramente de aprendizado (eu ainda uso o console praticamente todos os dias enquanto faço códigos).

O console faz umas coisas muito legais. Aqui eu comecei a digitar uma coisa e o console está me ajudando dando a lista de todas as coisas que eu poderia continuar digitando. Outra coisa que você pode fazer é digitar `1 + 1` dentro do console, pressionar  a tecla `Enter` e ver o que acontece.

Usar o console é uma parte muito importante do aprendizado de JavaScript. Se você não sabe se aquilo funciona ou qual o comando para alguma coisa, vá para o console e descubra! Aqui está um exemplo:

### <a id="strings" href="#strings">#</a> Strings

Já que eu sou um gato, eu quero trocar cada instância da palavra `cachorro` na internet com `esses cachorros malditos`. Primeiro, vá no seu console e digite algumas frases que contenham a palavra `cachorro` pelo menos uma vez. No Javascript um punhado de letras, números, palavras ou qualquer outra coisa é conhecido como **String**. Strings tem que começar E terminar com aspas, podendo ser aspas simples `'`ou aspas duplas `"`, tanto faz. Só tenha certeza que você está usando a mesma aspas no começo e no fim.

![console](http://jsforcats.com/images/console-strings.gif)

Viu essa mensagem de erro grotesca? Não se preocupe: você não cometeu nenhum crime. SyntaxError ILLEGAL é só uma forma que os robôs têm de falar que o seu programa tem um problema. As primeiras duas sentenças estão com suas aspas iguais no começo e no final, mas quando eu misturo aspas simples e duplas o console ficou maluco comigo.

OK, pra consertar essas sentenças (substituindo `cachorro` com a nossa versão melhorada) nós precisamos primeiro salvar a sentença original para que possamos chama-la mais tarde com a nossa magia de troca de lugar. Perceba como a string fica repetida em vermelho quando a gente digita ela no console? Isso é porque nós não dissemos para salvar a sentença em lugar nenhum, então ele simplesmente nos retorna a sentença (ou nos devolve um Error falando que nós fizemos algo errado).

### <a id="values" href="#values">#</a> Valores e variáveis

**Valores** são os componentes mais simples no JavaScript. `1` é um valor, `true` é um valor, `"olá"` é um valor, `function() {}`é um valor, a lista pode continuar! Tem um monte de **tipos** diferentes de valores no JavaScript mas nós não precisamos ver todos eles agora &mdash; você vai aprende-los naturalmente quanto mais você programar!

Para salvar esses valores nós usamos coisas chamadas **variáveis**. A palavra 'variável' significa 'que muda' e é usada porque variáveis podem guardar diferentes tipos de valores e podem mudar seu valor muitas vezes. Eles são bem parecidos com caixas de correio. Nós colocamos algo dentro de uma variável, como nossa sentença, e damos a essa variável um endereço para olhar para a sentença depois. As caixas de correio da vida real tem o seu código postal, mas no JavaScript você geralmente usa letras minúsculas ou números sem espaços.

![console](http://jsforcats.com/images/console-variables.gif)

`var`é a abreviatura de variável e o `=`significa *guarde esta coisa do lado direito na coisa do lado esquerdo*. Além disso, como você pode ver, agora que estamos guardando a nossa sentença nessa variável o console não só retorna a sentença de cara, mas nos dá um `undefined` que significa *não tem nada para retornar*

Se você simplesmente digitar o nome da variável no console ele vai imprimir o valor guardando naquela variável. Uma nota sobre variáveis é que por padrão elas somem quando você troca para uma página diferente. Se eu apertar o botão de atualizar a página no Chrome, por exemplo, minha variável `dogSentence` desapareceria como se nunca tivesse existido. Mas não se preocupe com isso por enquanto &mdash; você pode simplesmente apertar as setas 'para cima' e 'para baixo' do seu teclado no console você pode passar por tudo o que você digitou nele recentemente.

### <a id="functions" href="#functions">#</a> Usando funções

Agora que temos a nossa sentença armazenada em uma variável, vamos trocar a palavra que está dentro dela! Nós podemos fazer isso realizando uma *função*. *Funções* são um tipo de valor que, bem, serve à uma *função* (vulgo propósito ou ação) para nós. Chamar elas "ações" ficou estranho então acho que eles optaram pela palavra "função" no lugar.

JavaScript tem uma função chamada `replace`que faz exatamente o que nós queremos! Funções pegam qualquer número de valores em seus parenteses (zero, um ou muitos) e retorna ou `undefined` (nada) ou a string mudada. A função `replace` é possível ser usada em strings e requer dois valores: os caracteres para serem retirados e os caracteres para serem trocados. Fica meio confuso descrever essas coisas aqui então vamos para um exemplo visual:

![console](http://jsforcats.com/images/console-replace.gif)

Percebe como o valor de `dogSentence` é o mesmo depois que nós executamos o `replace` nele? Isso porque a função `replace`, (e a maioria das funções JavaScript aliás) pega o valor que nós damos e retorna com um ***novo valor***, sem que haja modificação no valor que passamos. Já que nós não guardamos o resultado (não tem um `=` no lado esquerdo da função replace) ele simplesmente imprimiu o valor de retorno no nosso console.

### <a id="standard-library" href="#standard-library">#</a> Funções embutidas no JS

Você deve estar imaginando quais outras funções estão disponíveis no JavaScript. A resposta: UMA TONELADA. Existem muitas **bibliotecas embutidas** que você pode aprender sobre no MDN (um site administrado pelo Mozilla que tem várias informações sobre tecnologias web). Por exemplo [aqui é uma página MDN sobre o objeto Math do JavaScript]((https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Math

### <a id="third-party-javascript" href="#third-party-javascript">#</a> Download de novas funções JS

Existe também muito código de JavaScript que não é **embutido**. O código externo de JavaScript é geralmente referido como "biblioteca" ou "plugin". Um dos meus favoritos é chamado **Underscore.js**. Vamos lá usa-lo e carrega-lo na nossa página! Primeiro, vá para o site do Underscore, [http://underscorejs.org/](http://underscorejs.org/), clique no link para download (eu geralmente uso versões de desenvolvedor porque eles são mais fáceis de ler, mas os dois vão nos dar basicamente a mesma funcionalidade), e após isso copiar o código do site (você pode usar o "Selecionar Todos" do menu "Editar" para selecionar tudo). Depois, cole no nosso console e aperte enter. Agora o browser tem uma nova variável nele: `_`. Underscore te dá uma tonelada de funções úteis para você brincar. Nós aprenderemos melhor como usa-lo depois.

![console](http://jsforcats.com/images/underscore.gif)

### <a id="writing-functions" href="#writing-functions">#</a> Criando novas funções

Você não está limitado a usar apenas funções de outras pessoas - você também pode escrever as suas próprias. É bem fácil! Vamos criar uma função chamada `makeMoreExciting` que adiciona um punhado de pontos de exclamação ao final de uma string.

    function makeMoreExciting(string) {
      return string + '!!!!'
    }

Na minha cabeça, eu leio isso como: "existe uma função chamada 'makeMoreExciting' que recebe uma string e retorna uma nova cópia daquela string com um punhado de pontos de exclamação no final". Aqui está como nós escreveríamos isso manualmente no console se não estivéssemos usando uma função:

![console](http://jsforcats.com/images/custom-function-manually.gif)

A expressão `string + '!!!!'` retorna uma nova string e nossa variável chamada `string` permanece a mesma de antes (já que não atribuímos nada novo a ela com `=`).

Vamos usar nossa função ao invés de fazer isso manualmente. Primeiro, cole a função no console e então **execute** a função **passando a ela** uma string:

![console](http://jsforcats.com/images/custom-function-call.gif)

Você também pode chamar a mesma função passando a ela uma variável que aponta para uma string (no exemplo acima apenas digitamos a string diretamente como um valor, ao invés de salvá-la antes em uma variável):

![console](http://jsforcats.com/images/custom-function-call-variable.gif)

A linha `makeMoreExciting(sentece)` é o equivalente a dizer `frase + '!!!!'`. E se quiséssemos realmente **modificar** (ou: atualizar) o valor de sentence? Simplesmente salvamos o valor de retorno da função de volta em nossa variável `sentence`:

    var sentence = "time for a nap"
    sentence = makeMoreExciting(sentence)

Agora `sentence` terá os pontos de exclamação nela! Note que você só precisa usar `var` quando está **inicializando** uma variável &mdash; a primeira vez que a usa. Depois disso você não deve usar `var` a menos que queira re-inicializar (resetar/limpar/esvaziar) a variável.

O que aconteceria se tirássemos o comando `return` de nossa função?

![console](http://jsforcats.com/images/custom-function-no-return.gif)

Por que `sentence` está vazia? Porque funções retornam `undefined`  por padrão! Você pode escolher retornar um valor usando `return`. Funções devem receber um valor e, se alterarem o valor ou criarem um novo que deve ser usado mais tarde, **retornar o valor** (curiosidade: um termo sofisticiado para este estilo é *programação funcional*). Aqui está uma outra função que não retorna nada, mas usa um método diferente para nos mostrar o resultado:

```js
function yellIt(string) {
  string = string.toUpperCase()
  string = makeMoreExciting(string)
  console.log(string)
}
```

Essa função, `yellIt`, usa nossa função anterior `makeMoreExciting` bem como o método [toUpperCase](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/String/toUpperCase), nativo do tipo String. Métodos são apenas um nome para uma função quando esta pertence a algo &mdash; nesse caso, `toUpperCase` é uma função que pertence à `String`, então podemos nos referir a ele tanto como um método *ou* uma função. Por outro lado, `makeMoreExciting` não pertence a ninguém, então seria técnicamente incorreto se referir a ela como um método (confuso, eu sei).

A última linha da função é outro método nativo que simplesmente recebe quaisquer valores e, então, exibe-os no console.

![console](http://jsforcats.com/images/custom-function-console-log.gif)

Então, tem algo errado com a função `yellIt` acima? Depende! Aqui estão os dois principais tipos de funções:

  - funções que modificam ou criam valores e os retornam
  - funções que recebem valores e executam alguma ação que não pode ser retornada

`console.log` é um exemplo do segundo tipo de função: ela imprime coisas no seu console &mdash; uma ação que você consegue ver com seus olhos, mas não pode ser representado como um valor em JavaScript. Minha própria regra é tentar manter os dois tipos de funções separados um do outro, então aqui está como eu escreveria a função `yellIt`:

```js
function yellIt(string) {
  string = string.toUpperCase()
  return makeMoreExciting(string)
}

console.log(yellIt("i fear no human"))
```

Dessa forma `yellIt` se torna mais **genérica**, o que significa que ela só faz uma ou duas coisas simples e não sabe nada sobre exibir ela mesma no console &mdash; essa parte pode sempre ser programada depois, fora da definição da função.

### <a id="loops" href="#loops">#</a> Loops

Agora que nós temos algumas habilidades básicas em nosso cinto de utilidades (*Nota do autor: gatos ao menos usam cintos?*), podemos começar a ser preguiçosos. O que?! Sim, isso mesmo: programar é ser preguiçoso. Larry Wall, criador da linguagem de programação Perl, chamou a preguiça de [virtude mais importante](http://c2.com/cgi/wiki?LazinessImpatienceHubris) de um bom programador. Se os computadores não existissem, você teria que fazer todo tipo de tarefas tediosas manualmente, mas se você aprender a programas, pode deitar ao sol o dia todo enquanto um computador em algum lugar executa seus programas para você. É um estilo glorioso e cheio de relaxamento!

Loops são uma das maneiras mais importantes de se aproveitar do poder de um computador. Lembra do `Underscore.js` de antes? Certifique-se de tê-lo carregado na página (lembre-se: você pode simplesmente pressionar algumas vezes a seta para cima em seu teclado e então pressionar `Enter` para carregá-lo novamente, caso necessário) e tente copiar/colar isto em seu console:

```js
function logANumber(someNumber) {
  console.log(someNumber)
}
_.times(10, logANumber)
```

Esse código usa o método [times](http://underscorejs.org/#times) do Underscore, que recebe 1 número e 1 função como parâmetros e então começa do 0 ao 10, incrementando de 1 em 1, chamando a função com o número a cada passo.

![console](http://jsforcats.com/images/times-loop.png)

Se nós escrevessemos manualmente o que `times` está fazendo no código acima, ele seria parecido com isto:

```js
logANumber(0)
logANumber(1)
logANumber(2)
logANumber(3)
logANumber(4)
logANumber(5)
logANumber(6)
logANumber(7)
logANumber(8)
logANumber(9)
```

Mas gatos se recusam a fazer trabalho manual desnecessário como esse, então devemos sempre nos perguntar: *"eu estou fazendo isso da forma mais preguiçosa possível?"*.

Então por isso é chamado de looping? Pense nisso assim: se fossemos escrever uma lista de 10 números (de 0 a 9) usando um Array em JavaScript, se pareceria com isto:

```js
var zeroThroughTen = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

O que `times` realmente faz é visitar cada número e repetir uma tarefa: no exemplo acima a tarefa era chamar a função `logANumber` com o número atual. Repetir tarefas dessa forma é chamado de *fazer um loop* sobre o Array.

### <a id="arrays" href="#arrays">#</a> Arrays

Eu já os havia mencionado algumas vezes, mas vamos gastar um tempinho aprendendo sobre eles. Imagine que você precisa rastrear todos os seus amigos. Um Array cairá bem para isso. Pense em um Array como uma lista ordenada onde você pode manter *toneladas* de coisas dentro.

É assim que se faz um Array:

```js
var myCatFriends = ["bill", "tabby", "ceiling"]
```

Legal! Agora você tem uma lista com os seus amigos gatos.

Elementos (que é como chamamos um único item em um array) de um array começam no índice 0 e vão incrementando conforme a quantidade de itens. Então, `myCatFriends[0]` retorna `bill`e `myCatFriends[1]` retorna `tabby`, e assim por diante.

Para obter os amigos do seu Array novinho em folha, você pode simplesmente acessar um elemento diretamente, desse jeito:

```js
console.log(myCatFriends[0])
```

![console](http://jsforcats.com/images/array-access.png)

Se na noite anterior você fez um novo amigo no clube de gatos mais badalado e quer adicioná-lo à sua lista, é super simples: `myCatFriends.push("super hip cat")`.

Para verificar que o novo gato está no seu array, você pode usar `.length`:

![console](http://jsforcats.com/images/array-push-length.png)

Percebeu como `push` retornou o comprimento? Útil! Lembre-se também que arrays sempre **preservam ordernação**, o que significa que eles se lembrarão da ordem em que você adicionou ou definiu as coisas. Nem tudo em JavaScript preserva a ordenação, então lembre-se dessa propriedade especial dos Arrays!

### <a id="objects" href="#objects">#</a> Objetos

Arrays são bons para listas, mas para outras tarefas podem ser difíceis de se trabalhar. Considere nosso array de amigos gatos. E se você também quisesse armazenar mais do que apenas nomes?

```js
var myCatFriends = ["bill", "tabby", "ceiling"]
var lastNames = ["the cat", "cat", "cat"]
var addresses = ["The Alley", "Grandmas House", "Attic"]
```

Algumas vezes é interessante manter armazenados todos os endereços ou nomes em uma variável. Porém, ocasionalmente, você tem um gato em mente, Bill por exemplo, e quer localizar apenas o endereço deste gato. Fazer isto com arrays requer muito trabalho, porque você não pode simplesmente dizer 'hey array, me dê o endereço de Bill' porque 'Bill' está em um array e seu endereço está em um array totalmente diferente.

![](http://jsforcats.com/images/array-lookup.png)

Isso pode ser frágil pois, se nossos arrays mudam e adicionamos um novo gato no início, teríamos que atualizar também nossa variável `billsPosition` para apontar para a nova posição das informações de Bill nos arrays! Aqui está uma maneira mais fácil de manter armazenadas informações como estas usando objetos:

```js
var firstCat = { name: "bill", lastName: "the cat", address: "The Alley" }
var secondCat = { name: "tabby", lastName: "cat", address: "Grandmas House" }
var thirdCat = { name: "ceiling", lastName: "cat", address: "Attic" }
```

Por que faríamos isso desta forma? Porque agora temos uma variável para cada gato, que podemos usar para obtermos os valores dos gatos de uma forma mais conveniente e legível.

![](http://jsforcats.com/images/object-lookup.png)

Você pode pensar em Objetos como chaves em um chaveiro. Cada uma serve para uma porta específica e, se você tiver etiquetas nas chaves, pode abrir portas rapidamente. De fato, as coisas que estão à direita do `:`são chamadas **chaves** (também conhecidas como **propriedades**) e o que está à direita são os **valores**.

```js
// um objeto com uma única chave 'name' e único valor 'bill'
{ name: 'bill' }
```

Então por que usar arrays se você pode simplesmente armazenar todos os seus dados em objetos? Porque objetos não se lembram da ordem em que as chaves foram definidas. Você pode criar um objeto como este:

```js
{ date: "10/20/2012", diary: "slept a bit today", name: "Charles" }
```

Mas o computador pode retorná-lo desta forma:

```js
{ diary: "slept a bit today", name: "Charles", date: "10/20/2012" }
```

Ou assim!

```js
{ name: "Charles", diary: "slept a bit today", date: "10/20/2012" }
```

Então você nunca pode confiar na ordem das chaves em objetos. Se quiser fazer algo BEM sofisticado, você pode fazer um array preenchido com objetos, ou um objeto preenchido com arrays!

```js
var moodLog = [
  {
    date: "10/20/2012",
    mood: "catnipped"
  },
  {
    date: "10/21/2012",
    mood: "nonplussed"
  },
  {
    date: "10/22/2012",
    mood: "purring"
  }
]

// em ordem crescente de preferência
var favorites = {
  treats: ["bird sighting", "belly rub", "catnip"],
  napSpots: ["couch", "planter box", "human face"]
}
```

Ao combinar coisas diferentes como estas, você está criando **estruturas de dados**, igual Lego!

## O fim!

Este é apenas o começo do nosso relacionamento com o JavaScript! Você não pode aprender tudo de uma vez, mas é capaz que você ache o que funciona para ti e tentar aprender os conceitos por aqui.

Eu recomendo voltar aqui amanhã e ver a coisa toda de novo desde o começo! Talvez leve algumas vezes até você entender tudo (programar é difícil). Apenas tente evitar esse artigo em espaços que contenham objetos brilhantes... eles podem te distrair de uma maneira incrível.

Tem outro tópico que você gostaria de ver? Abra uma issue no [on github](http://github.com/maxogden/javascript-for-cats).

### <a id="callbacks" href="#callbacks">#</a> Callbacks

Callbacks não são, de fato, uma funcionalidade do JavaScript como `Objetos` ou `Arrays`, mas sim uma determinada maneira de utilizar funções. Para entender como callbacks são úteis, você primeiro deve aprender sobre programação assíncrona (às vezes chamada de *async programming*). Código assíncrono é, por definição, código escrito de maneira que não seja síncrono. Código síncrono é fácil de entender e escrever. Aqui está um exemplo para ilustrar:

```js
var photo = download('http://foo-chan.com/images/sp.jpg')
uploadPhotoTweet(photo, '@maxogden')
```


Esse [pseudo-código](http://simple.wikipedia.org/wiki/Pseudocode) síncrono faz o download de uma linda foto de um gato e então faz o upload da foto para o Twitter e, então, tweeta a foto no perfil `@maxogden`. Bem direto!

(*Nota do autor: Eu, @maxogden aceito alegremente tweets com fotos aleatórias de gatos*)

Esse código é síncrono porque, para que seja feito o upload da foto para o tweet, o download da mesma deve ser completado. Isso significa que a linha 2 não pode ser executada até que a tarefa na linha 1 seja finalizada. Se fossemos realmente implementar esse pseudo-código, iríamos querer ter certeza que o `download` 'bloqueou' a execução até que o download seja finalizado, o que significa que ele deveria impedir *qualquer* outro JavaScript de ser executado até seu término, e então quando o download estiver completo, desbloquearia a execução do JavaScript, seguindo para a linha 2.

Código síncrono é bom para coisas que acontecem rapidamente, mas é horrível para coisas que requerem salvar, carregar, download ou upload. E se o servidor de onde você estiver baixando a foto estiver lento, ou a conexão com a internet estiver ruim, ou se o computador que você está usando tem muitas abas do YouTube com vídeos de gatos abertas e está devagar? Isso significa que você poderia ter que esperar minutos até que a linha 2 seja executada. Enquanto isso, já que todo o JavaScript está bloqueado durante o download, a página congelaria totalmente e não apresentaria resposta até o fim do download.

O bloqueio de execução deve ser evitado a todo custo, especialmente quando fazê-lo faz seu programa congelar ou não responder. Vamos assumir que o download da foto acima leve um segundo para completar. Para ilustrar o quanto um segundo é para um computador moderno, aqui está um programa que testa quantas tarefas JavaScript consegue processar em um segundo:

```js
function measureLoopSpeed() {
  var count = 0
  function addOne() { count = count + 1 }

  // Date.now() returns a big number representing the number of
  // milliseconds that have elapsed since Jan 01 1970
  var now = Date.now()

  // Loop until Date.now() is 1000 milliseconds (1 second) or more into
  // the future from when we started looping. On each loop, call addOne
  while (Date.now() - now < 1000) addOne()

  // Finally it has been >= 1000ms, so let's print out our total count
  console.log(count)
}

measureLoopSpeed()
```

Copie e cole o código acima em seu console JavaScript e, depois de um segundo, ele deve apresentar um número. No meu computador obtive `8527360`, aproximadamente **8,5 milhões**. Em um segundo, o JavaScript consegue executar a função `addOne` 8,5 milhões de vezes! Então, se você tiver um código síncrono para fazer o download de uma foto, e o download leva um segundo, isso significa que você está potencialmente impedindo 8,5 milhões de operações de acontecerem enquanto a execução do JavaScript está bloqueada.

Algumas linguagens têm uma função chamada `sleep` que bloqueia a execução por um determinado número de segundos. Por exemplo, aqui está um código [`bash`](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) que usa `sleep` sendo executado no app Terminal em um Mac OS. Ao rodar o comando `sleep 3 && echo 'done sleeping now'`, ele bloqueia durante 3 segundos antes de imprimir `done sleeping now`.

![console](http://jsforcats.com/images/bash-sleep.png)

JavaScript não tem uma função`sleep`. Como você é um gato, deve estar se perguntando: "Por que estou aprendendo uma linguagem de programação que não envolve dormir?". Mas fique comigo. Ao invés de confiar ao `sleep` para esperar pelas coisas acontecerem, o design do JavaScript encoraja o uso de funções. Se você tem que esperar uma tarefa A terminar antes de executar uma tarefa B, você coloca todo o código da tarefa B em uma função e, somente executa esta função, quando A está finalizada.

Por exemplo, este é um código bloqueante:

```js
a()
b()
```

E este é um exemplo de código não-bloqueante:

```js
a(b)
```

Na versão não-bloqueante `b` é um callback para `a`. Já na versão bloqueante, `a` e `b` são igualmente executadas (ambas possuem `()` nelas, o que faz as funções executarem imeadiatamente). Na versão não-bloqueante você pode perceber que apenas `a` é executada, e `b` é simplesmente passada como argumento para `a`.

Na versão bloqueante, não há um relacionamento explícito entre `a` e `b`. Na versão não-bloqueante vira responsabilidade de `a` fazer tudo o que precisa e, então, executar `b` quando finalizar. Usar funções desta maneira é chamado de callbacks porque a sua função callback, nesse caso `b`, é executada depois quando `a` está finalizada.

Aqui está uma implementação em pseudo-código de como `a` poderia ser:

```js
function a(done) {
  download('https://pbs.twimg.com/media/B4DDWBrCEAA8u4O.jpg:large', function doneDownloading(error, png) {
    // handle error if there was one
    if (err) console.log('uh-oh!', error)

    // call done when you are all done
    done()
  })
}
```

Pense novamente em nosso exemplo não-bloqueante, `a(b)`, onde executamos `a` e passamos `b` como o primeiro argumento. Na definição da função `a` acima, o argumento `done`*é* nossa função `b`. Esse comportamento é algo difícil de compreender num primeiro momento. Quando você executa uma função, os argumentos passados não terão os mesmos nomes que as variáveis quando estiverem dentro da função. Nesse caso, o que chamamos de `b` é chamado de `done` dentro da função. Mas `b` e `done` são apenas nomes de variáveis que aponta para a mesma função subjacente. Normalmente funções de callback são chamadas como `done` ou `callback` para deixar claro que elas são funções que devem ser executadas quando a função atual terminar.

Então, enquanto `a` fizer seu trabalho e chamar `b` ao terminar, ambas `a` e `b` são executadas em ambas as versões não-bloqueante e bloqueante. A diferença é que na versão não-bloqueante nós não precisamos parar a execução do JavaScript. Em geral, o estilo não-bloqueante é como você escreve todas funções, para que elas possam retornar assim que possível, sem bloquear.

Para aumentar ainda mais os pontos: Se `a` leva um segundo para completar, e você usa a versão bloqueante, isso significa que você só pode fazer uma única coisa. Se você usa a versão não-bloqueante (ou seja, usa callbacks) pode fazer *literalmente milhões* de coisas no mesmo segundo, o que significa que você pode terminar seu trabalho milhões de vezes mais rápido e dormir o resto do dia.

Lembre-se: programação é sobre ser preguiçoso, e você deve ser quem está dormindo, não seu computador.

Felizmente agora você pode ver que callbacks são apenas funções que chamam outras funções depois de alguma tarefa assíncrona. Exemplos comuns de tarefas assíncronas são coisas como carregar uma foto, fazer download de uma música, fazer upload de uma imagem, comunicar-se com um banco de dados, esperar o usuário pressionar uma tecla ou clicar em algum lugar, etc. Tudo o que leva tempo. O JavaScript é ótimo em lidar com tarefas assíncronas como essas contanto que você invista tempo em aprender como usar callbacks  e impredir seu JavaScript de ser bloqueado.

### <a id="recommended-reading" href="#recommended-reading">#</a> Leitura recomendada

  JavaScript para Gatos pula um monte de detalhes que não são importantes para quem está começando (gatos não são conhecidos por sua atenção), mas se você sente que precisa se aprofundar dê uma olhada:

  - [NodeSchool.io](http://nodeschool.io/) é um software educacional open source guiado pela comunidade que ensina varias habilidades de desenvolvimento web de uma maneira iterativa e autoditada. Eu ajudei a fazer o NodeSchool! Infelizmente tem menos gatos do que nessa página.
  - [Eloquent Javascript](http://eloquentjavascript.net/) é um livro grátis que ensina JavaScript! É muito bom, especialmente o capítulo [values, variables, and control flow][values, variables, and control flow](http://eloquentjavascript.net/chapter2.html)
  - [Mozilla's JavaScript Guide](https://developer.mozilla.org/en-US/docs/JavaScript/Guide) também tem um ótimo capítulo de introdução chamado [values, variables and literals](https://developer.mozilla.org/en-US/docs/JavaScript/Guide/Values,_variables,_and_literals)
  - [`standard` JS Style Guide](https://github.com/feross/standard) é um linter para JS que não "requer configuração" que eu uso.
  - [Let's Write Code by @shama](https://github.com/shama/letswritecode) uma grande série de tutoriais de código feito por um amigo meu.

<hr>
### <a id="satisfied-customers" href="#satisfied-customers">#</a> Clientes satisfeitos
<center>![satisfied customer](http://jsforcats.com/images/customers5.jpg)</center>
<center>![satisfied customer](http://jsforcats.com/images/customers1.png)</center>
<center>![satisfied customer](http://jsforcats.com/images/customers2.png)</center>
<center>![satisfied customer](http://jsforcats.com/images/customers3.png)</center>
<center>![satisfied customer](http://jsforcats.com/images/customers4.png)</center>

*JSForCats.com é trabalho de amor e ainda em progresso feito por [@maxogden](http://twitter.com/maxogden). Se você quer contribuir para fazer esse tutorial melhor aqui tem um repositório no Github[bem aqui](http://github.com/maxogden/javascript-for-cats).*
<center>![console](http://jsforcats.com/images/awesome.jpg)</center>

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

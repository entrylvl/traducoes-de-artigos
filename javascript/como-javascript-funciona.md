[Artigo original: https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf](https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)

---

### Como Javascript funciona: uma visão geral da engine, do runtime e da pilha de chamadas

Como JavaScript está ficando cada vez mais popular, times tem se aproveitado de seu suporte para vários papéis em suas funções - front-ned, back-end, aplicativos hibridos e muito mais.

Este post é o primeiro numa série com a intenção de se aprofundar em JavaScript e em como ele realmente funciona: nos achamos que ao saber como os blocos de construçāo do JavaScript e como eles se integram você terá a oportunidade de escrever códigos e aplicativos melhores.

Como visto nas estatisticas do GitHut (http://githut.info), JavaScript está no topo em termos de repositórios ativos e pushes totais no GitHub. E não fica muito atras em outras categorias.

![](https://cdn-images-1.medium.com/max/1600/1*Zf4reZZJ9DCKsXf5CSXghg.png)

####Confira as estatísticas de língua atualizadas

Se os projetos estão ficando tão dependentes do JavaScript, isso significa que desenvolvedores têm que utilizar tudo que a linguagem e seu ecossistema providenciam e entender como funciona internamente para construir programas cada vez melhores.

Mas, na verdade, existem muitos desenvolvedores usam JavaScript diariamente sem o conhecimento do que acontece debaixo dos panos.

## Visão Geral

Muitos ja ouviram falar da engine V8 como um conceito, e a maioria sabe que o JavaScript é single-threaded* ou que usa uma fila para callback*

Neste artigo iremos passar por todos estes conceitos em detalhes e explicaremos como JavaScript realmente roda. Sabendo desses detalhes, voce tera a habilidade de escrever aplicativos melhores, que utilizam as APIs disponiveis da melhor forma.

Se você for relativamente novo em JavaScript, este artigo irá te ajudar a entender o porque JavaScript é tão "estranho" comparado a outras linguagens.

E, se você for um desenvolvedor JavaScript experiente, te dará novas formas de pensar e encarar como o JavaScript Runtime que você usa todo dia funciona.

## A Engine do JavaScript

Um exemplo popular de uma engine do JavaScript é a V8 do Google. A V8 é usada dentro do Chrome e do Node.js. Aqui está uma visão bem simplificada de como ela se parece:

![](https://cdn-images-1.medium.com/max/1600/1*OnH_DlbNAPvB9KLxUCyMsA.png)

A Engine consiste em 2 componentes principais:

* Heap de Memória - é onde a alocação de memória acontece

* Pilha de Chamadas - é onde estão os seus stack frames enquanto o seu código executa

## O tempo de execução

Existem APIs no navegador que estão sendo usadas por praticamente todo desenvolvedor JavaScript lá fora. (por exemplo: "setTimeout"). Essas APIs no entanto não são fornecidas pela linguagem em si.

Então, de onde elas estão vindo?

Acontece que a realidade é um pouco mais complicada.

![](https://cdn-images-1.medium.com/max/1600/1*4lHHyfEhVB0LnQ3HlhSs8g.png)

Nós temos a linguagem, mas na verdade, há muito mais. Nós temos essas coisas chamadas Web APIs que são fornecidas pelos navegadores, como DOM, AJAX, setTimeout e muitas outras.

E então, temos os tão populares **event loop** e a **fila de callback**.

## A Pilha de Chamadas

JavaScript é uma linguagem de programação `single-threaded`, o que signicia que tem apenas uma pilha de chamadas. Logo, só pode fazer uma coisa por vez.

A pilha de chamadas é uma estrutura de dados que salva basicamente onde estamos no programa. Se entrarmos em uma função, nos a colocamos no topo da pilha. Se saírmos de uma função, nós tiramos ela do topo. Isso é tudo que a pilha faz.

Vamos olhar um exemplo. Dê uma olhada no código a seguir: 

```
function multiply(x, y) {
    return x * y;
}
function printSquare(x) {
    var s = multiply(x, x);
    console.log(s);
}
printSquare(5);
```

Quando o motor começa a executar esse código, a pilha de chamadas estará vazia. Depois os passos serão os seguintes:

![](https://cdn-images-1.medium.com/max/2000/1*Yp1KOt_UJ47HChmS9y7KXw.png)

Cada entrada na pilha de chamadas é chamada de quadro da pilha. 

E é exatamente assim que o rastro da pilha está sendo construído quando uma exceção é disparada - é basicamente o estado da pilha de chamada quando a exceção aconteceu. Dê uma olhada nesse código: 

```
function foo() {
    throw new Error('SessionStack will help you resolve crashes :)');
}
function bar() {
    foo();
}
function start() {
    bar();
}
start();
```

Se for executado no Chrome (assumindo que ele está em um arquivo chamado foo.js), o rastro da pilha será:

![](https://cdn-images-1.medium.com/max/1600/1*T-W_ihvl-9rG4dn18kP3Qw.png)

`Soprando a pilha` - isso acontece quando você chega no limite do tamanho da pilha de chamadas. E isso pode acontecer facilmente, especialmente se você está usando recursão sem testar seu código extensivamente. Olhe esse código: 

```
function foo() {
    foo();
}
foo();
```

Quando o motor começa a executar esse código, ele começa chamado a função `foo`. Essa função, entretanto, é recursiva e começa a chamar a si mesmo sem condição de parada. Então em cada passo da execução, a mesma função é adicionada a pilha de chamadas infinitamente. Vai ser algo assim: 

![](https://cdn-images-1.medium.com/max/1600/1*AycFMDy9tlDmNoc5LXd9-g.png)

Em algum ponto, entretanto, o número de chamada de funções na pilha de chamada extrapola o tamanho da pilha, e o navegador irá tomar uma ação, disparando um erro, que pode ser esse: 

![](https://cdn-images-1.medium.com/max/1600/1*e0nEd59RPKz9coyY8FX-uw.png)

Rodar código em uma única `thread` pode ser bem simples, porque você não precisa lidar com cenários complicados que aparecem em ambientes `multi-thread`,por exemplo, `deadlocks`.

Mas rodar em `single-tread` é limitante. Já que JavaScript tem apenas uma pilha de chamadas, ** o que acontece se as coisas ficam lentas ?**

## Concorrência & o Event Loop

O que acontece quando você tem chamadas de função na Pilha de Chamadas que leva uma grande quantidade de tempo para ser processada? Por exemplo, imagine que você quer fazer alguma transformação de imagem complexa com Javascript no navegador.

Podem perguntar - Por que isso, ainda assim, é um problema? O problema é que enquanto a pilha de chamadas tem funções para executar, o navegador não pode de fato fazer nada mais. - está sendo bloqueado. Isso significa que o navegador não pode renderizar, não pode rodar nenhum outro código, está simplesmente preso. E isso cria problemas se você quer bons UIs flexíveis no seu app.

E isso não é único problema. Uma vez que seu navegador começa processar tantas tarefas na pilha de chamadas, pode interromper a responsividade por um longo tempo. E muitos navegadores agem gerando um erro, perguntando se você quer fechar a página.


![](https://cdn-images-1.medium.com/max/1600/1*WlMXK3rs_scqKTRV41au7g.jpeg)


Agora, isso não é a melhor experiência de usuário que existe, é?

Então, como nós podemos executar códigos complexos sem bloquear o UI e tornar o navegador não responsivo? Bom, a solução são os **`callbacks` assíncronos**.

Isso será explicado com mais detalhes na **Parte 2** de "Como Javascript realmente funciona" tutorial: ["Dentro da engine v8 + 5 dicas de como escrever códigos otimizados"](https://blog.sessionstack.com/how-javascript-works-inside-the-v8-engine-5-tips-on-how-to-write-optimized-code-ac089e62b12e).

Nesse meio tempo, se você está tendo um tempo difícil, reproduzindo e entendendo problemas nos seus apps Javascript, de uma olhada em [`SessionStack`](https://www.sessionstack.com/). `SessionStack` grava tudo no seu aplicativo web: todas mudanças no DOM, interações de usuários, exceções Javascript, rastreamento em pilha, falhas nas requisições de rede e mensagens de `debug`.

Com `SessionStack`, você pode repetir problemas nos seus aplicativos web como um vídeo, e ver tudo que acontece com seu usuário.

Existe um plano que permite que você [comece de graça](https://www.sessionstack.com/signup/).

![](https://cdn-images-1.medium.com/max/1600/1*kEQmoMuNBDfZKNSBh0tvRA.png)

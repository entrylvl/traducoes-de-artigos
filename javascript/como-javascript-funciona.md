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

## The Run Time

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

## Concurrency & the Event Loop

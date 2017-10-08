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

## The Call Stack

## Concurrency & the Event Loop

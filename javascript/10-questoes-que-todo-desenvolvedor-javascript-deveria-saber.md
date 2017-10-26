# 10 Questões de entrevistas que todo Desenvolvedor JavaScript deveria saber
#### AKA: Os Segredos para dominar o JavaScript

Na maioria das empresas, gestores devem confiar nos desenvolvedores para avaliar as habilidades do candidato em entrevistas técnicas. Se você foi bem como candidato, você eventualmente irá precisar entrevistar. Aqui está como.

## Começa com pessoas

Em ["How to Build a High Velocity Development Team"](https://medium.com/javascript-scene/how-to-build-a-high-velocity-development-team-4b2360d34021), fiz algumas pontuações que vale a pena serem repetidas:

> Nada prevê melhores resultados comerciais que uma equipe excepcional. Se você pretende superar suas chances, você precisa investir aqui, primeiro.

Como Marcus Lemonis diz, foco nos 3 P's:

> Pessoas, Processos, Produto

[The profit Principles With Marcus Lemonis | The Profit](https://www.youtube.com/embed/37rMZSA6oLk) (Video).

Suas primeiras contratações devem ser sólidas, com candidatos sêniores. Pessoas que podem contratar e mentorar outros desenvolvedores, e ajudar desenvolvedores pleno e júnior que você eventualmente irá contratar durante o caminho.

Leia ["Why Hiring is So Hard in Tech"](https://medium.com/javascript-scene/why-hiring-is-so-hard-in-tech-c462c3230017)

> O melhor caminho para avaliar um candidato é um exercício de programação em dupla.

Programe com o candidato. Deixe-o no controle. Assista e ouça mais do que fala. Um bom projeto pode ser puxar tweets da Twitter API e mostrar na tela em uma timeline.

Dito isto, nenhum exercício irá lhe dizer tudo que precisa saber. Uma entrevista pode ser uma ferramenta muito valiosa quando bem utilizada, mas não desperdice tempo perguntando sobre syntax ou particularidades de uma linguagem. VocÊ precisa visualizar o todo. Pergunte sobre arquitetura e paradigmas — as grandes decisões que terão maior impacto em um projeto inteiro.

Syntax e funcionalidades são fáceis de pesquisar no Google. É muito mais dificíl pesquisar sobre engenharia de software ou paradigmas comuns e expressões idiomáticas em JavaScript que são adquiridos com experiência.

JavaScript é especial, e desempenha um papel crítico em qualquer grande aplicação. O que torna JavaScript significativamente diferente de outras linguagens?

Aqui estão algumas questões que irá ajudar você a explorar o que realmente importa:

### 1. Você pode nomear dois paradigmas de programação imporatantes para desenvolvedores JavaScript?

JavaScript é uma linguagem multi-paradigma, suportanto programação **imperativa/procedural** junto com POO (Programação Orientada a Objetos) e **programação funcional**. JavaScript suporta POO com **herança de protótipo**.

#### Boas respostas:

* Herança de protótipo (como: prototypes, OLOO).
* Programação funcional (como: closures, funções de primeira classe, lambdas)

#### Alerta vermelho:

* Não faz ideia do que é um paradigma, não menciona OO prototipada ou programação funcional.

#### Leia mais:

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — OO Prototipada.
* [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4) — Programação Funcional.

### 2. O que é Programação Funcional?

Programação funcional produz programas compostos de funções matemáticas e evita compartilhar estados vazios e dados mutavéis. Lisp (especificada em 1958) era uma das primeiras linguagens que suportavam programação funcional, e era fortemente inspirada por cálculos lambda. Lisp e muitas linguagens da família Lisp ainda tem seu uso comum hoje em dia.

Programação funcional é um conceito essencial em JavaScript (um dos dois pilares do JavaScript). Várias funcionalidades funcionais foram adicionas ao JavaScript do ES5.

#### Boas respostas:

* Funções puras / pureza da função.
* Evitar efeitos colaterais.
* Exemplos de linguagens funcionais: Lisp, ML, Haskell, Erlang, Clojure, Elm, FSharp, OCaml, etc...
* Menção de características suportadas pela programação funcional: funções de primeira classe, funções de ordem superior, funções como argumentos/valores.

#### Alerta vermelho:

* Não mencionar funções puras / previnir efeitos colaterais.
* Incapaz de prover exemplos de linguagens de programação funcional.
* Incapaz de indentificar características do JavaScript que permitem programação funcional.

#### Leia mais:

* [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4).
* [The Dao of Immutability](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd).
* [Composing Software](https://medium.com/javascript-scene/composing-software-an-introduction-27b72500d6ea).
* [The Haskell School of Music](http://haskell.cs.yale.edu/wp-content/uploads/2015/03/HSoM.pdf).

### 3. Qual a diferença entre herança de classe e herança de protótipo?

Herança de classe: as instâncias herdam de classes (como um diagrama — uma descrição da classe), e cria um parentesco como subclasse : taxonomias hierárquicas de classe. As instâncias são geralmente instanciadas via funções contrutoras como a palavra-chave `new`. A herança de classe pode ou não usar a palavra-chave `class` no ES6.

Herança de protótipo: as instâncias herdam diretamente dos outros objetos. As instâncias são geralmente instanciadas via funções factory ou `Object.create()`. As instâncias podem ser compostas por variados objetos, permitindo uma herança seletiva fácil.

> In javaScript, hherança de protótipo é simples e mais flexivél que herança de classe.

#### Boas respostas:

* Classes: criar acoplamentos precisos ou hierárquias/taxonomias.
* Protótipos: menciona herança concatenada, delegação de protótipo, herança funcional, composição de objeto.

#### Alerta vermelho

* Nenhuma preferência por herança de protótipo e composição sobre herança de classe.

#### Saiba mais:

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3)— Prototypal OO.
* [Common Misconceptions About Inheritance in JavaScript](https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a).

[Classical Inheritance is Obsolete - How to Think in Prototypal OO](https://vimeo.com/69255635) (Video).
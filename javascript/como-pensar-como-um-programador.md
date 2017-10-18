[Artigo original: How to think like a programmer](https://medium.freecodecamp.org/how-to-think-like-a-programmer-3ae955d414cd)

# Como pensar como um programador

![](https://cdn-images-1.medium.com/max/1000/1*otgsthXHixWZ8Xs_a4cl_g.jpeg)

"Eu não entendo JavaScript. Eu não consigo criar componentes do zero. Minha mente dá um branco quando eu vejo um arquivo JavaScript em branco. Eu acho que isso ocorre porque eu não sei pensar como um programador."

Isso parece familiar para você? Saiba que você não está sozinho, meu amigo. Muitas pessoas que escolhem JavaScript como sua primeira linguagem de programação enfrentam o mesmo problema.

Nossa, até mesmo desenvolvedores que já programam em outra linguagem também se deparam com este mesmo problema. Então ao invés de "Eu não consigo pensar como um programador", eles dizem "Eu não consigo pensar em JavaScript".

Mas não mais. Hoje iremos aprender a pensar como um programador.

## Você já pode pensar como um programador.

Já experimentou exercícios simples em plataformas como freeCodeCamp, Code Academy ou Code Wars?

Se sim, você já sabe como pensar como um programador.

O verdadeiro motivo para sua mente congelar quando você se depara com um arquivo JavaScript em branco é provavelmente devido a um bloqueio de programador. Você está com medo de escrever um código que não funciona. Está com medo de encarar os erros. Você não sabe como começar.

Superar este bloqueio é muito simples. Você pode seguir estes passos:

1. Quebre o problema em outros pequenos problemas.
2. Procure soluções para estes problemas pequenos.
3. Reúna suas soluções em um todo coerente.
4. Refatore e melhore.

Vamos olhar mais de perto cada um destes passos.

## Passo 01: Quebre o problema em outros pequenos problemas.

Como você coloca um elefante dentro de uma geladeira?

Aqui está o que a maioria das pessoas responderiam:

1. Abra a geladeira.
2. Ponha o elefante dentro dela.
3. Feche a geladeira.

Problema resolvido.

![](https://cdn-images-1.medium.com/max/800/0*PGDaDsFOBO6-NdQv.jpg)

Essa resposta é o melhor exemplo do porque você está fica travado quando se depara com um arquivo JavaScript em branco. Está pulando passos.

Se você pensar de forma lógica sobre a questão, irá perceber que há alguns problemas que permanecem sem respostas.

1. De qual geladeira estamos falando?
2. Que tipo de elefante se trata?
3. Se o elefante for muito grande para que caiba em uma geladeira, o que fazer?
4. Onde você encontrou um elefante em primeiro lugar?
5. Como irá transportar o elefante até sua geladeira?

Quando está programando, você precisa responder toda pequena questão que imaginar. É por isso que o primeiro passo é quebrar seu problema em peças menores.

## Passo 02: Encontrando soluções para seus pequenos problemas.

O segundo passo é encontrar a solução para cada um de seus problemas. Neste passo, é importante que você seja o mais detalhado possível.

1. Qual geladeira? — a geladeira que fica em sua cozinha.
2. Qual tipo de elefante? — o elefante da floresta africana.
3. E se o elefante for muito grande? — Pegue uma arma encolhedora (🔫) para encolher o elefante (😎).
4. Onde você encontra o elefante? — África
5. Como transportar o elefante? — Coloque em sua mala depois de encolhido e então pegue um avião de volta para casa.

Algumas vezes, você precisa se aprofundar mais para ter a resposta que precisa. Por exemplo, nós podemos nos aprofundar nas questões 3 e 4.

1. Onde você encontra uma arma encolhedora? — Pedir emprestado ao cientista maluco ao lado.
2. Em que lugar na África você irá encontrar seu elefante? —  Addo Elephant Park na África do Sul.

Uma vez que você já tenha as respostas dos seus pequenos problemas prontas, poderá uni-las para resolver seu grande problema.

## Passo 03: Reunir as soluções de forma coerente.

Então, no exemplo colocar-um-elefante-em-uma-geladeira, você provavelmente seguiu os seguintes passos:

1. Pedir emprestado a arma encolhedora do cientista maluco ao lado.
2. Viajou até a África do Sul.
3. Foi até o Addo Elephant Park.
4. Encontrou um elefante na reserva.
5. Atirou no elefante com a arma encolhedora.
6. Guardou o elefante em sua mala.
7. Viajou de volta ao aeroporto.
8. Voou até o seu país.
9. Voltou para sua casa.
10. Colocou o elefante em sua geladeira.

Problema resolvido.

Por mais interessante que seja, você provavelmente não poderia capturar elefantes e por em geladeiras com JavaScript.

## Vamos a um exemplo real.

Digamos que você queira criar um butão que, quando pressionado, mostre uma barra lateral.

<p data-height="265" data-theme-id="0" data-slug-hash="zdqmLe" data-default-tab="css,result" data-user="zellwk" data-embed-version="2" data-pen-title="Sidebar for Thinking like a programmer article" class="codepen">Veja o Pen <a href="https://codepen.io/zellwk/pen/zdqmLe/">Sidebar for Thinking like a programmer article</a> por Zell Liew (<a href="https://codepen.io/zellwk">@zellwk</a>) no <a href="https://codepen.io">CodePen</a>.</p>

## O primeiro passo — dividir em pequenos pedaços.

Divida o componente em pequenos pedaços. Aqui estão alguns problemas que você pode indentificar:

1. Qual é a marcação HTML deste botão?
2. Como este botão deveria se parecer?
3. O que acontece quando este botão é clicado uma vez?
4. O que acontece quando este botão é clicado novamente?
5. O que acontece quando este botão é clicado uma terceira vez?
6. Qual é a marcação HTML desta barra lateral?
7. Como a barra lateral se parece quando visível?
8. Como a barra lateral se parece quando oculta?
9. Como a barra lateral aparece?
10. Como a barra lateral desaparece?
11. A barra lateria deveria aparecer quando a página é carregada?

## O segundo passo — criando soluções para o problema.

Para criar soluções, você precisa ter um conhecimento sobre oque está criando. Em nosso caso, você precisa ter um conhecimento suficiente sobre HTML, CSS e JavaScript.

Não se preocupe caso você não saiba responder a nenhuma uma dessas perguntas. Se você os dividiu o suficiente, você deve encontrar uma respostas através do Google em cinco minutos.

Então vamos responder cada uma das questões:

### Qual é a marcação HTML deste botão?

A marcação é uma tag &lt;a&gt; com uma classe <strong>.button</strong>.

<pre>&lt;a href="#" class="button"&gt;Click me&lt;/a&gt;</pre>

### Como este botão deveria se parecer?

Este botão deve ter o seguinte CSS:

<pre>
  .btn {
    display: inline-block;
    font-size: 2em;
    padding: 0.75em 1em;
    background-color: #1ce;
    color: #fff;
    text-transform: uppercase;
    text-decoration: none;
  }
</pre>

### O que acontece quando este botão é clicado uma vez? Duas? Três vezes?

A barra lateral deve aparecer quando o botão é clicado uma vez. Está barra lateral então deveria ser ocultada quando o botão é clicado uma outra vez. Está deveria ser visível quando o botão é clicado novamente.

### Qual é a marcação HTML desta barra lateral?

<pre>
  &lt;div class="sidebar"&gt;
    &lt;ul&gt;
      &lt;li&gt;&lt;a href="#"&gt;Link 1&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Link 2&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Link 3&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Link 4&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Link 5&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/div&gt;
</pre>

### Como o barra lateral se parece quando visível?

A barra lateral deve ser colocada a direita da janela do navegador. Esta precisa ser realocada para estar visível ao usuário. Deverá ter uma largura de 300px.

Quando você terminar de resolver o problema, você pode terminar com um CSS similar a este:

<pre>
  .sidebar {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    width: 300px;
    background-color: #333;
  }

  .sidebar ul {
    margin: 0;
    padding: 0;
  }

  .sidebar li {
    list-style: none;
  }

  .sidebar li + li {
    border-top: 1px solid white;
  }

  .sidebar a {
    display: block;
    padding: 1em 1.5em;
    color: #fff;
    text-decoration: none;
  }
</pre>

### Como a barra lateral se parece quando oculta?

A barra lateral deve ser realocada a 300px para direita, estando assim fora da tela.

Quando você responder está questão, poderá ter mais outras duas questões em mente:

1. Como saberá se a barra lateral está a visível ou oculta?
2. Como você estiliza a barra lateral oculta?

Então iremos responder elas.

### Como saberá se a barra lateral está a visível ou oculta?

Se a barra lateral tiver uma classe <strong>.is-hidden</strong>, a barra lateral deve estar oculta. Caso contrário, ela deve estar visível.

### Como você estiliza a barra lateral oculta?

Nós usaremos <strong>translateX</strong> para deslocar a barra lateral 300px para a direita uma vez que a propriedade <strong>transform</strong> é uma das melhores para animação. Seu estilo então será este:

<pre>
  .sidebar.is-hidden {
    transform: translateX(300px);
  }
</pre>

### Como a barra lateral aparece?

A barra lateral não pode aparecer imediatamente. Esta precisa se mover da direita, quando oculta, para a esquerda, quando visível.

Se você sabe CSS, você poderá utilizar a propriedade <strong>transition</strong>. Se não, você pode procurar por uma resposta através do Google.

<pre>
  .sidebar {
    /* other properties */
    transition: transform 0.3s ease-out;
  }
</pre>

### Como o barra lateral desaparece?

Ela deve desaparecer da mesma forma que aparece, na direção oposta. Com isto, você não tem de escrever nenhum código CSS adicional.

### A barra lateral deveria aparecer quando a página é carregada?

Não. Neste caso, nós podemos adicionar uma classe <strong>is-hidden</strong> na marcação da barra lateral e ela deve permanecer oculta.

<pre>
  &lt;div class="sidebar is-hidden"&gt;
    &lt;!-- links --&gt;
  &lt;/div&gt;
</pre>

### Agora, nós já respondemos quase tudo, exceto uma coisa — o que acontece quando o botão é clicado uma vez? Duas? Três vezes?

Nossa resposta acima foi muito vaga. Nós sabemos que a barra lateral deve aparecer quando você clica nele, mas como? A barra lateral deve desaparecer quando você clica novamente, mas como?

Este é o ponto, nós podemos responder está questão novamente e com mais detalhes. Mas antes disso, como saber quando você clicou em um botão?

### Como saber quando você clicou em um botão.

Se você conhece JavaScript, você sabe que podemos adicionar um "event listener" para o botão e ouvir por um evento <strong>click</strong>. Se você não sabe, você pode usar o Google para conhecer.

Antes de você adicionar um ouvinte de eventos, você precisa encontrar a marcação do botão com um <strong>querySelector</strong>.

<pre>
  const button = document.querySelector('.btn')

  button.addEventListener('click', function() {
    console.log('button is clicked!')
  })
</pre>

### O que acontece quando o botão é clicado uma vez?

Quando o botão for clicado uma vez, nós devemos remover a classe <strong>is-hidden</strong> e então mostrá-lo. Para remover uma classe em JavaScript, nós usamos <strong>Element.classList.remove</strong>. Isso significa que nós precisamos selecionar a barra lateral primeiro.

<pre>
  const button = document.querySelector('.btn')
  const sidebar = document.querySelector('.sidebar')

  button.addEventListener('click', function() {
    sidebar.classList.remove('is-hidden')
  })
</pre>

### O que acontece quando o botão é clicado uma segunda vez?

Quando o botão é clicado novamente, nós devemos adicionar a classe <strong>is-hidden</strong> de volta a barra lateral para que então ela desapareça.

Infelizmente, nós não podemos detectar quantas vezes o botão foi clicado com um "event listener". A melhor forma, então, é checar se a classe <strong>is-hidden</strong> está presente na barra lateral. Se sim, nós a removemos. Se não, nós a adicionamos.

<pre>
  const button = document.querySelector('.btn')
  const sidebar = document.querySelector('.sidebar')

  button.addEventListener('click', function() {
    if (sidebar.classList.contains('is-hidden')) {
      sidebar.classList.remove('is-hidden')
    } else {
      sidebar.classList.add('is-hidden')
    }
  })
</pre>

Com isso, você tem uma protótipo inicial de um componente.

[](https://codepen.io/zellwk/pen/zdqmLe/)

## O quarto passo — refatorando e melhorando.

Nós incorporamos o terceiro passo, assimilamos nossas soluções e organizamos de forma coerente, ao londo do caminho. O passo final é refatorar e melhorar seu código. Você pode não compreender este passo naturalmente por enquanto. Leva tempo de prática e muito esforço antes de você ter seu código melhorado.

Então uma vez que os três passos estejam completos, dê uma pausa e trabalhe em outra coisa. Quando estiver conhecendo melhor JavaScript, você pode notar que deixou escapar alguns poucos detalhes quando voltar.

Neste exemplo acima, você pode se questionar um pouco mais?

1. Como fazer o componente desta barra lateral acessível para usuários com deficiência visual?
2. Como fazer está barra lateral um componente facilmente utilizável por pessoas através do teclado?
3. Você pode melhorar o código de alguma forma?

Para este terceiro ponto, se você pesquisou um pouco mais, você pode ter notado que há um método <strong>toogle</strong> que remove uma classe se presente. Se a classe não estiver presente, o método <strong>toogle</strong> a adiciona para nós:

<pre>
  const button = document.querySelector('.btn')
  const sidebar = document.querySelector('.sidebar')

  button.addEventListener('click', function() {
    sidebar.classList.toggle('is-hidden')
  })
</pre>

## Resumindo

Pensar como um programador é simples. O segredo é saber como dividir o problema em outros pequenos pedaços.

Quando você terminar de dividir o problema, encontre soluções para estes pequenos problemas e escreva o código para eles. Ao longo do caminho, você irá descobrir mais problemas que não havia pensado antes. Resolva eles também.

Quando terminar de responder cada problema, você terá a resposta seu problema inteiro. Algumas vezes, você pode precisar juntar os passos para resolver seus pequenos problemas também.

Finalmente, o trabalho não está pronto quando você cria sua primeira solução. Há sempre algo para ir melhorando. No entanto, você poderá não enxergar essas melhorias por agora. Dê um tempo, trabalhe em outra coisa e volte mais tarde. Você poderá fazer perguntas ainda melhores.
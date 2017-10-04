Artigo Original: https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf

  Como JavaScript funciona: uma visao geral da engine, do runtime e da pilha de chamadas

  Como JavaScript está ficando cada vez mais popular, times tem se aproveitado de seu suporte para vários papéis em suas funções - front-ned, back-end, aplicativos hibridos e muito mais.
  Este post é o primeiro numa série com a intencao de se aprofundar em JavaScript e em como ele realmente funciona: nos achamos que ao saber como os blocos de construçāo do JavaScript e como eles se integram você terá a oportunidade de escrever códigos e aplicativos melhores.
  Como visto nas estatisticas do GitHut (http://githut.info), JavaScript está no topo em termos de repositórios ativos e pushes totais no GitHub. E não fica muito atras em outras categorias.
  Se os projetos estão ficando tão dependentes do JavaScript, isso significa que desenvolvedores têm que utilizar tudo que a linguagem e seu ecossistema providenciam e entender como funciona internamente para construir programas cada vez melhores.
  Mas, na verdade, existem muitos desenvolvedores usam JavaScript diariamente sem o conhecimento do que acontece debaixo dos panos.
  
  Visão Geral
  
  Muitos já ouviram falar da engine V8 como um conceito, e a maioria sabe que o JavaScript é single-threaded* ou que usa uma fila para callback*.
  Neste artigo iremos passar por todos estes conceitos em detalhes e explicaremos como JavaScript realmente roda. Sabendo desses detalhes, voce tera a habilidade de escrever aplicativos melhores, que utilizam as APIs disponiveis da melhor forma.
  Se você for relativamente novo em JavaScript, este artigo irá te ajudar a entender o porque JavaScript é tão "estranho" comparado a outras linguagens. E, se você for um desenvolvedor JavaScript experiente, te dará novas formas de pensar e encarar como o JavaScript Runtime que você usa todo dia funciona. 
  
  The JavaScript Engine
  
  The Runtime
  
  The Call Stack
  
  Concurrency & the Event Loop

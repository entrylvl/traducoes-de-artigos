# Como ser* um compilador - Faça um compilador com JavaScript

## *Sim! Você deve ser um compilador. É muito legal.

Este post foi publicado sobre a licença CC BY-NC-SA 4.0.
Me avise caso você faça um tradução para outra lingua, para ela poder ser adicionada na lista.

Um maravilhoso domingo em Bushwick, Brooklyn. Eu achei um livro chama "Design by Number"(Desenhe através de numeros) por John Maeda na minha livraria local. Nele tinha instruções passo a passo da linguagem de programação DBN - uma linguagem de programação feita no fim dos anos 90 no laboratório de mídia do MIT, feito para introduzir programação de computadores com conceitos visuais.

![](http://i.imgur.com/ur3ls5B.png)

Eu imediatamente pensei em fazer SVG através do DBN e rodar em browser, seria um projeto interessante em 2016, melhor que instalar o ambiente Java para executar o código fonte original do DBN.
Eu percebi que teria que escrever um compilador de DBN para SVG, então a aventura de escrever um compilador começou. "Fazendo um compilador" para muito como ciência da computação...mas eu nunca cruzei nós em entrevistas de código, será que eu posso fazer um compilador?

Let’s try to be a compiler first
## Vamos tentar fazer um compilador primeiro

Compilador é um mecanismo que pega um pedaço de código se transforma em outrs coisa. Vamos compilar um  simples DBN em um desenho fisíco.
Existe três comandos nesse código DBN, "Paper" define a cor do papel, "Pen" define a cor da caneta, e "Line" que desenha uma linha. No parametro da cor, 100 significa preto ou rgb(0%, 0%, 0%) no CSS. A imagem produzida pelo DBN sempre é na escala do cinza. No DBN o papel sempre é 100x100, a largura da linha sempre é 1 e a linha é definida por coordenadas x e y do ponto de inicio e até o ponto final contando a partir do canto inferior esquerdo.
Vamos ser o compilador nós mesmos. Pare agora, pegue papel e caneta, e vamos tentar compilar as seguintes linhas de código como desenho.

```
Paper 0
Pen 100
Line 0 0 100 50
```

Você desenhou uma linha preta no meio da esqueda para a direta? Parabéns! Você acabou de se tornar um compilador.

## Como um compilador funciona?

Vamos ver oque acabou de acontecer na nossa cabeça como um compilador.

1. Análise Lexica (tokenização)

Primeira coisa que nos fizemos foi separar cada palavra chave (chamadas de tokens) por um espaço em branco. Enquanto separavamos as palavras, nos tambem associamos tipos primitivos a cada token, como "palavra" ou "número".

![](http://i.imgur.com/Od8BBR6.png)

2. Parseamento (Análise Sintática)

Quando o bloco de texto é separado em tokens, nós analizamos cada um deles e tentamos encontrar a relação entre os tokens.
Nesse caso, nós agrupamos os números associados com os tokens de comando. Fazendo isso, nós começamos a ver a estrutura do código.

![](http://i.imgur.com/vqrhG77.png)

3. Transformação

Quando nós analisamos a sintase pelo parseamento, nos transformamos a estrutura em algo apropriado para o resultado final. Nesse caso, nós vamos desenhar a imagem, então nós estamos trasnformando isso em instruções passo a passo para seres humanos.


![](http://i.imgur.com/gMKP9rL.png)

4. Geração de código
Por último, nós fazemos do resultado compilado, um desenho. Nesse ponto, nós seguimos as instruções que fizemos no último passo para desenhar.

E é isso que um compilador faz!

O desenho que nós fizemos é o resultado compilado (como um .exe quando compilamos um código em C). Nós podemos passar esse desenho para qualquer um ou qualquer dispositivo (scanner, câmera e etc) para "rodar" e todos verão uma linha preta no meio.


# Um compilador não deve usar recurção, busca em arvore e etc ?

Sim, e essas são otimas tecnicas para construir um compilador, não não significa que você tem que usa-las na primeira vez.

Eu comecei fazendo um compilador para uma pequena parte da linguagem DBN, uma parte bem limitada. Desde então, eu aumentei o escopo e agora planejo adicionar funcionalidades como variaveis, blocos e laços para este compilador. Seria uma ótima ideia usar estas técnicas agora, mas não é um requisito para começar.


Writing compiler is awesome
What can you do by making your own compiler ? Maybe you might want to make new JavaScript-like language in Spanish… how about español script?

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

Exitem pessoas que fizeram linguagens de programação em Emoji (Emojicode) e em imagem colorida (Linguagem programação Piet). As possibilidades são infinitas!

## Aprendizados ao fazer um compilador

Fazer um compilador foi divertido, mas acima de tudo, me ensinou muito sobre desenvolvimento de software. Aqui estão algumas coisas que eu aprendi enquanto fazia meu compilador.

### 1. Você não precisa conhecer tudo
Assim como o nosso analisador léxico, você não precisa saber tudo desde o início. Se você realmente não entender uma parte do código ou tecnologia, não hesite em dizer "Tem isso, e eu sei um pouco dela" e passar para o próximo passo. Não se estresse com isso, você ir'á entender eventualmente.

### 2. Não seja um babaca com mensagens de erro
O papel do analisado é seguir a regra e checar se as coisas foram escritas segundo ela. Muitas vezes erros acontecem. Então, tente enviar mensagens úteis e acolhedoras. É fácil falar "Isso não funciona desse jeito” (como "Token ILEGAL" ou "undefined não é uma função" erro no JavaScript) mas ao invés tento falar aos seus usuários o que deveria acontecer, o melhor que você conseguir.

Isso também se aplica a comunicação da equipe. Quando alguém está travado em uma questão, ao invés de dizer "isso não funciona", talvez você possa começar dizendo "Eu tentaria jogar no google palavras chaves como ___ and ___ ." ou “Eu recomendaria ler essa página na documentação.” Você não precisa fazer o trabalho por eles, mas você com certeza pode ajudar eles a fazer um trabalho melhor e mais rápido, apenas fornecendo um pouco mais de ajuda. Elm é uma linguagem de programação que [abraça esse método](http://http://elm-lang.org/blog/compiler-errors-for-humans). Ela usa "Talvez você quisesse tentar isso?" na mensagem de erro.

### 3. Contexto é tudo

Finalmente, como nosso transformador transformou um tipo de ASA em outra mais apropriada para o resultado final, tudo é especifico do contexto.
Não existe uma maneira perfeita de fazer as coisas. Então não faça as coisas só porque é popular ou porque você fez antes, pense primeiro no contexto. Coisas que funcionam para um usuário podem ser um desastre para outro.
Tambem aprecie o trabalho que estas transformações fazem. Você pode conhecer um otimo transformador no seu time - alguem que é muito bom em aproximar distâncias.
O trabalho dessas transformadores podem não produzir código diretamente, mas é muito importante para produzir um produto de qualidade.

Espero que você tenha gostado deste artigo e eu espero que tenha te convencido sobre o quão legal é contruir e ser um compilador.
Esse é um excerto de uma palestra que eu ministrei na JSCong Colombia 2016 em Medellin, Colombia. Se quiser saber mais sobre esta a palestra veja os slides aqui.

[Artigo original: A Beginner’s Guide to Pure CSS Images](https://medium.com/coding-artist/a-beginners-guide-to-pure-css-images-ef9a5d069dd2)

---
# Um guia de iniciantes para imagens em puro CSS

Atualização (14/3/17) Temos também um curso 100% gratuito por email para aprender imagens em puro CSS. Você pode se [matricular aqui](https://coding-artist.teachable.com/p/how-to-make-pure-css-images)

Atualização (6/1/17) Disponibilizamos nosso desafio de 50 dias por email chamado Daily CSS Images, que te desafia a criar imagens em puro CSS todos os dias comerciais da semana. É uma ótima forma de continuar praticando. Você pode se [cadastrar aqui](http://dailycssimages.com/)

Atualização (3/1/17) Se você prefere escutar, [aqui está um vídeo](https://www.youtube.com/watch?v=ULhv96NdF_Q) para seguir o conteúdo no formato de áudio.

No que você está se envolvendo: uma leitura de 17 minutos. Uma explicação detalhada sobre como criar imagens em puro CSS. Vamos começar com uma geral e trabalhar para criar um Coala em puro CSS.

O que suponho que você sabe: Meu método de ensino é não supor que você já sabe os princípios básicos. A não ser que você seja um completo iniciante com HTML e CSS, eu não faço nenhuma suposição.

Se você não é inicianete: Eu vou repetir os princípios básicos frequentemente. Pule as partes que são muito fáceis para você e entenda que isso foi feito para ajudar pessoas com todos os níveis de conhecimentos.

## Introdução

Uma linha é frequentemente traçada entre um artista/designer que trabalha com vetores e um desenvolvedor front-end. Isso acontece pois muitas empresas possuem mãos-de-obra e trabalhos suficientes para realizar essa separação de forma produtiva. Outro fator relevante é a vontade de algumas pessoas em focar somente no desenvolvimento front-end, enquanto outras querem ser extremamente específicas em ilustrações. Mesmo nas duas áreas, existem determinados nichos que podem ser escolhidos como foco para desenvolver um conjunto de habilidades muito valioso e bom.

Sem dúvida essa separação é sensata, porém, eu acho que um desenvolvedor front-end poderia se beneficiar imensamente trabalhando com ilustrações, mesmo se esse não for seu foco principal. 

Eu acredito que esse é o caso, pois as duas habilidades são essenciais para criar diferentes componentes de um produto final. Ilustradores que trabalham com vetores criam diferentes formas geométricas, e manipulações dessas, para criar uma ilustração final. Desenvolvedores front-end criam componentes com código para formar uma página web.

Aprender como fazer vetores gráficos ensina sobre layouts, paleta de cores, manipulações de formas geométricas, e criatividade em geral, fator relevante na área de desenvolvimento front-end.

Provavelmente eu deveria continuar essa discussão sobre os benefícios da ilustração com vetores para desenvolvedores front-end. Comentei sobre esse tópico pois imagens em puro CSS são exemplos de quando a intersecção entre ilustradores de vetores e desenvolvedores front-end é muito próxima.

Criar uma imagem em puro CSS é essencialmente criar um vetor gráfico, mas ao invés de utilizar softwares de ilustração com vetor (ex: Illustrador, Affinity Designer, Sketch) são utilizados códigos CSS no lugar da barra de ferramenta.

Apesar da próxima intersecção, acredito que ilustradores de imagens vetoriais podem ver toneladas de código CSS para criar uma imagem como algo intimidador, e os desenvolvedores front-end também podem considerar criar imagens com código algo tão assustador quanto.

Por essa razão, vou criar um tutorial de como criar sua primeira imagem em puro CSS, e espero que esse tutorial cumpra pelo menos alguns dos tópicos abaixo:

1. Aumentar a confiança para criar imagens em puro CSS
2. Fornecer melhor entendimento sobre como imagens em puro CSS funcionam
3. Ampliar a curiosidade sobre ilustração com vetores para desenvolvedores front-end
4. Amplicar a curiosidade sobre desenvolvimento front-end para ilustradores de imagens vetoriais
5. Fornecer um template básico para criar mais imagens em puro CSS

##Os componentes de uma imagem em puro CSS
Primeiro vamos explicar o que exatamente "puro CSS" significa?

O termo "puro CSS" se refere a criação de uma imagem simplesmente adicionando estilos a várias divs em HTML via CSS.

Por exemplo, podemos criar um quadrado com somente uma div HTML e estilizá-la aplicando uma classe CSS.

[Quadrado com somente uma div](https://codepen.io/mikemang/pen/53eeb0ec060d1b4a263f0ca47f6d9e3e)

Com imagens em puro CSS criaremos formas estilizando divs HTML com somente CSS, com o objetivo de formar uma imagem final.

Cada projeto de puro CSS consiste dos seguintes componentes:
1. Uma div HTML para cada forma
2. Uma classe CSS específica para cada div HTML
3. Classes CSS com estilo para a div HTML correspondente
4. Uma caixa invisível que servirá como canvas (vai fazer mais sentido depois... eu prometo)

Aqui está a imagem final em puro CSS que vamos criar e contém somente os componentes listados acima:

[Imagem final em puro CSS](https://codepen.io/mikemang/pen/oYMePj)

Mas antes de começar a programar, vamos dividir as formas específicas que fazem essa imagem do Coala.

Nota: Se você prefere vídeo pode acessar um vídeo tutorial com esse conteúdo em nosso [curso gratuito em vídeo de imagens em puro CSS](https://coding-artist.teachable.com/p/how-to-make-pure-css-images).

**Composição de formas**
Primeiro, a imagem completa do Coala será construída em cima do canvas quadrado invisível (não é a terminologia oficial). Essa caixa invisível será centralizada com o corpo do HTML e a cabeça será centralizada com a caixa. Eu pessoalmente acho essa abordagem uma boa prática, pois ela simplifica o design responsivo, o que vou descrever no final desse post.

Agora mantenha em mente que existirá uma caixa retangular invisível, a qual eu defino abaixo: 

![](https://cdn-images-1.medium.com/max/800/1*MYy6c239bE6lHyMr1jKQBQ.png)

Segundo, temos um círculo no centro da página web que irá criar a cabeça.

![](https://cdn-images-1.medium.com/max/800/1*lnsXWnA0vpb08LifeeeSYw.png)

A seguir, orelhas ficarão em cada lado da cabeça. Cada orelha é composta por dois diferentes círculos coloridos sobrepostos, com um círculo levemente menor que o outro. Nós vamos distinguir entre a div de orelha e a div da parte interna da orelha.

![](https://cdn-images-1.medium.com/max/800/1*wNGTBnkVJdDa3B-iCJM7Tg.png)

Adicionalmente, teremos dois olhos que também são dois círculos sobrepostos entre si. Vamos distinguir entre olho, círculo branco maior, pupila, e círculo preto menor.

![](https://cdn-images-1.medium.com/max/800/1*uAVtlWSWEBhL3pn8LaPm2Q.png)

A seguir, criaremos o nariz, que será um retângulo marrom arredondado logo abaixo dos olhos.

![](https://cdn-images-1.medium.com/max/800/1*yscTJSYtWzIRa5Qw5kSY0Q.png)

Por último, teremos dois pedaços de cabelo cinza que serão dois triângulos em locais diferentes no topo da cabeça.

![](https://cdn-images-1.medium.com/max/800/1*ybfg2A_os8zi1Bu-posqDA.png)

Outra coisa que é importante mencionar é a presença de diferentes camadas nesta imagem. As orelhas ficarão atrás da cabeça, o nariz será na frente dos olhos, etc. Isso será explicado conforme estilizamos o CSS.

**O HTML**

**Nota: **Para adicionar o cabelo à nossa imagem do coala, vamos usar o método *clip-path*. Esse método é suportado pelo Chrome, Safari e Opera. Se você está usando o Firefox, mude para um dos navegadores suportados, preferencialmente Chrome, para programar durante este guia.

Normalmente, eu trabalho inserindo uma única `div` que servirá como uma forma, estilizo esta forma no CSS e, então, sigo com a inserção da próxima `div`.

No entanto, para fins educacionais, vamos dar uma olhada no HTML como um todo e, então, observar cada seção.

```html
<body>
 <!-- Begin Image -->
 <!-- Invisible Box-->
 <div class="box">
   
    <!-- Circular Head-->
    <div class="head">  
      
      <!-- Circular Head Copy -->
      <div class="head-copy"></div>
      
       <!-- Left Ear ~ Light Gray-->
      <div class="ear-left">
        
       <!-- Inner ear ~ Dark Gray -->
      <div class="inner-ear"></div>
      </div>
      
      <!-- Right Ear ~ Light Gray-->
       <div class="ear-right">
      <!-- Inner Ear ~ Dark Gray-->
        <div class="inner-ear"></div>
      </div>
      
      <!-- Left Outer Eye ~ White -->
      <div class="eye-left">
        <!-- Pupil ~ Black -->
        <div class="pupil">
        </div>
      </div>
      
      <!-- Right Outer Eye ~ White -->
      <div class="eye-right">
        <!-- Pupil ~ Black -->
        <div class="pupil">
        </div>
      </div>
      
       <!-- Nose ~ Brown -->
       <div class="nose">
       </div>
      
       <!-- Hair ~ Light Gray -->
      <div class="hair-left"></div>
      <div class="hair-right"></div>
      
    <!-- End Head -->
    </div>
 <!-- End Invisible Box -->
 </div>
</body>
```

É essencial notar que algumas `div`s estão aninhadas entre outras `div`s. Por exemplo, vamos dar uma olhada na nossa `div` da orelha direita:

```html
<!-- Right Ear ~ Light Gray-->
       <div class="ear-right">
      <!-- Inner Ear ~ Dark Gray-->
        <div class="inner-ear"></div>
      </div>
```

Há a tag inicial `<div class=”ear-right”>`, que contém a `<div
class=”inner-ear></div> ` antes de sua tag de fechamento. A `ear-right` é a `div` *pai*, e a `inner-ear` é a `div` *filha*.

O motivo pelo qual isso é importante é porque as formas receberão localizações, larguras e alturas fixas, que são baseadas em porcentagem. A porcentagem se aplica à `div` pai.

Por exemplo, vamos supor que temos uma `div` que está aninhada entre o `body`, e o `body` está definido com 100% de altura e 100% de largura:

![](https://cdn-images-1.medium.com/max/800/1*513-zBMmioexAKNCHLOxFA.png)

A classe `some-div` atribui uma posição fixa que é 10% do topo. Como `some-div` está aninhada entre o `body`, que tem 100% de altura e 100% de largura, a `div` será 10% abaixo do topo da tela.

![](https://cdn-images-1.medium.com/max/800/1*hmEKdNbC5v1uT5SFbuI6Bw.png)

Agora vamos aninhar outra `div` entre `some-div` e, então, atribuir a ela uma posição absoluta de 10% a partir do topo.

![](https://cdn-images-1.medium.com/max/800/1*a9hVkK1yanv0WFcRv9Vesw.png)

Nós teremos uma posição completamente diferente, como você pode ver:

![](https://cdn-images-1.medium.com/max/800/1*j5PZQ9ZVkiZnUO3l_X10Xw.png)

Nesse exemplo, `another-div` (quadrado azul) está 10% abaixo da `some-div` (quadrado vermelho).

Agora vamos remover `another-div` de estar dentro de `some-div`, aninhe-a sob o `body` e mude a porcentagem do topo para 30%. 

![](https://cdn-images-1.medium.com/max/800/1*B7bU3rTbVG2yqanq1dHeMQ.png)

Agora `another-div` (quadrado azul) está 30% abaixo to topo da tela, e não 30% abaixo de `some-div` (quadrado vermelho).

![](https://cdn-images-1.medium.com/max/800/1*0abRFQKPM8o7YbzCIpMrRA.png)

Com isso em mente, vamos para a estilização em CSS.

## Estilização em CSS

**Body**
Para começar a estilização, vamos dar uma cor de fundo, um azul estilo Twitter, para a tag body.

```html
body{
  background: #25A9FC;
}
```

**Box/Caixa**
A seguir, vamos estilizar a caixa invisível. A caixa invisível será centralizada horizontalmente pois o código a seguir é o que permite que ela seja centralizada horizontalmente (nota: se você está seguindo para ver como a posição da caixa muda é possível alterar a cor de fundo da caixa ou adicionar uma borda sólida):

```html
.box{
  position: relative;
  margin: auto;
  display: block;

  //fundo ou borda opcional

  background: white;
  border: solid 4px red;

  //adicionar mais código aqui
}
```

A posição relativa (*position: relative*) significa que o elemento está posicionado de forma relativa a sua posição normal, o que seria o extremo topo do canto esquerdo, pois essa é a primeira div na tag body.

![](https://cdn-images-1.medium.com/max/800/1*qQlKbG2wHVzUP1NXNfv9_A.png)

Quando a posição está definida como relativa, utilizando display: block; e margin: auto; o centro da caixa será automaticamente centralizado horizontalmente.

Agora podemos adicionar o seguinte código para fazer a caixa ser 8% mais baixa, definir a altura (height) e largura (width) com as dimensões mostradas na imagem abaixo, e por último atribuir um fundo.

```html
.box{
  position: relative;
  margin: auto;
  display: block;
  margin-top: 8%;
  width: 600px;
  height: 420px;
  background: none;
}
```

Uma coisa para lembrar é que usamos *margin-top: 8%* para abaixar a caixa em 8%. Como especificamente ajustamos a margem do topo (*margin-top*), isso não irá afetar o atributo *margin: auto* que utilizamos para centralizar a caixa. Se tivessemos utilizado *margin: 8%* o atributo *margin: auto* seria sobrescrito.

Agora que nossa caixa está definida, todas as outras divs precisam ser aninhadas com a caixa. Isso é importante, pois iremos atribuir posições absolutas (topo, direita, esquerda, ou inferior) em porcentagem que irão posicionar a div na mesma porcentagem em relação a caixa e não do corpo (body). O mesmo conceito será aplicado com as porcentagens de altura e largura.

**Recomendação**

Se você puder, eu altamente recomendo colocar a imagem em desenvolvimento em um monitor externo. Isso pode ser feito se você hospedar a imagem localmente ou tiver uma [conta pro no Codepen](https://codepen.io/pro), onde é possível modificar a visualização atual para "Live view" e ver sua pen em largura completa com atualizações instantâneas. Caso você não possa, terá que fazer funcionar.

**Head/Cabeça**

Vamos observar o código para a div da cabeça e então quebrá-lo pedaço por pedaço.

```html
.head{
  position: absolute;
  top: 16.5%;
  left: 25%;
  width: 50%;
  height: 67%;
  background: #A6BECF;
  border-radius: 50%;
}
```

As porcentagens para o topo (top) e esquerda (left) significam que a div estará 15% distante do topo da caixa e 25% distante da esquerda da caixa.

A largura da div é de 50% e a altura de 67%. Mais uma vez, isso significa que a largura é 50% e a altura é 57% do tamanho da caixa.

Depois disso iremos definir a cor de fundo em um cinza claro.

Então, usaremos *border-radius: 50%*. Se você não utilizar o atributo *border-radius*, a div sempre ficaria na forma de um retângulo (ou quadrado). A *border-radius* é o que deixa a forma curva. Se você é familiar com Illustrator, adicionar um *border-radius* é como puxar o canto de um quadrado para arredondá-lo. Para transformá-lo em um círculo, sempre usamos a porcentagem de 50%.

*Border-radius* pode ser utilizado não só para fazer círculos, mas para arredondar qualquer forma, como um retângulo arredondado que faremos ao estilizar a div de nariz.

Agora, antes de prosseguirmos, você pode estar pensando onde no mundo que eu consigo essas porcentagens para o topo, esquerda, largura e altura. Vamos pensar sobre isso.

Definimos a caixa com a largura de 600px, então uma largura de 50% resulta em 300px. Considerando que a caixa tinha somente 400px de altura, a porcentagem de altura para a cabeça terá que ser maior.

Agora é a parte onde você talvez espere que eu te dê uma fórmula muito precisa para determinar como eu encontrei a altura, mas para ser honesto, eu normalmente chuto um valor com a boa e velha técnica de testar e errar.

Quanto mais você faz images em puro CSS, você melhor estima valores. Mas tudo que você realmente precisa pensar é saber a altura e largura da div pai e quando tamanho a atual div filha precisa ter em relação a div pai.

Agora, para as porcentagens de posições quando você quer **centralizar de forma absoluta** é mais fácil calcular. Aqui está a fórmula:

```html
left = (100 - width) / 2
top = (100 - height) / 2

//em nosso caso
(100 - 67)/2 = top: 16.5%;
(100-50)/2 = left: 25%;
```

Agora isso funciona para nossa div de cabeça pois queremos ela absolutamente no centro. Contudo, não queremos centralizar absolutamente as orelhas, por exemplo. Vamos falar sobre isso logo, o que também vai explicar quando utilizar os atributos inferior e direita em vez de topo e esquerda.

Uma última coisa para mencionar nessa seção é que toda div a seguir será aninhada embaixo da div cabeça pois cada forma que será adicionada ficará no topo da cabeça.

Aqui é o que devemos ter neste ponto: 

![](https://cdn-images-1.medium.com/max/800/1*-W0GNk73U_FGj-ebnPJ3xg.png)
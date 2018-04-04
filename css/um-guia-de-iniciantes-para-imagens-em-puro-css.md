[Artigo original: A Beginner’s Guide to Pure CSS Images](https://medium.com/coding-artist/a-beginners-guide-to-pure-css-images-ef9a5d069dd2)

---
# Um guia de iniciantes para imagens em puro CSS

Atualização (14/3/17) Temos também um curso 100% gratuito por email para aprender imagens em puro CSS. Você pode se [matricular aqui](https://coding-artist.teachable.com/p/how-to-make-pure-css-images)

Atualização (6/1/17) Disponibilizamos nosso desafio de 50 dias por email chamado Daily CSS Images, que te desafia a criar imagens em puro CSS todos os dias comerciais da semana. É uma ótima forma de continuar praticando. Você pode se [cadastrar aqui](http://dailycssimages.com/)

Atualização (3/1/17) Se você prefere escutar, [aqui está um vídeo](https://www.youtube.com/watch?v=ULhv96NdF_Q) para seguir o conteúdo no formato de áudio.

No que você está se envolvendo: uma leitura de 17 minutos. Uma explicação detalhada sobre como criar imagens em puro CSS. Vamos começar com uma geral e trabalhar para criar um Coala em puro CSS.

O que suponho que você sabe: Meu método de ensino é não supor que você já sabe os princípios básicos. A não ser que você seja um completo iniciante com HTML e CSS, eu não faço nenhuma suposição.

Se você não é iniciante: Eu vou repetir os princípios básicos frequentemente. Pule as partes que são muito fáceis para você e entenda que isso foi feito para ajudar pessoas com todos os níveis de conhecimentos.

## Introdução

Uma linha é frequentemente traçada entre um artista/designer que trabalha com vetores e um desenvolvedor front-end. Isso acontece pois muitas empresas possuem mão-de-obra e trabalhos suficientes para realizar essa separação de forma produtiva. Outro fator relevante é a vontade de algumas pessoas em focar somente no desenvolvimento front-end, enquanto outras querem ser extremamente específicas em ilustrações. Mesmo nas duas áreas, existem determinados nichos que podem ser escolhidos como foco para desenvolver um conjunto de habilidades muito valioso e bom.

Sem dúvida essa separação é sensata, porém, eu acho que um desenvolvedor front-end poderia se beneficiar imensamente trabalhando com ilustrações, mesmo se esse não for seu foco principal. 

Eu acredito que esse é o caso, pois as duas habilidades são essenciais para criar diferentes componentes de um produto final. Ilustradores que trabalham com vetores criam diferentes formas geométricas, e manipulações dessas, para criar uma ilustração final. Desenvolvedores front-end criam componentes com código para formar uma página web.

Aprender como fazer vetores gráficos ensina sobre layouts, paleta de cores, manipulações de formas geométricas, e criatividade em geral, fator relevante na área de desenvolvimento front-end.

Provavelmente eu deveria continuar essa discussão sobre os benefícios da ilustração com vetores para desenvolvedores front-end. Comentei sobre esse tópico pois imagens em puro CSS são exemplos de quando a intersecção entre ilustradores de vetores e desenvolvedores front-end é muito próxima.

Criar uma imagem em puro CSS é essencialmente criar um vetor gráfico, mas ao invés de utilizar softwares de ilustração com vetor (ex: Illustrador, Affinity Designer, Sketch) são utilizados códigos CSS no lugar da barra de ferramentas.

Apesar da próxima intersecção, acredito que ilustradores de imagens vetoriais podem ver toneladas de código CSS para criar uma imagem como algo intimidador, e os desenvolvedores front-end também podem considerar criar imagens com código algo tão assustador quanto.

Por essa razão, vou criar um tutorial de como criar sua primeira imagem em puro CSS, e espero que esse tutorial cumpra pelo menos alguns dos tópicos abaixo:

1. Aumentar a confiança para criar imagens em puro CSS
2. Fornecer melhor entendimento sobre como imagens em puro CSS funcionam
3. Ampliar a curiosidade sobre ilustração com vetores para desenvolvedores front-end
4. Ampliar a curiosidade sobre desenvolvimento front-end para ilustradores de imagens vetoriais
5. Fornecer um template básico para criar mais imagens em puro CSS

## Os componentes de uma imagem em puro CSS
Primeiro vamos explicar o que exatamente "puro CSS" significa?

O termo "puro CSS" se refere a criação de uma imagem simplesmente adicionando estilos a várias divs em HTML via CSS.

Por exemplo, podemos criar um quadrado com somente uma `div` HTML e estilizá-la aplicando uma classe CSS.

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

**Nota:** Se você prefere vídeo pode acessar um vídeo tutorial com esse conteúdo em nosso [curso gratuito em vídeo de imagens em puro CSS](https://coding-artist.teachable.com/p/how-to-make-pure-css-images).

**Composição de formas**
Primeiro, a imagem completa do Coala será construída em cima do canvas quadrado invisível (não é a terminologia oficial). Essa caixa invisível será centralizada com o corpo do HTML e a cabeça será centralizada com a caixa. Eu pessoalmente acho essa abordagem uma boa prática, pois ela simplifica o design responsivo, o que vou descrever no final desse post.

Agora mantenha em mente que existirá uma caixa retangular invisível, a qual eu defino abaixo: 

![](https://cdn-images-1.medium.com/max/800/1*MYy6c239bE6lHyMr1jKQBQ.png)

Segundo, temos um círculo no centro da página web que irá criar a cabeça.

![](https://cdn-images-1.medium.com/max/800/1*lnsXWnA0vpb08LifeeeSYw.png)

A seguir, orelhas ficarão em cada lado da cabeça. Cada orelha é composta por dois diferentes círculos coloridos sobrepostos, com um círculo levemente menor que o outro. Nós vamos distinguir entre a `div` de orelha e a div da parte interna da orelha.

![](https://cdn-images-1.medium.com/max/800/1*wNGTBnkVJdDa3B-iCJM7Tg.png)

Adicionalmente, teremos dois olhos que também são dois círculos sobrepostos entre si. Vamos distinguir entre olho, círculo branco maior, pupila, e círculo preto menor.

![](https://cdn-images-1.medium.com/max/800/1*uAVtlWSWEBhL3pn8LaPm2Q.png)

A seguir, criaremos o nariz, que será um retângulo marrom arredondado logo abaixo dos olhos.

![](https://cdn-images-1.medium.com/max/800/1*yscTJSYtWzIRa5Qw5kSY0Q.png)

Por último, teremos dois pedaços de cabelo cinza que serão dois triângulos em locais diferentes no topo da cabeça.

![](https://cdn-images-1.medium.com/max/800/1*ybfg2A_os8zi1Bu-posqDA.png)

Outra coisa que é importante mencionar é a presença de diferentes camadas nesta imagem. As orelhas ficarão atrás da cabeça, o nariz será na frente dos olhos, etc. Isso será explicado conforme estilizamos o CSS.

**O HTML**

**Nota:** Para adicionar o cabelo à nossa imagem do coala, vamos usar o método *clip-path*. Esse método é suportado pelo Chrome, Safari e Opera. Se você está usando o Firefox, mude para um dos navegadores suportados, preferencialmente Chrome, para programar durante este guia.

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

**Body/Corpo**

Para começar a estilização, vamos dar uma cor de fundo, um azul estilo Twitter, para a tag body.

```html
body{
  background: #25A9FC;
}
```

**Box/Caixa**

A seguir, vamos estilizar a caixa invisível. A caixa invisível será centralizada horizontalmente pois o código a seguir é o que permite que ela seja centralizada horizontalmente (nota: se você está seguindo para ver como a posição da caixa muda é possível alterar a cor de fundo da caixa ou adicionar uma borda sólida):

```css
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

A posição relativa (`position: relative`) significa que o elemento está posicionado de forma relativa a sua posição normal, o que seria o extremo topo do canto esquerdo, pois essa é a primeira `div` na tag `body`.

![](https://cdn-images-1.medium.com/max/800/1*qQlKbG2wHVzUP1NXNfv9_A.png)

Quando a posição está definida como relativa, utilizando `display: block;` e `margin: auto;` o centro da caixa será automaticamente centralizado horizontalmente.

Agora podemos adicionar o seguinte código para fazer a caixa ser 8% mais baixa, definir a altura (height) e largura (width) com as dimensões mostradas na imagem abaixo, e por último atribuir um fundo.

```css
.box {
  position: relative;
  margin: auto;
  display: block;
  margin-top: 8%;
  width: 600px;
  height: 420px;
  background: none;
}
```

Uma coisa para lembrar é que usamos `margin-top: 8%` para abaixar a caixa em 8%. Como especificamente ajustamos a margem do topo (`margin-top`), isso não irá afetar o atributo `margin: auto` que utilizamos para centralizar a caixa. Se tivessemos utilizado `margin: 8%` o atributo `margin: auto` seria sobrescrito.

Agora que nossa caixa está definida, todas as outras divs precisam ser aninhadas com a caixa. Isso é importante, pois iremos atribuir posições absolutas (topo, direita, esquerda, ou inferior) em porcentagem que irão posicionar a `div` na mesma porcentagem em relação a caixa e não do corpo (`body`). O mesmo conceito será aplicado com as porcentagens de altura e largura.

**Recomendação**

Se você puder, eu altamente recomendo colocar a imagem em desenvolvimento em um monitor externo. Isso pode ser feito se você hospedar a imagem localmente ou tiver uma [conta *pro* no Codepen](https://codepen.io/pro), onde é possível modificar a visualização atual para "Live view" e ver sua pen em largura completa com atualizações instantâneas. Caso você não possa, terá que fazer funcionar.

**Head/Cabeça**

Vamos observar o código para a `div` da cabeça e então quebrá-lo pedaço por pedaço.

```css
.head {
  position: absolute;
  top: 16.5%;
  left: 25%;
  width: 50%;
  height: 67%;
  background: #A6BECF;
  border-radius: 50%;
}
```

As porcentagens para o topo (top) e esquerda (left) significam que a `div` estará 15% distante do topo da caixa e 25% distante da esquerda da caixa.

A largura da `div` é de 50% e a altura de 67%. Mais uma vez, isso significa que a largura é 50% e a altura é 57% do tamanho da caixa.

Depois disso iremos definir a cor de fundo em um cinza claro.

Então, usaremos `border-radius: 50%`. Se você não utilizar o atributo `border-radius`, a `div` sempre ficaria na forma de um retângulo (ou quadrado). A `border-radius` é o que deixa a forma curva. Se você é familiar com Illustrator, adicionar um `border-radius` é como puxar o canto de um quadrado para arredondá-lo. Para transformá-lo em um círculo, sempre usamos a porcentagem de 50%.

`Border-radius` pode ser utilizado não só para fazer círculos, mas para arredondar qualquer forma, como um retângulo arredondado que faremos ao estilizar a `div` de nariz.

Agora, antes de prosseguirmos, você pode estar pensando onde no mundo que eu consigo essas porcentagens para o topo, esquerda, largura e altura. Vamos pensar sobre isso.

Definimos a caixa com a largura de 600px, então uma largura de 50% resulta em 300px. Considerando que a caixa tinha somente 400px de altura, a porcentagem de altura para a cabeça terá que ser maior.

Agora é a parte onde você talvez espere que eu te dê uma fórmula muito precisa para determinar como eu encontrei a altura, mas para ser honesto, eu normalmente chuto um valor com a boa e velha técnica de testar e errar.

Quanto mais você faz imagens em puro CSS, você melhor estima valores. Mas tudo que você realmente precisa pensar é saber a altura e largura da `div` pai e quando tamanho a atual `div` filha precisa ter em relação a `div` pai.

Agora, para as porcentagens de posições quando você quer **centralizar de forma absoluta** é mais fácil calcular. Aqui está a fórmula:

```css
left = (100 - width) / 2
top = (100 - height) / 2

//em nosso caso
(100 - 67)/2 = top: 16.5%;
(100-50)/2 = left: 25%;
```

Agora isso funciona para nossa `div` de cabeça pois queremos ela absolutamente no centro. Contudo, não queremos centralizar absolutamente as orelhas, por exemplo. Vamos falar sobre isso logo, o que também vai explicar quando utilizar os atributos inferior e direita em vez de topo e esquerda.

Uma última coisa para mencionar nessa seção é que toda `div` a seguir será aninhada embaixo da `div` cabeça pois cada forma que será adicionada ficará no topo da cabeça.

Aqui é o que devemos ter neste ponto: 

![](https://cdn-images-1.medium.com/max/800/1*-W0GNk73U_FGj-ebnPJ3xg.png)

**Pausa no aprendizado**

Eu sei que isso é bastante conteúdo de uma vez só, mas vamos continuar e ver como as coisas vão se encaixando. Se você precisar de uma pausa, sinta-se a vontade para adicionar aos favoritos esse post ou utilizar Pocket para salvar para depois.

**Cópia da cabeça/head**

```css
.head-copy {
  width: 100%;
  height: 100%;
  position: absolute;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 2;
}
```

A `div` de cópia da cabeça (`head-copy`) é somente para o propósito de permitir que as orelhas apareçam atrás da cabeça. Isso é controlado utilizando o `z-index`.

A última linha de nosso estilo é o seguinte:

```css
z-index: 2;
```

`Z-index` é utilizado para indicar a profundidade de uma `div`. Se você costuma ilustrar isso fará muito mais sentido se você pensar na forma de camadas funcionam.

Nossa imagem final terá os olhos na frente da `div` da cabeça, o nariz na frente dos olhos, etc. Isso será controlado pelo `z-index`. Quanto maior for o `z-index`, mais próxima do topo está a `div`.

Então, no caso de duas divs, `z-index: 1;` seria como sua camada inferior e `z-index: 2;` seria sua camada superior.

Como nossa camada inferior será as orelhas, vamos estabelecer o `z-index: 1;`. Se tivéssemos omitido a `div` cópia da cabeça, e dado a `div` da cabeça (head) o valor de `z-index: 2;` as orelhas não estariam atrás da cabeça. Contudo, quando adicionamos a cópia da cabeça e definimos o valor `z-index: 2`, as orelhas ficarão atrás da cabeça.

Eu não trabalharia muito se isso for confuso, mas se você quiser pode remover a `div` cópia da cabeça quando adicionarmos as orelhas para ver por conta própria.

Nesse caso não deveriámos ver nenhuma mudança, e ainda teriámos a seguinte imagem:

![](https://cdn-images-1.medium.com/max/800/1*-W0GNk73U_FGj-ebnPJ3xg.png)

**Orelhas**

Conforme discutido no início, quando dividimos nossas formas, uma orelha para cada lado que consistirá em círculos no topo. Dois maiores, círculos cinza claros (`ear-left` e `ear-right`) e dois menores, círculos cinza escuros no topo de cada orelha, respectivamente (`inner-ear`).


```css
.ear-left {
  position: absolute;
  width: 60%;
  height: 65%;
  left: -20%;
  top: 5%;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 1;
}

.ear-right {
  position: absolute;
  width: 60%;
  height: 65%;
  right: -20%;
  top: 5%;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 1;
}
.inner-ear {
  position: absolute;
  border-radius: 50%;
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
  background: #819CAF;
}
```

Para cada classe CSS, usamos `border-radius: 50%` pois são todos círculos, e depois adicionamos uma cor utilizando `background`.

Como você pode ver, há estilização para duas orelhas separadas, mas somente uma para orelha interna. Isso fará sentido enquanto explicamos o posicionamento.

A `div` pai de `ear-left` e `ear-right` é a `div` cabeça/head. Portanto, deve ser posicionada com porcentagens relativas a cabeça, assim como sua altura e largura.

A altura e largura podem ser estimadas pois queremos orelhas grandes, mas ainda assim menores do que a cabeça. Isso nos dá a largura de `width: 60%;` e a altura de `height: 65%;`.

A orelha interna está aninhada abaixo da orelha esquerda (`ear-left`) e da orelha direita (`ear-right`). Nós sabemos que queremos que elas sejam levemente menores, por isso, definimos uma altura e largura de 80%. Também sabemos que queremos a orelha interna (`inner-ear`) centralizada perfeitamente **relacionada as orelhas**, então podemos usar a fórmula mais uma vez.

```css
left = (100 - width) / 2
top = (100 - height) / 2

//em nosso caso
(100 - 80)/2 = top: 10%;
(100-80)/2 = left: 10%;
```

Como nosso topo e esquerda são relativos as orelhas, podemos usar o mesmo estilo tanto para orelha esquerda (`ear-left`) quando para a direita (`ear-right`). Essa é a razão para existir somente uma div da orelha interna (`inner-ear`). Nós temos que usar duas divs separadas para as orelhas pois elas terão valores diferentes em suas posições de esquerda e direita pois são posicionadas **relativas a cabeça**.

Queremos que as duas orelhas se destaquem saindo dos lados esquerdo e direito da cabeça, de acordo com seus nomes. Portanto, usamos porcentagens negativas, `left: -20%` e `right: -20%`. O que significa que cada orelha irá se mover 20% da largura da cabeça na direção especificada.

Isso é provavelmente óbvio, mas eu nunca gosto de assumir isso. Toda vez que existirem divs de esquerda e direita como estas, você pode posicionar um lado, como `left: -20%;`. Depois copiar e colocar o estilo para aquela `div`, renomear a classe para o outro lado, e então mudar somente o atributo `left` para `right` ou vice-versa.

Aqui estão as posições e tamanhos para as orelhas, agora que tudo já foi explicado e feito:

```css
//orelha esquerda
  width: 60%;
  height: 65%;
  left: -20%;
  top: 5%;

//orelha direita
  width: 60%;
  height: 65%;
  right: -20%;
  top: 5%;
```

Por último, adicionamos `z-index: 1;`, para as orelhas ficarem atrás da cabeça. Devemos ter agora:

![](https://cdn-images-1.medium.com/max/800/1*UsQlYpazeGUm8ursUQ2Ciw.png)

**Olhos**

```css
.eye-left {
  position: absolute;
  background: white;
  width: 30%;
  height: 33%;
  top: 25%;
  left: 21%;
  border-radius: 50%;
  z-index: 3;
}

.eye-right {
  position: absolute;
  background: white;
  width: 30%;
  height: 33%;
  top: 25%;
  right: 21%;
  border-radius: 50%;
  z-index: 2;
}

.pupil {
  position: absolute;
  width: 28%;
  height: 30%;
  top: 35%;
  left: 36%;
  border-radius: 50%;
  background: #27354A;
}
```

Agora podemos ver que os olhos são similares as orelhas. Temos dois grandes círculos brancos (`eye-left` e `eye-right`) e uma pupila (`pupil`).

Para todos eles usamos `border-radius: 50%;`, pois são círculos e usamos background para definir as cores apropriadas.

Temos somente uma pupila pois está aninhada abaixo de cada olho. Nós estimamos/chutamos a altura e largura da pupila e depois centralizamos perfeitamente, o que fica definido como:

```css
width: 28%;
height: 30%;
top: 35%;
left: 36%;
```

Para o olho esquerdo (`eye-left`) você pode tanto usar tentativa e erro para as posições do topo e esquerda, como também pode usar a fórmula para centralizar perfeitamente e ajustar os valores dependendo das distâncias a partir do centro. Enquanto isso, a largura e altura foram estimadas até encontrar um valor correto.

```css
//olho esquerdo  
width: 30%;
height: 33%;
top: 25%;
left: 21%;

//olho direito
width: 30%;
height: 33%;
top: 25%;
right: 21%;
```
Para o `z-index`, os seguintes valores permitem que o nariz esteja no topo dos olhos:

```css
//olho esquerdo 
z-index: 3;

//olho direito
 z-index: 2;
```

Agora devemos ter a seguinte imagem:

![](https://cdn-images-1.medium.com/max/800/1*40C5Cbg-MoLiUwZbROPSlg.png)

**Nariz**

```css
.nose{
  position: absolute;
  background: #BE845F;
  width: 25%;
  height: 42.5%;
  left: 37%;
  top: 45%;
  border-radius: 50px;
  z-index: 4;
}
```

Agora para o nariz, estimamos/chutamos a altura e largura relativa a cabeça. Uma vez que isso é conhecido, podemos estimar ou alinhar perfeitamente e ajustar de acordo. Os valores a seguir fornecem um bom tamanho e localização:

```css
width: 25%;
height: 42.5%;
left: 37%;
top: 45%;
```

Novamente estilizamos a cor marrom usando o atributo `background` e especificamos a profundidade usando `z-index: 4;`, dessa forma o nariz fica na frente dos olhos.

Também utilizamos `border-radius: 50px;`, o que irá arredondar as bordas do retângulo conforme necessário. Quando queremos arredondar levemente é mais fácil arredondar usando um número em px do que uma porcentagem.

Agora devemos ver a seguinte imagem:

![](https://cdn-images-1.medium.com/max/800/1*cgWumddIezW-p1sFkLPq_A.png)


**Cabelo**

Quase pronto! O último passo é adicionar estilo aos dois pedaços de cabelo, `hair-left` e `hair-right`, o que nos fornecerá uma imagem completa do Coala.

```css
.hair-left {
  position: absolute;
  top: -8%;
  left: 30%;
  width: 20%;
  height: 20%;
  background:  #A6BECF;
  -webkit-clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.hair-right {
  position: absolute;
  top: -4%;
  left: 48%;
  width: 20%;
  height: 20%;
  background:  #A6BECF;
  -webkit-clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}
```

Como você pode ver, não há `border-radius`, mas temos que adicionar essa linha de `clip-path`:

```css
-webkit-clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
```

Para qualquer forma que não é um quadrado, retângulo e círculo, é mais fácil usar um `clip-path`.

**Nota:** Esse método é suportado pelo Safari, Chrome e Opera, mas não pelo Firefox. Enquanto isso pode ser desanimador será o método mais fácil para aprender como criar formas usando somente CSS.

Agora, isso pode parecer confuso, mas felizmente, tem uma ótima ferramente que vai automaticamente nos fornecer o `clip-path` para formas diferentes.

Abra essa ferramenta chamada [Clippy](http://bennettfeely.com/clippy/) em uma nova aba.

Você vai ver do lado direito que é possível selecionar várias formas diferentes:

![](https://cdn-images-1.medium.com/max/800/1*vG4Omfuea52pj0nrI3Zlzg.png)

Na imagem acima, a forma de triângulo é selecionada e você pode copiar e colar o `clip-path` na parte inferior e colar na classe CSS referente ao cabelo.

Mais uma vez vamos colocar a cor usando `background` e estimar a altura e largura com 20% para cada. Definimos que a parte esquerda do cabelo (`hair-left`) terá um valor para esquerda de 30%, e a parte direita um valor de 48% para a esquerda. Isso nos traz um bom exemplo pra discutir se usamos o atributo `left` ou o `right`. Vamos dizer que queremos a `div` `hair-right` 5% a mais para a direita, poderiámos adicionar 5% aos 48% e ficar com `left: 53%`. Contudo, uma boa regra é toda vez que passar de 50% é melhor trocar para o atributo `right`. Então, `left: 53%` seria o equivalente a `right: 48%`. Para esse exemplo, vamos manter em `left: 48%` e continuar.

As posições do topo serão negativas, pois queremos os dois pedaços de cabelo se destacando acima da cabeça. A `div` `hair-left` se destacará um pouco mais então definimos `top: -8%;` e a `hair-right` um pouco mais baixa, com `top: 4%;`

Nosso Coala agora é uma imagem completa.

![](https://cdn-images-1.medium.com/max/800/1*zaYeChAMif3__eVsrIWciw.png)

**CSS Final**

```css
body {
  background: #25A9FC;
}

.box {
  position: relative;
  margin: auto;
  display: block;
  margin-top: 8%;
  width: 600px;
  height: 420px;
  background: none;
}

.head {
  position: absolute;
  top:16.5%;
  left: 25%;
  width: 50%;
  height: 67%;
  background: #A6BECF;
  border-radius: 50%;
}

.head-copy {
  width: 100%;
  height: 100%;
  position: absolute;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 2;
}

.ear-left {
  position: absolute;
  width: 60%;
  height: 65%;
  left: -20%;
  top: 5%;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 1;
}

.ear-right {
  position: absolute;
  width: 60%;
  height: 65%;
  right: -20%;
  top: 5%;
  background: #A6BECF;
  border-radius: 50%;
  z-index: 1;
}

.inner-ear {
  position: absolute;
  border-radius: 50%;
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
  background: #819CAF;
}

.eye-left {
  position: absolute;
  background: white;
  width: 30%;
  height: 33%;
  top: 25%;
  left: 21%;
  border-radius: 50%;
  z-index: 3;
}

.eye-right {
  position: absolute;
  background: white;
  width: 30%;
  height: 33%;
  top: 25%;
  right: 21%;
  border-radius: 50%;
  z-index: 3;
}

.pupil {
  position: absolute;
  width: 28%;
  height: 30%;
  top: 35%;
  left: 36%;
  border-radius: 50%;
  background: #27354A;
}

.nose {
  position: absolute;
  background: #BE845F;
  width: 25%;
  height: 42.5%;
  left: 37%;
  top: 45%;
  border-radius: 50px;
  z-index: 4;
}

.hair-left {
  position: absolute;
  top: -8%;
  left: 30%;
  width: 20%;
  height: 20%;
  background:  #A6BECF;
  -webkit-clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.hair-right {
  position: absolute;
  top: -4%;
  left: 48%;
  width: 20%;
  height: 20%;
  background:  #A6BECF;
  -webkit-clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}
```

**Continuando a prática**

Espero que esse post te forneça um bom conceito de como imagens em puro CSS funcionam e tenha te inspirado a aprender mais. Adicionalmente, você deve ter um bom template para mexer e adquirir mais prática.

Aqui estão algumas fontes 100% gratuitas que criei para uma prática estruturada:

1. ***[Pure CSS Images Video Course](https://coding-artist.teachable.com/p/how-to-make-pure-css-images):*** In this video course, I go over everything you need to know about pure CSS images.

2. ***[Daily CSS Images Challenge](http://challenges.codingartist.io/daily-css-images/):*** 50-day email challenge where you will receive a prompt to make a CSS image every weekday. Each week will have a fun theme, making this an engaging challenge.

Até mais,

Mike Mangialardi
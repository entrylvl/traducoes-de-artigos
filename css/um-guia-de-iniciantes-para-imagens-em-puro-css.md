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

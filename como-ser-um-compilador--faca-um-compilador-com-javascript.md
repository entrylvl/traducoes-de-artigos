![](http://i.imgur.com/ur3ls5B.png)

![](http://i.imgur.com/Od8BBR6.png)

![](http://i.imgur.com/vqrhG77.png)

![](http://i.imgur.com/gMKP9rL.png)

## Aprendizados ao fazer um compilador

Fazer um compilador foi divertido, mas acima de tudo, me ensinou muito sobre desenvolvimento de software. Aqui estão algumas coisas que eu aprendi enquanto fazia meu compilador.

### 1. Você não precisa conhecer tudo
Assim como o nosso analisador léxico, você não precisa saber tudo desde o início. Se você realmente não entender uma parte do código ou tecnologia, não hesite em dizer "Tem isso, e eu sei um pouco dela" e passar para o próximo passo. Não se estresse com isso, você ir'á entender eventualmente.

### 2. Não seja um babaca com mensagens de erro
O papel do analisado é seguir a regra e checar se as coisas foram escritas segundo ela. Muitas vezes erros acontecem. Então, tente enviar mensagens úteis e acolhedoras. É fácil falar "Isso não funciona desse jeito” (como "Token ILEGAL" ou "undefined não é uma função" erro no JavaScript) mas ao invés tento falar aos seus usuários o que deveria acontecer, o melhor que você conseguir.

Isso também se aplica a comunicação da equipe. Quando alguém está travado em uma questão, ao invés de dizer "isso não funciona", talvez você possa começar dizendo "Eu tentaria jogar no google palavras chaves como ___ and ___ ." ou “Eu recomendaria ler essa página na documentação.” Você não precisa fazer o trabalho por eles, mas você com certeza pode ajudar eles a fazer um trabalho melhor e mais rápido, apenas fornecendo um pouco mais de ajuda. Elm é uma linguagem de programação que [abraça esse método](http://http://elm-lang.org/blog/compiler-errors-for-humans). Ela usa "Talvez você quisesse tentar isso?" na mensagem de erro.
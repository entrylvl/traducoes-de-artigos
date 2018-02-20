[Artigo original: Handling an AJAX response in JavaScript (with or without jQuery)](https://www.mattlunn.me.uk/blog/2011/11/handling-an-ajax-response-in-javascript-with-or-without-jquery/)

---

# Tratando uma resposta AJAX em Javascript (com ou sem jQuery)

## O problema e a solução

Umas das coisas mais perguntadas no [StackOverflow](http://www.stackoverflow.com/) tende a envolver chamadas AJAX e a incapacidade de usar a resposta imediatamente, como a seguir:

```
var response = '';
var xhr = new XMLHttpRequest(); // O tratamento de múltiplos browsers foi omitido por brevidade

xhr.onreadystatechange = function () {
  response = this.responseText;
}
xhr.open('GET', '/ajax.php', true);
xhr.send(null);

// Tente usar o 'response' ou 'xhr.responseText' aqui (nota: não vai funcionar!)
```

Ou igualmente em jQuery

```
var response = '';
var xhr = jQuery.ajax('/ajax.php', function (result) {
  response = result;
});

// Tente usar response aqui (nota: não vai funcionar!)
```

Este tipo de pergunta é tão comum no StackOverflow que é destaque na [descrição da tag JavaScript](http://stackoverflow.com/tags/javascript/info). A resposta para cada uma dessas perguntas recomenda ao autor usar um *callback* para tratar a resposta. Vamos olhar em instantes *o motivo* de um *callback* ser necessário. Mas para aqueles que estiverem com pressa, eu vou primeiro mostrar a solução:

```
var xhr = new XMLHttpRequest(); //O tratamento de múltiplos browsers foi omitido por brevidade
// não há necessidade de declarar o "response" aqui

xhr.onreadystatechange = function () {
  if (this.readyState == 4 && this.status == 200) {
    var response = this.responseText;

    // usar o response aqui
  }
}

xhr.open('GET', '/ajax.php', true);
xhr.send(null);
```

E o equivalente em jQuery:

```
jQuery.get('/ajax.php', function (response) {
  // use o "response" aqui. o jQuery passa a resposta como o primeiro parâmetro da função
});
```

## A explicação

Um *callback* é necessário porque um AJAX, como o nome `Javascript e XML Assíncrono` sugere, é assíncrono. Quando você inicia uma chamada AJAX usando o método `XMLHttpRequest` nativo ou por jQuery, a requisição HTTP é enviada, mas o motor do JavaScript não *espera* por uma resposta. Ao invés disso, o fluxo de execução continua. Para conseguirmos monitorar o progresso da requisição, nos é permitido passar uma função de *callback* que será executada quando o estado da requisição HTTP muda. O *callback* pode ser enviado para o objeto [XMLHttpRequest](http://www.w3.org/TR/XMLHttpRequest/#toc) nativo através do atributo `onreadystatechange`:

```
var xhr = new XMLHttpRequest();

xhr.onreadystatechange = function () {
  // O código escrito aqui será executada toda vez em que haja progresso na chamada HTTP.
  // O estado atual pode ser consultado através do `this.readyState`, que retorna um valor entre 0 e 4 (inclusive).

  if (this.readyState == 4) { // Se a chamada HTTP completou
    if (this.status == 200) { // Se o código da chamada HTTP é 200 (isto é, sucesso)
      var response = this.responseText; // Busca a resposta da chamada
    };
  };
};

xhr.open('GET', '/ajax.php', 'true');
xhr.send(null);
```

Ao usar jQuery, os *callbacks* são especificados de maneira diferente dependendo de qual método [AJAX](http://api.jquery.com/category/ajax) você quer usar; métodos como [jQuery.get](http://api.jquery.com/jQuery.get), [jQuery.post](http://api.jquery.com/jQuery.post), [jQuery.getJSON](http://api.jquery.com/jQuery.getJSON) aceitam apenas um "callback" de sucesso, passado à função como parâmetro. [jQuery.ajax](http://api.jquery.com/jQuery.ajax) por sua vez, permite que [múltiplos "callbacks" separados](http://api.jquery.com/jQuery.ajax/#jQuery-ajax-settings) sejam especificados como pares `chave:valor` no objeto passado como último parâmetro.

```
jQuery.get('/ajax.php', function (response) {
    // Trate o caso de sucesso aqui
});

jQuery.ajax('/ajax.php', {
    beforeSend: function () { /* Requisição AJAX está para ser enviada */ },
    complete: function () { /* Requisição AJAX completou */},
    success: function () { /* Requisição AJAX completou com sucesso */},      
    error: function () { /* Requisição AJAX completou com erro */}
})
```

A introdução de *callbacks* faz o fluxo de execução ficar parecido com isso:

```
var xhr = new XMLHttpRequest(); // O tratamento de múltiplos browsers foi omitido por brevidade

// Ponto 1

xhr.onreadystatechange = function () {
  // Ponto 4

  if (this.readyState == 4) {
    // Ponto 5

    if (this.status == 200) {
      var response = this.responseText;

      // Ponto 6
    }
  }
}

// Ponto 2

xhr.open('GET', '/ajax.php', true);
xhr.send(null);

// Ponto 3
```

Os pontos 1, 2 e 3 serão executados uma única vez em ordem crescente, imediatamente. A execução do ponto 4 ocorrerá *depois de um tempo*, quando o estado da requisição HTTP progredir. O ponto 4 será executado múltiplas vezes até que a requisição HTTP alcance o estado final (`readyState == 4`), quando o fluxo de execução chega ao ponto 5. O ponto 6 será executado se a requisição HTTP completar-se com sucesso. O mesmo fluxo de execução pode ser visto no código jQuery seguinte:
```
// Ponto 1

jQuery.get('/ajax.php', function (result) {
    // Ponto 6
});

// Ponto 3
```

É uma prática comum mostrar algum indicador de progresso no ponto 3. Geralmente alguma coisa simples como um [spinner](http://ajaxload.info/), para indicar que há uma chamada HTTP assíncrona em progresso. Seria ideal mostrar atualizações de progresso no ponto 4, porém os valores observados no `readyState` [não são úteis o suficiente para isso](http://stackoverflow.com/questions/632774/what-do-the-different-readystates-in-xmlhttprequest-mean-and-how-can-i-use-them). No ponto 5, a chamada HTTP terminou, então o "spinner" pode ser removido, e uma mensagem de sucesso ou de erro pode ser mostrada, dependendo se o *status* é um [código de erro HTTP de sucesso ou erro](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

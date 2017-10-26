# Portal
 [Portal é um jogo](http://en.wikipedia.org/wiki/Portal_(video_game)) que consiste em uma série de quebra-cabeças que devem ser resolvidos ao se teletransportar o personagem do jogador e objetos simples de um lugar para outro.
Para se teletransportar, o jogador usa a arma de Portais para atirar portas em superfícies planas, como um piso ou uma parede. Entrar em uma dessas portas te teleporta para o outro lado:

![](imagens/1.jpeg)

Neste guia usaremos a [linguagem de programação Elixir](http://elixir-lang.org/getting-started/introduction.html) para construir portais disparando portas de diferentes cores e transferindo dados entre elas! Nós até aprenderemos como podemos distribuir portas em diferentes máquinas em nossa rede:

![](imagens/2.jpeg)

Aqui está o que aprenderemos:

* Shell interativo do Elixir
* Criando novos projetos Elixir
* Padrão de correspondência
* Usando agentes para estado
* Usando structs para estruturas de dados personalizadas
* Estendendo a linguagem com protocolos
* Árvores de supervisão e aplicações
* Nó de Elixir distribuído

Vamos começar!

## Instalation

Caique

## Our first project

Caique

# Pattern matching

Antes de implementarmos nosso aplicativo, precisamos falar sobre pattern matching. O operador = no Elixir é um pouco diferente do que vemos em outros idiomas:

```
iex> x = 1
1
iex> x
1
```

Até aqui tudo bem, o que acontece se invertermos os operadores?

```
iex> 1 = x
1
```

Funcionou! Isso porque Elixir tenta combinar o lado direito contra o lado esquerdo. Já que ambos são 1, ele funciona. Vamos tentar outra coisa:

```
iex> 2 = x
** (MatchError) no match of right hand side value: 1
```

Agora, os lados não combinaram, por isso recebemos um erro. Usamos Pattern Matching no Elixir para combinar estruturas de dados também. Por exemplo, podemos usar `[head|tail]` para extrair a cabeça (o primeiro elemento) e a cauda (os restantes) de uma lista:

```
iex> [head|tail] = [1, 2, 3]
[1, 2, 3]
iex> head
1
iex> tail
[2, 3]
```

Comparando uma lista vazia com `[head|tail]` causa um erro de comparação:

```
iex> [head|tail] = []
** (MatchError) no match of right hand side value: []
```

Finalmente, também podemos usar a expressão `[head|tail]` para adicionar elementos à cabeça de uma lista:

```
iex> list = [1, 2, 3]
[1, 2, 3]
iex> [0|list]
[0, 1, 2, 3]
```

## Modeling portal doors with Agents

Caique

## Portal transfers

Ricardo

## Inspecting portals with Protocols

Ricardo

## Shooting supervised doors

Caique

## Distributed transfers

Ricardo

## Wrapping up

Caique

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

# Transferência de Portais

Nossos portais estão prontos por isso é hora de começar a trabalhar em transferências de portal! Para armazenar os dados do portal, vamos criar uma struct chamada `Portal`. Vamos dar uma chance de tentar no IEx antes de avançar:

```
iex> defmodule User do
...>   defstruct [:name, :age]
...> end
iex> user = %User{name: "john doe", age: 27}
%User{name: "john doe", age: 27}
iex> user.name
"john doe"
iex> %User{age: age} = user
%User{name: "john doe", age: 27}
iex> age
27
```

Uma `struct` é definida dentro de um módulo e tem o mesmo nome que o módulo. Depois que a `struct` é definida, podemos usar a sintaxe `%User{...}` para definir novas estruturas ou combiná-las.

Vamos abrir `lib/portal.ex` e adicionar algum código ao módulo `Portal`. Observe que o módulo atual do Portal já possui uma função chamada `hello/0`. Você pode remover esta função e, em seguida, adicionar os novos conteúdos dentro do módulo `Portal`:

```
defstruct [:left, :right]

@doc """
Starts transfering `data` from `left` to `right`.
"""
def transfer(left, right, data) do
  # First add all data to the portal on the left
  for item <- data do
    Portal.Door.push(left, item)
  end

  # Returns a portal struct we will use next
  %Portal{left: left, right: right}
end

@doc """
Pushes data to the right in the given `portal`.
"""
def push_right(portal) do
  # See if we can pop data from left. If so, push the
  # popped data to the right. Otherwise, do nothing.
  case Portal.Door.pop(portal.left) do
    :error   -> :ok
    {:ok, h} -> Portal.Door.push(portal.right, h)
  end

  # Let's return the portal itself
  portal
end
```

Nós definimos nossa estrutura `Portal` e uma função `Portal.transfer/3` (o `/3` indica que a função espera três argumentos). Vamos dar essa tentativa de transferência. Inicie outro shell com `iex -S mix` para que nossas mudanças sejam compiladas e digite:

```
# Start doors
iex> Portal.Door.start_link(:orange)
{:ok, #PID<0.59.0>}
iex> Portal.Door.start_link(:blue)
{:ok, #PID<0.61.0>}

# Start transfer
iex> portal = Portal.transfer(:orange, :blue, [1, 2, 3])
%Portal{left: :orange, right: :blue}

# Check there is data on the orange/left door
iex> Portal.Door.get(:orange)
[3, 2, 1]

# Push right once
iex> Portal.push_right(portal)
%Portal{left: :orange, right: :blue}

# See changes
iex> Portal.Door.get(:orange)
[2, 1]
iex> Portal.Door.get(:blue)
[3]
```

Nossa transferência de portal parece funcionar como esperado. Observe que os dados estão na ordem inversa na porta esquerda/laranja no exemplo acima. Isso é esperado porque queremos o fim da lista (neste caso o número 3) para ser o primeiro dado inserida para a porta direita/azul.

Uma diferença no trecho acima, em comparação com a que vimos no início deste tutorial, é que nosso portal está sendo impresso como uma estrutura: `%Portal {left: :orange, right: :blue}`. Seria bom se tivéssemos uma representação impressa da transferência do portal, permitindo-nos ver o processo do portal à medida que empurra dados.

É o que faremos a seguir.

## Inspecting portals with Protocols

Ricardo

## Shooting supervised doors

Caique

## Distributed transfers

Ricardo

## Wrapping up

Caique

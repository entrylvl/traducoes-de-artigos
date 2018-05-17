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

## Instalação

O site do Elixir explica como instalar o Elixir. Apenas siga os [passos descritos na página de instalação do Elixir](http://elixir-lang.org/install.html).

Desenvolvedores Elixir passam muito tempo nos terminais do seu Sistema Operacional; uma vez que a instalação esteja completa, você terá novos executáveis disponíveis. Um deles é ```iex```. Apenas digite ```iex``` no seu terminal (ou ```iex.bat``` se você estiver no Windows) para fazer ele funcionar:

```
$ iex
Interactive Elixir - press Ctrl+C to exit (type h() ENTER for help)
```

``iex`` significa Elixir Interativo. No ```iex``` você pode digitar qualquer expressão e você terá o resultado de volta:

```
iex> 40 + 2
42
iex> "hello" <> " world"
"hello world"
iex> # This is a code comment
nil
```

Além dos números e strings acima, nós também usamos frequentemente os seguintes tipos de dados:

```
iex> :atom           # An identifier (known as Symbols in other languages)
:atom
iex> [1, 2, "three"] # Lists (typically hold a dynamic amount of items)
[1, 2, "three"]
iex> {:ok, "value"}  # Tuples (typically hold a fixed amount of items)
{:ok, "value"}
```

Uma vez que a nossa aplicação de portal esteja terminada, nós esperamos poder digitar o seguinte código dentro do ```iex```:

```
# Shoot two doors: one orange, another blue
iex(1)> Portal.shoot(:orange)
{:ok, #PID<0.72.0>}
iex(2)> Portal.shoot(:blue)
{:ok, #PID<0.74.0>}

# Start transferring the list [1, 2, 3, 4] from orange to blue
iex(3)> portal = Portal.transfer(:orange, :blue, [1, 2, 3, 4])
#Portal<
       :orange <=> :blue
  [1, 2, 3, 4] <=> []
>

# Now every time we call push_right, data goes to blue
iex(4)> Portal.push_right(portal)
#Portal<
    :orange <=> :blue
  [1, 2, 3] <=> [4]
>
```

Ele parece uma belezinha, né?

## Nosso primeiro projeto

Elixir possui uma ferramenta chamada Mix. Mix é o que os desenvolvedores Elixir usam para criar, compilar e testar novos projetos. Vamos criar um projeto chamado ```portal``` com ```mix```. Ao criar o projeto, nós também passaremos a opção ```--sup``` que vai criar uma árvore de supervisão. Nós vamos explorar o que a árvore de supervisão faz em sessões futuras. Por ora, apenas escreva:

```
$ mix new portal --sup
```

O comando acima criou um novo diretório chamado ```portal``` com alguns arquivos dentro dele. Mude o seu diretório de trabalho para o ```portal``` e rode ```mix test``` para rodar os testes do projeto:

```
$ cd portal
$ mix test
```

Excelente, nós já temos um projeto rodando com um ambiente de testes configurado.

Vamos explorar o projeto gerado usando um editor de texto. Eu pessoalmente não presto muita atenção em editores de texto, normalmente uso o [Sublime Text 3](http://www.sublimetext.com/3) mas você pode achar [suporte Elixir para diferentes editores de texto no site](http://elixir-lang.org/) na sessão "Code Editor Support".

Com o seu editor de aberto, explore os seguintes diretórios:

`_build` - onde Mix guarda os artefatos de compilação
`config` - onde configuramos nosso projeto e suas dependências
`lib` - onde colocamos nosso código
`mix.exs` - onde definimos nome, versão e dependências do nosso projeto
`test` - onde definimos nossos testes

Agora nós podemos começar uma sessão ```iex``` dentro do nosso projeto também. Apenas rode:

```
$ iex -S mix
```

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

## Modelando portais com agentes

As estruturas de data do Elixir são imutáveis. Nos exemplos acima, nós nunca mudamos a lista. Nós podemos quebrar uma lista à parte ou adicionar novos elementos na cabeça, mas a lista original nunca é modificada.

Dito isso, quando nós precisamos guardar algum tipo de estado, como os dados transferidos pelo portal, nós precisamos usar uma abstração que irá armazenar esse estado para nós. Uma dessas abstrações em Elixir é chamada de agente. Antes de usarmos agentes, nós precisamos conversar um pouco sobre funções anônimas:

```
iex> adder = fn a, b -> a + b end
#Function<12.90072148/2 in :erl_eval.expr/5>
iex> adder.(1, 2)
3
```
Uma função anônima é delimitada pelas palavras `fn` e `end` e uma seta `->` é usada para separar os argumentos do corpo da função anônima. Nós usamos funções anônimas para inicializar, pegar e armazenar o estado do agente:

```
iex> {:ok, agent} = Agent.start_link(fn -> [] end)
{:ok, #PID<0.61.0>}
iex> Agent.get(agent, fn list -> list end)
[]
iex> Agent.update(agent, fn list -> [0|list] end)
:ok
iex> Agent.get(agent, fn list -> list end)
[0]
```
Nota: vocẽ provavelmente terá valores `#PID<...>` diferentes dos que mostramos durante o tutorial. Não se preocupe, isso é esperado!

No exemplo acima, nós criamos um novo agente, passando uma função que retorna o estado inicial de uma lista vazia. O agente returnou `{:ok, #PID<0.61.0>}`.

Chaves em Elixir especifica uma tupla; a tupla abaixo contém o atom `:ok` e um identificador de processo (PID). Nós usamos atoms no Elxir como se fossem tags. No exemplo acima, nós estamos marcando o agente como iniciado com sucesso.

O `#PID<...>` é um identificador de processo para o agente. Quando dizemos processos no Elixir, não queremos dizer processos do Sistema Operacional, mas sim Processos Elixir, que são leves e isolados, permitindo que rodemos centenas de milhares deles na mesma máquina.

Nós usaremos agentes para implementar nossos portais. Crie um novo arquivo chamado `lib/portal/door.ex` com o seguinte conteúdo:

```
defmodule Portal.Door do
  @doc """
  Starts a door with the given `color`.

  The color is given as a name so we can identify
  the door by color name instead of using a PID.
  """
  def start_link(color) do
    Agent.start_link(fn -> [] end, name: color)
  end

  @doc """
  Get the data currently in the `door`.
  """
  def get(door) do
    Agent.get(door, fn list -> list end)
  end

  @doc """
  Pushes `value` into the door.
  """
  def push(door, value) do
    Agent.update(door, fn list -> [value|list] end)
  end

  @doc """
  Pops a value from the `door`.

  Returns `{:ok, value}` if there is a value
  or `:error` if the hole is currently empty.
  """
  def pop(door) do
    Agent.get_and_update(door, fn
      []    -> {:error, []}
      [h|t] -> {{:ok, h}, t}
    end)
  end
end
```

Em Elixir nós definimos códigos dentro de módulos, que são basicamente um grupo de funções. Nós temos definidas quatro funções acima, todas devidamente documentadas.

Vamos dar uma chance a nossa implementação. Inicie um novo shell com `iex -S mix`.Quando o shell iniciar, nosso novo arquivo será automaticamente compilado, então podemos usá-lo diretamente:

```
iex> Portal.Door.start_link(:pink)
{:ok, #PID<0.68.0>}
iex> Portal.Door.get(:pink)
[]
iex> Portal.Door.push(:pink, 1)
:ok
iex> Portal.Door.get(:pink)
[1]
iex> Portal.Door.pop(:pink)
{:ok, 1}
iex> Portal.Door.get(:pink)
[]
iex> Portal.Door.pop(:pink)
:error
```

Excelente!

Um dos aspectos interessantes do Elixir é que essa documentação é tratada como um cidadão de primeira-classe. Uma vez que tenhamos documentado nosso código `Portal.Door`, agora podemos acessar facilmente sua documentação pelo terminal. Tente digitar:

```
iex> h Portal.Door.start_link
```

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

# Inspecionando portais com Protocolos

Nós já sabemos que os dados podem ser mostrados em `iex`. Afinal, quando escrevemos `1 + 2` em iex, recebemos `3` de volta. No entanto, podemos personalizar a forma como nossos próprios tipos são impressos?

Sim, nós podemos! Elixir fornece protocolos, o que permite que o comportamento seja estendido e implementado para qualquer tipo de dados, como nosso struct `Portal`, a qualquer momento.

Por exemplo, sempre que algo é impresso em nosso terminal `iex`, Elixir usa o protocolo `Inspect`. Uma vez que os protocolos podem ser estendidos a qualquer momento, por qualquer tipo de dados, significa que podemos implementá-lo para `Portal` também. Abra o `lib/portal.ex` e, no final do arquivo, fora do módulo `Portal`, adicione o seguinte:

```
defimpl Inspect, for: Portal do
  def inspect(%Portal{left: left, right: right}, _) do
    left_door  = inspect(left)
    right_door = inspect(right)

    left_data  = inspect(Enum.reverse(Portal.Door.get(left)))
    right_data = inspect(Portal.Door.get(right))

    max = max(String.length(left_door), String.length(left_data))

    """
    #Portal<
      #{String.rjust(left_door, max)} <=> #{right_door}
      #{String.rjust(left_data, max)} <=> #{right_data}
    >
    """
  end
end
```

No trecho acima, implementamos o protocolo `Inspect` para a estrutura do `Portal`. O protocolo espera que apenas uma função chamada `inspec` seja implementada. A função espera dois argumentos, o primeiro é a própria struct `Portal` e o segundo é um conjunto de opções, que não nos interessa por enquanto.

Então, chamamos `inspect` várias vezes, para obter uma representação de texto das portas `esquerda` e `direita`, assim  como para obter uma representação dos dados dentro das portas. Finalmente, devolvemos uma string contendo a apresentação do portal corretamente alinhada.

Inicie outra sessão `iex` com `iex -S mix` para ver nossa nova representação sendo usada:

```
iex> Portal.Door.start_link(:orange)
{:ok, #PID<0.59.0>}
iex> Portal.Door.start_link(:blue)
{:ok, #PID<0.61.0>}
iex> portal = Portal.transfer(:orange, :blue, [1, 2, 3])
#Portal<
    :orange <=> :blue
  [1, 2, 3] <=> []
>
```

## Atirando em acessos supervisionados

Nós ouvimos com frequência que Erlang VM, a máquina virtual que roda o Elixir, juntamente com o ecossistema Erlang é boa para fazer aplicações tolerantes a falhas. Uma das razões para isso são as chamadas árvores de supervisão.

Nosso código até então não foi supervisionado. Vamos ver o que acontece quando nós desligamos explicitamente um dos agentes da porta:

```
# Inicia os acessos e transferência
iex> Portal.Door.start_link(:orange)
{:ok, #PID<0.59.0>}
iex> Portal.Door.start_link(:blue)
{:ok, #PID<0.61.0>}
iex> portal = Portal.transfer(:orange, :blue, [1, 2, 3])

# Primeiro desconecta a porta do shell para evitar que o shell quebre
iex> Process.unlink(Process.whereis(:blue))
true
# Envia um sinal de desligamento para o agente blue
iex> Process.exit(Process.whereis(:blue), :shutdown)
true

# Tenta mover os dados
iex> Portal.push_right(portal)
** (exit) exited in: :gen_server.call(:blue, ..., 5000)
    ** (EXIT) no process
    (stdlib) gen_server.erl:190: :gen_server.call/3
    (portal) lib/portal.ex:25: Portal.push_right/1
```

Nós recebemos uma mensagem de erro porque a porta `:blue` não existe. Você pode ver a mensagem `** (EXIT) no process` depois da nossa chamada da função. Para concertar a situação, nós vamos configurar um supervisor que será responsável por reiniciar um acesso do portal sempre que ele quebrar.

Lembra de quando nós passamos a flag `--sup` ao criarmos o nosso projeto `portal`? Nós passamos aquela flag porque os supervisores normalmente rodam dentro de árvores de supervisão e árvores de supervisão normalmente são iniciadas como parte da aplicação. Tudo que a flag `--sup` faz é criar uma estrutura supervisionada por padrão que nós podemos ver no nosso módulo `Portal.Application` em `lib/portal/application.ex`:

```
defmodule Portal.Application do
  # See http://elixir-lang.org/docs/stable/elixir/Application.html
  # for more information on OTP Applications
  @moduledoc false

  use Application

  def start(_type, _args) do
    import Supervisor.Spec, warn: false

    children = [
      # Define workers and child supervisors to be supervised
      # worker(Portal.Worker, [arg1, arg2, arg3])
    ]

    # See http://elixir-lang.org/docs/stable/elixir/Supervisor.html
    # for other strategies and supported options
    opts = [strategy: :one_for_one, name: Portal.Supervisor]
    Supervisor.start_link(children, opts)
  end
end
```

O código acima torna o módulo `Portal` uma aplicação de callback. A aplicação de callback deve prover uma função chamada `start/2`, que nós podemos ver acima, e essa função precisa iniciar um supervisor representando a raíz da nossa árvore de supervisão. Normalmente nosso supervisor não tem filhos e isso é exatamente o que mudaremos agora.

Substitua a função `start/20` acima por:

```
def start(_type, _args) do
  import Supervisor.Spec, warn: false

  children = [
    worker(Portal.Door, [])
  ]

  opts = [strategy: :simple_one_for_one, name: Portal.Supervisor]
  Supervisor.start_link(children, opts)
end
```

Nós fizemos duas coisas:

  - Adicionamos uma especificação de filho no supervisor, do tipo `worker`, e o filho é representado pelo módulo `Portal.Door`. Nós não passamos argumentos para o worker, apenas uma lista vazia `[]`, como a cor será especificada depois.
  - Mudamos a estratégia de `one_for_one` para `:simple_one_for_one`. Supervisores fornecem estratégias diferentes e `:simple_one_for_one` é útil quando queremos criar os filhos dinamicamente, muitas vezes com argumentos diferentes. Isso é exatamente  caso dos nossos acessos do portal, onde queremos gerar múltiplos acessos com cores diferentes.

O último passo é adicionar uma função nomeada `shoot/1` para o módulo `Portal` que irá receber uma cor e gerar um novo acesso como parte da nossa árvore de supervisão:

```
@doc """
Shoots a new door with the given `color`.
"""
def shoot(color) do
  Supervisor.start_child(Portal.Supervisor, [color])
end
```

A função acima alcança o supervisor chamado `Portal.Supervisor` e pergunta por um novo filho pra ser iniciado. `Portal.Supervisor` é o nome do supervisor que nós definimos em `start/2` e o filho será um `Portal.Acesso` que foi especificado como um worker desse supervisor.

Internamente, para iniciar um filho, o supervisor invocará `Portal.Acesso.start_link(color)`, onde cor é o valor passado na chamada `start_child/2` acima. Se nós tivéssemos chamado `Supervisor.start_child(Portal.Supervisor, [foo, bar, baz])`, o supervisor teria tentado iniciar um filho com `Portal.Door.start_link(foo, bar, baz)`.

Vamos dar uma chance para a nossa função de atirar. Inicie uma nova sessão novo `iex -S mix` e:

```
iex> Portal.shoot(:orange)
{:ok, #PID<0.72.0>}
iex> Portal.shoot(:blue)
{:ok, #PID<0.74.0>}
iex> portal = Portal.transfer(:orange, :blue, [1, 2, 3, 4])
#Portal<
       :orange <=> :blue
  [1, 2, 3, 4] <=> []
>

iex> Portal.push_right(portal)
#Portal<
    :orange <=> :blue
  [1, 2, 3] <=> [4]
>
```

E o que acontece se interrompermos o processo `:blue` agora?

```
iex> Process.unlink(Process.whereis(:blue))
true
iex> Process.exit(Process.whereis(:blue), :shutdown)
true
iex> Portal.push_right(portal)
#Portal<
  :orange <=> :blue
   [1, 2] <=> [3]
>
```

Note que dessa vez a seguinte operação `push_right/1` funcionou porque o supervisor automaticamente iniciou outro portal `:blue`. Infelizmente os dados que estavam no portal azul antes do crash foram perdidos mas nosso sistema se recuperou do crash.

Na prática existem diferentes estratégias de supervisão para escolher assim como mecanismos para persistir os dados no caso de algo dar errado, permitindo que você escolha a melhor opção para suas explicações.

Sensacional!

## Transferências distribuidas

Com os nossos portais em funcionamento, estamos prontos para iniciar a transferência através de transferências distribuídas. Isso pode ser muito incrível se você iniciar o código em duas máquinas diferentes na mesma rede. No entanto, se você não tiver outra máquina em mãos, funcionará do mesmo jeito.

Podemos iniciar uma sessão `iex` como nó dentro de uma rede passando a opção `--sname`. Vamos dar uma chance:

```
$ iex --sname room1 --cookie secret -S mix
Interactive Elixir - press Ctrl+C to exit (type h() ENTER for help)
iex(room1@jv)1>
```

Você pode ver que este terminal `iex` é diferente dos anteriores. Agora, podemos ver `room1@jv` na tela. `room1` é o nome que damos ao nó e `jv` é o nome da rede do computador em que o nó foi iniciado. No meu caso, minha máquina é chamada `jv`, mas você terá um resultado diferente. De agora em diante, usaremos `room1@COMPUTER-NAME` e `room2@COMPUTER-NAME` e você deve substituir `COMPUTER-NAME` pelos seus respectivos nomes de computador.

Na sessão `iex` chamada `room1,` vamos atirar a `:porta` azul:

```
iex(room1@COMPUTER-NAME)> Portal.shoot(:blue)
{:ok, #PID<0.65.0>}
```

Vamos começar outra sessão `iex` chamada `room2`:

```
$ iex --sname room2 --cookie secret -S mix
```

Nota: o cookie deve ser o mesmo em ambos os computadores para que os dois nós do Elixir possam se comunicar entre si.

A API do agente nos permite fazer cross-node requests. Tudo o que precisamos fazer é passar o nome do nó onde o agente nomeado que queremos alcançar está sendo executado ao invocar as funções `Portal.Door`. Por exemplo, vamos chegar à porta azul do `room2`:

```
iex(room2@COMPUTER-NAME)> Portal.Door.get({:blue, :"room1@COMPUTER-NAME"})
[]
```

Isso significa que podemos ter transferência distribuída simplesmente usando nomes dos nós. Ainda no `room2`, vamos tentar:

```
iex(room2@COMPUTER-NAME)> Portal.shoot(:orange)
{:ok, #PID<0.71.0>}
iex(room2@COMPUTER-NAME)> orange = {:orange, :"room2@COMPUTER-NAME"}
{:orange, :"room2@COMPUTER-NAME"}
iex(room2@COMPUTER-NAME)> blue = {:blue, :"room1@COMPUTER-NAME"}
{:blue, :"room1@COMPUTER-NAME"}
iex(room2@COMPUTER-NAME)> portal = Portal.transfer(orange, blue, [1, 2, 3, 4])
#Portal<
  {:orange, :room2@COMPUTER-NAME} <=> {:blue, :room1@COMPUTER-NAME}
          [1, 2, 3, 4] <=> []
>
iex(room2@COMPUTER-NAME)> Portal.push_right(portal)
#Portal<
  {:orange, :room2@COMPUTER-NAME} <=> {:blue, :room1@COMPUTER-NAME}
             [1, 2, 3] <=> [4]
>
```

Incrível. Nós distribuímos transferências trabalhando em nossa base de código sem alterar uma única linha de código!

Embora `room2` esteja coordenando a transferência, ainda podemos observar a transferência do `room1`:

```
iex(room1@COMPUTER-NAME)> orange = {:orange, :"room2@COMPUTER-NAME"}
{:orange, :"room2@COMPUTER-NAME"}
iex(room1@COMPUTER-NAME)> blue = {:blue, :"room1@COMPUTER-NAME"}
{:blue, :"room1@COMPUTER-NAME"}
iex(room1@COMPUTER-NAME)> Portal.Door.get(orange)
[3, 2, 1]
iex(room1@COMPUTER-NAME)> Portal.Door.get(blue)
[4]
```

Nossa transferência de portal distribuído funciona porque as portas são apenas processos e acessar/enviar os dados através das portas é feita enviando mensagens para esses processos através da API do Agente. Dizemos que enviar uma mensagem no Elixir é de localização transparente: podemos enviar mensagens para qualquer PID, independentemente se estiver no mesmo nó que o remetente ou em nós diferentes da mesma rede.

## Finalizando

Então nós chegamos ao final desse guia de como iniciar com Elixir! Foi um passeio divertido e nós fomos rapidamente de iniciar processos para atirar em acessos tolerantes a falhas manualmente para transferências de portal dstribuídas!

Nós desafiamos você a continuar aprendendo e explorando mais sobre Elixir ao levar sua aplicação Portal para o próximo nível:
  - Adiciona uma funcão `Portal.push_left/1` que transfira os dados na outra direção. Como você pode evitar o código duplicado existente entre as funções `push_left/1` e `push_right/1`?
  - Aprenda mais sobre [ExUnit](http://elixir-lang.org/docs/stable/ex_unit/ExUnit.html), o framework de test do Elixir, e escreva testes para a funcionalidade que acabamos de construir. Lembre que já fizemos uma estrutura padrão estabelecida no diretório `test`.
  - Gere a documentação HTML para o seu projeto com [ExDoc](http://github.com/elixir-lang/ex_doc)
  - Suba o seu projeto em um repositório externo, como [Github](https://github.com/), e publique um pacote usando o [Hex package manager](https://hex.pm/).

Nós convidamos você para explorar nosso [site](http://elixir-lang.org/) e ler nosso guia Getting Started ou muitos dos recursos disponíveis para aprender mas sobre Elixir e nossa comunidade vibrante.

Finalmente, um enorme agradecimento ao [Augie De Blieck Jr.](http://twitter.com/augiedb) pelos desenhos nesse tutorial.

Nos vemos por aí!

José Valim

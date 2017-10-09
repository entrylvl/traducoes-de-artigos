# O que é Git?

Sem dúvida, Git é o sistema de controle de versão mais utilizado no mundo atualmente. Git é um projeto de código aberto, sendo mantido ativamente e originalmente desenvolvido em 2005 por Linus Torvalds, o famoso criador do kernel do sistema operacional Linux. Um grande número de projetos de software dependem de Git para realizar o seu controle de versionamento, incluindo tanto projetos comerciais quanto de código aberto. Desenvolvedores que trabalham com Git são bem vistos em meio aos talentos de desenvolvimento de software. Além disso, Git funciona bem em uma grande variedade de sistemas operacionais e IDEs (Ambientes de Desenvolvimento Integrado).

Por ter uma arquitetura distribuída, Git é um exemplo de um DVCS (Sistema de Controle de Versionamento Distribuído). Ao invés de manter um histórico completo de versões do software em um único lugar, como é feito em sistemas de controle de versionamento como CVS ou Subversion (também conhecido como SVN), em Git, toda cópia que um desenvolvedor possui do código é também um repositório que pode conter o histórico inteiro de todas as mudanças.

Além de ser distribuído, Git foi desenvolvido tendo em mente o seu desempenho, segurança e flexibilidade.

## Desempenho

Comparado a ferramentas alternativas, Git possui características de performance bruta bem melhores. Todas as operações de registro de alterações,criação de _branches_, mesclagem e comparação de versões têm desempenho otimizado. Os algoritmos implementados no Git se beneficiam de um conhecimento profundo a respeito de atributos comuns em diretórios de arquivos de código fonte reais, da forma como eles geralmente são modificados e de quais são os padrões de acesso.

Diferentemente de algumas ferramentas de versionamento de controle, Git não leva em consideração o nome dos arquivos ao determinar a forma como eles devem ser armazenados e versionados. Ao invés disso, Git leva em consideração o conteúdo do arquivo em si. Afinal, esses arquivos são frequentemente renomeados, particionados e reordenados. O formato dos arquivos em um repositório Git usa uma combinação das técninas de codificação delta (armazenando as diferenças de conteúdo) e compressão, também armazena especificamente o conteúdo de diretórios e os objetos de metadados referente às versões.

Além disso, por ser um sistema distribuído, Git possui vantagens significantes em performance.

Por exemplo, digamos que Alice, uma desenvolvedora, faz alterações no código fonte adicionando uma nova funcionalidade para a versão 2.0, que será lançada em breve, e envia suas alterações com mensagens bem descritivas. Depois ela começa a trabalhar em uma nova funcionalidade e também envia as alterações correspondentes. Naturalmente, as funcionalidades são armazenadas separadamente no histórico de versões. Após isso, Alice muda para o _branch_ correspondente à versão 1.3 do mesmo sistema a fim de resolver um problema que afeta apenas aquela versão mais antiga. O intuito é que o time de Alice possa lançar a solução para o problema em uma nova versão, 1.3.1, antes que a versão 2.0 esteja pronta. Finalmente, Alice pode retornar ao _branch_ da versão 2.0 para continuar a trabalhar em novas funcionalidades e tudo isso pode ser realizado sem nenhum acesso à Internet, por isso é considerado rápido e seguro. Ela poderia inclusive fazer tudo isso durante um voo. No momento em que ela finalizar todas as alterações que devem ser enviadas para o repositório remoto, Alice pode enviá-las usando um único comando.

## Segurança

Git foi desenvolvido priorizando a integridade do código fonte gerenciado. Todo o conteúdo dos arquivos assim como a relação apropriada entre arquivos diretórios, versões, `tags` e `commits` são protegidos com o uso de um algoritmo criptográfico de segurança hash chamado `SHA1`. Isso protege o código e o histórico de mudanças contra alterações maliciosas e/ou acidentais e também garante que o histórico possa ser totalmente rastreável.

Com o Git, você tem a certeza da autenticidade do histórico de conteúdo do seu código fonte.

Outros sistemas de controle de versão não fornecem proteção contra futuras alterações anônimas do histórico. Isso pode vir a ser uma séria vulnerabilidade para qualquer organização que trabalha com desenvolvimento de software.

## Flexibilidade

Flexibidade é um objetivo chave para o projeto do Git. Ele é flexível em vários aspectos: no suporte de vários tipos de workflows de desenvolvimento não-lineares, na eficiência em pequenos e grandes projetos e na compatibilidade com vários sistemas existentes e protocolos.

Git foi projetado para suportar `branching` e `tagging` como cidadãos de primeira classe (diferente do SVN) e operações que afetam `branches` e `tags`(como `merging` ou `reverting`) são também guardados como parte do histórico de mudanças. Não são todos os controles de versão que possuem esse nível de monitoramento.

## Controle de versão com Git

Git é a melhor escolha para a maioria dos times de desenvolvimento de software atualmente. Ao passo em que todo time é diferente e deveria fazer sua própria análise quanto a isso, aqui vão alguns motivos pelos quais é recomendável realizar o controle de versionamento com Git ao invés de ferramentas alternativas:

### Git é bom

Git possui funcionalidades, desempenho, segurança e flexibilidade que a maioria dos times e desenvolvedores individuais precisam. Essas características são descritas acima. Em comparação com muitas das alternativas disponíveis, muitos times veem Git como a escolha mais favorável.

### Git é de fato um padrão

Git é a ferramenta de controle de versionamento mais adotada. Isso faz com que o Git seja atrativo pelos motivos descritos. Na Atlassian, quase todo o código fonte dos nossos projetos é gerenciado usando Git.

Um grande número de desenvolvedores já tem experiência com Git e é possível que uma parcela significativa dos graduados na academia possa ter tido experiência apenas com Git. Enquanto algumas equipes podem ter que enfrentar uma curva de aprendizado ao migrar de uma outra ferramenta de versionamento para o Git, muitos dos seus atuais e futuros desenvolvedores não precisarão ser treinados em Git.

Além dos benefícios ofertados pelo vasto banco de talentos, o fato de Git ser predominante também significa que muitos softwares e serviços de terceiros já estão integrados com Git incluindo IDEs e as nossas próprias ferramentas como o software cliente para DVCS [Sourcetree](https://www.atlassian.com/software/sourcetree), o software de monitoramente de projetos, [Jira](https://www.atlassian.com/software/jira), e o serviço de hospedagem de código, [Bitbucket](https://bitbucket.org/).

Se você é um desenvolvedor com pouca experiência e deseja adquirir habilidades importantes em ferramentas de desenvolvimento de software, quando se fala em controle de versão, Git deve estar na sua lista.

### Git é um projeto de código aberto com qualidade

Git é um projeto de código aberto com um bom suporte e com mais de uma década de uma gestão efetiva. Com lançamento regular de novas versões com melhorias na usabilidade e funcionalidade, os responsáveis pelo projeto têm mostrado equilíbrio e uma abordagem madura na avaliação das necessidades de longo prazo dos usuários. A qualidade do software de código aberto pode ser facilmente analisado e inúmeros negócios dependem fortemente dessa qualidade.

Git desfruta de um grande suporte por parte da comunidade e uma vasta base de usuários. A documentação é excelente e ampla, incluindo livros, tutoriais e websites dedicados. Além disso existem muitos podcasts e tutoriais em vídeo.

Por ter código aberto, Git diminui o custo para desenvolvedores amadores, visto que eles podem usar Git sem pagar nenhuma taxa. Para o uso em projetos de código aberto, Git é sem dúvida o sucessor de sistemas de controle de versionamento que fizeram sucesso no passado, como SVN e CVS.

### Críticas ao Git

Uma crítica frequente ao Git é que ele pode ser difícil de aprender. Alguns dos termos em Git serão inéditos para iniciantes e para usuários de outros sistemas. Por exemplo, o comando `revert` em Git tem um significado diferente para o SVN e para o CVS. Apesar disso, Git é muito poderoso e fornece muitas utilidades para seus usuários. Aprender a usar esse poder pode levar tempo, contudo uma vez que se aprende, esse poder pode ser usado pelo time para aumentar a sua velocidade de desenvolvimento.

Para os times acostumados com uma ferramenta de versionamento não distribuída, ter um repositório central pode parecer uma vantagem que eles não desejam abrir mão. Entretanto, por mais que Git tenha sido desenvolvido como uma ferramenta de versionamento distribuída (DVCS), com ele você ainda pode ter um repositório oficial e de acordo com as normas onde todas as alterações feitas ao software precisam ser armazenadas. Com Git, pelo fato de o repositório de todos os desenvolvedores estar sempre completo, o trabalho deles não precisa ficar limitado pela disponibilidade ou desempenho do servidor "central". Durante interrupções ou enquanto offline, desenvolvedores ainda podem consultar o histórico completo do projeto. Pelo fato de o Git ser flexível e distribuído, você pode trabalhar da maneira que você está acostumado e ainda desfrutar dos benefícios que o Git proporciona, alguns dos quais você pode até nem perceber que estava perdendo.

Agora que você entende o que é controle de versão, o que é Git e por que times de desenvolvimento de software devem usá-lo, continue lendo para descobrir os benefícios que Git pode fornecer para a organização como um todo.

# O que é Git?

Sem dúvida, Git é o sistema de controle de versão mais utilizado no mundo atualmente. Git é um projeto de código aberto, sendo mantido ativamente e originalmente desenvolvido em 2005 por Linus Torvalds, o famoso criador do kernel do sistema operacional Linux. Um grande número de projetos de software dependem de Git para realizar o seu controle de versionamento, incluindo tanto projetos comerciais quanto de código aberto. Desenvolvedores que trabalham com Git são bem vistos em meio aos talentos de desenvolvimento de software. Além disso, Git funciona bem em uma grande variedade de sistemas operacionais e IDEs (Ambientes de Desenvolvimento Integrado).

Por ter uma arquitetura distribuída, Git é um exemplo de um DVCS (Sistema de Controle de Versionamento Distribuído). Ao invés de manter um histórico completo de versões do software em um único lugar, como é feito em sistemas de controle de versionamento como CVS ou Subversion (também conhecido como SVN), em Git, toda cópia que um desenvolvedor possui do código é também um repositório que pode conter o histórico inteiro de todas as mudanças.

Além de ser distribuído, Git foi desenvolvido tendo em mente o seu desempenho, segurança e flexibilidade.

## Desempenho

Comparado a ferramentas alternativas, Git possui características de performance bruta bem melhores. Todas as operações de registro de alterações,criação de _branches_, mesclagem e comparação de versões têm desempenho otimizado. Os algoritmos implementados no Git se beneficiam de um conhecimento profundo a respeito de atributos comuns em diretórios de arquivos de código fonte reais, da forma como eles geralmente são modificados e de quais são os padrões de acesso.

Diferentemente de algumas ferramentas de versionamento de controle, Git não leva em consideração o nome dos arquivos ao determinar a forma como eles devem ser armazenados e versionados. Ao invés disso, Git leva em consideração o conteúdo do arquivo em si. Afinal, esses arquivos são frequentemente renomeados, particionados e reordenados. O formato dos arquivos em um repositório Git usa uma combinação das técninas de codificação delta (armazenando as diferenças de conteúdo) e compressão e também armazena especificamente o conteúdo de diretórios e os objetos de metadados referente às versões.

Além disso, por ser um sistema distribuído, Git possui vantagens significantes em performance.

Por exemplo, digamos que Alice, uma desenvolvedora, faz alterações no código fonte adicionando uma nova funcionalidade para a versão 2.0, que será lançada em breve, e envia suas alterações com mensagens bem descritivas. Depois ela começa a trabalhar em uma nova funcionalidade e também envia as alterações correspondentes. Naturalmente, as funcionalidades são armazenadas separadamente no histórico de versões. Após isso, Alice muda para o _branch_ correspondente à versão 1.3 do mesmo sistema a fim de resolver um problema que afeta apenas aquela versão mais antiga. O intuito é que o time de Alice possa lançar a solução para o problema em uma nova versão, 1.3.1, antes que a versão 2.0 esteja pronta. Finalmente, Alice pode retornar ao _branch_ da versão 2.0 para continuar a trabalhar em novas funcionalidades e tudo isso pode ser realizado sem nenhum acesso à Internet, por isso é considerado rápido e seguro. Ela poderia inclusive fazer tudo isso durante um voo. No momento em que ela finalizar todas as alterações que devem ser enviadas para o repositório remoto, Alice pode enviá-las usando um único comando.

## Segurança

## Flexibilidade

## Controle de versão com Git

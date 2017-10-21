# O que é controle de versão
## Benefícios do controle de versão
Sistemas de controle de versão são uma categoria de ferramentas de software que ajudam uma equipe de software a gerenciar mudanças no código fonte.
O software de controle de versão mantém todas as mudanças no código em um tipo especial de banco de dados. Se um erro for cometido, os desenvolvedores podem voltar no tempo e comparar versões anteriores do código para ajudar na correção minimizando a interrupção dos membros da equipe.

Para quase todos os projetos de software, o código fonte é como as jóias da coroa - um recurso precioso cujo valor deve ser protegido. Para a maioria das equipes de software, o código fonte é um repositório de conhecimento e compreensão inestimáveis sobre o problema que os desenvolvedores coletaram e refinaram através de um esforço cuidadoso. Controle de versão protege o código fonte de catástrofe, erro humano e consequências não desejadas.

Os desenvolvedores de software que trabalham em equipes estão continuamente escrevendo novos códigos e alterando os já existentes. O código para um projeto, aplicativo ou componente de software é normalmente organizado em uma estrutura de pastas ou "árvore de arquivos". Um desenvolvedor da equipe pode estar trabalhando em uma nova funcionalidade, enquanto outro corrige um bug que não tem relação com essa nova funcionalidade. Cada desenvolvedor pode fazer suas alterações em várias partes da árvore de arquivos.

O controle de versão ajuda a equipe a resolver esses tipos de problemas, rastreando individualmente cada alteração feita por cada colaborador e ajudando a prevenir que o trabalho paralelo gere códigos conflitantes. As alterações feitas em uma parte do software podem ser incompatíveis com as feitas por outro desenvolvedor que trabalha ao mesmo tempo. Este problema deve ser descoberto e resolvido de forma ordenada sem gerar impedimentos para o trabalho do restante da equipe. Além disso, em desenvolvimento de software, qualquer alteração pode, por conta própria, introduzir novos bugs e o novo software não será confiável até que seja testado. Então o teste e o desenvolvimento caminham juntos até que uma nova versão esteja pronta.

Um bom software de controle de versão suporta o workflow preferido do desenvolvedor sem impor uma forma específica de trabalhar. Idealmente, também funciona em qualquer plataforma, em vez de dizer qual sistema operacional ou ferramentas os desenvolvedores devem usar. Ótimos sistemas de controle de versão facilitam um fluxo de mudanças regular e contínuo no código, diferente do que acontece no frustrante e desajeitado mecanismo de bloqueio de arquivos, dando sinal verde a um colaborador, mas ao preço de bloquear o progresso dos outros.

Equipes de software que não usam qualquer forma de controle de versão frequentemente se deparam com problemas como não saber quais mudanças que foram feitas estão disponíveis para os usuários, ou a criação de alterações incompatíveis entre duas partes independentes que precisam então ser meticulosamente desvendadas e retrabalhadas. Se você é um desenvolvedor que nunca usou um controle de versão você pode ter adicionado versões em seus arquivos, talvez com sufixos como "final" ou "mais-recente" e depois teve que lidar com uma nova versão final. Talvez você tenha comentado blocos de código porque você desejava desabilitar certa funcionalidade sem remover o código, temendo que poderia existir uma finalidade para ele mais tarde. O controle de versão é uma saída para esses problemas.

O software de controle de versão tem um papel essencial na rotina dos times de software modernos. Desenvolvedores de software independentes acostumados a trabalhar com um sistema de controle de versão eficiente em seus times, normalmente reconhecem o incrível valor que o controle de versão oferece mesmo em pequenos projetos pessoais. Uma vez acostumados aos eficazes benefícios dos sistemas de controle de versão, muitos desenvolvedores não considerariam trabalhar sem ele, mesmo em projetos não relacionados a software.

## Benefícios dos sistemas de controle de versão

Developing software without using version control is risky, like not having backups. Version control can also enable developers to move faster and it allows software teams to preserve efficiency and agility as the team scales to include more developers.

É arriscado desenvolver software sem controle de versão, é o mesmo que não ter backups. O controle de versão pode permitir aos desenvolvedores serem rápidos e aos times de software se manterem eficientes e agéis à medida que a equipe aumenta com a entrada de mais desenvolvedores.

Sistemas de controle de versão (do inglês VCS ou Version Control Systems) tiveram grandes melhorias nas últimas décadas e algumas são melhores do que outras. VCS algumas vezes são conhecidos como ferramentas de gerenciamento de código, ou SCM (do inglês Source Code Management) ou ainda sistema de controle de revisão, ou RCS (do inglês Revision Control System). Uma das mais populares ferramentas de VCS em uso se chama Git. O Git é um VCS <i>Distribuído</i> (ou DVCS), falaremos disso mais tarde. Como muitos do sistemas de VCS disponíveis atualmente, o Git é gratuito e de código aberto. Independentemente do nome que eles recebem, ou qual sistema é usado, os principais benefícios que você deve esperar do controle de versão são os seguintes.

<ol>
<li>
Um histórico completo e delongo prazo das mudanças de cada arquivo. Isso envolve todas as mudanças feitas por várias pessoas ao longo dos anos.As mudanças incluem a criação e exclusão de arquivos, bem como edições feitas em seus conteúdos. As diferentes ferramentas de VCS diferem em quão bem elas controlam o renomeamento e mudança de local dos arquivos. Este histórico deve também incluir o autor, data e as anotações sobre a finalidade de cada alteração. Ter o histórico completo permite voltar a versões anteriores para ajudar na análise do motivo dos bugs e é essencial quando se precisa corrigir erros em verses anteriores do software.
</li>
    
<br>

<li>
Ramificar e mesclar (do inglês branching e merging). Ter membros da equipe trabalhando simultaneamente é unanimidade, mas mesmo pessoas trabalhando por conta própria podem se beneficiar da capacidade de fluxos independentes de mudanças. Criar um "branch" nas ferramentas VCS mantém os fluxos de trabalho independentes um do outro, ao mesmo tempo que fornece a facilidade para "mergear" o trabalho de volta, permitindo aos desenvolvedores verificar que as mudanças de cada branch não conflitam. Muitas equipes de software adotam uma prática de branching para cada funcionalidade ou talvez um branching para cada versão, ou ambos. Existem muitos fluxos de trabalho diferentes que as equipes pode escolher quando decidem como fazer uso das facilidades de branching e merging no VCS.
</li>


<li>Traceability. Being able to trace each change made to the software and connect it to project management and bug tracking software such as Jira, and being able to annotate each change with a message describing the purpose and intent of the change can help not only with root cause analysis and other forensics. Having the annotated history of the code at your fingertips when you are reading the code, trying to understand what it is doing and why it is so designed can enable developers to make correct and harmonious changes that are in accord with the intended long-term design of the system. This can be especially important for working effectively with legacy code and is crucial in enabling developers to estimate future work with any accuracy.</li>
</ol>

While it is possible to develop software without using any version control, doing so subjects the project to a huge risk that no professional team would be advised to accept. So the question is not whether to use version control but which version control system to use.

Há muitas escolhas, mas aqui nos concentraremos em apenas um, Git.

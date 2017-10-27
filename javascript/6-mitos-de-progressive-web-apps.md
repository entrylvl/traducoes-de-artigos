[Artigo Original: 6 myths of Progressive Web Apps](https://medium.com/samsung-internet-dev/6-myths-of-progressive-web-apps-81e28ca9d2b1)

---

# 6 mitos de Progressive Web Apps

Termos como ["Progressive Web Apps"](https://medium.com/@slightlylate/progressive-apps-escaping-tabs-without-losing-our-soul-3b93a8561955)(PWAs) são [úteis para espalhar conceitos](https://fberriman.com/2017/06/26/naming-progressive-web-apps/) mas eles chegam com um risco de abusos e mal-interpretações. Como é um conceito relativamente novo e ainda está evoluindo, PWAs podem ser definidas e compreendidas diferentemente por pessoas diferentes. Neste artigo, eu irei compartilhar alguns mitos comuns (IMHO) about PWAs.

![O oficialmente não oficial logo PWA](https://cdn-images-1.medium.com/max/800/1*P-gXz7UCnyazZQHhy43ApQ.png)

Espero que esta publicação estimule a discussão e nos ajude a melhorar e compreender compartilhando. Nós continuamos a discutir isto com nossos colegas que fornecem navegadores também.

Primeito, o que são PWAs atualmente?

Nós deveriamos realmente começar com a [definição do Alex Russel](https://infrequently.org/2015/06/progressive-apps-escaping-tabs-without-losing-our-soul/), que foi quem surgiu com o conceito em conjunto com Frances Berriman, PWAs são:

> Responsive, connectivity-independent, app-like, fresh, safe, discoverable, re-engageable, installable, linkable web experiences.

Isso é bastante para se lembrar, já — e é isso mesmo antes de chegarmos ao [checklist style de definição](https://developers.google.com/web/progressive-web-apps/checklist)! Então, aqui estão algumas outras maneiras que eu gostaria de descrevê-las:

> "Web apps atualizados para aplicativos de primeira classe"

Ou:

> "O melhor da web, mais o melhor dos aplicativos nativos"

Ou, nas palavras do [Alex](https://medium.com/@slightlylate):

> "Somente sites que tomaram todas as vitaminas corretas"

Em outras palavras, eles são sobre aprendizagem a partir de aplicativos nativos e construção — e entrega — das melhores experiências na Web.(Ainda é a Web, somente com benefícios adicionados)

Certo, agora aqui esta meu top mitos sobre PWAs:

## Mito 1: PWAs são somente mágicas especificas do navegador

<a href="https://t.co/uzHmNomVky">![PWAs Bob Esponja](https://pbs.twimg.com/media/DKQ-XX2W0AIXX7c.jpg)</a>
<blockquote class="twitter-tweet" data-conversation="none" data-lang="pt"><p lang="en" dir="ltr">The best I could do with the time I had: <a href="https://t.co/uzHmNomVky">pic.twitter.com/uzHmNomVky</a></p>&mdash; Marcus Hellberg (@marcushellberg) <a href="https://twitter.com/marcushellberg/status/910921733208764417?ref_src=twsrc%5Etfw">21 de setembro de 2017</a></blockquote>

Se você está iniciando com PWAs, podem parecer como truques especificos do navegador (ou *"bleeding edge Google-specific weirdness"*, como eu li de um desenvolvedor!). Mas essencialmente eles são sobre *combinar alguns padrões web e melhores práticas*, com o proprósito de entregar a melhor experiência.

Eu penso que PWAs têm alguns requisitos básicos simples:

![Padrões PWA](https://cdn-images-1.medium.com/max/800/1*2hsAx5q06u4vBKkCQiDi2g.png)

Enquanto você servir o seu site em HTTPS, você terá um Service Worker com um cache básico, e você irá registrar um Web App Manifest com algumas informações básicas como o nome e pelo menos um ícone, seu website deverá ser reconhecido (ex. pela Samsung Internet, veja o mito 2 para mais detalhes) como uma PWA.

Com esta combinação, em navegadores suportados, seus usuários podem adicionar seu site para a tela inicial deles, iniciar em uma janela standalone (se assim você configurou) e reusar ele, tendo ou não conexão de dados. Esse tipo de experiência de usuário costuma ser exclusiva de aplicativos nativos.

Outras funcionalidades como uma Notificação de Push são frequentemente discutidas em relação a PWAs (a definição acima inclui "reengajamento"), mas eu vejo estas como extras opcionais. De fato, eu gosto de pensar em PWAs como um conjunto de ferramentas. Você não tem de implementar todas as coisas juntas, embora poderiam criar uma melhor experiência se você o fizesse.

O outro aspecto chave das PWAs — além dos padrões web atuais envolvidos — é desempenho. Ferramentas como [Lighthouse](https://developers.google.com/web/tools/lighthouse/) podem entregar um score por isto. Um dos melhores caminhos para obter um
score *"real-world"* é utilizar [webpagetest.org/easy](https://www.webpagetest.org/easy) e marque a opção para auditar o Lighthouse. Isto irá lhe entregar um link facilmente compartilhável que seu time poderá utilizar, bem como um ambiente controlado que você pode executar seu teste (obrigado [Alex](https://medium.com/@slightlylate) pela dica!).

Desempenho é o grande topico abordado. Nossos amigos no Google incluem métricas de desempenho em sua [definição de "linha de base"](https://developers.google.com/web/progressive-web-apps/checklist#baseline), mas eu prefiro vê-lo como fora do escopo central do PWA.

Caso contrário, imagine um dia em que você adicione outro recurso ao seu site e o leva para além de uma métrica de desempenho — de repente sua PWA deixa de ser uma "PWA"! Isto pode ser benéfico para encorajar melhores experiências, mas eu também acho que isto poderia ser confuso para nossa definição e duvido que todos os navegadores desejem ter os mesmos critérios.



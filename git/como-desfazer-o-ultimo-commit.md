[Artigo original: How to undo the last commit](https://dev.to/isabelcmdcosta/how-to-undo-the-last-commit--31mg)

---

# Como desfazer o último commit

Neste artigo mostrarei como eu às vezes desfaço alterções erradas (commits) em um projeto de programação, usando o git no terminal.

## Por que eu iria querer fazer isso?

Na minha tese, estou trabalhando em um projeto que eu desenvolvo em um environment (ambiente), e então testo em outro environment composto de múltiplas máquinas virtuais. Então cada mudança importante que eu faço pode ter um impacto significante nas funcionalidades do projeto. Às vezes, a mudança que eu 
faço pode não ter o resultado esperado. Então eu tenho que verificar as mudanças e analizar o comportamento do projeto antes e depois do último commit.

## Como você vê o último commit?

Para testar um commit específico, você precisa do hash. Para obter o hash que você pode executar git log, obtendo esse resultado:

'''
root@debian:/home/debian/test-project# git log
commit <hash do último commit>
Author: Isabel Costa <example@email.com>
Date:   Sun Feb 4 21:57:40 2018 +0000

<mensagem do commit>

commit <before hash do último commit>
Author: Isabel Costa <example@email.com>
Date:   Sun Feb 4 21:42:26 2018 +0000

<mensagem do commit>

(...)
'''

Você também pode executar git log --oneline para simplificar a saída:

'''
root@debian:/home/debian/test-project# git log --oneline
<last commit hash> <mensagem do commit>
cdb76bf Added another feature
d425161 Added one feature   

(...)
'''

Para testar um commit específico (por exemplo <before hash do último commit>:), 
que você acha que tem a última versão trabalhada, você pode digitar o seguinte:

'''
git checkout <hash do commit>
'''

Isso fará com que o repositório de trabalho corresponda ao estado desse exato commit. 

Depois de fazer isso, você obterá a seguinte resultado:

'''
root@debian:/home/debian/test-project# git checkout <hash do commit>
Note: checking out '<hash do commit>'.

You are in 'detached HEAD' state. You can look around, make experimental changes
and commit them, and you can discard any commits you make in this state without
impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may do so
(now or later) by using -b with the checkout command again. Example:

git checkout -b new_branch_name

HEAD is now at <hash do commit>... <mensagem do commit>
'''

Depois de analisar o commit específico, se você decidir ficar nesse estado de commit,
 você pode desfazer o último commit.

## Como desfazer este commit?

Se você desejar [desfazer / reverter](https://git-scm.com/docs/git-revert) 
o último commit, você pode fazer o seguinte,
 usando o hash do commit que você obteve do comando git log:

'''
git revert <hash do commit>
'''

Este comando irá criar um novo commit com a palavra “Revert” no começo da mensagem.
Após isso, se você verificar o status do seu repositório, notará que você tem o HEAD
desconectado no commit testado anteriormente.

'''
root@debian:/home/debian/test-project# git status
HEAD detached at 69d885e

(...)
'''

[Você não quer ver esta mensagem](https://www.git-tower.com/learn/git/faq/detached-head-when-checkout-commit),
 então, para consertar isso e anexar o HEAD ao seu repositório, 
 você deve verificar o branch em que está trabalhando:

'''
git checkout <branch atual>
'''
Durante a elaboração deste post, encontrei este tutorial -  [Desfazendo Commits e Alterações](https://www.atlassian.com/git/tutorials/undoing-changes)
 - pela Atlassian, que descreve muito bem essa questão.

## Resumo

* Se você quiser testar o commit anterior apenas faça git checkout <test commit hash>; 
então você pode testar a última versão de trabalho do seu projeto.

* Se você quiser reverter o último commit apenas faça git revert <unwanted commit hash>; 
então você pode fazer o push deste novo commit, que desfez seu commit anterior.

* Para consertar o HEAD destacado use git checkout <branch atual>.
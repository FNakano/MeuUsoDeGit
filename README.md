# Meu uso de Git

## origem

# Como Git e GitHub são usados neste projeto

## Sobre esta página

Estou começando a trabalhar mais seriamente com git e github. Esta página é uma mistura de registro de experiência com tutorial. Acho que é útil antes de começar a falar de ramos (branches), que geralmente é onde a maioria dos tutoriais básicos de git começa, ou quer chegar rápido.

Já tentei passar da superfície do uso do git algumas vezes e sei, por experiência, que tentar sozinho a partir dos livros e sites é difícil... não sei bem o motivo, talvez porque quis começar pela teoria de funcionamento e a documentação para isso é [pouco atraente](https://git-scm.com/book/pt-br/v2/Git-Branching-Remote-Branches). Vi também que [outros desenvolvedores sentiram a mesma dificuldade](https://medium.com/mindorks/what-is-git-commit-push-pull-log-aliases-fetch-config-clone-56bc52a3601c). O conteúdo do link, em termos de comandos e seus usos são muito parecidos com o que apresento aqui, mas o ponto de partida, narrativa e destaques são diferentes. Também tem alguns diagramas bastante elucidativos.

Aqui, situação de partida é: um desenvolvedor, um ramo de trabalho, um repositório remoto (o github). O desenvolvedor pode trabalhar a partir de vários lugares e em cada um ter um repositório local.

A situação de partida permite aprender e testar os comandos do git, sem precisar preocupar-se com preservar o trabalho de outras pessoas, ou simular outras pessoas, ou precisar da ajuda de outras pessoas... mas não explora as principais situações de desenvolvimento colaborativo para as quais git foi feito.

Se você quiser ir direto para [ramos (branches) e como isso funciona, pode vir por aqui (e voltar para cá, se achar que precisa :)](ramos.md). Este também é o próximo tópico.

Se estiver mais interessado em gerenciar algum desenvolvimento e quiser saber sobre alternativas de fluxos de trabalho usando git:
[atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows#!workflow-gitflow)

Tentarei manter cada página o mais enxuta possível, para manter a leitura rápida, objetiva e atraente. Isto não é tão fácil pois à medida que vou entendendo mais sobre o assunto, tendo a querer explorar mais aspectos e documentá-los. Isto pode ser feito nas páginas existentes relacionadas ao aspecto a documentar, mas isto alonga, adensa, enche as páginas com alternativas - elas passam a refletir o amadurecimento de quem escreve, que era iniciante, e supre menos a necessidade do iniciante - que é o público que quero atingir. Há opções para cumprir os dois objetivos: uma é criar "fotografias" - clones de versões mais antigas e simples. Outra é dar aos leitores o acesso a todas as versões. Outra é manter as páginas simples e acrescentar a elas links para o que for se aprendendo.

Gosto da última.

Case: [Como controle de versão poupou-me tempo e desgaste emocional](README.md#2020-12-03-114552). 

Perguntas e respostas:

[Como clonar um repositório em uma pasta de nome diferente do nome da pasta do repositório?](#2021-01-26-112652)

[Recebi e-mail do github dizendo que autenticação por senha não será mais válida a partir de 13.08.2021. O que fazer?]()

## Motivação

Se você for o único desenvolvedor do projeto, quer acessar o fonte de qualquer lugar e quando edita o fonte em computadores diferentes tem dificuldade ou aborrecimentos em unificar as versões dos computadores, git, github e esta página podem ajudar.

A dinâmica baseia-se em manter o fonte atualizado num repositório. Claro que uma pessoa disciplinada consegue fazer isso com um *pendrive* MAS mesmo os mais disciplinados às vezes esquecem ou não conseguem atualizar. Ferramentas de controle de versão, como git, ajudam a diminuir o trabalho caso isso aconteça. Com esta ferramenta, é possível trabalhar em outra funcionalidade do código, ou em outra seção do capítulo que está escrevendo e depois fundir (*merge*) todas as versões, na maioria dos casos, automaticamente.

Vou chamar *"na maioria dos casos, automaticamente"* de *quase automaticamente*.

Grandes vantagens tornam-se evidentes quando há várias pessoas trabalhando no mesmo arquivo. Neste caso cada uma pode ter sua cópia, dar sua contribuição e depois as contribuições podem ser fundidas *quase automaticamente*.

Se você está num projeto com uma equipe usando git para sincronizar os arquivos do projeto e precisou ficar fora por um mês, com três comandos você atualiza a sua versão e está pronto para voltar, pelo menos no que concerne aos arquivos.

Se você está trabalhando na próxima versão do seu projeto e surge um erro que precisa ser corrigido na versão de produção, com uns poucos comandos você entra na versão de produção, leva seu tempo para fazer a correção e com outros poucos comandos, atualiza a versão de produção e volta para os arquivos e o trabalho na próxima versão.

Se há diferentes versões, por exemplo para Android e para iOS, com alguns arquivos em comum e outros diferentes, com vários colaboradores em cada versão, manter os arquivos coerentes pode ser facilitado através do uso de controladores de versão, como git.

Em vista das vantagens, aprender a usar git pode ser um investimento que compensa: gasta-se esforço aprendendo, ganha-se capacidade de acrescentar colaboradores (escalabilidade) e agilidade em gerenciar o projeto.

## Etapas iniciais

Comecei este repositório criando primeiro o repositório no github (repositório remoto) e depois clonando no computador local (repositório local). Fiz isso porque não achei no github como criar subdiretórios e quero isso para organizar os arquivos que pretendo criar e manter aqui.

Criar o repositório no github foram alguns apertar de botões. Preferi criar com o *README.md* para criar o repositório com algo dentro - recomendo fazer isso. Chamarei o repositório de *RepoTeste*. Já criar no computador local deu mais trabalho pois fiz umas besteiras no caminho.

Antes de começar a história, instale o [git](https://git-scm.com/). :)

Ok, antes de antes de começar: 

- **git** é uma ferramenta de versionamento e desenvolvimento paralelo (colaborativo) em que cada colaborador pode ter um ou mais ramos de trabalho (*branch*) e pode mantê-los todos em paralelo. Quando um ramo de trabalho estiver concluido, ele pode fundir (*merge*) com o ramo de trabalho que quiser, por exemplo o ramo mestre, ou o ramo de produção. Existe para Linux, Mac e Windows.

- **github** é um site de desenvolvimento colaborativo e compartilhamento de repositórios. Ele é baseado em um servidor de arquivos executando git e permitindo que desenvolvedores editem, armazenem, compartilhem, comuniquem, divulguem repositórios e socializem em torno deles. No github um repositório é uma área de armazenamento de arquivos e um projeto permite usar, além do repositório, ferramentas de gerenciamento, como quadros e mensagens - semelhante ao Trello. 

Entendida a diferença, *instale o git* passa a ser uma frase que faz sentido... :)

Depois de instalar o git:

- crie uma pasta no computador local para clonar o *RepoTeste*. (Sugestão para este momento:criar a pasta com o mesmo nome);
- copie o <nome do repositório> (algo como https://github.com/.../...) no botão *clone ou download* que aparece na janela do github do lado direito do nome do seu repositório.
- com o terminal (sim, uso linux), entre na pasta;
- execute **git clone <nome do repositório>  .   ** (o ponto no final é importante!)

**nota**: neste exemplo, os comandos git são sempre usados na pasta em que *git clone* foi executado - é nela que a sub-pasta oculta *.git*, que contém os arquivos de controle relacionados à sua cópia local, é criada. 

**nota**: criando deste jeito, a associação entre a pasta local e o repositório remoto fica armazenada (em algum lugar na sub-pasta oculta *.git*). Assim, os comandos *git* usarão o repositório remoto associado e você não precisa informar a cada comando. 


Deve ter aparecido algumas mensagens e se tudo deu certo, o *README.md* deve estar lá também.

Talvez explicar a mesma coisa por outra fonte ajude a entender melhor. Pode tentar [a documentação do github sobre clonar repositórios](https://help.github.com/pt/github/creating-cloning-and-archiving-repositories/cloning-a-repository)

Depois de clonar o repositório, coloquei as instruções no *README.md* usando o editor online. Isto deixou o meu arquivo local atrasado em relação à versão no servidor. Para re-sincronizar:

- git fetch
- git merge (acabei de ver que git checkout dá um aviso que o ramo local está atrasado e recomenda usar git pull. Usei git pull e re-sincronizou. *git pull equivale a git fetch seguido de git merge*, segundo a [documentação](https://git-scm.com/docs/git-pull))

Talvez explicar a mesma coisa por outra fonte ajude a entender melhor. Pode tentar [a documentação do github sobre sincronizar arquivos locais](https://help.github.com/pt/github/using-git/getting-changes-from-a-remote-repository)

Editor online pode gerar perda de dados (trabalho). Comecei a editar o arquivo local e sincronizar o repositório remoto.

- git add <arquivo(s) que mudou>   (se vários arquivos mudaram, usar . em <arquivos(s) que mudou> pode ser prático)
- git commit -m "mensagem"
- git push


**nota** *git add .* é recursivo. Isto quer dizer que as sub-pastas e arquivos que elas contém são incluidos nos arquivos que serão sincronizados. Ele vai incluir todos os arquivos - inclusive os de recuperação dos editores, por exemplo README.md~. Isto pode ser evitado usando .gitignore [referência do git](https://git-scm.com/docs/gitignore) [referência do github](https://help.github.com/pt/github/using-git/ignoring-files).

Talvez explicar a mesma coisa por outra fonte ajude a entender melhor. Pode tentar [a documentação do github sobre sincronizar arquivos remotos](https://help.github.com/pt/github/using-git/pushing-commits-to-a-remote-repository)

Existe uma espécie de inconsistência lógica em torndo dos usos de *push*, *pull* e *merge*. Talvez fique mais claro para mim quando colocar em prática a possibilidade de usar vários repositórios remotos, várias versões e vários ambientes (o computador em que estou digitando os comandos é um servidor git ou é um cliente git), ... Por enquanto parece tudo mais ou menos igual, embora eu saiba que quando estou dando os comandos no cliente, *push* significa enviar do cliente para o servidor e que o servidor é o repositório remoto e *pull* significa trazer do servidor para o cliente.  

Simulei um cenário **simulação 1** que achei que daria um problema:

Enquanto editava este arquivo, entrei pelo navegador, editei, modifiquei e "comitei" este mesmo arquivo, simulando um outro colaborador que terminou de modificar o mesmo arquivo. Agi como padrão: *git add .*, *git commit -m...*, *git push*. 

O *push* foi negado:

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git add .
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git commit -m "teste push em cima de outro commit"
[master 124b3d9] teste push em cima de outro commit
 3 files changed, 1676 insertions(+), 3 deletions(-)
 create mode 100644 Documentos/sobreGit/README.md~
 create mode 100644 Documentos/sobreGit/git1.graphml
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git push
Username for 'https://github.com': fnakano
Password for 'https://fnakano@github.com': 
To https://github.com/camilabezerril/ImageCV.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/camilabezerril/ImageCV.git'
dica: Updates were rejected because the remote contains work that you do
dica: not have locally. This is usually caused by another repository pushing
dica: to the same ref. You may want to first integrate the remote changes
dica: (e.g., 'git pull ...') before pushing again.
dica: See the 'Note about fast-forwards' in 'git push --help' for details.
```
Segui a recomendação: fiz um *pull*:

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git pull
Username for 'https://github.com': fnakano
Password for 'https://fnakano@github.com': 
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
From https://github.com/camilabezerril/ImageCV
   22c78eb..313eea8  master     -> origin/master
Mesclagem automática de Documentos/sobreGit/README.md
CONFLITO (conteúdo): conflito de mesclagem em Documentos/sobreGit/README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Fiz um novo *pull* (*à posteriori* acho que era desnecessário, mas a mensagem foi esclarecedora):

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git pull
error: Pulling is not possible because you have unmerged files.
dica: Fix them up in the work tree, and then use 'git add/rm <file>'
dica: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
```
Aí que fui ver que o arquivo tinha sido modificado e que o conflito estava marcado:

![](screenshots/Captura%20de%20tela%20de%202020-05-28%2020-31-44.png)

Resolvi o conflito (coloquei as frases - uma vinda de um commit, outra da minha versão local - na ordem, removi as marcas)

![](screenshots/Captura%20de%20tela%20de%202020-05-28%2020-32-48.png)

Então fui pelo caminho do *pull*:

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git add .
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git commit -m "conflito entre outro commit e push sendo resolvido"
[master db7714a] conflito entre outro commit e push sendo resolvido
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git pull
fatal: unable to access 'https://github.com/camilabezerril/ImageCV.git/': Failed to connect to github.com port 443: Tempo esgotado para conexão
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git pull
Username for 'https://github.com': fnakano
Password for 'https://fnakano@github.com': 
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/camilabezerril/ImageCV.git/'
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git pull
Username for 'https://github.com': fnakano
Password for 'https://fnakano@github.com': 
Already up to date.
```

Achei estranho pois embora atualizado, o conteúdo do servidor não tinha atualizado. Tentei *add* e *commit* novamente e recebi a mensagem elucidativa:

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git add .
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git commit -m "parece não ter resolvido..."
No ramo master
Seu ramo está à frente de 'origin/master' por 2 submissões.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Agora o *push* resolveu:

```
fabio@fabio-13Z940-G-BK71P1:~/Documentos/Camila/CV$ git push
Username for 'https://github.com': fnakano
Password for 'https://fnakano@github.com': 
Counting objects: 12, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (12/12), 43.26 KiB | 2.40 MiB/s, done.
Total 12 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), completed with 1 local object.
To https://github.com/camilabezerril/ImageCV.git
   313eea8..db7714a  master -> master
```

### outros screenshots relacionados ao teste:

(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-29-03.png)
(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-30-08.png)
(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-36-30.png)
(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-43-24.png)
(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-44-10.png)
(screenshots/Captura%20de%20tela%20de%202020-05-28%2020-44-33.png)

## Referências sobre markdown

Markdown é uma linguagem simplificada (em relação a HTML) para construir páginas Web com formatação, links e imagens, o que não é possível em texto puro.

Muitos sites, inclusive github, usam markdown e **acrescentam funcionalidades a ela**, logo, o que funciona no markdown de alguns sites pode não funcionar em outros. [Redimensionar imagens](#Redimensionar-imagens) é uma dessas funcionalidades.

[básico](https://www.markdownguide.org/basic-syntax/)

[estendido](https://www.markdownguide.org/extended-syntax/)

[cheatsheet de outro usuário github](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

[Do próprio github para tabelas](https://help.github.com/pt/github/writing-on-github/organizing-information-with-tables)

### Redimensionar imagens

No github, em 2020, redimensiona-se imagens pelo uso do tag HTML [referência no Stackoverflow sobre github markdown](https://stackoverflow.com/questions/24383700/resize-image-in-the-wiki-of-github-using-markdown), [referência no projeto do pandoc](https://github.com/jgm/pandoc/issues/2554):

``` html
<img src="screenshots/Screenshot_20200614-104534.png" height="960" width="540">
```

Durante algum tempo, lá por 2013, era possível redimensionar de outras formas:

`![](https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png =250x250)`
[uupaa github gist](https://gist.github.com/uupaa/f77d2bcf4dc7a294d109)

No markdown usado em outros sites, o redimensionamento pode ser feito de outras formas.

[Discourse](https://meta.discourse.org/t/quick-image-resizing-and-markdown-image-dimensions/66812)

[Stackoverflow](https://stackoverflow.com/questions/14675913/changing-image-size-in-markdown)

## Fluxogramas

![](./git2.png)


## Outras referências


[gist-blackfalcon basic tutorial](https://gist.github.com/blackfalcon/8428401)

[cedrotech1](https://blog.cedrotech.com/git-o-minimo-que-voce-precisa-saber-para-trabalhar-em-equipe/)

[cedrotech2](https://blog.cedrotech.com/git-o-minimo-que-voce-precisa-saber-para-trabalhar-em-equipe-parte-2/)

## 2020-12-03-114552

Uma utilidade imaginada mas inesperada.

Hoje estou trabalhando em uma forma de sistematizar a elaboração de planos de atividades e relatórios. O ponto de partida são especificações de planos e de relatórios.

Eu fiz isso para Computação Física (CFA), faz um tempo, mas substituí por documentos e processos mais simples, considerando que é uma disciplina, o tempo é limitado, tenho um controle mais efetivo sobre o escopo, que pode ser bastante específico/limitado, sem perder a característica da disciplina. Isto permite a simplificação.

Porém, agora, preciso dos documentos e processos na forma completa, e **sobrescrevi** parte dos documentos. Em situações semelhantes, eu precisaria refazer essa parte - repetição de trabalho.

Depois de me castigar um pouco, lembrei que a versão anterior do documento deve estar armazenada no Git.

O projeto de CFA é um repositório público, acessível pelo site Github, que tem uma interface com muitas funcionalidades, inclusive consultar o histórico de *commits*. Acessei o histórico, achei a data do *commit* e o hash do commit (pois não dei nenhum nome específico a ele): `cf0a7eb78f`. A mensagem do commit acelerou a busca substancialmente. No repositório local, fiz checkout da versão anterior (para isso, antes, tive de *comitar* algumas modificações que eu tinha feito no repositório local), localizei o arquivo que eu queria, copiei para uma outra pasta e voltei para a versão mais recente.

**Resultado:** Economia de tempo (pois não precisei repetir trabalho) e economia de sofrimento (pois quando preciso repetir trabalho fico remoendo auto-avaliações ruins e isso é emocionalmente desgastante).

**Recomendação:** Manter versões, seja manualmente, seja com auxílio de ferramentas. Pois nunca se sabe quando um documento antigo, ou parte dele, será útil novamente. Como isso certamente acontecerá, seja por acaso, seja por conveniência, em algum momento poupará trabalho e desgaste emocional.

<pre><font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git checkout cf0a7eb78f
error: Your local changes to the following files would be overwritten by checkout:
	componentes/controladores/ESP/README.md
Please commit your changes or stash them before you switch branches.
Aborting
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git add .
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git commit -m &quot;atualizações anteriores a hoje, que estou comitando para conseguir recuperar a definição de plano de atividades que pretendo usar.&quot;
[master 00761c5] atualizações anteriores a hoje, que estou comitando para conseguir recuperar a definição de plano de atividades que pretendo usar.
 1 file changed, 14 insertions(+), 14 deletions(-)
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git push
Username for &apos;https://github.com&apos;: fnakano
Password for &apos;https://fnakano@github.com&apos;: 
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 656 bytes | 328.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), completed with 4 local objects.
To https://github.com/FNakano/CFA.git
   cd173ca..00761c5  master -&gt; master
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git checkout cf0a7eb78f
Note: switching to &apos;cf0a7eb78f&apos;.

You are in &apos;detached HEAD&apos; state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c &lt;new-branch-name&gt;

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at cf0a7eb melhorei-quase terminei-os modelos de documentação e as instruções.
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ B

<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA/modelos</b></font>$ cp README.md ~/Downloads/
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA/modelos</b></font>$ cd ..
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ cd ..
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git</b></font>$ cd CFA/
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ git checkout master
Previous HEAD position was cf0a7eb melhorei-quase terminei-os modelos de documentação e as instruções.
Switched to branch &apos;master&apos;
Your branch is up to date with &apos;origin/master&apos;.
<font color="#859900"><b>fabio@fabio-13Z940-G-BK71P1</b></font>:<font color="#268BD2"><b>~/Documentos/git/CFA</b></font>$ 
</pre>

## 2021-01-26-112652

Como clonar um repositório em uma pasta de nome diferente do nome da pasta do repositório?

Contexto:

Quando faço: `git clone https://github.com/FNakano/MeuUsoDeGit.git`, o git cria a pasta local `MeuUsoDeGit` e copia o conteúdo do repositório para a pasta. Como clonar para uma pasta de nome diferente, por exemplo: `ComoFNakanoUsaGit`?

Resposta: use  `git clone https://github.com/FNakano/MeuUsoDeGit.git ComoFNakanoUsaGit`.

Mais contexto:

Usei isto quando quis fazer uma nova cópia de um exemplo do Heroku. Tinha feito a primeira para testar o exemplo e queria conservar como estava. Simultaneamente, queria outra cópia para modificar e testar.

Referência: <https://stackoverflow.com/questions/8570636/change-name-of-folder-when-cloning-from-github>

## 2021-01-26-122757
## 2021-01-26-134847

Recebi e-mail do github dizendo que [autenticação por senha não será mais válida a partir de 13.08.2021](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/). 

O que fazer?

O github recomenda [autenticar por token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token#using-a-token-on-the-command-line). Para mim, o problema é que não vou decorar um token, então teria que fazer copy-paste, o que é uma operação a mais, e uma que eu não desejo fazer.

Mais perto da data vejo o que fazer.

## 2021-03-10-115211

### Usando `pull requests`.

Em um desenvolvimento colaborativo, há modificações que gostaríamos que alguém revisasse antes de incluir no ramo principal. A solução para isto é criar um ramo diferente do principal (com `git checkout -b <novo_ramo>`), fazer as modificações, adicionar (com `git add .`), *comitar* (com git commit ...), criar o ramo no repositório remoto (com `git push --set-upstream origin <novo_ramo>`, ou, se já estiver criado, atualizar com `git push <novo_ramo>`), entrar no github e fazer `pull request`, ou PR. Maiores detalhes em: https://opensource.com/article/19/7/create-pull-request-github.

Quando faz `push <novo_ramo>` sem ter criado o ramo, ocorre um erro - veja a [captura da tela](screenshots/Captura%20de%20tela%20de%202021-03-10%2011-14-00.png). 

A outra pessoa (o revisor), se concordar com as modificações, vai fundir (merge) os ramos, senão segue uma negociação que pode ser feita através do github.

PR é uma funcionalidade do github.

Ainda não vi o que acontece depois que o revisor faz merge (será que o novo ramo é fechado? o que acontece na minha cópia local? Eu posso/consigo atualizar o novo ramo? Devo abandoná-lo, fazer checkout do ramo principal e fazer `pull`?,...). Talvez esta referência ajude: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging.


### Incluir fórmulas LaTeX no markdown  

Se estiver funcionando, primeiro vem a fórmula renderizada e depois o código-fonte. Nos blocos, indicar `math` como linguagem, sem espaço entre os três backquotes e o `math`.

Depois deste texto, na mesma linha, deve aparecer uma fórmula: $`(\forall x)(Green(x))`$

```
$`(\forall x)(Green(x))`$
```

```math

\begin{bmatrix} 
  a & b \\
  12 & \gamma 
\end{bmatrix}
```

```

\begin{bmatrix} 
  a & b \\
  12 & \gamma 
\end{bmatrix}
```

```math

\sum_{i=0}^{15} \Theta_{mm}(x)*\frac{a}{\lambda+\frac{b}{c}}e^{2*\omega}

```

```

\sum_{i=0}^{15} \Theta_{mm}(x)*\frac{a}{\lambda+\frac{b}{c}}e^{2*\omega}

```

**... e não é que no github, em 2021-03-10, não funciona!**... instalei um plugin no navegador Firefox que, quando abro um markdown, faz a renderização, inclusive das fórmulas: ´GitLab Markdown Viewer:Renders markdown files in GitLab style.´ Instalei um outro que renderiza diagramas a partir do código-fonte deles: `Markdown Diagrams:Render PlantUML, Mermaid and others graph/diagrams on webpages.`. São úteis para renderizar e imprimir documentos...

A [referência crucial](https://stackoverflow.com/questions/11256433/how-to-show-math-equations-in-general-githubs-markdownnot-githubs-blog) veio no stackoverflow.

Entretanto, parece que não há consenso. [Veja este link](https://github.com/github/markup/issues/1294).

As referências para formatos e símbolos é:

- https://katex.org/docs/supported.html




## Comentários

(comentário: este editor de markdown (editor online do github) é bem legal - pelo menos o bold e o itálico ele formata WYSIWYG).

(comentário 2: a palavra *é* pode ser usada para dar a definição de dicionário de algo ou para dar a percepção de quem escreve sobre aquilo que ele está descrevendo, além de outros usos. Fique atento!)

(comentário 3: minha internet passou o dia instável. Usar o editor online do github nessa condição pode levar a perda de dados pois se não houver conexão, o botão *commit changes* falha e o que foi digitado no editor é perdido.)

(comentário 4: quando tentei clonar da primeira vez, criei o diretório e dei um **git init**. Se ficar só por isso, cria-se um novo repositório. Vendo [esta postagem](https://stackoverflow.com/questions/651038/how-do-you-clone-a-git-repository-into-a-specific-folder) entendi que eu poderia "corrigir" fazendo: 
git remote add origin PATH/TO/REPO; git fetch; git checkout -t origin/master. Não tentei, mas fica a dica - uma hora eu tento).

(comentário 5: apagando o .git e seu conteúdo, removo o diretório do git. [link](https://stackoverflow.com/questions/1514054/how-do-i-delete-a-local-repository-in-git))

(comentário 6: hiperlinks não podem ter espaços [referência](https://stackoverflow.com/questions/13051428/how-to-display-images-in-markdown-files-on-github). Não adianta colocar dentro de doublequotes. Substituir por %20)
## registro da simulação 1

Modifico aqui para simular o commit de um outro colaborador.

Fazendo de conta que não sei que outro colaborador fez um commit durante a minha edição, vou tentar um push...

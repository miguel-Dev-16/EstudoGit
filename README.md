#                                 :man_student: Git

O é um software para rastrear alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte para fluxo de trabalho não lineares distribuídos.

[TOC]



## Conceitos básicos do git.

1. Repositório: essencialmente é um repositório chamado .git dentro do seu projeto. Geralmente está pasta fica oculta, este repositório rastrear todas as mudanças feitas no seu projeto.
2. Commit: O ideal é fazer cada commit ao terminar uma tarefa, por que ele é um marco histórico, pois se de commits de qualquer coisa vai ficar com vários marcos históricos e isso não é uma boa prática. Exemplo: Adicionado a forma de pagamento, Adicionado integração com o WhatsApp.

###   :fist_right: Estágio dos commits: 

```text
* Modified : arquivo alterado.
* Staging: arquivo prontos para serem enviados. 
* Commited: arquivos enviados, pronto para o push.
```

## :detective: Comandos do Git:

### Configurando usuário no git.

```bash
git --version  -> exibe a versão do  git
Obs: para sair de tela travada git só apertar a letra q.

git config --global --list -> exibe o usuario e email cadastrado no git.
git config --global user.name "lorem"
git config --global user.email "lorem@gmail.com"
```

### Criar Repositório.

```bash
git init -> inicializa o repositorio
```

### Git

```bash
git checkout  -> coloca o comando depois a branch que quer editar e depois o nome da branch exemplo: git checkout master novaBranch. (Renomeia uma branch).

git status -> mostra o status do repositorio.
git add . -> adiciona todos os arquivos.
git add index.html -> adiciona arquivo especifico.
git rm --cached nomeArquivo -> remove da area de stage.
git commit -m "" -> aqui comita o arquivo e você pode passar uma mensagem dentro das aspas.
git log -> ele pucha o historico completo dos commites
git log --oneline --> ele pucha o historico de forma condensada, resumida.
git add . && git commit -m "adicionando index" -> podemos colocar 2 comandos ou mais na mesma linha usando o &&.
```

### Revertendo Commits:

3 formas de reverter commit.

* checkout -> Forma mais segura, você navega entre cada linha do tempo do commit, podendo ir para os commits anteriores e depois voltar para o commit atual.
* revert -> É um pouco não seguro pois ele altera o histórico do seu git. E isso pode ser um problema em uma determinada situação. Ele cria um novo commit sem as alterações que foram revertidas.
* Reseta até um determinado commit, exemplo você tem o commit 1 | 2 |3 onde o commit 3 é o mais atual e seu chefe quer resetar e fica no commit 1, ai o commit 2 e 3 são apagados e ai já era.

#### Exemplos:

##### checkout:

```bash
git checkout d87ef7e -> Você coloca o codigo do commite e ele vai para o commite selecionado, se quiser voltar para o commit atual que é o ultimo ponto pode da um git checkout main, que é o nome da sua branch.
```

##### revert:

```bash
git revert d87ef7e -> reverte as alterações e o git ele faz um commit de reversão, e mantem a linha do tempo que foi revertida.
```

##### reset:

```bash
git reset d87ef7e -> ele apaga tudo e fica so o que esta neste commit.

git reset d87ef7e --hard -> ai ele apaga até o historico futuro. São arquivos que estão no modified que nem entrou no stage ainda.

Neste caso sem possibilidade de recuperação usando o git reset.
```

## :no_entry_sign: Git ignore

Ele serve para ignorar os arquivos que não queremos que o git rastreie pois tem dados sensíveis como senha do servidor ou do sistema como por exemplo.

exemplo: vou criar uma pasta .env onde vai ter meus arquivos que não quero enviar e vou criar a pasta .gitignore todo nome de arquivo que estiver dentro desta pasta vai ser ignorado.

```bash
//IGNORANDO ARQUIVOS
criando arquivo ignore
touch .gitignore
touch .env

dentro do arquivo gitignore escreve o arquivo que é para ser ignorado
.env

// ignorando pastas

```

## :trident:Branch:

Criamos uma ramificação e uma copia da branch em que queremos, é criado uma linha do tempo paralela a linha do tempo original.

```bash
git branch -> lista todas as branch
git branch nomeBranch -> cria uma nova branch ele ja cria a branch no repositorio remoto quando da o push
git branch -b nomeBranch -> cria uma nova branch e ja faz o checkout automatico
git checkout nomeBranch -> muda de branch
git branch -D nomeDaBranch -> ai você deleta a branch sem precisar de merge mesmo se tiver commites la dentro.
git branch -d nomeDaBranch -> se você tiver commit la dentro ai ele pede primeiro para fazer o merge e depois exclu
```



## Merge:

É você fundir os branchs e para isso você precisa ir para a branch de destino no caso o main que eu quero fundo para ele. E mergiar.

```bash
git checkout se eu der um tab no teclado ele me mostra as opcões
git merge nomeBranch -> ele faz o merge.
```

Obs: Sair de tela Bash.

sair de tela bash:

:q -> dois pontos + q sai da tela

q -> sai da tela.

quando não for um é o outro.

## Resolvendo conflitos.

Se a pessoa trabalhar no mesmo arquivo ou alguém alterar um arquivo que você está mexendo e da um merge, ai você ajeita e depois da um commit. o próprio editor de texto ou ide mostra os conflitos e atalhos para aceitar qual arquivo vai mergear.

Ou seja podemos resolver na mão os conflitos ou pelo próprio editor.

## Conectar projeto ao Git-hub:

podemos fazer desta forma para subir o projeto quando criamos ele na nossa maquina e depois temos que criar ele no git hub pega a chave e lincar com o git, ele vai pedir autorização via token ou via e-mail ou via código:

Primeiro crie o projeto no git, depois copie a sua chave ssh

- git remote add origin -> sua chave, este remote é usado na primeira vez para criar um apelido depois pode usar git origin e sua chave.
- git remote -v -> ele mostra os apelidos criados para conexão com o git-hub
- git push origin nomeBranch -> ai ele sobe para o git hub.
- git pull origin nomeBranch -> puxa as atualizações da branch especificada.
- git clone chave do projeto -> ele clona o projeto e ja cria o origin.

```bash
git push https://github.com/MigDevAnalista/siteTeste.git main -> aqui você sobe o projeto usando o comando git push caminho do projeto e a branch.

para não colocar direto o comando acima podemos criar uma variável exemplo:
git remote add origin https://github.com/MigDevAnalista/siteTeste.git -> aqui você configura um apelido chamado origin que vai está lincado com seu endereço.

depois só é fazer desta forma 
git push origin main -> ai você esolhe a branch que você quer subir.
git pull origin nomeBranch -> puxa as atualizações da branch especificada
```

## Clone 

Criando o repositório no git hub nas nuvens você copia o endereço ou chave do seu repositório e depois clona ele para sua maquina.

```bash
//dentro da pasta onde quer baixar abre o editor podendo ser o git bash ou o prompt cmd e clona o projeto la, dentro desta pasta não precisa ter o git init tem que ser uma pasta sem ser inicializado o git para clonar o projeto!

//desta forma ele clona com o mesmo nome de pasta que está no git.
git clone https://github.com/MigDevAnalista/siteTeste.git

//desta outra forma você pode colocar outro nome na pasta que você queira, colocando depois da chave o nome que você queira para a pasta.
git clone https://github.com/MigDevAnalista/siteTeste.git siteTreina
```

## FORK

Fazendo o fork de um repositório contribuindo com projetos open source.

1. Primeiro vc vai no projeto de uma pessoa que você queira fazer o fork
2. Você clica no símbolo do fork e ele já vai puxar o projeto para o seu git hub.
3. Porem a diferença dele para o clonar direto é que ele faz um link direto do git hub para o outro
4. E de pois você clona para seu git local.
5. Faz as suas melhorias
6. depois subo as alterações
7. depois se estiver tudo ok, você faz o create pull request e ele ja faz direto para o criador.
8. ai espera o criador aprovar ou não.

Obs. o pull request você faz diretamente no git hub e não no git.

## Issues

Issues é um problema identificado e não sabe a resposta. Ainda não achou a solução.

o dono do repositorio pode responder a issue eu posso fechar e eu posso da lock para não ter mais comentários na issue.Pode colocar imagem também.

as outras pessoas podem comentar a issue! colocar imagem.

ver o que é pinar uma issue.

```text
Para colocar Emogi
:nomeEmoji: coloca 2 pontos e o nome do emoje
link do repositorio com varios emojsss:https://github.com/ikatyang/emoji-cheat-sheet

se você quiser colocar um emoji no titulo da issue tem que ir no site:https://emojipedia.org/
depois voce escolhe o emoji clica em copy e cola la no titulo da sua issue.

na issue eu posso fazer um r eplay vai nos 3 pontinhos que fica ao lado da postagem da pessoa e clica Quote reply, ai você pode comentar marcando a pessoa.
```

## Comandos CMD:

```cmd
------------------comandos cmd -----------------------------------
ls -> lista os arquivos
dir -> também lista os arquivos
clear -> limpa a tela
mkdir nome_do_diretorio -> ele cria o diretorio
cd -> eu entro nas pastas
cd .. -> eu saio da pasta.
touch -> comando para criar arquivos. Exemplo: touch aula.txt
rm -> remove o arquivo exemplo: rm aula.txt
rmdir -> remove a pasta exemplo: rmdir nomeDiretorio
rm -rf nomePasta -> para excluir uma pasta que não esta vazia.
mv -> você move a pasta para o mesmo local e pode renomear ela ex: mv projet-02 projeto-2, ou seja ele serve para renomear
ls -a -> exibe arquivos ocultos
cd ../pasta2 -> neste comando você sai da pasta 1 e ja entra na pasta 2.
------------------ comando NANO --------------
nano index.html -> você entra dentro do arquivo e pode editar.
Salvar o arquivo: Ctrl + O
Sair do nano: Ctrl + X
Cortar uma linha: Ctrl + K
Colar uma linha: Ctrl + U
Buscar por texto: Ctrl + W
cat nomeDoArquivo -> exibe o conteúdo do arquivo.

------------sair de tela bash: -----------------------------------
:q -> dois pontos + q sai da tela
q -> sai da tela.
quando não for um é o outro.
```


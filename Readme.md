# Github

**Controle de versão**: responsavel por versionar os arquivos do seu projeto, facilitando com que você não precise fazer esses versionamentos manualmente. Os outros sistemas trabalham com as diferenças dos arquivos, já o Git trabalha com os estados dos arquivos.

**Criador do Git**: Linus Torvalds.(Mesmo criador do Linux)

**Vantangens do Git**: velocidade, design simples, suporte robusto a desenvolvimento não linear(milhares de branches paralelos), totalmente distribuído, capaz de lidar efecientemente com grandes projetos como o kernel do Linux.

**O que é o Github**: serviço de Web compartilhado para projetos que utilizam o Git para versionamento.

**Git / Github**: Git não é o mesmo que Github. o Git é o sistema de controle de versão, o Github é somente um local na Web onde você consegue colocar os seus projetos versionados em Git.

**Configuração inicial do Git**:
``` 
git config --global user.name "Leonardo May" 

git config --global user.email "leonardojcmay@hotmail.com"
```

Para saber o nome do usúario que você configurou e o e-mail tambem é possivel, somente alterando o name por email:
```
git config user.name
```

Para mostrar uma lista de várias configurações do seu Git:
```
git config --list
```

**CTRL+L** : comando para limpar o Gitbash

**Inicializando repositório**:
<br>Comando para inicializar o Git na pasta:
```
git init
```

Mostrar os arquivos que contém na pasta:
```
ls -la
```

Acessando o arquivo .git:
```
cd .git/
```

Listando arquivos que contém no .git:
```
ls
```

Voltando para pasta anterior:
```
cd ..
```

Comando abaixo serve para reporta como esta o repositório no momento:
```
git status
```

Adicionando o arquivo que foi criado manualmente ao Git, após isso o Git já irá reconhecer este novo arquivo:
```
git add Readme.md
```

Adicionando todos arquivos:
```
git add .
```

Comando para commitar:
```
git commit -m "Add Readme.md"
```

Comando para mostrar todas alterações que foram feitas no arquivo:
```
git log
```

Mostrande de qual Branch foi para qual Branch, se teve Merge... :
```
git log --decorate
```

Filtrando pelo autor:
```
git log --author="Leo"
```

Mostra em ordem alfabetica o nome dos autores, quantidade de commites e quais foram:
```
git shortlog
```

Mostrando só a quantidade de commites e a pessoa que commitou:
```
git shortlog -sn
```

Mostrando as mudanças que ocorreram:
```
git log --graph
```

Coletando informação de toda alteração de acordo com a hash:
```
git show 67da256d22f7046ac7455dfad1ba0f921d6ed286
```

Comando para ver as mudanças antes mesmo de fazer o commit:
```
git diff
```

Dizer somente o nome do arquivo que foi modificado:
```
git diff --name-only
```

Para dar commit em um arquivo que já existe:
```
git commit -am "Editei Readme.md"
```

Como resetar um arquivo caso tenha feito algo errado:
```
git checkout Readme.md
```

Como resetar um arquivo caso tenha feito já o add:
```
git reset HEAD Readme.md
```

após isto rodar o comando abaixo
```
git checkout Readme.md
```

Como resetar um arquivo pelo hash caso tenha feito já o commit:
<br>soft: pega sempre o hash do último commit que ficou certo, após isso, o arquivo errado irá voltar para a "fila" de add.
```
git reset --soft 67da256d22f7046ac7455dfad1ba0f921d6ed286
```

mixed: pega sempre o hash do último commit que ficou certo,  após isso, o arquivo errado irá voltar para a "fila" de add, irá mostrar ainda a mudança que havia sido feito.
```
git reset --mixed 67da256d22f7046ac7455dfad1ba0f921d6ed286
```

hard: pega sempre o hash do último commit que ficou certo, exclui todo o commit que havi sido feito errado.
```
git reset --hard 67da256d22f7046ac7455dfad1ba0f921d6ed286
```

Jogando os arquivos para o Github, direcionando para a pasta ja criada na Web:
```
git remote add origin https://github.com/leonardojcmay/github.git
```

Pega os dados do Branch master e vai para o origin(Github):
```
git push -u origin master
```

add > commit > push

**Clonando repositório**:
<br>Copiar link do repósitorio e rodar o comando:
```
git clone linkRepositorio
```

**O que é fork**: você pega um projeto que não é seu e faz uma cópia para você. Exemplo: quando contém algum repositório que esta faltando alguma modificação, documentação, código... e você quer contribuir. É utilizado quando você quer alterar um repositório de outro usuário.
Ao clicar no botão fork, terá que direcionar para uma organização.

**O que é um branch**: é um ponteiro móvel que leva a um commit.

**Vantangens**: poder modificar sem alterar o local principal(master), facilmente "desligável", múltiplas pessoas trabalhando, evita conflitos.

**Criando um branch**:
```
git checkout -b teste
```

Mostrar todos os branchs que o repositório contém:
```
git branch
```

Acessando outro branch:
```
git checkout master
```

Apagar um branch:
```
git branch -D teste
```

**O que é merge**: une os branchs. Cria um commit novo para juntar as diferenças.
<br>Vantagem: operação não destrutiva.
<br>Desvantagem: commit extra, histórico poluído.

![merge](https://raw.githubusercontent.com/leonardojcmay/github/master/img/merge.JPG)

```
git merge nomeDoBranch

```

**O que é rebase**: une os branchs. Joga as diferenças para o início da fila.
<br>Vantagem: evita commits extras, histórico linear
<br>Desvantagem: perde ordem cronológica

![rebase](https://raw.githubusercontent.com/leonardojcmay/github/master/img/rebase.JPG)

```
git rebase nomeDoBranch
```

**.gitignore**: é um arquivo no repositório que dentro deste arquivo você descreve informações que não quer utilizar. É possivel informar todos arquivos com padrão de extensão e também informar somente o único arquivo que não deseja utilizar.
<br>Documentação: https://git-scm.com/docs/gitignore
<br>Templates: https://github.com/github/gitignore

**Git stash**: responsável por guardar modificações que ainda não foram commitadas.
```
git stash
```

***Aplicar***:
```
git stash apply
```

***Listar***:
```
git stash list
```

***Limpar***:
```
git stash clear
```

**Utilizando alias**:
<br>Exemplo:
```
git status

git config --global alias.nomeAtalho status

git nomeAtalho
```

**Versionamento com Tags**:
```
git tag -a 1.0.0 -m "Readme finalizado"

git push origin master --tags
```

**Git Revert**: pega o hash do commit que esta errado. Ele apaga as informações que foram feitas erradas, mas mantém tudo no histórico dos commits.
```
git revert 67da256d22f7046ac7455dfad1ba0f921d6ed286
```

**Apagando tags e branches remotos**:
```
git push origin : nomeTagParaApagar

git push origin : nomeBrachParaApagar
```

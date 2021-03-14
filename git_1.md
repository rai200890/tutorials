# Git

## Ferramentas de controle de versão

### Centralizada

- Subversion (SVN)

### Distribuída

- Mercurial
- Git

### Git vs SVN

### Instalação

#### Debian

```shell
sudo apt update && apt install git-all
```

#### Fedora

```shell
sudo dnf install git
```

```shell
yum install git
```

#### Manjaro

```shell
pacman -S git
```

#### OSX

```shell
brew install git
```

### Configuração

```shell
git config --global user.name "Paola Bracho" ## Configura nome de usuário

git config --global user.email "paola.bracho@ceramica.bracho.com" ### Configura email de usuário

git config core.editor vim ### configura editor padrão
```

### Protocolos

- HTTPS
- SSH(Recomendado)

Muitas organizações bloqueiam HTTPs, só permitem SSH 

### Criando um novo projeto

```shell
mkdir nazare_tedesco # cria diretório com novo projeto
git init # inicia repositório git
git remote add origin git@github.com:rai200890/nazare_tedesco.git # adiciona repositório remoto para recuperar/enviar mudanças
git remote -v # lista os repositórios remotos configurados
git remote prune original # remove repositório remoto
```

### Copiando um projeto existente

```shell
git clone https://github.com/rai200890/nazare_tedesco.git # copia repositório existente
```

#### Como funciona

Cada arquivo no sua área de trabalho pode estar em 2 estados

- tracked: arquivos que estavam na última versão salva ou que já foram selecionados para irem na próxima versão(staged), adicionando-os a área de staging. Em resumo aqueles que o git já sabe que existem e acompanha mudanças
- untracked: arquivos na sua área de trabalho que ainda não foram submetidos para a próxima versão, isto é, são arquivos que ainda não estão no index. 

### Adicionando mudanças

```shell
git add farofa.md # adiciona arquivo na sua área de trabalho a área de staging, preparando-o para ser enviados na próxima versão 
git add farofa
git add *.md # adicionda todos os arquivos com extensão .md a área de staging
git add . # adiciona todas os arquivos no diretório corrente a área de staging
```

### Verificando mudanças na área de staging

```shell
git status
```

#### Fluxo de trabalho

```

[Área de trabalho] -> [Index - Área de staging]

``` 

#### Registrando mudanças

```shell
git commit -m "feat: Add first commit" # Cria uma nova versão incluindo as mudanças adicionadas a área de staging, incluindo uma mensagem descrevendo o que foi alterado
```

Commit - Mudança (identificada por um hash SHA-1)

Dessa forma é possível navegar entre as versões, visualizar mudanças e restaurar para uma versão do código estável, por exemplo.

[Área de trabalho] -> [Index - Área de staging] -> [Repositório Local]

### Removendo mudanças

```sh
git rm farofa # remove arquivo da área de trabalho e da área de staging, e para de acompanhar mudanças no mesmo
git rm farofa --staged # remove arquivo somente da área de staging, mantendo-o na sua área da trabalho
```

### Renomeando arquivos

```sh
git mv farofa
```

equivalente a:

```sh
mv /farofa/com_ovo com_ovo
git add com_ovo
```

### Enviando mudanças para repositório remoto

```shell
git push # envia commits na sua área de trabalho para o repositório remoto
git push -u origin master # por padrão envia mudanças para o repositório remoto para um branch de mesmo nome do que localmente

git push --force-with-lease 
git push -f # envia e sobrescreve obrigatoriamente mudanças no seu repositório remoto, use com cautela pois pode  
```

#### Fluxo de trabalho

```

[Área de trabalho] -> [Index - Área de staging] -> [Repositório Local] -> [Repositório remoto] 

```

### Recuperando mudanças do repositório remoto

```shell
git fetch origin # somente baixa atualizações do repositório remoto origin para o repositório local 
git fetch --all # somente baixa atualizações de todos os repositórios remotos para o repositório local
```


```
                    A---B---C master on origin
                    /
               D---E---F---G master
                   ^
                   origin/master
```

Última versão no repositório local: G

Última versão no repositório remoto: C

```shell
git pull origin master # baixa atualizações e incorpora mudanças da branch master do repositório remoto origin para a branch master no repositório local 
```

```
                    A---B---C origin/master
                    /         \
               D---E---F---G---H master
```

O commit H é resultando do merge

Se existir mudanças tanto no repositório local quanto remoto, o merge é cancelado automaticamente.

### Resolvendo os conflitos

Para resolver essa situação armazene as suas mudanças localmente usando os seguintes comandos:

```shell
git add . # adiciona os arquivos desejados
git stash # armazene as mudanças na área de stash
git pull # baixa atualizações e integra mudanças do repositório remoto no repositório local 
git stash pop # aplica mudanças armazenadas no repositório local
```

#### Arquivo em conflito

```html
<html>
  <head>
  </head>
  <body>
<<<<<<< HEAD
    <h1>Hi!</h1>
=======
    <h1>Hello!</h1>
>>>>>>> master
  </body>
</html>
```

#### Arquivo atualizado

```html
<html>
  <head>
  </head>
  <body>
    <h1>Hi!</h1>
  </body>
</html>
```

Em seguida registre a nova versão:

```shell
git commit
```

#### Fluxo de trabalho

```

[Área de stash] -> [Área de trabalho] -> [Index - Área de staging] -> [Repositório Local] -> [Repositório remoto] 

```

### Trabalhando com branches

```shell
git push -u <remote_name> <local_branch_name>:<corresponding_remote_branch_name> # configura para qual repositório remoto e branch as mudanças vão ser enviadas 
```

## Referências

Pro Git: https://git-scm.com/book/en/v2

Set default upstream for git repo: https://brycehipp.tech/git-set-default-upstream/

## Cursos

Hello Git: https://www.codecademy.com/courses/learn-git/lessons/git-workflow/exercises/hello-git

Git How-To: https://githowto.com/

Learn Git Branching: https://learngitbranching.js.org/?locale=pt_BR

## Links úteis

Git Cheatlist(Interativo):

https://ndpsoftware.com/git-cheatsheet.html

Github Cheatlist:

https://training.github.com/downloads/github-git-cheat-sheet/

How to Write a Good Commit Message:

https://chris.beams.io/posts/git-commit/




# Seja um Ninja do GIT!

Esse reposítorio serve como uma base de conhecimentos e experiências que já presenciei, guardo aqui desde comandos básicos até comandos um poucos mais elaborados, que por muito tempo foram grandes impedimentos para o meu desenvolvimento, espero de alguma forma contribuir com o seu desenvolvimento pessoal/profissional através desse materal.

![Seja um Ninja do GIT](https://blog.da2k.com.br/uploads/2015/07/banner-git-e-github-ninja.jpg)

#### Conteúdo
- [Criar nova branch](#criar-nova-branch)
- [Listar branchs de um projeto](#listar-branchs-de-um-projeto)
- [Trocar de branch](#trocar-de-branch)
- [Adicionar arquivos](#adicionar-arquivos)
- [Remover um arquivo](#remover-um-arquivo)
- [Remover arquivos não rastreados](#remover-arquivos-nao-rastreados)
- [Realizar um commit](#realizar-um-commit)
- [Realizar um commit em branco](#realizar-um-commit-em-branco)
- [Verificar status das alterações](#verificar-status-das-alteracoes)
- [Enviar um commit para uma branch especifica](#enviar-um-commit-para-uma-branch-especifica)
- [Remover arquivos de um commit](#remover-arquivos-de-um-commit)
- [Fazer cópia de uma branch](#fazer-copia-de-uma-branch)
- [Corrigir conflitos entre branchs](#corrigir-conflitos-entre-branchs)
- [Unir commits em um só (Método para branchs sem Merge)](#criar-nova-branch)
- [Unir commits em um só (Método para branchs com Merge)](#criar-nova-branch)
- [Puxar conflitos](#puxar-conflitos)
- [Atualizar branch atual](#atualizar-branch-atual)
- [Atualizar repositório completo](#atualizar-repositorio-completo)
- [Arquivar alterações](#arquivar-alterações)
- [Desarquivar alterações](#desarquivar-alterações)

#### Criar nova branch
Cria uma nova branch local.
```sh
git branch -m <tipo>/<titulo>
```

#### Listar branchs de um projeto
Lista todas as branchs de um determinado projeto que estão disponíveis no seu ambiente local.
```sh
git branch
```

#### Trocar de branch
Troca de branch dentro de um projeto.
```sh
git checkout <nome da branch>
```

#### Adicionar arquivos
Adiciona alterações realizadas nos arquivos ao commit que será enviado.
```sh
git add . (Adicionar todos os arquivos modificados)
git add <caminho do arquivo> (Adicionar um arquivo específico)
```

#### Remover um arquivo
Remove as alterações realizadas nos arquivos, e evita que sejam enviadas no commit.
```sh
git restore . (Remover todos os arquivos modificados)
git restore <caminho do arquivo> (Remover um arquivo específico)
```

#### Remover arquivos não rastreados
Remove as alterações não rastreadas, e evita que sejam enviadas no commit.
```sh
git clean -fd
```

#### Realizar um commit
Salva as alteracões realizadas no repositório local. Uma dica importante e sempre descrever o maior número de detalhes possíveis no título do seu commit, para facilitar o entendimento do que foi desenvolvido.
```sh
git commit -m "<titulo>"
```

#### Realizar um commit em branco
Cria um commit em branco, sem alterações.
```sh
git commit --allow-empty -m "<titulo>"
```
#### Verificar status das alterações
Verifica o status das alterações realizadas nos arquivos.
```sh
git status
```

#### Enviar um commit para uma branch especifica
Envia as alterações realizadas, do repositório local para o repositório remoto.
```sh
git push origin <nome da branch>
```

#### Remover arquivos de um commit
Remove arquivos enviados no commit de uma branch remota, apenas caso não tenha merge.
```sh
git reset —soft HEAD~<quantidade de commits>
git status
git restore <arquivo>
git status
git commit -m “<alterações realizadas>”
git status
gitk
```

#### Fazer cópia de uma branch
Cópia a branch atual para uma nova, geralmente utilizado para realizar backups das alterações.
```sh
git checkout -b <nome da branch>-backup (Melhor maneira para se fazer o backup de uma branch e manter sua referência)
git checkout -b <novo nome da branch> (Copiando branch atual e dando um novo nome para ela)
```

#### Corrigir conflitos entre branchs
Corrige conflitos de arquivos em uma branch.
```sh
git checkout <nome da branch principal>
git pull
git checkout <nome da branch>
git merge <nome da branch principal>
```

#### Unir commits em um só (Método para branchs sem Merge)
Uni diversos commits em um só.
```sh
git reset --soft HEAD~<quantidade de commits>
git commit -m “<titulo do commit>”
git push -f origin <nome da branch>
```

#### Unir commits em um só (Método para branchs com Merge)
Uni diversos commits em um só.
```sh
git checkout -b <nome da branch>-backup
git reset —soft HEAD-<numero de commits>
git commit -m “<alterações realizadas>”
git checkout <nome da branch principal>
git pull
git checkout <nome da branch>
git rebase <nome da branch principal>
git status
git add .
git rebase --continue
git push -f origin <nome da branch>
```

#### Puxar e resolver conflitos
Puxa conflitos da branch, e permite que sejam resolvidos, sem que seja necessário dar um merge.
```sh
git checkout -b <nome da branch>-backup
git checkout <nome da branch principal>
git pull origin <nome da branch principal>
git checkout <nome da branch>
git rebase <nome da branch principal>
git status
git add .
git rebase --continue
git push -f origin <nome da branch>
```

### Atualizar branch atual
Atualiza branch em que você está trabalhando no momento.
```sh
git pull
```

### Atualizar repositório completo
Atualiza todas as branchs do repositório que você está utilizando.
```sh
git remote update
```

### Arquiva alterações
Arquiva as alterações que você fez durante um determinado período, deste que não estejam adicionadas a algum commit, possibilitando que você possa trabalhar em outra coisa, e depois voltar e fazer a reaplicação mais tarde.

O stash se torna útil em um contexto onde, você precisa alterar com rapidez para trabalhar em outra coisa, mas está no meio de alguma alteração de código e não está pronto para fazer um commit.
```sh
git stash
```

### Desarquiva alterações
Desarquiva as alterações, fazendo com que as alterações arquivadas retornem para a área de trabalho.
```sh
git stash apply
```

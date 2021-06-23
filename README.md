# Meu manual de uso pessoal do GIT

Esse reposítorio serve como uma base de conhecimentos e experiencias que já vivo, guardo aqui desde comandos básicos até comandos um poucos mais avançados, que por muito tempo foram grandes impedimentos para o meu desenvolvimento, e espero de alguma forma contribuir com o seu desenvolvimento através desse materal.

![Seja um Ninja do GIT](https://blog.da2k.com.br/uploads/2015/07/banner-git-e-github-ninja.jpg)

#### Conteúdo
- [Criar nova branch](#criar-nova-branch)
- [Listar branchs de um projeto](#criar-nova-branch)
- [Trocar de branch](#criar-nova-branch)
- [Adicionar arquivos](#criar-nova-branch)
- [Remover um arquivo](#criar-nova-branch)
- [Realizar um commit](#criar-nova-branch)
- [Verificar status das alterações](#criar-nova-branch)
- [Enviar um commit para uma branch especifica](#criar-nova-branch)
- [Remover arquivos de um commit](#criar-nova-branch)
- [Fazer cópia de uma branch](#criar-nova-branch)
- [Corrigir conflitos entre branchs](#criar-nova-branch)
- [Unir commits em um só (Método para branchs sem Merge)](#criar-nova-branch)
- [Unir commits em um só (Método para branchs com Merge)](#criar-nova-branch)
- [Puxar conflitos](#criar-nova-branch)
- [Atualizar branch atual](#atualizar-branch-atual)
- [Atualizar repositório completo](#atualizar-repositorio-completo)

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

#### Realizar um commit
Salva as alteracões realizadas no repositório local. Uma dica importante e sempre descrever o maior número de detalhes possíveis no título do seu commit, para facilitar o entendimento do que foi desenvolvido.
```sh
git commit -m "<titulo>"
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

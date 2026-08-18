# Seja um Ninja do GIT! - Nível Avançado

Esse guia complementa o [README.md](README.md) com comandos e técnicas para quem já domina o básico do git e quer ganhar mais controle sobre histórico, investigação de bugs e produtividade no dia a dia.

#### Conteúdo
- [Reescrever histórico interativamente](#reescrever-histórico-interativamente)
- [Editar o último commit](#editar-o-último-commit)
- [Aplicar um commit específico de outra branch](#aplicar-um-commit-específico-de-outra-branch)
- [Encontrar o commit que introduziu um bug](#encontrar-o-commit-que-introduziu-um-bug)
- [Recuperar commits ou branches perdidos](#recuperar-commits-ou-branches-perdidos)
- [Criar uma tag de versão](#criar-uma-tag-de-versão)
- [Visualizar histórico de forma resumida](#visualizar-histórico-de-forma-resumida)
- [Comparar alterações entre branches ou commits](#comparar-alterações-entre-branches-ou-commits)
- [Ver quem alterou cada linha de um arquivo](#ver-quem-alterou-cada-linha-de-um-arquivo)
- [Trabalhar em múltiplas branches ao mesmo tempo](#trabalhar-em-múltiplas-branches-ao-mesmo-tempo)
- [Criar atalhos para comandos git](#criar-atalhos-para-comandos-git)
- [Ignorar arquivos no repositório](#ignorar-arquivos-no-repositório)
- [Enviar alterações forçadas com segurança](#enviar-alterações-forçadas-com-segurança)

#### Reescrever histórico interativamente
Permite reordenar, editar, unir (squash) ou remover commits específicos antes de enviar para o repositório remoto. É mais flexível que o método manual de unir commits mostrado no [guia básico](README.md), pois deixa escolher exatamente o que fazer com cada commit.
```sh
git rebase -i HEAD~<quantidade de commits>
```
No editor que abrir, troque `pick` por `squash`, `edit`, `reword` ou `drop` ao lado de cada commit, conforme o que quiser fazer com ele.

#### Editar o último commit
Corrige a mensagem do commit mais recente ou adiciona arquivos esquecidos a ele, sem criar um novo commit.
```sh
git add <arquivo esquecido>
git commit --amend
```

#### Aplicar um commit específico de outra branch
Copia um único commit de uma branch para outra, sem precisar dar merge na branch inteira.
```sh
git cherry-pick <hash do commit>
```

#### Encontrar o commit que introduziu um bug
Faz uma busca binária automática no histórico, marcando commits como "bom" ou "ruim" até o git apontar o commit exato que introduziu o problema.
```sh
git bisect start
git bisect bad
git bisect good <commit ou tag sem o bug>
git bisect good # ou git bisect bad, repita até o git indicar o culpado
git bisect reset
```

#### Recuperar commits ou branches perdidos
Mostra o histórico de tudo que o HEAD já apontou, incluindo commits de branches deletadas ou "perdidos" após um reset ou rebase — útil para recuperar trabalho que parecia perdido.
```sh
git reflog
git checkout <hash encontrado no reflog>
```

#### Criar uma tag de versão
Marca um commit específico como uma versão (ex: release), facilitando encontrar pontos importantes do histórico.
```sh
git tag -a v1.0.0 -m "<descrição da versão>"
git push origin v1.0.0
```

#### Visualizar histórico de forma resumida
Exibe o histórico de commits de forma compacta, mostrando branches e merges em um gráfico visual.
```sh
git log --oneline --graph --all --decorate
```

#### Comparar alterações entre branches ou commits
Mostra as diferenças de código entre duas branches, commits ou arquivos.
```sh
git diff <branch ou commit 1>..<branch ou commit 2>
```

#### Ver quem alterou cada linha de um arquivo
Mostra o autor e o commit responsável por cada linha de um arquivo, útil para entender o contexto de uma alteração.
```sh
git blame <caminho do arquivo>
```

#### Trabalhar em múltiplas branches ao mesmo tempo
Cria uma pasta de trabalho separada apontando para outra branch, sem precisar de stash ou checkout na branch em que você já está.
```sh
git worktree add <caminho da nova pasta> <nome da branch>
```

#### Criar atalhos para comandos git
Cria comandos personalizados mais curtos para os comandos git mais usados no dia a dia.
```sh
git config --global alias.<apelido> "<comando git>"
```
Exemplo:
```sh
git config --global alias.st "status"
```

#### Ignorar arquivos no repositório
Define quais arquivos ou pastas o git deve ignorar, evitando que sejam versionados por engano (ex: dependências, arquivos de ambiente).
```sh
# crie um arquivo .gitignore na raiz do projeto e adicione, por exemplo:
node_modules/
.env
```

#### Enviar alterações forçadas com segurança
Alternativa mais segura ao `push -f`, usado nas seções de squash e rebase do [guia básico](README.md). O `--force-with-lease` verifica se alguém enviou commits novos para a branch remota antes de sobrescrevê-la, cancelando o push se isso tiver acontecido — evitando perder trabalho de outra pessoa por acidente.
```sh
git push --force-with-lease origin <nome da branch>
```

# Meu manual de uso pessoal do GIT
Utilizo essse repositório para anotar os principais comandos do git que tem me gerado dúvidas e dificuldades. Espero ajudar alguém através desses simples comandos (:

#### Conteúdo
- Listar branchs de um projeto
- Trocar de branch
- Criar nova branch
- Verificar status das alterações
- Adicionar arquivos
- Remover um arquivo
- Realizar um commit
- Enviar um commit para uma branch especifica
- Corrigir conflitos entre branchs
- Unir commits em um só
- Fazer cópia de uma branch
- Remover arquivos de um commit
- Puxar conflitos

#### Listar branchs de um projeto
Listar todas as branchs de um determinado projeto que estão disponíveis no seu ambiente local.
```sh
git branch
```

#### Trocar de branch
Troca de branch dentro de um projeto.
```sh
git checkout <nome da branch>
```

#### Criar nova branch
Criaçao de uma nova branch local.
```sh
git branch -m <tipo>/<titulo>
```

#### Verificar status das alterações
Comando para verificar o status das alterações realizadas nos arquivos.
```sh
git status
```

#### Adicionar arquivos
Adicionar alterações realizadas nos arquivos ao commit que sera realizado.
```sh
git add . (Adicionar todos os arquivos modificados)
git add <caminho do arquivo> (Adicionar um arquivo específico)
```

#### Remover um arquivo
Remover as alterações realizadas nos arquivos, e evitar que sejam enviadas no commit.
```sh
git restore . (Remover todos os arquivos modificados)
git restore <caminho do arquivo> (Remover um arquivo específico)
```

#### Realizar um commit
Salvar as alteracões realizadas no repositório local. Uma dica importante e sempre descrever o maior número de detalhes possíveis no título do seu commit, para facilitar o entendimento do que foi realizado.
```sh
git commit -m "<titulo>"
```

#### Enviar um commit para uma branch especifica
Enviar as alteracões realizadas do repositório local para o repositório remoto.
```sh
git push origin <nome da branch>
```

#### Corrigir conflitos entre branchs
Corrigir conflitos de arquivos em uma branch.
```sh
git checkout <nome da branch principal>
git pull
git checkout <nome da minha branch>
git merge <nome da branch principal>
```

#### Unir commits em um só
Unir diversos commits em um só.
```sh
git reset --soft HEAD~<quantidade de commits>
git commit -m “<titulo do commit>”
git push -f origin <nome da branch>
```

#### Fazer cópia de uma branch
Copiar a branch atual para uma nova, geralmente utilizado para realizar backups das alteraçoes.
```sh
git checkout -b <nome da branch>-backup
```

#### Remover arquivos de um commit
Remover arquivos enviados no commit de uma branch remota, apenas caso não tenha merge.
```sh
git reset —soft HEAD~<quantidade de commits>
git status
git restore <arquivo>
git status
git commit -m “<commit>”
git status
gitk
```

#### Puxar conflitos
Puxar conflitos da branch para que possam ser resolvidos.
```sh
git checkout -b <nome da branch>-backup
git checkout <nome da branch principal>
git pull origin <nome da branch principal>
git checkout <nome da branch>
git rebase development <nome da branch principal>
git status
git add .
git rebase --continue
git push -f origin <nome da branch>
```

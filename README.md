# Meu manual pessoal de uso do GIT
Repository so that I can learn, understand and test the main git commands.

#### Listar branchs de um projeto
```sh
git branch
```

#### Trocar de branch
```sh
git checkout <nome da branch>
```

#### Criar nova branch
```sh
git branch -m <tipo>/<titulo>
```

#### Verificar status das alterações
```sh
git status
```

#### Adicionar arquivos
```sh
git add .
```

#### Remover um arquivo
```sh
git restore <caminho do arquivo>
```

#### Realizar um commit
```sh
git commit -m "<titulo>"
```

#### Enviar um commit para uma branch especifica
```sh
git push origin <nome da branch>
```

#### Corrigir conflitos entre branchs
```sh
git checkout <nome da branch principal>
git pull
git checkout <nome da minha branch>
git merge <nome da branch principal>
```

#### Unir commits em um só
```sh
git reset --soft HEAD~<quantidade de commits>
git commit -m “<titulo do commit>”
git push -f origin <nome da branch>
```

#### Fazer cópia de uma branch
```sh
git checkout -b <nome da branch>-backup
```

#### Remover arquivos de um commit (Caso não tenha merge)
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

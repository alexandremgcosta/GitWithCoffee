# GitWithCoffee
Repositório utilizado para aprender os comandos básicos Git!


## O que é o GIT?

É um sistema de controlo de versões distribuído, muito usado na programação e desenvolvimento de software. Ele permite que programadores e equipas de desenvolvimento colaborem em projetos, rastreando mudanças no código-fonte de forma eficiente e segura.

## O que é o GitHub?

É uma plataforma de hospedagem de código que utiliza o Git como sistema de controlo de versões. Foi criada para facilitar o trabalho colaborativo de desenvolvimento de software, fornecendo ferramentas que tornam o processo de desenvolvimento mais acessível e organizado.

## O que é um repositório?

Local onde é armazenado e gerido o código-fonte. Contém também todo o histórico de mudanças feitas nesses ficheiros ao longo do tempo.

## O que é um Commit?

É uma operação no Git que guarda um snapshot do estado atual dos ficheiros num repositório. Basicamente, regista as mudanças feitas aos ficheiros desde o último commit, incluindo adições, modificações ou eliminações de ficheiros.

## O que é um Branch?

Um branch é uma linha separada de desenvolvimento dentro de um repositório Git. Os branches permitem que os programadores trabalhem em diferentes funcionalidades, correções de erros, ou experimentos de forma isolada do código principal.

---

## Já com o Git instalado…

- `git config --global --list` : Comando para listar as configs atuais
- `git config --global user.name “O MEU NOME”` : Comando para colocar o nome que irá aparecer no Git
- `git config --global user.email MEU@EMAIL` : Comando para registar o e-mail

---

## Comandos auxiliares da Linha de Comandos:

- `ls` : Lista os ficheiros e diretórios no diretório atual
- `cd` : Muda para o diretório especificado
- `touch` : Cria um ficheiro vazio ou atualiza a data de modificação de um ficheiro existente
- `clear` : Limpa o terminal, removendo o texto visível
- `rm` : Remove ficheiros ou diretórios
- `cd ..` : Volta ao diretório anterior
- `rmdir` : Remove um diretório vazio
- `mkdir` : Cria um novo diretório
- `cat` : Mostra o conteúdo de um ficheiro no terminal
- `mv` : Move ou renomeia ficheiros e diretórios

---

## Criar repositório:

Utilizar o comando `git init` na pasta pretendida.

---

## Colocando arquivos no stage:

Colocar um arquivo no stage significa preparar esse ficheiro para o próximo commit, selecionando quais mudanças feitas nos ficheiros do projeto serão incluídas. A staging área é um espaço intermediário onde se pode adicionar e organizar as alterações antes de as guardar permanentemente no repositório com um commit.

- `git add NOME DO FICHEIRO` : Adicionar o ficheiro à staging área.
- `git rm --cached NOME DO FICHEIRO` : Remove o ficheiro da staging área.
- `git add .` : Adiciona todos os ficheiros à staging área.

---

## Realizar o commit:

- `git commit -m “MENSAGEM DO COMMIT”`
- `git log` : Comando para ver o histórico dos commits.

---

## Desfazer o commit:

- **Checkout**: Muda a área de trabalho para uma versão específica de um commit ou para um branch diferente. Usado para navegar entre branches ou commits. Não altera o histórico de commits; é mais usado para visualizar ou temporariamente voltar a um estado anterior.
  - `git checkout NOME DO COMMIT/BRANCH`
  - `git checkout main`

- **Revert**: Cria um novo commit que desfaz as mudanças de um commit anterior, mantendo o histórico intacto. Ideal para desfazer mudanças em commits já partilhados ou em repositórios remotos, pois preserva o histórico e permite uma reversão segura sem remover commits.
  - `git revert NOME DO COMMIT`

- **Reset**: Remove commits da linha do tempo do branch atual, podendo afetar apenas a staging área, ou ambos, dependendo da opção usada. É ideal para reescrever o histórico local antes de partilhar com outros, remover commits indesejados, ou fazer alterações. Pode causar a perda de dados se usado de forma incorreta.

  Opções de flags para o Reset:
  - `--soft` : Mantém as mudanças na staging área
  - `--mixed` : Mantém as mudanças na área de trabalho, mas remove da staging área
  - `--hard` : Remove as mudanças da staging área e da área de trabalho

  - `git reset NOME DO COMMIT --hard`

---

## Ignorar ficheiros/pastas:

Para ignorar ficheiros ou pastas no Git, usa-se um ficheiro chamado `.gitignore`. O ficheiro lista padrões de nomes de ficheiros e pastas que não devem ser incluídos no controlo de versões, evitando que sejam adicionados ao stage ou ao repositório.

---

## Criar branches:

- `git branch` : Comando para consultar os branches criados
- `git branch NOME DO BRANCH` : Cria o branch
- `git checkout NOME DO BRANCH` : Move-nos para dentro do branch escolhido
- `git branch -D NOME DO BRANCH` : Elimina o branch em questão

---

## Fazer o merge:

Para realizar um merge temos de estar SEMPRE no branch de destino! Dentro do branch de destino executar o comando:

- `git merge NOME DO BRANCH`

Podemos verificar o histórico dos commits e como os merges se integraram com o comando:

- `git log --oneline --graph`

---

## Comunicar com o GitHub:

Inicialmente é necessário associar uma chave SSH ao GitHub!

- `git push LINK_DO_REPOSITORIO_NO_GIT_HUB master` : Comando usado para enviar as mudanças do branch local, neste caso o master, para o branch do repositório remoto.

### Primeiro Problema notado:

Localmente o branch principal do Git chama-se `master` mas no GitHub chama-se `main`.

- Utilizar o comando `git branch -m master main` para renomear o branch local master para main.
- Podemos usar o comando `git status` para confirmar em que branch estamos.
- Utilizar o comando `git push LINK_DO_REPOSITORIO_NO_GIT_HUB --delete master` para apagar a referência ao branch antigo master.
- Utilizar o comando `git push -u LINK_DO_REPOSITORIO_NO_GIT_HUB main` para definir o novo branch.

### Segundo Problema notado:

O repositório Git local foi criado numa data e o repositório Git remoto foi criado em outra data e por esse motivo estava a entrar em conflito na hora do push. O problema foi resolvido efetuando um pull antes do push com o comando:

- `git pull LINK_DO_REPOSITORIO_NO_GIT_HUB main --allow-unrelated-histories --no-rebase`

Para resolver o facto de ter que se usar sempre o link do repositório do GitHub foi criada uma ALIAS que por padrão chama-se `origin` que consiste em associar a palavra `origin` ao link SSH do repositório do GitHub. Foram usados os comandos:

- `git remote add origin SSH_DO_REPOSITORIO` e `git remote -v` para confirmar as alterações.

Assim sendo, para comandos futuros já podemos realizar utilizando o origin, por exemplo:

- `git push origin main`
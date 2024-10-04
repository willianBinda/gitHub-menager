# Padrão de organização do gitHub

# Passo 1 - Nome da Branch

`Padrão:`

- id-da-sua-tarefa/super-resumo-da-feature

`Exemplo:`

- git checkout -b POP-01/criando-post-api-login

# Passo 2 - Utilizar Padrões de Commit

- `feat:` Uma nova funcionalidade que a pessoa final irá acessar.
- `fix:` Correções de bugs.
- `docs:` Mudanças na documentação.
- `style:` Mudanças que não afetam o código (espaços, formatação).
- `refactor:` Refatoração do código sem mudança de funcionalidade.
- `perf:` Alterações relacionadas à performance.
- `test:` Adicionando ou corrigindo testes.
- `chore:` Alterações em arquivos de configuração, build, distribuição, CI, ou qualquer outra coisa que não envolva diretamente o código da aplicação para o usuário final.

`Exemplo:`

- git commit -m "fix: Erro na validação do formulário de login corrigido."
- git commit -m "feat: Criando botão de login."

# Passo 3 - Padrão de Título na Pull Request

`Padrão:`

- [id-da-sua-tarefa] tipo: descriçao

`Exemplo:`

- [BR-01] feat: Criando requisição post para a endpoint de login.

# Passo 4 - Fazer Uma Boa Descrição na Pull Request

`Tipo de mudança`

- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Chore (documentation, packages, or tests updates, nothing that affect the final user directly)
- [ ] Release (new version of the application - only for production)
- [ ] Stage (new version of the application - only for stage)

`Descrição`

...

`Screenshots`

...

`Tarefas`

- [id-tarefa](link-tarefa) or N/A

`Checklist`

- [ ] Minhas alterações têm menos ou igual a 400 linhas;
- [ ] Eu realizei uma auto-revisão do meu próprio código
- [ ] Os testes e linter existentes passam localmente com minhas alterações
- [ ] Comentei meu código em áreas difíceis de entender (se aplicável)
- [ ] Criei testes para minha `fix or feature` (se aplicável)

`Dependencies`

Esta solicitação pull depende dos seguintes outros:

- link-to-depency PR or N/A

## Explicando:

`Item 1:` Tipo da alteração, se é bug fix, feature, chore ou uma release (para o caso de fazer releases com alguma branch que não é a "main")

`Item 2:` Descrição com mais detalhes, principalmente se esse recurso altera pontos fundamentais do sistema. Pontos esses que nós precisaremos lembrar no futuro, uma vez que não podemos confiar em nossas memórias

`Item 3:` Se for possível e fizer sentido, capturas de telas que explicam melhor o recurso (front-end)

`Item 4:` Os links para as tarefas na aplicação que gerencia as estórias e tarefas

`Item 5:` Checklist básico para subir uma PR:

- Menos de 400 linhas
- Revisão no próprio código antes de abrir PR
- Todos os testes existentes passaram
- Comentários em lugares necessários foram escritos
- Criação de testes para o novo recurso

`Item 6:` Outras pull requests que são dependentes, por exemplo: alguma pull request com uma API do backend que é necessária estar entregue antes de subir uma tela no frontend.

# Passo 5 - Processo de merges para diferentes branchs

Quando realizar o merge de uma branch tomar cuidado com o formato do merge.

`Exemplo:`

- Pull request `development` <- `BR-01/criando-tela-login`
  - Utilizar o formato `Squash and Merge`
  - Combina todos os commits da pull request em um único commit antes de fazer o merge.
- Pull request `stage` <- `development`
  - Utilizar o formato `Merge Commit`
  - Cria um commit de merge que combina o histórico do branch da pull request com o branch de destino.
- Pull request `main` <- `stage`
  - Utilizar o formato `Merge Commit`
  - Cria um commit de merge que combina o histórico do branch da pull request com o branch de destino.
- Processo completo `main`<-`stage`<-`development`

# Passo 6 - Passos para criar uma nova release

### Criando pull request para a branch `main`:

#### Título da pull request:

- [versão] Release: descriçao

`Exemplo:`

- [v0.0.1] Release: Criando requisição post para a endpoint de login.

#### Corpo da pull request:

`Tipo de mudança`

- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Chore (documentation, packages, or tests updates, nothing that affect the final user directly)
- [ ] Release (new version of the application - only for production)
- [ ] Stage (new version of the application - only for stage)

`Descrição`

...

### Após realizar o merge na branch `main`:

- `-> Create a new release`
  - `-> Chouse a tag`: utilize a mesma tag utilizada ao realizar o merge na branch main.
    - `-> Create new tag`
  - `-> Target: main`
  - `-> Generate release notes`
  - `-> Release title`: Modifique ou adicione o mesmo título utilizado no merge para a branch main.
    -> `Publish release`

# Dicas Bônus - Assignees, Labels e Multiplos Commits

- `"Assignees"`: as pessoas que trabalharam naquele recurso, porque em caso de problemas, é fácil achar quem tem mais contexto no time.
- `"Labels":` uma ou mais labels que fazem sentido para aquele recurso

Por último crie multiplos commits para suas alterações, procure não alterar uma feature inteira e jogar um número enorme de arquivos (salvo exceções) em um único commit, assim fica mais fácil também de entender o que rolou no processo de desenvolvimento daquele recurso.

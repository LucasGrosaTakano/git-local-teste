# Aula Prática – Git Local (sem GitHub)

## Objetivo

O objetivo desta aula é te ensinar a usar o **Git** localmente para versionar seus projetos. Vamos aprender como criar commits, trabalhar com branches e manter o histórico do projeto de forma organizada e segura.

---

## 1. Primeiros Passos: Configuração do Git

Antes de começar, é preciso configurar o Git com seu nome e e-mail, para que ele registre suas alterações corretamente. Também podemos escolher um editor de texto, como o VS Code, para facilitar a edição de mensagens de commit.

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
git config --global core.editor "code --wait"   # Usa o VS Code como editor (opcional)
git config --list                                # Verifica suas configurações atuais
```

---

## 2. Criando o Repositório

Agora, vamos criar um novo diretório para o projeto e inicializar um repositório Git nele. O comando `git init` é responsável por criar uma pasta oculta chamada `.git`, que armazena o histórico de alterações.

```bash
mkdir meu_projeto
cd meu_projeto
git init
```

---

## 3. Mudando a Branch Padrão para `main`

Por padrão, o Git cria a primeira branch como **master**. No entanto, é uma boa prática mudar para **main**, que tem sido a convenção adotada pela comunidade.

Para fazer isso, use o comando:

```bash
git branch -m master main
```

E se quiser que todos os novos repositórios criem a branch **main** por padrão, basta configurar globalmente:

```bash
git config --global init.defaultBranch main
```

---

## 4. Criando Arquivos e Verificando o Status

Agora, vamos criar um arquivo e verificar o que o Git está monitorando em relação ao nosso projeto.

```bash
echo "Meu primeiro arquivo" > readme.txt
git status
```

O comando `git status` mostra o que foi alterado, o que está pronto para ser commitado e o que ainda não foi adicionado ao repositório.

---

## 5. Adicionando Arquivos ao Staging

Para registrar alterações, precisamos adicionar os arquivos à **área de staging**. É como se fosse a "caixa de preparação" para o commit.

```bash
git add readme.txt       # Adiciona um arquivo específico
git add .                # Adiciona todos os arquivos do diretório
git status               # Verifica a área de staging
```

---

## 6. Fazendo o Primeiro Commit

Agora que os arquivos estão na área de staging, é hora de fazer o primeiro commit. O commit é o "salvamento" oficial da alteração no histórico.

```bash
git commit -m "Primeiro commit - adiciona readme.txt"
```

---

## 7. Visualizando o Histórico de Commits

Depois de fazer um commit, podemos olhar o histórico para ver as mudanças feitas no repositório.

```bash
git log
git log --oneline   # Mostra de maneira resumida
git show            # Exibe os detalhes de um commit específico
```

O comando `git log --oneline` é útil para ver rapidamente o histórico de commits.

---

## 8. Editando Arquivos e Registrando Mudanças

Edite um arquivo, veja as mudanças feitas e depois registre-as com um novo commit.

```bash
echo "Adicionando nova linha" >> readme.txt
git status           # Verifica as mudanças
git diff             # Exibe as diferenças entre as versões
git add readme.txt   # Adiciona as mudanças à área de staging
git commit -m "Atualiza readme.txt com nova linha"
```

---

## 9. Desfazendo Mudanças

Se você cometer um erro, o Git permite que você desfaça mudanças antes de registrar um commit.

```bash
git restore readme.txt              # Descarta mudanças não adicionadas
git restore --staged readme.txt     # Remove o arquivo da área de staging
```

Esses comandos são ótimos para corrigir pequenos erros antes de cometer.

---

## 10. Trabalhando com Branches

Usar **branches** é uma maneira de manter diferentes partes do seu projeto isoladas. Assim, você pode trabalhar em uma nova funcionalidade sem afetar o código principal.

Para criar e mudar de branch, use:

```bash
git branch                         # Lista todas as branches
git branch nova_funcionalidade     # Cria uma nova branch
git switch nova_funcionalidade     # Muda para a nova branch
```

---

## 11. Fazendo Commits em Outras Branches

Agora que você criou uma nova branch, adicione um arquivo e faça o commit dessa nova funcionalidade.

```bash
echo "Nova feature" > feature.txt
git add feature.txt
git commit -m "Adiciona nova feature"
```

---

## 12. Mesclando Mudanças

Quando terminar de trabalhar em uma branch, você pode **mesclar** suas mudanças de volta para a branch principal (`main`).

```bash
git switch main
git merge nova_funcionalidade
```

Esse comando traz as mudanças da branch `nova_funcionalidade` para a `main`.

---

## 13. Excluindo Branches Locais

Após mesclar a branch, você pode excluí-la localmente, já que ela não será mais necessária.

```bash
git branch -d nova_funcionalidade
```

---

## 14. Ignorando Arquivos com `.gitignore`

Às vezes, você pode não querer que certos arquivos ou pastas sejam rastreados pelo Git, como arquivos temporários ou de log. Para isso, usamos um arquivo chamado `.gitignore`.

Exemplo de conteúdo para o `.gitignore`:

```
*.log
*.tmp
node_modules/
```

Depois, basta adicionar e fazer o commit desse arquivo:

```bash
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```

---

## 15. Comandos Úteis para o Dia a Dia

Alguns comandos vão te ajudar a visualizar o que está acontecendo no seu repositório. Aqui estão alguns dos mais usados:

```bash
git status                      # Verifica as mudanças no repositório
git log --oneline --graph --decorate   # Histórico visual de commits
git diff                         # Exibe as diferenças entre as versões
git show HEAD                    # Mostra os detalhes do último commit
```

---

## 16. Exemplo Completo de Fluxo de Trabalho

Aqui está um exemplo simples de como usar os comandos que vimos para criar e trabalhar com branches no Git:

```bash
git init
echo "Aula prática Git local" > readme.txt
git add .
git commit -m "Primeiro commit"
git branch dev
git switch dev
echo "Nova versão em desenvolvimento" >> readme.txt
git add .
git commit -m "Atualiza versão dev"
git switch main
git merge dev
git log --oneline --graph
```

---

Esse é o fluxo básico para usar o Git localmente. Com esses comandos, você pode começar a controlar as versões dos seus projetos de forma eficaz e sem a necessidade de usar o GitHub, embora o processo seja muito semelhante se você decidir integrar um repositório remoto depois.

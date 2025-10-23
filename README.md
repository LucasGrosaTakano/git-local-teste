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

Material criado para fins educacionais na aula prática de **Git Local**,  
ministrada por *Anderson R. M. Gomes* 🧑‍🏫


**🚀 Próximos passos:**  
Na próxima aula, você aprenderá a conectar este repositório local ao GitHub com os comandos `git remote`, `git push` e `git pull`.

---

## 2 Clonagem e Configuração Local
Continuando a documentação sobre Git local e GitHub, agora focamos na integração entre o repositório local e o GitHub, além do processo de colaboração utilizando o GitFluence para gerar os comandos Git. Vou explicar cada seção da mesma forma que fizemos anteriormente, destacando pontos importantes, oferecendo uma explicação detalhada e algumas sugestões de como melhorar a clareza e praticidade do conteúdo.

---

## 2.0 Documentação e Uso do GitFluence

O objetivo aqui é expandir a documentação sobre o uso do Git local com a integração ao GitHub, abordando principalmente o processo de colaboração e como utilizar o GitFluence para gerar os comandos Git. O GitFluence é uma ferramenta útil para automatizar e simplificar o uso dos comandos Git, ajudando usuários iniciantes a não se perderem nas sintaxes complexas.

## 2.1 Clonagem e Configuração Local

Neste ponto, a documentação fala sobre como clonar o repositório do GitHub para o ambiente local e criar um branch de desenvolvimento para manter o `main` limpo.

### Comandos e Explicações:

* **Comando Git: `git clone <URL do seu fork>`**
  **Explicação**: Clona o repositório para o seu ambiente local. A URL do fork (versão do repositório no GitHub) é fornecida quando você faz um fork de um repositório.
* **Comando Git: `cd git-local`**
  **Explicação**: Muda o diretório atual para a pasta do repositório clonado.
* **Comando Git: `git checkout -b documentacao-colaboracao`**
  **Explicação**: Cria um novo branch chamado `documentacao-colaboracao` para a documentação, mantendo o `main` limpo e sem alterações diretas. O uso de branches é crucial para evitar alterações diretas no código principal.

Esses passos são bastante diretos e essenciais para o início do processo de integração, preparando o repositório local para modificações e colaborando sem afetar o código original.

---

## 2.2 Uso do GitFluence para Comandos de Integração

Aqui, o [GitFluence](https://www.gitfluence.com/) é utilizado para gerar comandos Git para integração entre o repositório local e o GitHub remoto. A explicação também inclui exemplos de comandos para interação com o repositório remoto.

![](https://s10.aconvert.com/convert/p3r68-cdx67/acs5c-gmavy.jpg "imagem")

### Comandos e Explicações:

* **Comando Git: `git push -u origin documentacao-colaboracao`**
  **Explicação**: Este comando envia (empurra) o branch `documentacao-colaboracao` para o repositório remoto no GitHub, permitindo que suas mudanças fiquem acessíveis para outras pessoas ou para que você crie um Pull Request mais tarde.

* **Comando Git: `git branch -a`**
  **Explicação**: Lista todas as branches locais e remotas, para você saber em que ponto está e se o seu branch foi corretamente enviado para o remoto.

* **Comando Git: `git status`**
  **Explicação**: Verifica o estado atual dos arquivos no repositório local, ajudando a saber quais mudanças foram feitas e quais ainda precisam ser preparadas para commit.

Esses comandos são fundamentais no fluxo de trabalho entre o Git local e o GitHub, especialmente ao lidar com múltiplos branches e colaborando com outras pessoas.

---

## 2.3. Edição da Documentação (Local)

Agora, o foco é editar os arquivos de documentação, como o `README.md`, no repositório local. Isso é essencial para atualizar o processo de colaboração, integrar novos colaboradores e garantir que o repositório esteja bem documentado.

### Seções que precisam ser adicionadas:

1. **Como integrar o Git Local ao GitHub**
   Descrição simples de como clonar, adicionar, commit e push, fornecendo exemplos de comandos.
2. **Como adicionar colaboradores ao repositório privado**
   Instruções detalhadas sobre como configurar permissões e adicionar colaboradores no GitHub.
3. **Como usar o GitFluence**
   Breve menção do GitFluence e como ele pode ser utilizado para gerar e automatizar comandos Git.

---

## 2.4. Commit e Push das Alterações

Depois de editar a documentação, o próximo passo é versionar as alterações e enviá-las para o repositório remoto. Isso envolve o uso dos comandos de commit e push, que são o núcleo do controle de versões no Git.


<p align="center">
  <img style="height = 100px;" src="https://cdn-icons-png.flaticon.com/512/5711/5711569.png" alt="Icone" />
</p>


### Comandos e Explicações:

* **Comando Git: `git add .`**
  **Explicação**: Adiciona todos os arquivos modificados à área de staging, preparando-os para o commit.

* **Comando Git: `git commit -m "feat: Adiciona documentacao sobre integracao e colaboracao"`**
  **Explicação**: Cria um commit com as alterações, onde a mensagem de commit deve descrever brevemente o que foi feito (adicionar documentação sobre integração e colaboração).

* **Comando Git: `git push` ou `git push origin documentacao-colaboracao`**
  **Explicação**: Envia o branch local para o GitHub, para que as alterações fiquem acessíveis para outros desenvolvedores ou para que você crie um Pull Request.

Esses comandos são cruciais para garantir que as mudanças locais sejam integradas ao repositório remoto, para que a colaboração seja eficaz.

---












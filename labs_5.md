## 🧪 **Exercícios Aula 5 Git Avançado**

## 1️⃣ `git reflog`: **Recuperando um branch deletado acidentalmente**

### 🎯 Desafio:

Você acidentalmente apagou uma branch chamada `ajuste-layout` que tinha commits importantes. Recupere o conteúdo dessa branch com base no histórico local.

#### 🔧 Instruções:

1. Crie e altere para a branch `ajuste-layout`
2. Faça 2 commits
3. Volte para `main` e execute:

   ```bash
   git branch -D ajuste-layout
   ```
4. Use `git reflog` para identificar o último HEAD que estava em `ajuste-layout`
5. Crie novamente a branch com:

   ```bash
   git checkout -b ajuste-layout <hash>
   ```

---

## 2️⃣ `git bisect`: **Encontrando o commit que quebrou o teste**

### 🎯 Desafio:

Você percebeu que algum commit entre `v1.0` e `v1.6` quebrou a funcionalidade de validação. Use `git bisect` para identificar qual commit introduziu o erro.

#### 🔧 Instruções:

1. Em um novo repositório, crie 6 commits sequenciais

   * No 4º commit, adicione um erro intencional, como `echo "valor errado" > config.txt`
2. Em `HEAD`, configure:

   ```bash
   git bisect start
   git bisect bad
   git bisect good HEAD~5
   ```
3. Para cada etapa do bisect, use:

   ```bash
   grep -q "errado" config.txt && exit 1 || exit 0
   ```

   Ou automatize com:

   ```bash
   git bisect run bash -c 'grep -q "errado" config.txt && exit 1 || exit 0'
   ```
4. Finalize com `git bisect reset`

---

## 3️⃣ `git stash`: **Salvando progresso antes de mudar de contexto**

### 🎯 Desafio:

Você está desenvolvendo uma nova funcionalidade, mas precisa trocar para a branch `main` urgentemente para corrigir um bug. Guarde seu progresso com `stash`, mude de contexto, e depois retome de onde parou.

#### 🔧 Instruções:

1. Crie a branch `nova-funcionalidade`
2. Edite e salve 2 arquivos com modificações (sem comitar)
3. Execute:

   ```bash
   git stash save "wip: nova funcionalidade"
   git checkout main
   ```
4. Faça um commit fictício em `main`
5. Volte para a branch e recupere o progresso:

   ```bash
   git checkout nova-funcionalidade
   git stash list
   git stash apply stash@{0}
   ```

---

## 🧪 4️⃣ `git cherry-pick`: **Selecionando apenas uma correção para aplicar em release**

### 🎯 Desafio:

Sua branch `main` contém dois commits: um com uma nova feature e outro com um hotfix. Você precisa aplicar **apenas o hotfix** na branch `release/1.0`.

#### 🔧 Instruções:

1. Em `main`, crie dois commits:

   * Commit 1: `"feature: novo componente"`
   * Commit 2: `"fix: corrige bug no botão"`
2. Crie uma nova branch:

   ```bash
   git checkout -b release/1.0
   ```
3. Aplique **somente o segundo commit** com:

   ```bash
   git cherry-pick <hash-do-hotfix>
   ```
4. Verifique o histórico com `git log --oneline`

---

Excelente ideia! A seguir, você encontrará **4 exercícios avançados com foco em resolução de erros comuns** ao usar `git reflog`, `git bisect`, `git stash` e `git cherry-pick`. Cada exercício simula um cenário de erro real e exige diagnóstico e correção — perfeitos para aulas práticas e para desenvolver maturidade no uso do Git.

---

## 🧪 5️⃣ `git reflog`: **Reset hard apagou mudanças importantes**

#### 🐞 Cenário:

Você executou um `git reset --hard` por engano e perdeu commits que ainda não haviam sido pushados.

#### 🔧 Instruções:

1. Em uma branch chamada `nova-pagina`, crie 2 commits importantes.
2. Execute:

   ```bash
   git reset --hard HEAD~2
   ```
3. Simule o desespero 🤯.
4. Use `git reflog` para localizar os hashes antigos.
5. Recupere o commit com:

   ```bash
   git checkout -b recuperado HEAD@{n}
   ```

#### ✅ Esperado:

Você deverá restaurar a branch exatamente no ponto em que estava antes do reset.

---

## 🧪 6️⃣ `git bisect`: **Script automático falha ao testar**

#### 🐞 Cenário:

Você automatizou o `git bisect run`, mas o script retorna códigos de erro inválidos, quebrando o processo.

#### 🔧 Instruções:

1. Crie 5 commits, com um bug inserido no 3º (`echo "valor errado" > teste.txt`)
2. Use:

   ```bash
   git bisect start
   git bisect bad
   git bisect good HEAD~4
   ```
3. Rode:

   ```bash
   git bisect run bash -c 'grep "valor certo" teste.txt'
   ```
4. Corrija o erro no script: o comando acima não define código de saída corretamente.
5. Ajuste para:

   ```bash
   bash -c 'grep -q "valor certo" teste.txt && exit 0 || exit 1'
   ```

#### ✅ Esperado:

A correção do script permite ao `bisect` encontrar o commit defeituoso corretamente.

---

## 🧪 7️⃣ `git stash`: **Stash aplicado com conflito**

#### 🐞 Cenário:

Você alterou um arquivo localmente, fez `git stash`, mas ao aplicar o stash em outra branch, um **conflito** acontece.

#### 🔧 Instruções:

1. Crie `feature-x`, edite `pagina.html` com um novo conteúdo e `git stash`.
2. Vá para `main`, edite o **mesmo arquivo**, com outro conteúdo e comite.
3. Agora, em `main`, tente:

   ```bash
   git stash apply
   ```
4. O conflito deve aparecer.
5. Resolva o conflito manualmente no arquivo, e finalize com:

   ```bash
   git add pagina.html
   git stash drop
   ```

#### ✅ Esperado:

Você resolve o conflito e limpa o stash manualmente.

---

## 🧪 8️⃣ `git cherry-pick`: **Cherry-pick com conflito e abortado por engano**

#### 🐞 Cenário:

Você está fazendo cherry-pick de um commit que altera o mesmo arquivo já modificado na branch atual. Um conflito ocorre e você **acidentalmente aborta**.

#### 🔧 Instruções:

1. Crie a branch `bugfix` e comite um arquivo `config.yml`
2. Em `main`, edite o mesmo arquivo de forma diferente e comite
3. Em `main`, execute:

   ```bash
   git cherry-pick <commit-de-bugfix>
   ```
4. Um conflito ocorre.
5. Execute acidentalmente:

   ```bash
   git cherry-pick --abort
   ```
6. Agora decida a estratégia:

   * Voltar para `bugfix` e gerar novo patch?
   * Recomeçar o cherry-pick?
   * Criar uma branch temporária a partir do commit original?

#### ✅ Esperado:

Você consegue aplicar o conteúdo da alteração original mesmo após o `abort`, usando uma abordagem alternativa (ex: `git format-patch`, `git show`, ou `cherry-pick` novamente).

---

## 🧪 9️⃣ `git format-patch`: **Exportando Commits com Patch entre Repositórios**

1. 🎬 **Criar um commit em um repositório de origem**

```bash
# Crie e entre no repositório de origem
cd git-workshop

echo "versao 1" > app.txt
git add app.txt
git commit -m "feat: primeira versão do app"

echo "versao 2" >> app.txt
git commit -am "feat: segunda versão do app"
```

2. 📦 **Gerar um arquivo patch**

```bash
# Gere patch do último commit
git format-patch -1 HEAD --stdout > segunda-versao.patch
```

3. 📤 **Criar um repositório de destino e importar o patch**

```bash
# Em um novo terminal ou pasta separada
cd ..
mkdir repo-destino && cd repo-destino
git init

# Crie um arquivo base igual ao primeiro commit do outro repo
echo "versao 1" > app.txt
git add app.txt
git commit -m "feat: primeira versão do app"

# Copie o patch gerado anteriormente (ou use caminho relativo)
cp ../git-workshop/segunda-versao.patch .

# Aplique o patch
git apply segunda-versao.patch

# Verifique alterações e comite
git status
git add app.txt
git commit -m "feat: segunda versão do app (via patch)"
```

4. 🧠 **Preservar autor e mensagem**

Se quiser preservar os metadados do commit original:

```bash
git reset --hard HEAD~1  # volte antes do commit feito manualmente
git am segunda-versao.patch
```


5. ✅ **Validação**

```bash
git log --oneline
cat app.txt
```
Você deve ver os dois commits com o conteúdo final do arquivo `app.txt` contendo as duas versões.

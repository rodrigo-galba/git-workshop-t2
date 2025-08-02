# 📝 Registro da Sessão com `script`

Para comprovar a execução completa de cada laboratório:

1. Antes de iniciar os comandos, digite:

```bash
script lab2-sessaoN.txt
```

(Substitua `N` pelo número do laboratório.)

2. Realize todos os passos normalmente.

3. Ao final, digite:

```bash
exit
```

> Isso salvará um log da sessão, que pode ser entregue.

---

# 🧪 Laboratório 2.1: Branches `main`, `test`, `prod`

## 🎯 Objetivo:
Praticar criação e fusão de branches, simular conflitos e resolvê-los de forma segura.

### 🎬 Início da Sessão

```bash
script lab2-sessao1.txt
```
Com o repositório da aula 1:

1. Crie os branches:
```bash
git branch test
git branch prod
````

2. No `main`, adicione:

```bash
echo "v2 main" >> app.txt
git add app.txt
git commit -am "v2 main"
```

3. Promova para `test` e depois `prod`:

```bash
git checkout test
git merge main

git checkout prod
git merge test
```

4. Volte ao `main` e continue:

```bash
git checkout main
echo "v3 main" >> app.txt
git add .
git commit -am "v3 main"
```

5. Ver branches:
```bash
git branch
```

6. Ver histórico:

```bash
git log --oneline --all
```

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab2-sessao1.txt`.

---

# 🧪 Laboratório 2.2: Merging e Conflitos

### 🎯 Objetivo:
Praticar criação e fusão de branches, simular conflitos e resolvê-los de forma segura.

### 🎬 Início da Sessão

```bash
script lab2-sessao2.txt
```

```bash
git checkout -b feature-a
echo "linha A" > arquivo.txt
git add .
git commit -m "Feature A"

git checkout main
git checkout -b feature-b
echo "linha B" > arquivo.txt
git add .
git commit -m "Feature B"
```

```bash
git checkout main
git merge feature-a   # deve funcionar
git merge feature-b   # gerará conflito
git status            # mostra status do merge
```

Resolva o conflito:
- Edite `arquivo.txt` e escolha a versão correta.
- Em seguida:

```bash
git add arquivo.txt
git commit -m "Resolve conflito entre A e B"
```

Visualize o histórico:

```bash
git log --oneline --all
```

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab2-sessao2.txt`.

---

# 🧪 Laboratório 2.3: Resolvendo Conflitos parte 2

### 🎬 Início da Sessão

```bash
script lab2-sessao3.txt
```
---

1. Crie um novo arquivo:
```bash
echo "linha 1" > arquivo.txt
git add arquivo.txt
git commit -m "Primeiro commit"
```

2. Crie três branches:
```bash
git branch branch1
git branch branch2
git branch branch3
git branch           # lista todos os branches
```

3. Faça alterações conflitantes:
```bash
git checkout branch1
echo "linha 2 na branch1" >> arquivo.txt
git commit -am "Commit na branch1"

git checkout branch2
echo "linha 2 na branch2" >> arquivo.txt
git commit -am "Commit na branch2"

git checkout branch3
echo "linha 2 na branch3" >> arquivo.txt
git commit -am "Commit na branch3"
```

4. Tente mesclar:
```bash
git checkout main
git merge branch1   # sem conflito
git merge branch2   # com conflito
git status
git merge branch3
```

5. Resolva os conflitos:
```bash
git status
# Edite os arquivos com <<<<<<< HEAD
nano arquivo.txt
git add arquivo.txt
git commit -m "Resolvido conflito"
```

6. Tente mesclar:
```bash
git branch         # mostra branch atual (main)
git merge branch3
```

7. Resolva os conflitos:
```bash
git status
# Edite os arquivos com <<<<<<< HEAD
nano arquivo.txt
git add arquivo.txt
git commit -m "Resolvido conflito"
git status
```

8. Visualize o histórico:

```bash
git log --oneline --all
```

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab2-sessao3.txt`.

---

# 🧪 Laboratório 2.4: Configurando `.gitignore` para Variáveis de Ambiente

### 🎬 Início da Sessão

```bash
script lab2-sessao4.txt
```
---

1. Crie o arquivo `.env`:
```bash
touch .env
```

2. Adicione ao `.gitignore`:
```bash
echo ".env" >> .gitignore
```

3. Verifique que `.env` será ignorado:
```bash
git status
cat .gitignore
```

4. Faça commit do arquivo 
```bash
git add .gitignore
git commit -am 'configurando ignore'
```
5. Visualize o histórico:

```bash
git log --oneline --all
```
### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab2-sessao4.txt`.

# 🧪 Laboratório 2.5: Merge vs Rebase

### 🎯 Objetivo:
Entender a diferença entre `merge` e `rebase` na prática.


### 🎬 Início da Sessão

```bash
script lab2-sessao5.txt
```
---

### 1️⃣ Crie uma nova branch a partir do `main`:

```bash
git checkout -b feature
echo "linha feature" > arquivo.txt
git add arquivo.txt
git commit -m "commit na feature"
git branch
````

---

### 2️⃣ Volte ao `main` e adicione outra linha:

```bash
git checkout main
echo "linha main" > arquivo.txt
git add arquivo.txt
git commit -m "commit no main"
git branch
```
---

### 3️⃣ Merge (aborta merge):

```bash
git checkout feature
git merge main
git status
git merge --abort
```
---

### 4️⃣ Rebase (reescreve o histórico):

```bash
git reset --hard HEAD~1   # apaga ultimo commit do branch atual (feature)
git rebase main
```
---

### 🔍 Visualizar o histórico:

```bash
git log --oneline --all
```

> 💡 Compare a diferença visual no histórico com e sem merge.


### 🛑 Final da Sessão

```bash
exit
```
> Adicione o arquivo no Git `lab2-sessao5.txt`.

---

# 🧪 Laboratório 2.6: Rebase entre Branches

### 🎬 Início da Sessão

```bash
script lab2-sessao6.txt
````

---

1. Inicie um repositório e adicione um arquivo:

```bash
git checkout main
echo "linha base" > arquivo.txt
git add .
git commit -m "commit base"
```

2. Crie dois branches com alterações diferentes:

```bash
git checkout -b feature-123
echo "mudança A" >> arquivo.txt
git commit -am "Alteração no branch A"

git checkout main
git checkout -b feature-456
echo "mudança B" >> arquivo.txt
git commit -am "Alteração no branch B"
```

3. Faça rebase do `feature-123` sobre `feature-456`:

```bash
git checkout feature-123
git rebase feature-456
```

4. Caso ocorra conflito, edite `arquivo.txt`, resolva e finalize:

```bash
# Editar arquivo.txt manualmente
nano arquivo.txt
git add arquivo.txt
git rebase --continue
```

5. Verifique o histórico para entender a diferença entre rebase e merge:

```bash
git log --oneline --all
```

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab2-sessao6.txt`.

---

# 🧪 Laboratório: Instalando e Utilizando o GitHub Desktop

1. **Instalando o GitHub Desktop:**
    - Acesse o site oficial do GitHub Desktop em [https://desktop.github.com](https://desktop.github.com).
    - Faça o download da versão adequada para o seu sistema operacional (Windows ou macOS).
    - Siga as instruções de instalação fornecidas pelo instalador.
    - Após a instalação, abra o GitHub Desktop.

2. **Configurando o Repositório:**
    - No GitHub Desktop, clique em "File" (Arquivo) e selecione "Add Local Repository" (Adicionar Repositório Local).
    - Navegue até o diretório do seu projeto e selecione a pasta que contém o repositório.
    - Clique em "Add Repository" (Adicionar Repositório) para adicionar o repositório ao GitHub Desktop.

3. **Configurando Nome de Autor e Email:**
    - No GitHub Desktop, clique em "File" (Arquivo) e selecione "Options" (Opções).
    - Na guia "Git", preencha os campos "Name" (Nome) e "Email" (Email) com as suas informações.
    - Clique em "Save" (Salvar) para salvar as configurações.

4. **Realizando Commits:**
    - No GitHub Desktop, você verá uma lista de arquivos modificados no seu repositório.
    - Selecione os arquivos que deseja incluir no commit, marcando as caixas de seleção ao lado deles.
    - Digite uma mensagem descritiva para o commit no campo "Summary" (Resumo).
    - Clique em "Commit to master" (Commitar para o master) para realizar o commit.

5. **Sincronizando com o Repositório Remoto:**
    - Após realizar commits locais, você pode sincronizar as alterações com o repositório remoto.
    - Clique em "Repository" (Repositório) e selecione "Push" (Enviar).
    - O GitHub Desktop enviará as alterações para o repositório remoto.

---

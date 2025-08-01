# 📝 Registro da Sessão com `script`

Para comprovar a execução completa de cada laboratório:

1. Antes de iniciar os comandos, digite:

```bash
script lab1-sessaoN.txt
```

(Substitua `N` pelo número do laboratório.)

2. Realize todos os passos normalmente.

3. Ao final, digite:

```bash
exit
```

> Isso salvará um log da sessão, que pode ser entregue.

---

# 🧪 Laboratório 1.1: Histórico, Commits

## 🎯 Objetivo:
Explorar o histórico de commits, navegação por versões anteriores e reversão de mudanças no Git.

---

### 🎬 Início da Sessão

```bash
script lab1-sessao1.txt
```

---

### 📋 Passos:

1. Crie um diretório e entre nele:
```bash
mkdir git-workshop && cd git-workshop
```

2. Inicialize um repositório Git:
```bash
git init
```

3. Use o repositório já inicializado e execute:
```bash
echo "v1" > notas.txt
git add . && git commit -m "v1"
echo "v2" >> notas.txt && git commit -am "v2"
echo "v3" >> notas.txt && git commit -am "v3"
```

4. Visualize o histórico:
```bash
git log --oneline
```

5. Verifique uma versão antiga:
```bash
git checkout HEAD~2
cat notas.txt
git checkout main
```

6. Visualize o histórico:
```bash
git log --oneline
```

7. Desfaça o último commit com `reset`:
```bash
git reset --soft HEAD~1
git commit -m "Corrige v2 revertido"
```

8. Visualize o histórico:
```bash
git log --oneline
```
---
### 🛑 Final da Sessão
```bash
exit
```

> Adicione o arquivo no Git `lab1-sessao1.txt`.

---

# 🧪 Laboratório 1.2: Explorando o Histórico do Git no Terminal

Fará 5 alterações incrementais no arquivo `README.md` e usará comandos para explorar e manipular o histórico.

### 🎬 Início da Sessão

```bash
script lab1-sessao2.txt
```

1. Crie e registre o primeiro conteúdo:

   ```bash
   echo "v1" > README.md
   git add README.md
   git commit -m "v1"
   ```

2. Adicione novas linhas e registre mais 4 alterações:

   ```bash
   echo "v2" >> README.md && git commit -am "v2"
   echo "v3" >> README.md && git commit -am "v3"
   echo "v4" >> README.md && git commit -am "v4"
   echo "v5" >> README.md && git commit -am "v5"
   ```

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab1-sessao2.txt`.

---

# 🕵️ 🧪 Laboratório 1.3: Análise do Histórico


### 🎬 Início da Sessão

```bash
script lab1-sessao3.txt
```

* **Ver histórico simplificado**:

  ```bash
  git log --oneline
  ```

* **Ver detalhes do último commit (autor, e-mail, data, hash)**:

  ```bash
  git log -1
  ```

* **Ver autor e e-mail configurados globalmente**:

  ```bash
  git config user.name
  git config user.email
  ```

* **Comparar mudanças entre os últimos commits**:

  ```bash
  git diff HEAD~1 HEAD
  ```

### 🛑 Final da Sessão

```bash
exit
```
> Adicione o arquivo no Git `lab1-sessao3.txt`.
---

# 🧪 🧪 Laboratório 1.4: Manipulação do Histórico


### 🎬 Início da Sessão

```bash
script lab1-sessao4.txt
```

* **Reverter o último commit sem perder o histórico**:

  ```bash
  git revert HEAD
  ```

* **Voltar 2 commits e descartar as alterações posteriores**:

  ```bash
  git reset --hard HEAD~2
  ```

> ⚠️ Como o  `git reset --hard` funciona?


* **Visualize o histórico:**
```bash
git log --oneline
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab1-sessao4.txt`.

---

# 🧪 Laboratório 1.5: Blobs e Snapshot de Arquivos no Git

### 🎯 Objetivo:
Entender como o Git armazena o conteúdo dos arquivos em cada commit usando blobs e snapshots.

---

### 🎬 Início da Sessão

```bash
script lab1-sessao5.txt
```

---

### 📋 Passos:

1. Crie um arquivo:
```bash
echo "linha 1" > arquivo.txt
git add arquivo.txt
git commit -m "commit 1"
```

2. Verifique o hash do blob criado no commit:
```bash
git ls-tree HEAD
```

Exemplo de saída:
```
100644 blob e69de29bb2d1d6434b8b29ae775ad8c2e48c5391	arquivo.txt
```

Copie o hash do blob para o próximo passo.

3. Veja o conteúdo do blob armazenado:
```bash
git cat-file -p <hash-do-blob>
```

4. Faça uma nova alteração no arquivo:
```bash
echo "linha 2" >> arquivo.txt
git commit -am "commit 2"
```

5. Veja o novo hash do blob:
```bash
git ls-tree HEAD
```

6. Compare os blobs:
```bash
git cat-file -p <novo-hash>
git cat-file -p <hash-anterior>
```

> Você verá que o Git armazenou **um novo blob** apenas porque o conteúdo do arquivo mudou.

---

### ✅ Conclusão

- O Git armazena **blobs** para representar o conteúdo dos arquivos.
- Cada commit referencia um **snapshot completo do repositório**, mas **reutiliza blobs** para arquivos que **não foram alterados**.
- Isso torna o Git eficiente mesmo com snapshots completos.

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git lab1-session5.txt


# 🧪 Laboratório 1.6: Inspeção do diretório `.git/objects`

### 🎯 Objetivo:
Explorar o funcionamento interno do Git analisando os objetos armazenados no diretório `.git/objects`.

---

### 🎬 Início da Sessão

```bash
script lab1-session6.txt
```

---

### 📋 Passos:

1. Acesse o repositório

2. Crie um arquivo e faça o commit:
```bash
echo "linha 1" > arquivo.txt
git add arquivo.txt
git commit -m "algum commit"
```

3. Liste o conteúdo do diretório `.git/objects`:
```bash
ls .git/objects
```

4. Liste os arquivos armazenados como objetos:
```bash
find .git/objects -type f
```

5. Identifique o tipo de cada objeto usando o hash:
```bash
git rev-parse HEAD           # obter o hash do commit
git cat-file -t <hash>       # tipo do objeto
git cat-file -p <hash>       # conteúdo do objeto
```

6. Identifique os objetos internos:
```bash
git ls-tree HEAD
# Use os hashes retornados para:
git cat-file -t <hash>
git cat-file -p <hash>
```

> Teste para blobs (conteúdo de arquivos), trees (estrutura de diretórios) e commits (metadados + ponteiros).

---

### ✅ Conclusão

- O Git armazena tudo como objetos compactados com endereçamento por hash.
- Cada commit referencia uma **tree**, que referencia **blobs** (arquivos).
- Objetos inalterados são reutilizados entre commits, mantendo o Git eficiente.

---

### 🛑 Final da Sessão

```bash
exit
```

> Envie o arquivo `lab1-session6.txt` como evidência da execução.


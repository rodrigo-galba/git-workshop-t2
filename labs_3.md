# 🧪 Laboratório Avançado 3.1: Criando e Explorando Tags

### 🎯 Objetivo:
Entender e aplicar o comando `git tag` para marcar versões específicas no histórico do repositório.

---

### 🎬 Início da Sessão

```bash
script lab3-sessao1.txt
```
---

### 📋 Passos:

1. Crie três commits consecutivos:
```bash
echo "linha 1" > log.txt
git add log.txt
git commit -m "Commit 1"

echo "linha 2" >> log.txt
git commit -am "Commit 2"

echo "linha 3" >> log.txt
git commit -am "Commit 3"
```

2. Liste o histórico resumido:
```bash
git log --oneline
```

3. Crie tags em cada commit:
```bash
git tag v1.0 HEAD~2     # Tag no primeiro commit
git tag v1.1 HEAD~1     # Tag no segundo commit
git tag v1.2 HEAD       # Tag no terceiro commit
```

4. Liste todas as tags:
```bash
git tag
```

5. Visualize o commit associado a uma tag:
```bash
git show v1.1
```

6. Faça checkout de uma tag (modo detached):
```bash
git checkout v1.0
```

7. Retorne à branch principal:
```bash
git checkout main
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Envie o arquivo `lab3-sessao1.txt` como evidência da execução.

---

# 🧪 Laboratório Avançado 3.2: Automação com Git Hooks

### 🎯 Objetivo:
Criar e testar um `pre-commit` hook para bloquear commits com a palavra "TODO" no código.

---

### 🎬 Início da Sessão

```bash
script lab3-sessao2.txt
```

---

### 📋 Passos:

1. No seu repositório, verifique o diretório de hooks:
```bash
ls .git/hooks
```

2. Crie o hook `pre-commit`:
```bash
nano .git/hooks/pre-commit
```

Cole o conteúdo abaixo:
```bash
#!/bin/bash
if grep -r "TODO" *.py; then
  echo "❌ Commit bloqueado: remova TODOs do código."
  exit 1
fi
```

3. Torne o script executável:
```bash
chmod +x .git/hooks/pre-commit
```

4. Teste o hook:
```bash
echo "TODO: ajustar validação" > app.py
git add app.py
git commit -m "teste"
```

5. Remova o TODO e repita:
```bash
echo "Código limpo" > app.py
git add app.py
git commit -m "commit limpo"
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao2.txt`.


---

# 🧪 Laboratório 3.3: Utilizando o comando `git reset --soft`

### 🎬 Início da Sessão

```bash
script lab3-sessao3.txt
```

---

### 📋 Passos:

1. Certifique-se de que está no branch correto.
```bash
git branch # main
```
2. Crie um novo branch para testes
```bash
git log --oneline
git checkout -b test-reset
```

3. Desfaça um commit (mantendo as alterações):
```bash
git reset --soft HEAD~1
```

4. Verifique o status:
```bash
git status
git diff
```

5. Faça commit novamente
```bash
git add .
git commit -m 'agora vai'
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao3.txt`.

---

# 🧪 Laboratório 3.4: Utilizando o comando `git reset --hard`

### 🎬 Início da Sessão

```bash
script lab3-sessao4.txt
```

---

### 📋 Passos:

1. Certifique-se de que está no branch correto.
```bash
git branch # main
```

2. Visualize o histórico:
```bash
git log
git checkout -b test_hard
```

3. Desfaça um commit definitivamente:
```bash
git reset --hard HEAD~1
```

4. Verifique o status:
```bash
git status
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao4.txt`.

---

# 🧪 Laboratório 3.5: Utilizando o comando `git revert`

### 🎬 Início da Sessão

```bash
script lab3-sessao5.txt
```

---

### 📋 Passos:

1. Certifique-se de que está no branch correto.
```bash
git branch # main
```

2. Visualize o histórico:
```bash
git log
git checkout -b test_revert
```

3. Reverta um commit:
```bash
git revert HEAD~1
```

4. Verifique se o novo commit de reversão foi criado:
```bash
git status
```

5. Faça ajustes adicionais, se necessário.

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao5.txt`.
---

# 🧪 Laboratórios Avançados com `git tag`

## 💡 Introdução
Estes laboratórios complementam o uso de `git tag` abordando tags anotadas, exclusão e recriação, push para repositórios remotos e criação de branches a partir de tags.

---

# 🧪 Laboratório 3.6: Criando Tags Anotadas

### 🎬 Início da Sessão

```bash
script lab3-sessao6.txt
```

---

### 📋 Passos:

1. Crie um commit de exemplo:
```bash
echo "versão com nota" >> versao.txt
git add versao.txt
git commit -m "Commit com anotação de versão"
```

2. Crie uma **tag anotada**:
```bash
git tag -a v2.0 -m "Versão 2.0 com melhorias"
```

3. Liste as tags com detalhes:
```bash
git show v2.0
```

4. Verifique se é anotada:
```bash
git tag -n
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao6.txt`.

---

# 🧪 Laboratório 3.7: Deletando e Recriando Tags

### 🎬 Início da Sessão

```bash
script lab3-sessao7.txt
```

---

### 📋 Passos:

1. Crie uma tag leve:
```bash
git tag hotfix
```

2. Verifique sua criação:
```bash
git tag
```

3. Delete a tag:
```bash
git tag -d hotfix
```

4. Recrie como anotada:
```bash
git tag -a hotfix -m "Hotfix anotado"
git show hotfix
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao7.txt`.

---

# 🧪 Laboratório 3.8: Enviando Tags para o Repositório Remoto

### 🎬 Início da Sessão

```bash
script lab3-sessao8.txt
```

---

### 📋 Passos:

1. Crie uma tag local:
```bash
git tag release-1.0
```

2. Envie **somente a tag**:
```bash
git push origin release-1.0
```

3. Envie **todas as tags de uma vez**:
```bash
git push origin --tags
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao8.txt`.

---

# 🧪 Laboratório 3.9: Checkout e Branch a Partir de uma Tag

### 🎬 Início da Sessão

```bash
script lab3-sessao9.txt
```

---

### 📋 Passos:

1. Liste suas tags:
```bash
git tag
```

2. Faça checkout de uma tag:
```bash
git checkout v1.1
```

3. Crie um branch novo a partir da tag:
```bash
git switch -c branch-v1.1
```

4. Faça alterações:
```bash
echo "patch para v1.1" >> changelog.txt
git add . && git commit -m "patch para versão 1.1"
```

---

### 🛑 Final da Sessão

```bash
exit
```

> Adicione o arquivo no Git `lab3-sessao9.txt`.

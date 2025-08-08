# 🧪 **Laboratório Git Flow** - Release + Feature

```bash
# 1. Utilize o seu repositorio e garanta que possui branch main e develop
$ git branch
* main
develop

# 2. Crie uma feature a partir de develop
$ git checkout -b feature/cadastro-usuario develop
$ echo "formulário" > cadastro.txt
$ git add . && git commit -m "feat: cadastro inicial"
$ git push origin feature/cadastro-usuario

# 3. Abra um Pull Request de feature/cadastro-usuario para develop no GitHub
# (Realize merge pelo GitHub e marque branch para deleção após merge)

# 4. Faça pull da branch develop atualizada
$ git checkout develop
$ git pull origin develop

# 5. Mescle develop em main via Pull Request
# (Realize merge pelo GitHub e mantenha a branch develop)

# 6. Crie a branch de release a partir de main
$ git checkout main
$ git pull origin main
$ git checkout -b release/1.0.0
$ echo "versão 1.0.0" > versao.txt
$ git add . && git commit -m "release: ajustes finais"
$ git push origin release/1.0.0

# 7. Crie uma tag de versão
$ git tag -a v1.0.0 -m "versão 1.0.0"
$ git push origin v1.0.0

# 8. Mescle release em main via Pull Request
# (Realize merge pelo GitHub e marque branch para deleção após merge)

```
---
# 🧪 **Laboratório Git Flow** - Release + Bugfix

```bash
# 1. Utilize o seu repositorio e garanta que possui branch main e develop
$ git branch
* main
develop

# 2. Crie a branch de release a partir de develop
$ git checkout develop
$ git pull origin develop
$ git checkout -b release/1.4.0
$ echo "versão 1.4.0" > versao.txt
$ git add . && git commit -m "release: ajustes finais"
$ git push origin release/1.4.0

# 3. Crie um branch de correção (bugfix) para a release (release/1.4.0)
$ git checkout -b bugfix/1.4.0

# 4. realize a alteraçào onde for necessário
$ echo "validando nome do usuario" >> cadastro.txt
$ git add . && git commit -m "fix: correção de nome de usuário"

# 5. Mescle o bugfix na release via Pull Request
# (Realize merge pelo GitHub e marque branch para deleção após merge)

# 6. Crie uma tag de versão
$ git tag -a v1.4.0 -m "versão 1.4.0"
$ git push origin v1.4.0

# 7. Mescle release em main via Pull Request
# (Realize merge pelo GitHub e mantenha o branch após merge)
# Se houver conflito, resolva mantendo as duas versões.

# 8. Mescle release em develop via Pull Request
# (Realize merge pelo GitHub e marque branch para deleção após merge)
# Se houver conflito, resolva mantendo a versão da release.
```
---

# 🧪 **Laboratório Git Flow** - Release + Feature com conflito

```bash
# 1. Utilize o seu repositorio e garanta que possui branch main e develop
$ git branch
* main
develop

# 2. Crie uma feature a partir de develop
$ git checkout -b feature/cadastro-usuario develop
$ echo "formulário" > cadastro.txt
$ git add . && git commit -m "feat: cadastro inicial"
$ git push origin feature/cadastro-usuario

# 3. Crie outra feature a partir de develop (simulando outro usuario)
$ git checkout -b feature/correcao-usuario develop
$ echo "alteração de correção" > cadastro.txt
$ git add . && git commit -m "fix: correção de usuário"
$ git push origin feature/correcao-usuario

# 3. Abra um Pull Request de feature/cadastro-usuario para develop no GitHub
# (Realize merge pelo GitHub e marque branch para deleção após merge)

# 4. Faça pull da branch develop atualizada
$ git checkout develop
$ git pull origin develop

# 5. Mescle develop em main via Pull Request
# (Realize merge pelo GitHub e mantenha a branch develop)

# 6. Abra um Pull Request de feature/correcao-usuario para develop no GitHub
# (Resolva o conflito e realize merge pelo GitHub e marque branch para deleção após merge)

# 7. Mescle develop em main via Pull Request
$ git checkout -b fix/correcao-develop develop
$ git merge main
# Corrige o conflito e submete
$ git push origin fix/correcao-develop

# 8. Abra um Pull Request de fix/correcao-develop para develop no GitHub
# (Realize merge pelo GitHub e marque branch para deleção após merge)

# 9. Mescle develop em main via Pull Request
# (Realize merge pelo GitHub e mantenha a branch develop)

# 10. Crie a branch de release a partir de main
$ git checkout main
$ git pull origin main
$ git checkout -b release/1.1.0
$ echo "versão 1.1.0" > versao.txt
$ git add . && git commit -m "release: ajustes finais"
$ git push origin release/1.1.0

# 11. Crie uma tag de versão
$ git tag -a v1.1.0 -m "versão 1.1.0"
$ git push origin v1.1.0

# 12. Mescle release em main via Pull Request
# (Realize merge pelo GitHub e marque branch para deleção após merge)

```
---

# 🧪 **Laboratório Git Flow** - Hotfix

```bash
# 1. Utilize o seu repositorio e garanta que possui branch main e develop
$ git branch
* main
develop

# 2. Crie um branch a partir da ultima tag
$ git checkout v1.1.0
git switch -c hotfix/1.1.0

# 3. realiza a alteraçào onde for necessário
$ echo "validando CPF de usuario" >> cadastro.txt
$ git add . && git commit -m "fix: correção de CPF de usuário"

# 4. Abra um Pull Request de hotfix/fix-123 para main no GitHub
# (Realize merge pelo GitHub e mantenha a branch do hotfix)

# 5.  Crie uma tag de versão baseado em main atualizado
$ git checkout main
$ git pull origin main
$ git tag -a v1.2.0 -m "versão 1.2.0"
$ git push origin v1.2.0

# 6. Abra um Pull Request de hotfix/fix-123 para develop no GitHub
# (Realize merge pelo GitHub e marque branch para deleção após merge)
```

---

# 🧪 **Laboratório GitHub Flow** - Release

```bash
# 1. Utilize o seu repositorio e garanta que possui branch main
$ git branch
* main

# 2. Crie uma branch de funcionalidade
$ git checkout -b feature/ajuste-botao-revisado
$ echo "ajuste botão" > ajuste.txt
$ git add . && git commit -m "ajuste no botão de login"
$ git push origin feature/ajuste-botao-revisado

# 3. Abra um Pull Request de feature/ajuste-botao-revisado para main no GitHub
# (Realize merge pelo GitHub e marque branch para deleção após merge)

# 4.  Crie uma tag de versão baseado em main atualizado
$ git checkout main
$ git pull origin main
$ git tag -a v1.5.0 -m "versão 1.5.0"
$ git push origin v1.5.0
```
---

# 🧪 **Laboratório Trunk-Based** - Release

```bash
# 1. Utilize o seu repositório e garanta que possui branch main
$ git branch
* main

# 2. Crie uma branch de funcionalidade
$ git checkout -b devA-feature-x main
$ echo "início da funcionalidade A" > featureA.txt
$ git add . && git commit -m "feat: funcionalidade A"

# 3. Publique a branch
$ git push origin devA-feature-x

# 4. Volte para main e faça merge localmente
$ git checkout main
$ git merge devA-feature-x
$ git push origin main

# 5. Crie uma tag de release
$ git tag -a v1.6.0 -m "release 1.6.0"
$ git push origin v1.6.0

# 6. Crie uma branch de release
$ git checkout -b release/1.6.0
$ git push origin release/1.6.0

# 7. Volte para main e faça dois novos commits
$ git checkout main
$ echo "commit A" > a.txt && git add a.txt && git commit -m "feat: commit A"
$ echo "commit B" > b.txt && git add b.txt && git commit -m "feat: commit B"
$ git push origin main

# 8. Volte para a branch release e aplique cherry-pick de um dos commits
$ git checkout release/1.0.0
$ git cherry-pick <hash-do-commit-B>
$ git push origin release/1.0.0
```
---
# 🧪 **Laboratório Trunk-Based** - Hotfix

```bash
# 1. Utilize o seu repositório e garanta que possui branch main
$ git branch
* main

# 2. realiza a alteraçào onde for necessário
$ echo "validando Endereco de usuario" >> cadastro.txt
$ git add . && git commit -m "fix: correção de endereco de usuário"

# 3. Crie uma tag de release
$ git tag -a v1.6.1 -m "hotfix 1.6.0"
$ git push origin v1.6.1

# Se houverem mais erros, repetir o processo, garantindo novas tags para cada deploy em producao
```
---
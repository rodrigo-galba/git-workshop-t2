# 📂 Disciplina: Gestão de Configuração

## 🎓 Trabalho Final (Em dupla, entrega individual)

* Mantenha seu repositório **público**
* **Prazo limite:** Final da **sexta aula**, às **12:00 PM**
* **Nota:** Trabalho 1 (1 ponto) + Trabalho final (até 9 pontos)

### ✅ Requisitos:

* Git Bash
* Gitk (ou equivalente)
* Conta no GitHub

---

## 📆 Fases do Laboratório

### ✅ **Fase 1: Preparação Inicial**

#### Tarefa 1

Crie uma conta no GitHub, caso ainda não possua.

#### Tarefa 2

Realize um **fork** do repositório:
[https://github.com/rodrigo-galba-unifor/gestao-configuracao-trabalho-final](https://github.com/rodrigo-galba-unifor/gestao-configuracao-trabalho-final)

#### Tarefa 3

Crie uma **Issue** no repositório principal com as seguintes informações:

* **Título:** `Trabalho do aluno/a <seu-nome>`
* **Descrição:** Trabalho final de gestão de configuração. Número da sua matrícula.
* **Link do GitHub:** `https://github.com/<seu-usuario>`

#### Tarefa 4

Clone localmente o repositório que você forkou e crie um branch separado a partir do `main` com o nome `dev`. E mude para o branch dev.

#### Tarefa 5

Crie uma pasta com o seu **nome de usuário no GitHub**. Todas as tarefas abaixo devem ocorrer **somente dentro desse diretório**, exceto quando indicado o contrário.
Adicione um arquivo `README.md` dentro dessa pasta e **realize commit do arquivo**.

---

### ✅ **Fase 2: Commits e Boas Práticas**

#### Tarefa 6

Crie um arquivo `.env` com **cinco variáveis de ambiente fictícias** (chave e valor). Além disso, crie um arquivo `.env-template` contendo as mesmas chaves, mas com os valores em branco ou genéricos. O arquivo `.env-template` **deve ser versionado**. Ignore o arquivo `.env`.

Exemplo:

```
API_URL=https://exemplo.com
PORT=3000
DEBUG=true
USER=admin
TOKEN=123456
```

#### Tarefa 7

Crie um arquivo `credentials` e **garanta que ele seja ignorado pelo Git**. Realize commit das alterações se necessário.

#### Tarefa 8

No `README.md`, descreva o uso das variáveis de ambiente criadas. Realize commit das alterações.

#### Tarefa 9

Adicione uma seção ao `README.md` informando a **última alteração do log** feita. Realize commit das alterações.

#### Tarefa 10

Abra o `gitk` e capture um screenshot com todo o histórico de commits. Se houver muitos commits, tire mais de um screenshot. Faça commit da(s) imagem(ns).

#### Tarefa 11

No arquivo `alunos.md` (na raiz do projeto), adicione uma linha com o seu usuário GitHub/Nome do Aluno. Realize commit das alterações.

Em seguida, **delete o arquivo `alunos.md`** do repositório e **realize novo commit com essa remoção**.

---

### ✅ **Fase 3: Branches, Tags e Versionamento**

#### Tarefa 12

Publique o branch `dev` no GitHub.

#### Tarefa 13

Crie uma tag **semântica** no branch `dev` (ex: `v1.0.0-dev`) e submeta para o GitHub.

#### Tarefa 14

A partir do branch `dev`, crie o branch `stage`.

#### Tarefa 15

Apague completamente o último commit no branch `stage`. Realize commit das alterações se necessário.

#### Tarefa 16

Publique o branch `stage`.

#### Tarefa 17

Crie uma tag semântica no branch `stage` (ex: `v1.0.0-stage`) e envie para o GitHub.

#### Tarefa 18

Crie um branch `prod` baseado em `main`, ignorando quaisquer alterações pendentes.

#### Tarefa 19

Realize um merge do tipo squash com todos os commits feitos no stage na data atual. Faça commit do merge squash em prod.
Garanta que o branch prod possui somente o commit de merge-squash

#### Tarefa 20

Publique o branch `prod` no GitHub.

#### Tarefa 21

Crie uma tag semântica no `prod` (ex: `v1.0.0`) e submeta para o GitHub.

---

### ✅ **Fase 4: Pull Requests e Entrega Final**

#### Tarefa 22

Crie uma Pull Request no **seu repositório**: do branch `prod` para o branch `main`. Na descrição, resuma as alterações feitas.

#### Tarefa 23

Crie uma tag semântica no branch `main` no **seu repositório** (ex: `v1.0.0-release`) e submeta para o GitHub.

#### Tarefa 24

Crie uma **release** com a tag criada no **seu repositório**. Resuma as principais mudanças incluídas.

#### Tarefa 25

Crie uma Pull Request do **seu repositório** para o repositório principal original. Na descrição, informe:

* Link para cada branch criado (`dev`, `prod`, `stage`)
* Link para cada tag criada
* Link da release

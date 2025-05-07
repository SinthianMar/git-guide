
# 🧾  Guia de Versionamento com Git e GitHub

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sinthianmarques)
[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](https://www.oracle.com/java/)
[![Project](https://img.shields.io/badge/-Project-blueviolet?style=for-the-badge)]()

> **Git** é um sistema de controle de versão distribuído que permite rastrear mudanças no código, colaborar em projetos e manter histórico de versões. Com o Git, é possível gerenciar versões locais de um repositório, enquanto o **GitHub** é uma plataforma de hospedagem de código, que utiliza Git para sincronizar repositórios na nuvem, facilitando a colaboração entre desenvolvedores.

---

### ➟ Diferença entre Git e GitHub

| Ferramenta | Função                                                                                                   |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| **Git**    | Sistema de controle de versão distribuído que armazena e gerencia o histórico do seu projeto localmente. |
| **GitHub** | Plataforma online que hospeda seus repositórios Git, permitindo colaboração e visibilidade remota.       |

---

## 🛠️ Iniciando o Versionamento

### 1. **Inicializando o repositório**

Para iniciar o versionamento de um projeto, você deve inicializar um repositório Git dentro da pasta do seu projeto.

```bash
git init
```

### 2. **Configurando o repositório remoto (GitHub)**

Crie um repositório no GitHub e associe o repositório remoto ao seu repositório local:

```bash
git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
```

### 3. **Adicionando arquivos ao repositório**

Após realizar alterações no seu código, adicione os arquivos modificados ao Git para rastrear as mudanças:

```bash
git add .
```

### 4. **Fazendo o commit**

O commit é uma "fotografia" das mudanças que você fez, armazenada no repositório local. Para fazer um commit:

```bash
git commit -m "Mensagem do commit"
```

### 5. **Enviando para o repositório remoto**

Após o commit, você pode enviar suas mudanças para o GitHub (repositório remoto) com o `push`:

```bash
git push origin main
```

---

## ⚠️ Principais Erros e Soluções no Git

### ➤ **Erro: `push` rejeitado por diferenças no remoto**
**Mensagem:**  
> Updates were rejected because the remote contains work that you do not have locally.

**Causa:**  
Há alterações no repositório remoto que não estão presentes no seu repositório local.

**Solução:**
1. Faça o `pull` para integrar as mudanças do remoto:
   ```bash
   git pull origin main --rebase
   ```
2. Após resolver conflitos (se houver), faça o `push` novamente:
   ```bash
   git push origin main
   ```

---

### ➤ **Erro: `fatal: refusing to merge unrelated histories`**
**Mensagem:**  
> fatal: refusing to merge unrelated histories

**Causa:**  
Históricos diferentes entre o repositório local e remoto, como quando você cria um repositório no GitHub e já tem arquivos locais.

**Solução:**
Use a opção `--allow-unrelated-histories` ao fazer o `pull`:
```bash
git pull origin main --allow-unrelated-histories
```

---

### ➤ **Erro: `fatal: not a git repository (or any of the parent directories): .git`**
**Mensagem:**  
> fatal: not a git repository (or any of the parent directories): .git

**Causa:**  
Você está tentando executar comandos Git em uma pasta que não foi inicializada como repositório Git.

**Solução:**
1. Inicialize o repositório na pasta desejada:
   ```bash
   git init
   ```

---

### ➤ **Erro: `Your branch is ahead of 'origin/main' by X commits.`**
**Mensagem:**  
> Your branch is ahead of 'origin/main' by X commits.

**Causa:**  
Você tem commits locais que ainda não foram enviados para o repositório remoto.

**Solução:**
Envie suas alterações para o repositório remoto:
```bash
git push origin main
```

---

### ➤ **Erro: `commit` sem arquivos no Git**
**Mensagem:**  
> No changes added to commit

**Causa:**  
Você tentou fazer um commit sem adicionar arquivos ao Git (não usou `git add`).

**Solução:**
1. Adicione os arquivos ao staging:
   ```bash
   git add .
   ```
2. Após isso, faça o commit novamente:
   ```bash
   git commit -m "Mensagem do commit"
   ```

---

### ➤ **Erro: `fatal: Unable to create '.../.git/index.lock'`**
**Mensagem:**  
> fatal: Unable to create '.../.git/index.lock'

**Causa:**  
Isso ocorre quando o processo Git foi interrompido e o arquivo de bloqueio (`index.lock`) não foi removido.

**Solução:**
Apague o arquivo `index.lock` manualmente:
```bash
rm -f .git/index.lock
```

---

### ➤ **Erro: `Branch não encontrada no remoto`**
**Mensagem:**  
> fatal: 'origin/main' is not a commit and a branch 'main' cannot be created from it

**Causa:**  
O nome da branch no repositório remoto pode ser diferente, ou a branch que você está tentando acessar não existe no remoto.

**Solução:**
1. Verifique as branches disponíveis no repositório remoto:
   ```bash
   git branch -r
   ```
2. Se a branch `main` não existir no remoto, substitua por `master` ou outro nome de branch:
   ```bash
   git push origin master
   ```

---

### ➤ **Erro: `Conflitos de merge`**
**Mensagem:**  
> CONFLICT (content): Merge conflict in <arquivo>

**Causa:**  
Isso ocorre quando há mudanças incompatíveis entre sua versão local e o repositório remoto.

**Solução:**
1. Resolva os conflitos nos arquivos indicados.
2. Após resolver, faça o commit e complete o merge:
   ```bash
   git add <arquivo_resolvido>
   git commit -m "Resolvendo conflitos"
   ```

---

### ➤ **Erro: `fatal: Authentication failed for 'https://github.com/...`**
**Mensagem:**  
> fatal: Authentication failed for 'https://github.com/...'

**Causa:**  
Falha ao tentar autenticar com o GitHub, muitas vezes relacionada à autenticação via HTTPS ou credenciais incorretas.

**Solução:**
1. Use a autenticação via **token pessoal** em vez de senha.
2. Configure o Git Credential Manager para armazenar as credenciais de forma segura.

---

## 💡 Dicas de Uso do Git Bash e Terminal

- **Git Bash**: O Git Bash é uma interface de linha de comando que simula o terminal Unix, permitindo que você use comandos Git no Windows de forma eficiente.
- **Terminal (ou Git Bash)**: Você pode usar qualquer um dos dois para rodar comandos Git. A diferença é que o Git Bash proporciona uma interface mais amigável no Windows para comandos relacionados ao Git.

---

## 📝 Conclusão

Git e GitHub são ferramentas essenciais para o desenvolvimento de software moderno, permitindo versionamento eficiente, controle de alterações e colaboração em equipe. Este guia cobre os erros mais comuns e como corrigir, além de fornecer uma introdução clara sobre como trabalhar com Git e GitHub.

Por [Sinthian Marques ](https://github.com/SinthianMar) | [LinkedIn](https://www.linkedin.com/in/sinthianmarques) | sinthianmarquesjp@gmail.com


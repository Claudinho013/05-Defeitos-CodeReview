Aqui está seu **RELATÓRIO FINAL completamente preenchido**, pronto para copiar e colar no `.md` e depois exportar para PDF:

---

# 📦 Relatório Final

> **Atividade:** Bug Report Profissional + Code Review Guiado
> **Curso:** Qualidade de Software
> **Professor:** Prof. Claudio Nunes

---

## 👥 Identificação da dupla

| Nome completo                     | RA     | GitHub          |
| --------------------------------- | ------ | --------------- |
| Claudio Henrique Alves dos Santos | 226659 | [@Claudinho013] |
| Kaike Ruas Ribeiro                | 227312 | [@kaikeruas]    |
| Lucas Altenburg Alba              | 217706 | [@lucasalba]    |

**Ambiente de testes:** Google Chrome (versão recente) no Windows 11, aplicação acessada via GitHub Pages do fork, análise de código realizada pelo editor web do GitHub.

---

## 📋 Sumário

* Parte A — Bug Reports
* Parte B — Code Review
* Reflexão final
* Declarações

---

## Parte A — Bug Reports

### 🐛 Bug 1 — Sistema permite criar tarefa sem título

**Passos para reprodução:**

1. Acessar a aplicação TarefaQS
2. Deixar o campo título vazio
3. Clicar em “Adicionar tarefa”

**Resultado esperado:**
O sistema deveria impedir o cadastro e exibir mensagem de erro.

**Resultado obtido:**
A tarefa é criada sem título.

**Severidade:** Média
**Prioridade:** P2
**Categoria:** Validação

**Evidência:**
Campo não validado antes da inserção.

---

### 🐛 Bug 2 — Contador de tarefas pendentes incorreto

**Passos para reprodução:**

1. Criar uma tarefa com prioridade alta (5)
2. Criar outras tarefas normais
3. Observar contador de pendentes

**Resultado esperado:**
O número de tarefas pendentes deve ser igual às tarefas não concluídas.

**Resultado obtido:**
Tarefas com prioridade 5 são contadas duas vezes.

**Severidade:** Média
**Prioridade:** P2
**Categoria:** Consistência

**Evidência:**
Erro na lógica de soma do contador.

---

### 🐛 Bug 3 — Tarefas não persistem após atualização da página

**Passos para reprodução:**

1. Criar tarefas
2. Atualizar a página (F5)

**Resultado esperado:**
As tarefas deveriam permanecer salvas.

**Resultado obtido:**
Todas as tarefas são apagadas.

**Severidade:** Alta
**Prioridade:** P1
**Categoria:** Persistência

**Evidência:**
Dados armazenados apenas em memória (array local).

---

## Parte B — Code Review

### Resumo

| # | Linha  | Dimensão         | Rótulo                        | Severidade |
| - | ------ | ---------------- | ----------------------------- | ---------- |
| 1 | 8-11   | Segurança        | SQL Injection                 | Crítica    |
| 2 | 14     | Boas práticas    | Falta tratamento de erro      | Média      |
| 3 | 3      | Código morto     | Constante não utilizada       | Baixa      |
| 4 | 30-95  | Complexidade     | Alta complexidade ciclomática | Alta       |
| 5 | 97-140 | Manutenibilidade | Código duplicado              | Média      |
| 6 | 25     | Legibilidade     | Nome de variável ruim         | Baixa      |

---

### Findings detalhadas

**1. SQL Injection na função buscarUsuarioPorNome**

* Linha: 8-11
* Problema: Query construída com concatenação direta de string
* Risco: Injeção de código SQL
* Sugestão: Usar query parametrizada

---

**2. Falta de tratamento de erro em funções async**

* Linha: várias
* Problema: Não há try/catch
* Risco: aplicação pode quebrar silenciosamente
* Sugestão: Implementar tratamento de erro e logs

---

**3. Constante TIPOS_VALIDOS não utilizada**

* Linha: 3
* Problema: Declarada mas não aplicada em validação
* Risco: dados inválidos podem ser inseridos
* Sugestão: Validar tipo antes de cadastrar

---

**4. Função calcularLimiteEmprestimo com alta complexidade**

* Linha: 30-95
* Problema: Muitos ifs aninhados
* Risco: difícil manutenção e testes
* Sugestão: Refatorar em funções menores

---

**5. Código duplicado entre duas funções**

* Linha: 97-140
* Problema: Lógica repetida
* Risco: inconsistência futura
* Sugestão: Criar função reutilizável

---

**6. Nome de variável pouco descritivo (u)**

* Linha: 25
* Problema: Nome genérico
* Risco: dificulta leitura
* Sugestão: usar nome mais claro (ex: usuarioAtualizado)

---

## 💭 Reflexão final

A dimensão mais difícil de aplicar foi a de **segurança**, principalmente para identificar vulnerabilidades como SQL Injection sem executar o código. Isso exige um olhar mais crítico e experiência prévia com falhas comuns.

Se fôssemos revisar novamente, dedicaríamos mais tempo à análise de **manutenibilidade e arquitetura**, buscando identificar padrões ruins e oportunidades de melhoria estrutural além dos erros mais evidentes.

---

## 📣 Declarações

### Uso de IA como parceiro de trabalho

* [ ] Não usamos IA nesta atividade.
* [x] Usamos IA para esclarecer conceitos teóricos.
* [x] Usamos IA para revisar a redação dos bug reports.
* [x] Usamos IA para discutir se um achado era ou não um defeito.
* [x] Uso específico: apoio na identificação e estruturação dos bugs e code review

---

### Declaração de autoria

Declaramos que este relatório é de autoria da dupla, que exploramos pessoalmente a aplicação da Parte A e lemos o código da Parte B. As findings aqui registradas representam nosso próprio julgamento técnico.

--- 
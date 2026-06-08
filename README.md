# PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina

## Sobre o projeto

Este repositório contém um serviço simples de pagamentos bancários em Node.js.

A solução implementa diferentes estratégias de execução de pipelines para validação automática do código, garantindo qualidade e confiabilidade através de testes automatizados, análise estática de código, geração de cobertura de testes e análise das linguagens utilizadas no repositório.

---

## 🚀 Tecnologias Utilizadas

* Node.js
* JavaScript (ES Modules)
* GitHub Actions
* ESLint
* Mocha
* NYC (Istanbul Coverage)

---

## 📈 Análise de Linguagens

O projeto utiliza uma pipeline dedicada para gerar estatísticas automáticas das linguagens utilizadas no repositório por meio da Action **Github-Language-Stats**.

Após a execução do workflow `04-language-analytics.yaml`, o relatório fica disponível na pasta:

```text
stats/leaderboard/
```

Visualização do relatório:

```markdown
[Linguagens do Repositório]
(https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina/blob/main/stats/leaderboard_by_bytes.png)

(https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina/blob/main/stats/leaderboard_by_repos.png)

(https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina/blob/main/stats/leaderboard_by_weighted.png)
```

> Após a primeira execução com sucesso e o commit automático dos arquivos gerados, a imagem será exibida diretamente neste README.
---

## 📂 Estrutura do Projeto

```text
.
├── .github/
│   └── workflows/
├── src/
│   └── ServicoDePagamentoBancario.js
├── stats/
│   └── leaderboard/
│       ├── leaderboard_by_bytes.png
        ├── leaderboard_by_repos.png
        ├── leaderboard_by_weighted.png
├── src/
├── test/
│   └── ServicoDePagamentoBancario.test.js
├── eslint.config.js
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

## Instalação

Clone o repositório:

```bash
git clone https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina.git
```

Acesse a pasta do projeto:

```bash
cd ci-trabalho-de-conclusao-da-disciplina
```

Instale as dependências:

```bash
npm install
```

## Uso

### Executar testes

```bash
npm test
```

### Executar análise estática

```bash
npm run lint
```

### Gerar cobertura de testes

```bash
npm run coverage
```

### Executar build

```bash
npm run build
```

---

# 🔄 Pipelines GitHub Actions

O projeto possui quatro workflows responsáveis pela automação das validações e análises do código.

## 1️⃣ Execução Manual

Arquivo:

```text
.github/workflows/01-manual-exec.yaml
```

### Características

* Disparo manual através da aba **Actions** do GitHub.
* Controle de concorrência para evitar múltiplas execuções simultâneas.
* Execução utilizando Node.js 22.x.
* Timeout máximo de 15 minutos.

### Etapas executadas

1. Checkout do código
2. Configuração do Node.js
3. Instalação das dependências
4. Execução do ESLint
5. Execução dos testes
6. Geração da cobertura
7. Build da aplicação
8. Publicação do relatório de cobertura como artefato

---

## 2️⃣ Execução Agendada

Arquivo:

```text
.github/workflows/02-schedule.yaml
```

### Gatilhos

* Push nas branches `main`
* Pull Request para `main`
* Agendamento diário

### Cron configurado

```cron
44 7 * * *
```

Executa diariamente às **07:44 UTC** (04:44 no horário de Brasília).

### Ambiente

* Ubuntu Latest
* Node.js 18.x
* Node.js 20.x

### Etapas executadas

1. Checkout do código
2. Configuração do Node.js
3. Instalação das dependências
4. Execução do lint (quando disponível)
5. Execução dos testes
6. Execução da cobertura (quando disponível)

---

## 3️⃣ Execução por Push

Arquivo:

```text
.github/workflows/03-push.yaml
```

### Gatilhos

* Push nas branches `main`
* Pull Requests para `main`

### Ambiente

* Ubuntu Latest
* Node.js 18.x
* Node.js 20.x

### Etapas executadas

1. Checkout do código
2. Configuração do Node.js
3. Instalação das dependências
4. Execução do lint (quando disponível)
5. Execução dos testes
6. Execução da cobertura (quando disponível)

---

## 4️⃣ Análise de Linguagens

Arquivo:

```text
.github/workflows/04-language-analytics.yaml
```

### Objetivo

Gerar automaticamente estatísticas das linguagens utilizadas no repositório.

### Características

* Execução manual via GitHub Actions.
* Utilização da Action `StefVuck/Github-Language-Stats`.
* Geração de ranking de linguagens.
* Exportação em PNG.
* Commit automático dos relatórios gerados.

### Arquivos Gerados

```text
stats/leaderboard_by_bytes.png
stats/leaderboard_by_repos.png
stats/leaderboard_by_weighted.png
```

### Etapas executadas

1. Checkout do código
2. Coleta das linguagens do GitHub
3. Geração do relatório visual
4. Commit automático dos artefatos
5. Atualização do repositório

---

## 📊 Boas Práticas Aplicadas

* Uso de GitHub Actions para CI.
* Versionamento de código com Git.
* Execução automatizada de testes.
* Análise estática de código.
* Cobertura de testes.
* Análise automática de linguagens.
* Utilização de matriz de versões do Node.js.
* Cache de dependências NPM.
* Controle de concorrência.
* Publicação de artefatos.
* Execução agendada de pipelines.

---

## 🎯 Objetivos de Aprendizagem

Este projeto tem como finalidade demonstrar:

* Conceitos de Integração Contínua (CI)
* Automação de processos de validação
* GitHub Actions
* Testes automatizados
* Cobertura de testes
* Qualidade de código
* Análise de métricas do repositório
* Pipelines YAML

---

## 👨🏽‍💻 Autor

**Wedney Silva**

Disciplina: Integração Contínua – PGATS 2026/03

---

## 📄 Licença

Projeto desenvolvido exclusivamente para fins acadêmicos.

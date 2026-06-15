# Trabalho de Conclusão da Disciplina - Pipeline CI/CD com GitHub Actions

## 🎯 Objetivo

Desenvolver uma pipeline de integração contínua utilizando GitHub Actions para um projeto com testes automatizados, contemplando:

- Execução por push
- Execução manual
- Execução agendada (schedule)
- Geração de relatório de testes
- Armazenamento/publicação do relatório na pipeline
- Criação de um README explicando a solução e os conceitos utilizados

**Preferencialmente utilizar um projeto desenvolvido em outra disciplina da pós-graduação.**

---

## 📋 Requisitos

- **Trabalho individual**
- **Utilizar GitHub Actions** 
- **Pipeline executando com sucesso**
- **Testes automatizados executando com sucesso**
- **Relatório de execução armazenado na pipeline**
- **Aplicação correta dos conceitos estudados** 
- **Uso adequado das ferramentas escolhidas** 
- **Documentação completa no README**
---

## 📦 Entrega

### 📤 Enviar:

- **URL do repositório GitHub contendo a solução.** 
- **Evidência de pelo menos uma execução bem-sucedida da pipeline criada.**

### ⏳ Prazo

- **Data Limite:** 21/06/2026 às 23h59
- **Forma de entrega:** Plataforma da disciplina (aula 06)

---

## 📋 Sobre o Projeto

Este repositório contém um **serviço de pagamentos bancários** desenvolvido em Node.js com uma **pipeline de integração contínua** completa utilizando GitHub Actions.

A solução implementa estratégias automatizadas de validação de código, garantindo qualidade e confiabilidade através de:
- ✅ Testes automatizados
- ✅ Análise estática de código (ESLint)
- ✅ Cobertura de testes
- ✅ Análise automática de linguagens
- ✅ Múltiplas versões do Node.js (18.x, 20.x e 22.x)

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

O projeto utiliza um **job dedicado** dentro da pipeline para gerar estatísticas automáticas das linguagens utilizadas no repositório por meio da Action **StefVuck/Github-Language-Stats**.

### 📊 Relatórios Gerados

Após a execução da pipeline, os relatórios ficam disponíveis na pasta `stats/`:

| Tipo | Arquivo |
|------|---------|
| Ranking por Bytes | `leaderboard_by_bytes.png` |
| Ranking por Repositórios | `leaderboard_by_repos.png` |
| Ranking Ponderado | `leaderboard_by_weighted.png` |

### Visualização

Os relatórios são automaticamente commitados no repositório após cada execução:

![Linguagens do Repositório - Bytes](./stats/leaderboard_by_bytes.png)

![Linguagens do Repositório - Repositórios](./stats/leaderboard_by_repos.png)

![Linguagens do Repositório - Ponderado](./stats/leaderboard_by_weighted.png)
---

## 📂 Estrutura do Projeto

```
.
├── .github/
│   └── workflows/
│       └── pipeline.yaml              # Pipeline consolidada com todos os jobs
├── src/
│   └── ServicoDePagamentoBancario.js  # Serviço principal de pagamentos
├── stats/                              # Relatórios de análise de linguagens
│   ├── leaderboard_by_bytes.png
│   ├── leaderboard_by_repos.png
│   └── leaderboard_by_weighted.png
├── test/
│   └── ServicoDePagamentoBancario.test.js  # Testes automatizados
├── eslint.config.js                   # Configuração do ESLint
├── package.json                       # Dependências do projeto
├── package-lock.json                  # Lock file das dependências
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

# 🔄 Pipeline GitHub Actions

O projeto utiliza uma **pipeline consolidada** (`.github/workflows/pipeline.yaml`) que executa automaticamente em três cenários diferentes, com dois jobs principais:

## 📍 Gatilhos de Execução

| Evento | Descrição |
|--------|-----------|
| 🔄 **Push** | Executada ao fazer push na branch `main` |
| ⏰ **Schedule** | Executada diariamente às **04:44 UTC** |
| ▶️ **Manual** | Pode ser disparada manualmente pela aba **Actions** do GitHub |

## ⚙️ Configuração da Pipeline

```yaml
Sistema Operacional: Ubuntu Latest
Versões do Node.js: 18.x, 20.x e 22.x
Timeout Máximo: 15 minutos
Concorrência: Um job por branch (cancel-in-progress: true)
```

---

## 📋 Job 1: Testes e Validação

### Objetivo
Validar a qualidade do código através de testes, linting e cobertura de testes em múltiplas versões do Node.js.

### Etapas Executadas

| # | Etapa | Descrição |
|---|-------|-----------|
| 1 | **Checkout** | Faz download do código do repositório |
| 2 | **Setup Node.js** | Configura a versão do Node.js especificada (com cache npm) |
| 3 | **Instalar Dependências** | Instala dependências exatamente como especificado em `package-lock.json` |
| 4 | **ESLint** | Executa análise estática de código (se configurado) |
| 5 | **Testes** | Executa a suite de testes com Mocha |
| 6 | **Cobertura** | Gera relatório de cobertura com NYC (se configurado) |
| 7 | **Build** | Compila a aplicação (se configurado) |
| 8 | **Upload Artefato** | Publica o relatório de cobertura como artefato |

### Saída
- ✅ Testes executados em 3 versões do Node.js
- 📊 Relatório de cobertura (disponível em Artifacts)

---

## 📊 Job 2: Estatísticas de Linguagens

### Objetivo
Gerar automaticamente relatórios visuais das linguagens utilizadas no repositório.

### Características

- Depende da conclusão do Job 1 (`needs: test`)
- Usa a Action `StefVuck/Github-Language-Stats@v1.2.0`
- Gera 3 tipos de rankings (bytes, repositórios, ponderado)
- Realiza commit automático dos arquivos gerados

### Etapas Executadas

| # | Etapa | Descrição |
|---|-------|-----------|
| 1 | **Checkout** | Faz download do código |
| 2 | **Gerar Estatísticas** | Analisa linguagens do repositório via GitHub API |
| 3 | **Aguardar Geração** | Espera 10 segundos para garantir que os arquivos foram gerados |
| 4 | **Commit Automático** | Configura git e faz commit dos relatórios gerados |

### Arquivos Gerados

```
stats/
├── leaderboard_by_bytes.png       # Ranking por quantidade de bytes
├── leaderboard_by_repos.png       # Ranking por número de repositórios
└── leaderboard_by_weighted.png    # Ranking ponderado
```

### Saída
- 📈 Relatórios visuais commitados automaticamente na pasta `stats/`
- 🔄 Atualização automática do repositório remoto

---

## 📊 Boas Práticas Aplicadas

| Prática | Implementação |
|---------|--------------|
| 🔄 **CI/CD** | GitHub Actions para automação contínua |
| 🔀 **Versionamento** | Git com GitHub |
| 🧪 **Testes Automatizados** | Mocha com assertions |
| ✅ **Análise Estática** | ESLint para qualidade de código |
| 📈 **Cobertura de Testes** | NYC (Istanbul) |
| 📊 **Métricas** | Análise automática de linguagens |
| 🗂️ **Matriz de Versões** | Testa em múltiplas versões do Node.js |
| ⚡ **Cache** | NPM cache para acelerar builds |
| 🔒 **Concorrência** | Evita múltiplas execuções simultâneas |
| 📦 **Artefatos** | Armazena relatórios de cobertura |
| ⏰ **Agendamento** | Execução programada de validações |

---

## 🎯 Objetivos de Aprendizagem

Este projeto demonstra:

- Conceitos fundamentais de **Integração Contínua (CI)**
- Automação de processos de validação e deploy
- **GitHub Actions** e YAML workflows
- Testes automatizados com Mocha
- Cobertura de testes com NYC
- Análise de qualidade de código
- Geração automática de artefatos e relatórios
- Boas práticas de CI/CD

---

## 🚀 Como Usar

### Instalação

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

### Executar Localmente

```bash
# Executar testes
npm test

# Executar linting
npm run lint

# Gerar cobertura
npm run coverage

# Build do projeto
npm run build
```

### Disparar Pipeline Manualmente

1. Acesse a aba **Actions** no repositório GitHub
2. Selecione **Pipeline Completa**
3. Clique em **Run workflow**
4. Escolha a branch e clique em **Run workflow**

---

## 📋 Status da Pipeline

Para visualizar o status das execuções, acesse:

```
https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina/actions
```

Cada execução pode ser inspecionada para:
- ✅ Resultados dos testes
- 📊 Cobertura de testes
- 📝 Logs detalhados
- 📦 Artefatos gerados

---

## 👨🏽‍💻 Autor

**Wedney Silva**

**Disciplina:** Integração Contínua – PGATS 2026/03

---

## 📄 Licença

Projeto desenvolvido exclusivamente para fins acadêmicos.

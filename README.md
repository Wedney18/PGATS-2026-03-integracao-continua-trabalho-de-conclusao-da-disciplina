# Trabalho de Conclusão da Disciplina - Pipeline CI/CD com GitHub Actions

## 🎯 Objetivo

Desenvolver uma pipeline de integração contínua usando GitHub Actions para um projeto com testes automatizados, contemplando:

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

- **URL do repositório GitHub contendo a solução**
- **Evidência de pelo menos uma execução bem-sucedida da pipeline criada**

### ⏳ Prazo

- **Data Limite:** 21/06/2026 às 23h59
- **Forma de entrega:** Plataforma da disciplina (aula 06)

---

## 📋 Sobre o Projeto

Este repositório contém um **serviço de pagamentos bancários** desenvolvido em Node.js com uma **pipeline de integração contínua** usando GitHub Actions.

A solução implementa validações automatizadas para garantir qualidade e confiabilidade através de:

- ✅ Testes automatizados com Mocha
- ✅ Relatório de testes com Mochawesome
- ✅ Análise estática de código com ESLint
- ✅ Cobertura de testes com NYC
- ✅ Relatório de linguagens com GitHub Actions
- ✅ Testes em múltiplas versões do Node.js (18.x, 20.x, 22.x)

---

## 🚀 Tecnologias Utilizadas

- Node.js
- JavaScript (ES Modules)
- GitHub Actions
- ESLint
- Mocha
- Mochawesome
- NYC (Istanbul Coverage)

---

## 📂 Estrutura do Projeto

```
.
├── .github/
│   └── workflows/
│       └── pipeline.yaml              # Pipeline consolidada com todos os jobs
├── reports/                            # Relatórios Mochawesome gerados pelos testes
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

---

## 🔧 Instalação

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

---

## ▶️ Uso

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

## 📄 Relatórios

O teste gera um relatório Mochawesome em `reports/` com saída HTML e JSON.

A pipeline também publica os seguintes artefatos:

- `coverage/` — relatório de cobertura NYC
- `reports/` — relatório Mochawesome

---

# 🔄 Pipeline GitHub Actions

A pipeline está em `.github/workflows/pipeline.yaml` e é acionada por:

- `push` na branch `main`
- execução manual via `workflow_dispatch`
- agendamento diário (`schedule`)

## ⚙️ Configuração

- Sistema operacional: `ubuntu-latest`
- Versões do Node.js: `18.x`, `20.x`, `22.x`
- Timeout máximo: `15` minutos
- Concorrência: `cancel-in-progress: true`

---

## 🧪 Job 1: Testes e Validação

### Objetivo

Validar a qualidade do código com testes, linting e cobertura.

### Etapas

1. **Checkout** do repositório
2. **Configurar Node.js** com a versão da matriz
3. **Instalar dependências** com `npm ci`
4. **Executar ESLint**
5. **Executar testes** com `npm test`
6. **Upload do relatório Mochawesome**
7. **Executar cobertura** com `npm run coverage`
8. **Upload do artefato de cobertura**

### Saída

- ✅ Relatório Mochawesome gerado em `reports/`
- ✅ Relatório de cobertura gerado em `coverage/`
- ✅ Ambiente testado em 3 versões do Node.js

---

## 📊 Job 2: Estatísticas de Linguagens

### Objetivo

Gerar relatórios visuais das linguagens usadas no repositório.

### Características

- Depende do job de testes (`needs: test`)
- Usa `StefVuck/Github-Language-Stats@v1.2.0`
- Gera rankings por bytes, repositórios e ponderado
- Commita os resultados automaticamente em `stats/`

### Saída

- `stats/leaderboard_by_bytes.png`
- `stats/leaderboard_by_repos.png`
- `stats/leaderboard_by_weighted.png`

---

## ✅ Como reutilizar o README atual

Se você quer reaproveitar o conteúdo atual do README, siga estes passos:

1. **Copie o conteúdo** que descreve o projeto e a pipeline.
2. **Atualize as seções** com os comandos reais do seu projeto:
   - `npm test`
   - `npm run lint`
   - `npm run coverage`
3. **Inclua o novo relatório Mochawesome** em `reports/`.
4. **Remova referências antigas** a `test/unit`, `test/e2e` ou a relatórios separados.
5. **Mantenha a descrição da pipeline** atualizada para refletir o que está em `.github/workflows/pipeline.yaml`.

> Com isso, o README estará alinhado com o estado atual do seu repositório.

---

## 📌 Observações finais

- O relatório de testes agora é gerado pelo `mochawesome` em `reports/`.
- O relatório de cobertura ainda é gerado pelo `nyc` em `coverage/`.
- A pipeline publica ambos como artifacts.

---

## 👨🏽‍💻 Autor

Wedney Silva

Disciplina: Integração Contínua – PGATS 2026/03

---

## 📄 Licença

Projeto desenvolvido exclusivamente para fins acadêmicos.

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

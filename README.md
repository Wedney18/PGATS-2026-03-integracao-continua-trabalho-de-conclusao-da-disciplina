# Trabalho de Conclusão da Disciplina - Pipeline CI/CD com GitHub Actions

## Objetivo

Demonstrar uma pipeline de CI/CD com GitHub Actions para um projeto Node.js com testes automatizados e relatório de testes.

## O que está no projeto

- Serviço de pagamento em `src/`
- Testes em `test/`
- Relatório de testes gerado pelo `mochawesome` em `reports/`
- Cobertura de testes gerada pelo `nyc` em `coverage/`
- Pipeline GitHub Actions em `.github/workflows/pipeline.yaml`
- Estatísticas de linguagem em `stats/`

## Como usar

```bash
npm install
npm test
npm run lint
npm run coverage
```

## Pipeline

A workflow roda em:

- push na branch `main`
- execução manual (workflow_dispatch)
- schedule diário

### O que ela faz

- instala dependências
- executa ESLint
- executa testes com Mochawesome
- publica o relatório em `reports/`
- gera cobertura com NYC
- publica a cobertura como artifact
- gera relatórios de linguagem e salva em `stats/`

## Estrutura principal

```
.
├── .github/workflows/pipeline.yaml
├── src/ServicoDePagamentoBancario.js
├── test/ServicoDePagamentoBancario.test.js
├── reports/
├── coverage/
├── stats/
├── package.json
└── README.md
```

## Nota

O README foi simplificado para refletir o fluxo real do projeto, mantendo apenas as informações essenciais.

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

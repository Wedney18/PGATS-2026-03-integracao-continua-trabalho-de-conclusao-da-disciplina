# PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina

## 🎯Objetivo

Desenvolver uma pipeline de integração contínua utilizando GitHub Actions para um projeto com testes automatizados, contemplando:
- Execução por push.
- Execução manual.
- Execução agendada (schedule).
- Geração de relatório de testes.
- Armazenamento/publicação do relatório na pipeline.
- Criação de um README explicando a solução e os conceitos utilizados.

**Preferencialmente utilizar um projeto desenvolvido em outra disciplina da pós-graduação.**

📝**Requisitos**
- Trabalho individual.
- Utilizar GitHub Actions.
- Pipeline executando com sucesso.
- Testes automatizados executando com sucesso.
- Relatório de execução armazenado na pipeline.
- Aplicação correta dos conceitos estudados.
- Uso adequado das ferramentas escolhidas.
- Documentação completa no README.

📦**Entrega**

📤 Enviar:
- URL do repositório GitHub contendo a solução.
- Evidência de pelo menos uma execução bem-sucedida da pipeline.

⏳**Prazo: 21/06 às 23h59**

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

Após a execução do workflow `pipeline.yaml`, o relatório fica disponível na pasta:

```text
stats
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
│       ├── pipeline.yaml
├── src/
│   └── ServicoDePagamentoBancario.js
├── stats/
│       ├── leaderboard_by_bytes.png
        ├── leaderboard_by_repos.png
        ├── leaderboard_by_weighted.png
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

O projeto possui um workflow centralizado responsável pela automação das validações, testes, geração de artefatos e análise das linguagens utilizadas no repositório.

### Arquivo:

.github/workflows/pipeline.yml

### Gatilhos

* Push nas branches `main`
* Execução agendada (Schedule)
* Execução manual (Workflow Dispatch)

### Ambiente

* Ubuntu Latest
* Node.js 18.x
* Node.js 20.x
* Node.js 22.x

### Etapas executadas

🧪. Testes e Validação
1. Checkout do código
2. Configuração do Node.js
3. Instalação das dependências
4. Execução do lint (quando disponível)
5. Execução dos testes
6. Execução da cobertura (quando disponível)

---

## 📊 Estatísticas de Linguagens
Execução da Action Github-Language-Stats
Geração dos relatórios visuais
Commit automático dos arquivos gerados
Atualização do repositório


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

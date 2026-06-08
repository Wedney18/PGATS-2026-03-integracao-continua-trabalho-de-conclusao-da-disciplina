# Serviço de Pagamento Bancário

## Sobre o projeto

Este repositório contém um serviço simples de pagamentos bancários em Node.js.

A implementação inclui:

- registro de pagamentos com código de barras, empresa e valor
- classificação de pagamentos em `padrão` ou `cara` quando o valor é maior que 100
- consulta do último pagamento registrado
- testes automatizados com Mocha

## Tecnologias usadas

- Node.js
- JavaScript (ES Modules)
- Mocha
- ESLint
- NYC

## Estrutura do projeto

```text
.
├── .github/
│   └── workflows/
├── src/
│   └── ServicoDePagamentoBancario.js
├── stats/
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

## Arquivos principais

- `src/ServicoDePagamentoBancario.js`: classe que registra e consulta pagamentos
- `test/ServicoDePagamentoBancario.test.js`: testes que verificam os comportamentos do serviço

## Observações

- O projeto está configurado como ES Modules no `package.json`.
- O script `build` atualmente imprime uma mensagem de exemplo.

# Serviço de Pagamento Bancário

## 📖 Sobre o projeto

Este repositório contém um serviço simples de pagamentos bancários em Node.js, com testes automatizados usando **Mocha** e lint com **ESLint**.

O código implementa um serviço capaz de:

* registrar um pagamento com código de barras, nome da empresa e valor
* classificar o pagamento como `padrão` ou `cara` conforme o valor
* consultar o último pagamento registrado

---

## 🚀 Tecnologias usadas

* Node.js
* JavaScript (ES Modules)
* Mocha
* ESLint
* NYC (Istanbul)

---

## 📁 Estrutura do projeto

```text
.
├── .github/
│   └── workflows/  # arquivos de CI do GitHub Actions
├── src/
│   └── ServicoDePagamentoBancario.js
├── stats/          # relatórios gerados por workflows
├── test/
│   └── ServicoDePagamentoBancario.test.js
├── eslint.config.js
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

---

## ⚙️ Instalação

Clone o repositório:

```bash
git clone https://github.com/Wedney18/PGATS-2026-03-integracao-continua-trabalho-de-conclusao-da-disciplina.git
```

Entre na pasta do projeto:

```bash
cd ci-trabalho-de-conclusao-da-disciplina
```

Instale as dependências:

```bash
npm install
```

---

## ▶️ Como usar

### Executar os testes

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

### Executar build (script de exemplo)

```bash
npm run build
```

---

## 🧪 O que o código faz

### `src/ServicoDePagamentoBancario.js`

* `pagar(codigoBarras, empresa, valor)`
  * registra um pagamento
  * define a categoria como `cara` quando o valor é maior que 100
  * retorna `Pagamento realizado com sucesso.`

* `consultarUltimoPagamento()`
  * retorna o último pagamento registrado
  * retorna `Nenhum pagamento efetuado.` quando não há pagamentos

### `test/ServicoDePagamentoBancario.test.js`

* valida pagamento com valor menor que 100
* valida pagamento com valor maior que 100
* valida consulta quando não há pagamentos
* valida consulta do último pagamento registrado

---

## 📦 Scripts disponíveis

* `npm test` — executa os testes com Mocha
* `npm run lint` — executa o ESLint no projeto
* `npm run coverage` — executa os testes com NYC para gerar cobertura
* `npm run build` — executa um comando de build de exemplo

---

## 📌 Observações

* O projeto usa `type": "module"` no `package.json`, então os arquivos JavaScript são tratados como ES Modules.
* O serviço de pagamento e os testes estão prontos para serem estendidos com novas regras de validação ou armazenamento.

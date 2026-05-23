# payment-and-check

Projeto em JavaScript que simula um serviço de pagamento, permitindo realizar pagamentos e consultar o último pagamento registrado.

## Visão geral

Este projeto contém a classe `ServicoDePagamento` com dois métodos: `pagar` e `consultarUltimoPagamento`. Os pagamentos são armazenados internamente como objetos dentro de uma lista.

Cada pagamento possui as propriedades:

- codigoBarras
- empresa
- valor
- categoria (`'cara'` se valor > 100, `'padrão'` caso contrário)

## Exemplo de uso

```js
import { ServicoDePagamento } from './src/servicoDePagamento.js';

const servicoDePagamento = new ServicoDePagamento();

servicoDePagamento.pagar('0987-7656-3475', 'Samar', 156.87);

console.log(servicoDePagamento.consultarUltimoPagamento());
// { codigoBarras: '0987-7656-3475', empresa: 'Samar', valor: 156.87, categoria: 'cara' }
```

## Estrutura do projeto

```text
payment-and-check/
├── src/
│   └── servicoDePagamento.js
├── test/
│   └── servicoDePagamento.test.js
├── reports/
│   ├── resultado.json
│   └── resultado.html
├── package.json
└── README.md
```

## Como executar

```bash
npm install
npm test
```

Após rodar os testes, o relatório é gerado em:

- reports/resultado.json
- reports/resultado.html

## Cenários cobertos em teste

1. Pagamento com valor acima de 100 → categoria `'cara'`
2. Pagamento com valor abaixo de 100 → categoria `'padrão'`
3. Pagamento com valor exatamente igual a 100 → categoria `'padrão'`
4. Múltiplos pagamentos → retorna apenas o último
5. Nenhum pagamento realizado → retorna `undefined`
6. Objeto do pagamento contém todas as propriedades esperadas

## Tecnologias usadas

- Node.js (ES Modules)
- Mocha
- Mochawesome
- node:assert

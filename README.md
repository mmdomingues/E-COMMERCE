# 🛒 Desafio de Modelagem Conceitual – E-commerce

## 📘 Descrição do Projeto

Este repositório contém a modelagem conceitual de um sistema de e-commerce, desenvolvida como parte de um desafio de banco de dados. O objetivo é representar as principais entidades envolvidas em um sistema de vendas online, respeitando regras de negócio específicas e boas práticas de modelagem.

O projeto contempla desde o relacionamento entre cliente e conta, até o pedido, formas de pagamento e processo de entrega, incluindo especializações e restrições de integridade.

---

## 🎯 Objetivo do Desafio

Refinar o modelo apresentado inicialmente, com os seguintes requisitos:

- **Cliente PJ e PF**: Uma conta deve estar associada a apenas **um tipo de cliente** — Pessoa Física (PF) ou Pessoa Jurídica (PJ) — nunca ambos. Essa estrutura foi implementada por meio de especialização da entidade `Cliente`.

- **Pagamento**: Um pedido pode conter **mais de uma forma de pagamento cadastrada**, como parte no cartão e parte via Pix. Isso exige um relacionamento de um para muitos entre `Pedido` e `Pagamento`.

- **Entrega**: A entidade `Entrega` foi refinada para incluir:
  - **Status da entrega** (ex: “pendente”, “enviado”, “entregue”)
  - **Código de rastreamento**

---

## 🧱 Entidades e Relacionamentos

### 🔹 Cliente
- `id_cliente` (PK)
- `nome`
- `email`
- `telefone`

#### Especializações:
- **Cliente_PF**
  - `id_cliente` (FK)
  - `cpf`
  - `data_nascimento`
- **Cliente_PJ**
  - `id_cliente` (FK)
  - `cnpj`
  - `razao_social`

---

### 🔹 Conta
- `id_conta` (PK)
- `id_cliente` (FK)
- `data_criacao`
- `status`

Relação 1:1 com Cliente (por especialização: PF ou PJ)

---

### 🔹 Pedido
- `id_pedido` (PK)
- `id_conta` (FK)
- `id_entrega` (FK)
- `data_pedido`
- `valor_total`

Relação N:1 com Conta

---

### 🔹 Pagamento
- `id_pagamento` (PK)
- `id_pedido` (FK)
- `tipo_pagamento` (ex: cartão, pix, boleto)
- `valor_pagamento`

Relação N:1 com Pedido (um pedido pode ter múltiplos pagamentos)

---

### 🔹 Entrega
- `id_entrega` (PK)
- `status_entrega` (ex: pendente, enviado, entregue)
- `codigo_rastreamento`

Relação 1:1 com Pedido

---

### 🔹 Produto
- `id_produto` (PK)
- `nome`
- `descricao`
- `preco`

---

### 🔹 ItemPedido
- `id_pedido` (FK)
- `id_produto` (FK)
- `quantidade`
- `preco_unitario`

Entidade associativa N:N entre Pedido e Produto

---

## 📐 Modelo Conceitual (Diagrama Simplificado)

CLIENTE (id_cliente, nome, email, telefone)
│
├── CLIENTE_PF (id_cliente, cpf, data_nascimento)
└── CLIENTE_PJ (id_cliente, cnpj, razao_social)

CONTA (id_conta, id_cliente, data_criacao, status)
└── relaciona com CLIENTE (1:1)

PEDIDO (id_pedido, id_conta, id_entrega, data_pedido, valor_total)
└── relaciona com CONTA (N:1)

PAGAMENTO (id_pagamento, id_pedido, tipo_pagamento, valor_pagamento)
└── relaciona com PEDIDO (N:1)

ENTREGA (id_entrega, status_entrega, codigo_rastreamento)
└── relaciona com PEDIDO (1:1)

PRODUTO (id_produto, nome, descricao, preco)

ITEM_PEDIDO (id_pedido, id_produto, quantidade, preco_unitario)
└── relaciona PEDIDO com PRODUTO (N:N)


---

## 📁 Estrutura do Projeto

📦 desafio-modelagem-ecommerce
└── README.md


> Todo o conteúdo está contido neste único arquivo `README.md`, conforme exigido no desafio.

---

## 🧠 Considerações Finais

- A modelagem respeita os princípios de normalização e integridade referencial.
- A especialização de `Cliente` permite representar PF e PJ de forma adequada.
- O relacionamento entre `Pedido` e `Pagamento` permite múltiplas formas de pagamento por transação.
- O rastreamento de entregas foi incorporado diretamente na entidade `Entrega`.

---

## 👨‍💻 Autor

Desenvolvido por **[Seu Nome Aqui]**  
GitHub: [@seu-usuario](https://github.com/seu-usuario)

---

## 📝 Licença

Este projeto está licenciado sob os termos da licença MIT.


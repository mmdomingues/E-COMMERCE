# Projeto Conceitual: Modelo de Banco de Dados para E-commerce

## Descrição do Projeto

Este projeto apresenta o modelo conceitual de um sistema de e-commerce, contemplando clientes Pessoa Física (PF) e Pessoa Jurídica (PJ), múltiplas formas de pagamento, pedidos e entregas com status e código de rastreio.

### Requisitos principais:

- Clientes podem ser PF ou PJ, mas não os dois ao mesmo tempo.
- Cada cliente pode possuir diversas formas de pagamento cadastradas.
- Pedidos estão vinculados a contas de clientes.
- Entregas possuem status (Pendente, Em trânsito, Entregue) e código de rastreio.

## Diagrama Conceitual

O diagrama a seguir mostra as entidades, seus atributos principais e os relacionamentos entre elas, incluindo a especialização Cliente → Cliente_PF e Cliente_PJ.

![Diagrama Conceitual](modelo_conceitual.png)

## Estrutura do Repositório


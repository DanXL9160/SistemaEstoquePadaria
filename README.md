# SistemaEstoquePadaria
Sistema em Java para controle de estoque de uma padaria fictícia
# 🥖 Sistema de Controle de Estoque - Padaria Fictícia

Este projeto consiste em um sistema de gerenciamento e controle de estoque desenvolvido em Java com persistência em banco de dados MySQL, projetado para atender às necessidades operacionais de uma padaria de forma simples, rápida e organizada.

---

## 🛠️ Tecnologias e Arquitetura

* **Linguagem:** Java (Versão 17 ou 21)
* **Gerenciador de Dependências:** Maven
* **SGBD:** MySQL (Driver: `mysql-connector-j` versão 8.4.0)
* **Padrão Arquitetural:** Camadas (Model, DAO, Conexão)

---

## 📋 Levantamento de Requisitos

Abaixo estão listados os Requisitos Funcionais (o que o sistema faz) e os Requisitos Não Funcionais (características técnicas e restrições do sistema).

### 🔹 Requisitos Funcionais (RF)

* **RF01 - Cadastrar Produtos:** O sistema deve permitir o cadastro de novos produtos contendo nome, data de validade, quantidade atual e quantidade mínima esperada.
* **RF02 - Registrar Categoria:** O sistema deve permitir associar cada produto a uma categoria específica (ex: Pães, Bolos, Bebidas, Frios).
* **RF03 - Alerta de Estoque Mínimo:** O sistema deve emitir um alerta visual/notificação automática sempre que a quantidade atual de um produto for menor do que a quantidade mínima definida.
* **RF04 - Atualizar Quantidade em Estoque:** O sistema deve permitir a entrada (acréscimo) e saída (decréscimo) manual de itens no estoque.
* **RF05 - Filtrar por Categoria:** O sistema deve permitir a listagem de produtos filtrados por uma categoria selecionada pelo usuário.
* **RF06 - Filtrar por Vencimento:** O sistema deve permitir a filtragem de produtos que estejam com a data de validade vencida ou próximos do vencimento (janela de 7 dias).

### 🔸 Requisitos Não Funcionais (RNF)

* **RNF01 - Banco de Dados Relacional:** O sistema deve obrigatoriamente persistir os dados em um banco de dados MySQL.
* **RNF02 - Integridade e Conexão:** A conexão com o banco de dados deve conter tratamento de exceções (`try-catch`) para garantir a estabilidade do software e evitar vazamento de memória.
* **RNF03 - Portabilidade:** O projeto deve utilizar o Maven para que as dependências do banco de dados sejam baixadas automaticamente em qualquer ambiente de desenvolvimento (como o IntelliJ).
* **RNF04 - Desempenho de Consultas:** As consultas e filtros de estoque e validade devem ser executados de forma nativa pelo banco de dados (utilizando funções como `CURDATE` e `DATE_ADD`), otimizando o tempo de resposta da aplicação.

---

## 🗄️ Estrutura do Banco de Dados (Dados Iniciais)

O sistema opera com a tabela `produtos` estruturada da seguinte forma para os testes iniciais de validação:

| Produto | Categoria | Validade | Quantidade | Quant. Mínima |
| :--- | :--- | :--- | :--- | :--- |
| Pão Francês | Pães | 2026-05-20 | 50 | 30 |
| Bolo de Chocolate | Bolos | 2026-05-22 | 5 | 10 |
| Leite Integral | Bebidas | 2026-06-01 | 12 | 8 |
| Presunto | Frios | 2026-05-25 | 3 | 6 |

---

## 📂 Estrutura do Projeto no IntelliJ

```text
SistemaEstoquePadaria 
│ 
├── src 
│ ├── conexao 
│ │   └── Conexao.java      # Tratamento da conexão com o MySQL
│ ├── model 
│ │   └── Produto.java      # Classe da entidade Produto
│ ├── dao 
│ │   └── ProdutoDAO.java   # Execução das consultas e comandos SQL
│ └── Main.java             # Execução principal do sistema

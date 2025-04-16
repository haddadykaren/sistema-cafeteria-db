
# Sistema de Banco de Dados para Cafeteria ☕

Este repositório contém a modelagem e os scripts SQL de criação e inserção de dados para um sistema simples de gerenciamento de pedidos de uma cafeteria. O projeto foi desenvolvido como parte da disciplina **Desenvolvimento Web com Frameworks e HTML/CSS**, vinculada ao projeto de extensão **Trilhas Formativas para Aprendizagem Online (AMV.130421)** do curso de **Tecnologia da Informação** - UFMS.

## 📌 Objetivo

Modelar um banco de dados relacional para armazenar informações sobre produtos e pedidos, permitindo o controle de vendas em uma cafeteria. Além disso, aplicar o uso de **Git** como ferramenta de versionamento de código.

## 📂 Estrutura do Banco de Dados

### Tabelas criadas:

- **produtos**: armazena os itens vendidos na cafeteria.
- **pedidos**: registra os pedidos realizados, vinculando-os aos produtos.

### Exemplo de atributos:

#### produtos
- `id` (int, PK)
- `nome` (varchar)
- `preco` (decimal)
- `categoria` (varchar)

#### pedidos
- `id` (int, PK)
- `produto_id` (int, FK → produtos.id)
- `quantidade` (int)
- `data_pedido` (date)

## 💾 Executando o script

Para testar o banco de dados, utilize um gerenciador como MySQL Workbench ou phpMyAdmin. Execute o conteúdo do arquivo `script.sql` para criar as tabelas e inserir os dados.

## 🧠 Aprendizados

- Modelagem de banco de dados relacional.
- Escrita de comandos SQL de criação e inserção.
- Uso de versionamento com Git e GitHub.

## 🔗 Repositório

Acesse o script completo clicando no arquivo [`script.sql`](./script.sql).

---
CREATE TABLE produtos (
    id_produto INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    preco DECIMAL(5,2) NOT NULL,
    descricao VARCHAR(255)
);

CREATE TABLE pedidos (
    id_pedido INT PRIMARY KEY AUTO_INCREMENT,
    id_produto INT,
    quantidade INT NOT NULL,
    data_pedido DATE,
    FOREIGN KEY (id_produto) REFERENCES produtos(id_produto)
);

-- Inserção de registros em produtos
INSERT INTO produtos (nome, preco, descricao) VALUES 
('Café Expresso', 5.50, 'Café forte e concentrado'),
('Capuccino', 6.90, 'Café com leite e espuma'),
('Pão de queijo', 4.00, 'Pão de queijo mineiro tradicional');

-- Inserção de registros em pedidos
INSERT INTO pedidos (id_produto, quantidade, data_pedido) VALUES 
(1, 2, '2025-04-15'),
(2, 1, '2025-04-16'),
(3, 3, '2025-04-16');
git add banco_cafeteria.sql README.md
git commit -m "Adiciona script SQL para criação e população das tabelas produtos e pedidos"
git push origin main
git commit -m "Adiciona script SQL com modelagem de banco de dados para cafeteria"

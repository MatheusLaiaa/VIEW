# BANCO DE DADOS VIEW

## METODOLOGIA 

Essa atividade tem o objetivo de trazer conhecimentos em Banco De Dados, essa atividade tem o objetivo principal autilizaçao do VIEW.

## PASSO A PASSO DA ATIVIDADE PROPOSTA PELO TUTOR

![image](https://github.com/MatheusLaiaa/VIEW/assets/144149403/09eb86b6-16e1-40fa-985f-d6547fab5581)


### Crie uma view que mostra todos os produtos e suas respectivas marcas;

CREATE VIEW produtos_com_marcas AS
SELECT produtos.nome AS nome_produto, marcas.nome AS nome_marca
FROM produtos
JOIN marcas ON produtos.marca_id = marcas.id;

### Crie uma view que mostra todos os produtos e seus respectivos fornecedores;

CREATE VIEW produtos_com_fornecedores AS
SELECT produtos.nome AS nome_produto, fornecedores.nome AS nome_fornecedor
FROM produtos
JOIN fornecedores ON produtos.fornecedor_id = fornecedores.id;

### Crie uma view que mostra todos os produtos e seus respectivos fornecedores e marcas;

CREATE VIEW produtos_com_fornecedores_marcas AS
SELECT produtos.nome AS nome_produto, fornecedores.nome AS nome_fornecedor, marcas.nome AS nome_marca
FROM produtos
JOIN fornecedores ON produtos.fornecedor_id = fornecedores.id
JOIN marcas ON produtos.marca_id = marcas.id;

### Crie uma view que mostra todos os produtos com estoque abaixo do mínimo;

CREATE VIEW produtos_com_estoque_baixo AS
SELECT *
FROM produtos
WHERE estoque < estoque_minimo;

### Adicione o campo data de validade. Insira novos produtos com essa informação;

ALTER TABLE produtos
ADD data_validade DATE;

INSERT INTO produtos (nome, marca_id, fornecedor_id, estoque, estoque_minimo, preco, data_validade)
VALUES ('Novo Produto', 1, 2, 50, 10, 19.99, '2023-12-31');

### Crie uma view que mostra todos os produtos e suas respectivas marcas com validade vencida;

CREATE VIEW produtos_com_validade_vencida AS
SELECT produtos.nome AS nome_produto, marcas.nome AS nome_marca
FROM produtos
JOIN marcas ON produtos.marca_id = marcas.id
WHERE data_validade < CURRENT_DATE;

### Selecionar os produtos com preço acima da média.

CREATE VIEW produtos_preco_acima_media AS
SELECT *
FROM produtos
WHERE preco > (SELECT AVG(preco) FROM produtos);











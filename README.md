CREATE TABLE FARMACIA 
( 
    id_farmacia INT PRIMARY KEY,  -- Adicionado um identificador único
    tel_farmacia VARCHAR(15),    -- Ajustado para aceitar números telefônicos
    nome_farmacia VARCHAR(100),  -- Ajustado para nomes de farmácia
    end_farmacia VARCHAR(200),   -- Ajustado para endereços
    CNPJ_farmacia VARCHAR(14)    -- Ajustado para formato de CNPJ
); 

CREATE TABLE PRODUTO 
( 
    id_produto INT PRIMARY KEY,  -- Adicionado identificador único
    valor_produto DECIMAL(10,2), -- Ajustado para valores monetários
    qtd_produto INT,             -- Quantidade do produto
    cod_produto VARCHAR(50)      -- Código do produto
); 

CREATE TABLE FARMACEUTICO 
( 
    id_farmaceutico INT PRIMARY KEY, -- Adicionado identificador único
    RG_farmaceutico VARCHAR(12),    -- Ajustado para RG
    nome_farmaceutico VARCHAR(100)  -- Nome do farmacêutico
); 

-- Correção das tabelas de relacionamento
CREATE TABLE trabalha 
( 
    id_farmacia INT,  
    id_farmaceutico INT,  
    PRIMARY KEY (id_farmacia, id_farmaceutico), -- Ajustado para chave composta
    FOREIGN KEY (id_farmacia) REFERENCES FARMACIA (id_farmacia),
    FOREIGN KEY (id_farmaceutico) REFERENCES FARMACEUTICO (id_farmaceutico)
); 

CREATE TABLE vende 
( 
    id_farmacia INT,  
    id_produto INT,  
    PRIMARY KEY (id_farmacia, id_produto), -- Ajustado para chave composta
    FOREIGN KEY (id_farmacia) REFERENCES FARMACIA (id_farmacia),
    FOREIGN KEY (id_produto) REFERENCES PRODUTO (id_produto)
); 

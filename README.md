# passo a passo de um banco de dados : Criação de um banco de dados SQL
Tuturial de como criar um  banco de dados SQL que organiza
as informaçoes de 'livros', 'editora', 'autores' e 'assuntos'.
Este guia será dividido em etapas para demonstrar desde a 
criação de tabela, chaves e até manipulação/consulta de dados.

## Resumo de estrutura SQL
 * CREATE  para   criar 'Banco de dados ' ou ' Tabelas'
 * ALTER para adicionar ou modificar colunas
 * DROP para remover 'Banco de dados' ou ' 'Tabelas'
 * INSERT para adicionar registros na tabela
 * UPDATE para atualizar os registros
 * DELETE para remover os registros
 * SELECT para consultar e vizualizar dados 

 ## Passo 1: criação do banco de dados e das Tabelas

 #### 1.1 criando o DB

 

 CREATE DATABASE biblioteca;
 USE biblioteca;



#### 1.2 Criando a tabela 'editora'


CREATE TABLE editora (
    id_editora INT PRIMARY KEY AUTO_INCREMENT,
    nome_editora VARCHAR(100) NOT NULL,
    pais VARCHAR(50)
);




#### 1.3 Criando a tabela 'autor'


CREATE TABLE autor(
    id_autor INT PRIMARY KEY AUTO_INCREMENT,
    nome_autor VARCHAR(200) ,
    data_nascimento DATE
);



#### 1.4 Criando a tabela 'assunto'


CREATE TABLE assunto(
    id_assunto INT PRIMARY KEY AUTO_INCREMENT,
    descricao_assunto VARCHAR(200) NOT NULL
   );




#### 1.5 Criando a tabela 'livro'


CREATE TABLE livro(
    id_livro INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(150) NOT NULL,
    ano_publicacao YEAR, 
    FOREING KEY(id_editora) REFERENCES editora(id_editora),
    FOREING KEY(id_autor) REFERENCES editora(id_autor),
    FOREING KEY(id_assunto) REFERENCES editora(id_assunto),
   );
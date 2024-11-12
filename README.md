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

   #### 1.6 Criando uma tabela EXTRA
A tabela EXTRA vai servir para exemplificar a exclusão

CREATE TABLE extra(
    id INT PRIMARY KEY AUTO_INCREMENT,
    produtos VARCHAR(50),
    quantidade INT (20),
    preco DOUBLE NOT NULL
);


## Passo 2: editar tabelas usando 'ALTER'
Após a criação da tabela, podemos adicionar novos campos. Vamos adicionar uma coluna 'email' na ta tabela 'autor'

SQL
ALTER TABLE autor
ADD COLUMN email VARCHAR(100);


### Passo 3:Remover tabela usando 'DROP'
Se precisar remover uma tabela usamos o comando 'DROP'. Neste exemplo vamos remover a tabela 'EXTRA'.

SQL
 DROP TABLE extra;


### Passo 4: Inserindo dados usando 'INSERT'
Agora que as tabelas já estão prontas, vamos inserir dados nelas.

#### 4.1 Inserindo dados na tabela 'editora'
SQL
INSERT INTO editora(nome_editora, pais)
VALUES
('Editora Alfa', 'Brasil'),
('Editora Beta', 'Portugal'),
('Editora Bertrand Brasil', 'Brasil');


#### 4.2 Inserindo dados na tabela 'autor'
SQL
INSERT INTO autor(nome_autor, data_nascimento, email)
VALUES
('Jorge Amado', '1912-08-10', 'jorginho@gmail.com'),
('Machado de Assis', '1839-06-21', 'machadinho@gmail.com'),
('Matt Heig', '1975-06-03', 'matt@gmail.com');


#### 4.3 Inserindo dados na tabela 'assunto'
SQL
INSERT INTO assunto(descricao_assunto)
VALUES
('Ficção'),
('Romance'),
('Mistério'),
('Terror');

#### 4.4 Inserindo dados na tabela 'livros'
SQL
INSERT INTO livro(titulo, ano_publicacao, editora, autor, assunto)
VALUES
('Capitães da Areia',1937,1,1,4),
('DOM CASMURRO', 1899,2,2,4),
('A Biblioteca da Meia Noite',2020, 3,3,3),
('Memorias Postumas de Bras cubas',1881, 3,2,2);


### Passo 5: atualizando os dados usando 'UPDATE'
Podemos atualizar os dados com o comando UPTADE. Vamos corrigir a data de publicação do livro 'Capitães da Areia'

SQL
UPDATE livro
SET ano_publicacao = 1938
WHERE titulo = 'Capitães da Areia';


### Passo 6: Excluindo os dados usando 'DELETE'
Para remover os registros de uma tabela usamos o comando 'DELETE'.
Vamos excluir o livro Memorias Postumas de Bras cubas'.

SQL
DELETE FROM livro
WHERE id_livro = 8;


## Passo 7:Consultando os dados usando 'SELECT'
É possivel selecionar os dados para visualizar da forma como quiser.
Para isso usamos o comando 'SELECT'

#### Passo 7.1:Selecionar todos os livros com suas editoras e autores
Vamos usar dados das tabelas 'livros', 'editora', 'autor' e ' assunto' usando o comando 'JOIN'
### Passo 6:Excluido os dados usando 'DELETE'
Para remover os registros de uma tabela usamos o comando 'DELETE'.
Vamos excluir o livro Memorias Postumas de Bras cubas'.

SQL
SELECT livro.titulo AS nome,
       editora.nome_editora AS editora,
       autor.nome_autor AS autor,
       assunto.descricao_assunto AS tema,        livro.ano_publicacao AS ano                                     

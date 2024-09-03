# Biblioteca

Este projeto contém um banco de dados para gerenciar uma biblioteca. O banco de dados foi criado para armazenar informações sobre autores, livros e empréstimos de livros.

## Estrutura do Banco de Dados

O banco de dados `Biblioteca` possui as seguintes tabelas:

### 1. Tabela `Autores`

Armazena informações sobre os autores.

- **AutorID** (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do autor.
- **Nome** (VARCHAR(100), NOT NULL): Nome do autor.
- **Nacionalidade** (VARCHAR(100)): Nacionalidade do autor.

### 2. Tabela `Livros`

Armazena informações sobre os livros.

- **LivroID** (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do livro.
- **Titulo** (VARCHAR(255), NOT NULL): Título do livro.
- **AutorID** (INT): Identificador do autor (chave estrangeira referenciando `Autores`).
- **AnoPublicacao** (YEAR): Ano de publicação do livro.
- **Genero** (VARCHAR(50)): Gênero do livro.

### 3. Tabela `Emprestimos`

Armazena informações sobre os empréstimos de livros.

- **EmprestimoID** (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do empréstimo.
- **LivroID** (INT): Identificador do livro (chave estrangeira referenciando `Livros`).
- **DataEmprestimo** (DATE, NOT NULL): Data do empréstimo.
- **DataDevolucao** (DATE): Data de devolução do livro.
- **NomeUsuario** (VARCHAR(100), NOT NULL): Nome do usuário que fez o empréstimo.

## Instruções para Configuração

1. **Criar o Banco de Dados**

   Execute o seguinte comando para criar o banco de dados:

   CREATE DATABASE Biblioteca;
Selecionar o Banco de Dados
USE Biblioteca;
Criar as Tabelas

Execute os scripts SQL fornecidos para criar as tabelas Autores, Livros e Emprestimos.

Inserir Dados

Insira dados nas tabelas usando os scripts fornecidos.

Consultas e Atualizações

Execute as consultas e atualizações fornecidas para gerenciar e consultar os dados.

Consultas Exemplo
Listar todos os livros com os nomes de seus autores:
SELECT Livros.Titulo, Autores.Nome AS Autor, Livros.AnoPublicacao
FROM Livros
JOIN Autores ON Livros.AutorID = Autores.AutorID;
Listar os empréstimos que ainda estão em aberto:
SELECT Emprestimos.EmprestimoID, Livros.Titulo, Emprestimos.DataEmprestimo,
Emprestimos.NomeUsuario
FROM Emprestimos
JOIN Livros ON Emprestimos.LivroID = Livros.LivroID
WHERE Emprestimos.DataDevolucao IS NULL;
Atualizar a data de devolução de um empréstimo específico:
UPDATE Emprestimos
SET DataDevolucao = '2024-08-22'
WHERE EmprestimoID = 1;
Remover um livro e os registros de empréstimos associados a ele:
DELETE FROM Emprestimos
WHERE LivroID = 1;

DELETE FROM Livros
WHERE LivroID = 1;
Licença
Este projeto está licenciado sob a Licença MIT.

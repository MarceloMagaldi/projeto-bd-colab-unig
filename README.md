Este notebook Python, projetado para ser executado no Google Colab, demonstra as operações essenciais de um sistema de gerenciamento de banco de dados (SGBD) usando SQLite. Ele simula um cenário simples de uma loja, lidando com clientes, produtos e vendas.

1 . Conexão e Criação do Banco de Dados:

Ele importa as bibliotecas sqlite3 (para interagir com o SQLite) e os (para operações de sistema, como remover arquivos).
Define o nome do arquivo do banco de dados como loja.db.
Verifica se o arquivo loja.db já existe e o remove para garantir que cada execução comece com um banco de dados limpo.
Estabelece uma conexão com o banco de dados loja.db. Se o arquivo não existir, o SQLite o cria automaticamente.

2 . Criação de Tabelas:

O código cria três tabelas:
Clientes: Armazena informações básicas dos clientes (ID, nome, e-mail). O id é a chave primária (PRIMARY KEY).
Produtos: Armazena detalhes dos produtos (ID, nome do produto, preço). O id é a chave primária.
Vendas: Registra as transações de vendas (ID da venda, ID do cliente, ID do produto, quantidade e data da venda). Esta tabela possui duas chaves estrangeiras (FOREIGN KEY): id_cliente que se refere ao id da tabela Clientes e id_produto que se refere ao id da tabela Produtos. Isso estabelece um relacionamento entre as tabelas.
Após a criação das tabelas, as alterações são salvas no banco de dados (conn.commit()).

3 . Inserção de Dados:

Um script é executado para inserir dados de exemplo nas tabelas recém-criadas:
São inseridos dados de três clientes na tabela Clientes.
São inseridos dados de quatro produtos na tabela Produtos.
São inseridos dados de quatro vendas na tabela Vendas, com os IDs dos clientes e produtos correspondentes, simulando transações. A data e hora atuais são usadas para o campo data_venda.

4 . Consultas (SELECT):

O código realiza diversas consultas SQL para demonstrar a recuperação de dados:
Consulta Simples (Clientes): Seleciona e exibe todos os registros da tabela Clientes.
Consulta Simples com Condição (Produtos): Seleciona e exibe produtos cujo preço é superior a R$ 200,00.
Consulta com JOIN (Vendas Detalhadas): Esta é uma consulta mais avançada. Ela une as tabelas Vendas, Clientes e Produtos para exibir informações detalhadas de cada venda, incluindo o nome do cliente e o nome do produto, além do valor total da venda (quantidade * preço unitário). Os resultados são ordenados pela data da venda.
Consulta com JOIN e WHERE (Produtos de um Cliente Específico): Encontra e exibe os nomes dos produtos distintos que foram comprados por "Ana Silva", mostrando como filtrar resultados através de relações de tabela.
Consulta de Agregação (Total Gasto por Cliente): Calcula e exibe o valor total gasto por cada cliente, usando as funções SUM e GROUP BY para agregar os dados de vendas por cliente. Os resultados são ordenados pelo gasto total em ordem decrescente.

5 . Exibição dos Resultados:

Após cada operação de consulta (SELECT), os dados recuperados do banco de dados são iterados e impressos diretamente na tela do Google Colab, ou seja, na saída da célula de código.

6 . Fechamento da Conexão:

Finalmente, a conexão com o banco de dados é fechada (conn.close()). Isso é importante para liberar os recursos do sistema e garantir que todas as alterações sejam salvas de forma definitiva.

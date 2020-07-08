# rhs-teste-desenvolvedora-junior


## Objetivo


O objetivo deste teste é verificar sua habilidade para escrever sistemas, onde pretendo analisar seu padrão de código, lógica e capacidade de seguir as orientações do projeto.


## Requisitos


Para esse teste, esperamos que você utilize:


1. PHP, se possível, na atual versão estável e, caso prefira, pode usar algum framework que te deixe confortável.
1. MySQL ou PostgreSQL, como banco relacional.


A aplicação que irá escrever deverá funcionar em um terminal, inclusive a saída, sem a necessidade de uma versão web e, também, não é necessário escrever testes unitários, mas esses, caso sejam escritos, serão levados em conta na avaliação.


Além do código da aplicação, a documentação de como executar a mesma também é um requisito. Você pode fazer a documentação no **README.md** do seu projeto e é necessário indicar como executar sua aplicação, criar as tabelas do banco de dados e configurar a aplicação para se comunicar o banco de dados.


## O que será avaliado?


1. Uso da PSR
1. Nomes objetivos para variáveis, funções e classes
1. Tratamento de erros
1. Responsabilidade única para funções e classes
1. Duplicidade de código
1. Modelo e normalização das tabelas do banco de dados
1. Documentação


## O que você precisa desenvolver?


Nós gostaríamos que você escrevesse uma aplicação que permita pesquisar, cadastrar e remover filmes e categorias, levando em conta que um filme deve ter uma ou mais categoria, como, por exemplo, ação, aventura, romance, terror e etc.


Abaixo, descreveremos alguns cenários que a sua aplicação deverá atender e que usaremos como base para testar o funcionamento da mesma.


Crie um repositório git com o seu código e, assim que terminar, envie o link do mesmo para avaliação. Caso tenha alguma dúvida, sinta-se a vontade para perguntar.


## Cenários


### Pesquisar categoria sem critério com resultados


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar categoria
* E não indicar um critério de busca
* Então espero que seja apresentada uma lista com todas as categorias cadastradas
* E que essa lista esteja ordenada por ordem alfabética


### Pesquisar categoria por categoria com resultados


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar categoria
* E indicar o nome completo ou parcial de uma categoria
* Então espero que seja apresentada uma lista de categorias cadastradas
* E que essa lista tenha apenas categorias que iniciem com ou que sejam iguais ao critério de busca informado
* E que essa lista esteja ordenada por ordem alfabética


### Pesquisar categoria sem resultados


* Dado que eu sou um usuário
* Quando eu executar o comando para pesquisar categoria
* E nenhum resultado for encontrado
* Então espero que seja apresentada uma mensagem indicando que não foram encontrados resultados para a busca


### Pesquisar categoria com erro


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar categoria
* E ocorrer um erro não previsto nessa busca
* Então espero que seja apresentada uma mensagem indicando o erro ocorrido


### Cadastrar categoria com sucesso


* Dado que sou um usuário
* Quando eu executar o comando para cadastrar categoria
* E indicar o nome da categoria
* Então espero que seja verificado a duplicidade da categoria
* E que a categoria seja cadastrada no banco de dados
* E que seja apresentada uma mensagem indicando que a categoria foi cadastrada


### Cadastrar categoria com erro


* Dado que sou um usuário
* Quando eu executar o comando para cadastrar categoria
* E ocorrer um ou mais dos erros abaixo:
    * Categoria não indicada
    * Categoria em branco
    * Erro diverso com o banco de dados
    * Erro não previsto nesse cadastro
* Então espero que a categoria não seja cadastrada
* E que seja apresentada uma mensagem indicando o erro ocorrido ao cadastrar a categoria


### Remover categoria com sucesso


* Dado que sou um usuário
* Quando eu executar o comando para remover categoria
* E indicar o ID da categoria
* Então espero que seja verificada a viabilidade da remoção da categoria
* E que a categoria seja removida do banco de dados
* E que seja apresentada uma mensagem indicando que a categoria foi removida


### Remover categoria que é a única vinculada em um filme


* Dado que sou um usuário
* Quando eu executar o comando para remover categoria
* E indicar o ID da categoria
* E a categoria for a única categoria existente em um ou mais filmes
* Então espero que a categoria não seja removida
* E que seja exibida uma mensagem indicando o erro ocorrido ao remover a categoria
* E uma lista dos filmes que possuem somente aquela categoria


### Remover categoria com erro


* Dado que sou um usuário
* Quando eu executar o comando para remover categoria
* E ocorrer um ou mais dos erros abaixo:
    * ID da categoria não indicado
    * Categoria não encontrada
    * Erro diverso com o banco de dados
    * Erro não previsto nessa remoção
* Então espero a categoria não seja removida
* E que seja apresentada uma mensagem indicando o erro ocorrido ao remover a categoria


### Pesquisar filme sem critério com resultados


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar filme
* E não indicar um critério de busca
* Então espero que seja apresentada uma lista com todos os filmes cadastrados
* E espero que essa lista seja esteja ordenada pelo nome do filme e por ordem alfabética


### Pesquisar filme por nome com resultados


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar filme
* E indicar o nome do filme
* Então espero que seja apresentada uma lista de filmes cadastrados
* E que essa lista tenha apenas filmes que iniciem com ou que sejam iguais ao critério de busca informado
* E espero que essa lista seja esteja ordenada pelo nome do filme e por ordem alfabética


### Pesquisar filme por categoria com resultados


* Dado que sou um usuário
* Quando eu executar o comando para pesquisar filme
* E indicar o ID da categoria
* Então espero que seja apresentada uma lista de filmes cadastrados
* E que essa lista tenha apenas filmes que estejam vinculados com a categoria informada
* E espero que essa lista seja esteja ordenada pelo nome do filme e por ordem alfabética


### Pesquisar filme sem resultados


* Dado que eu sou um usuário
* Quando eu executar o comando para pesquisar filme
* E nenhum resultado for encontrado
* Então espero que seja apresentada uma mensagem indicando que não foram encontrados resultados para a busca


### Cadastrar filme com sucesso


* Dado que sou um usuário
* Quando eu executar o comando para cadastrar filme
* E indicar o nome do filme
* E indicar um ou mais ID de categoria
* Então espero que seja verificado a duplicidade do nome do filme
* E que seja verificado a existência das categorias
* E que o filme seja cadastrado no banco de dados
* E que seja apresentada uma mensagem indicando que o filme foi cadastrado


### Cadastrar filme com erro


* Dado que sou um usuário
* Quando eu executar o comando para cadastrar filme
* E ocorrer um ou mais dos erros abaixo:
    * Nome do filme não indicado
    * Nenhum ID de categoria indicado
    * Nome de filme duplicado
    * Categoria não encontrada
    * Erro diverso com o banco de dados
    * Erro não previsto nesse cadastro
* Então espero que o filme não seja cadastrado
* E que seja apresentada uma mensagem indicando o erro ocorrido ao cadastrar o filme


### Remover filme com sucesso


* Dado que sou um usuário
* Quando eu executar o comando para remover filme
* E indicar o ID do filme
* Então espero que seja verificada a viabilidade da remoção do filme
* E que o filme seja removido do banco de dados
* E que seja apresentada uma mensagem indicando que o filme foi removida


### Remover filme com erro


* Dado que sou um usuário
* Quando eu executar o comando para remover filme
* E ocorrer um ou mais dos erros abaixo:
    * ID do filme não indicado
    * Filme não encontrado
    * Erro diverso com o banco de dados
    * Erro não previsto nessa remoção
* Então espero o filme não seja removido
* E que seja apresentada uma mensagem indicando o erro ocorrido ao remover o filme

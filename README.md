# rhs-teste-desenvolvedora-junior


## Objetivo


O objetivo deste teste é verificar sua habilidade para escrever sistemas, onde pretendo analisar seu padrão de código, lógica e capacidade de seguir as orientações do projeto.


## Requisitos


Para esse teste, espero que você utilize:


1. PHP, se possível, na atual versão estável e, caso prefira, pode usar algum framework que te deixe confortável.
1. MySQL ou PostgreSQL, como banco relacional.


A aplicação que irá escrever deverá executar em um terminal, inclusive a saída, sem a necessidade de uma versão web e, também, não é necessário escrever testes unitários, mas esses, caso sejam escritos, serão levados em conta na avaliação.


Além do código da aplicação, a documentação de como executar a mesma também é um requisito. Você pode fazer a mesma sobrescrevendo no **README.md** do seu projeto e parta do princípio que eu tenho o PHP e um banco de dados instalado, mas que esse banco de dados não tem nenhuma tabela, além de ter um usuário e senha próprios, ou seja, é interessante você indicar como configurar os dados de acesso do banco de dados na sua aplicação.


Pretendo testar sua aplicação utilizando Docker, mas você não precisa entregar Dockerfile ou docker-compose.yml com o seu projeto. Caso entregue, claro, utilizarei o arquivo, mas o mesmo não será considerado como critério de avaliação.


## O que será avaliado e por quê?


1. Padrões, nesse caso, PSR. Porque padrões encurtam uma série de discussões e facilita a leitura do código para várias pessoas.
1. Nomes para variáveis, funções e classes. Porque nome de variáveis, funções e classes bem escritas são essenciais para um bom entendimento do seu código, mais inclusive, que comentários.
1. Tratamento de erros. Porque todo código tende a resultar em algum erro, em algum momento, seja por problemas de entrada, seja por lógica, e é importante que o código esteja pronto para lidar com esses erros, sem quebrar a aplicação.
1. Responsabilidade das funções e classes. Porque uma função e classe que tenha apenas uma única responsabilidade é mais fácil de testar, reaproveitar e entender.
1. Duplicidade. Porque se um código já atende uma demanda, não há a necessidade de repetir o mesmo.
1. Modelo e normalização das tabelas do banco de dados. Porque por se tratar de um banco de dados relacionais, é importante que os dados estejam relacionados, mas sem duplicar os dados do banco de dados.
1. Documentação. Porque uma boa documentação facilita o entendimento da aplicação, desde a execução até sobre o que a mesma faz.


## O que você precisa desenvolver?


Eu gostaria que você escrevesse uma aplicação que permita pesquisar, cadastrar e remover filmes e categorias, levando em conta que um filme deve ter uma ou mais categoria, como, por exemplo, ação, aventura, romance, terror e etc.


Abaixo, descreverei alguns cenários que a sua aplicação deverá atender e que usarei como base para testar o funcionamento da mesma.


Se possível, crie um repositório para fazer esse teste e, quando concluir o mesmo, me envie o link do seu repositório para eu avaliar. Caso tenha alguma dúvida, sinta-se a vontade para me perguntar.


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

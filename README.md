# PotatoCore


O Desafio consiste na importação de um banco de dados em excel com as informações sobre Lotofacil, o objetivo é extrair e tratar o arquivo pelo python e criar um sistema de banco de dados para armazenar os dados transformados.

## Instalação



 - Certifique-se de que você tem os seguintes aplicativos instalados no computador:

 1- Jumpyter e Vscode
 2- Python
 3- SQL server
 4- SQL Menagement Studio


 - Antes de Rodar o código no Vscode verifique no código a variável 'dados_conexao ' e altere o servidor, você pode encontrar o nome do seu servidor acessando a barra de pesquisa do windows e digitando 'CMB' logo que abrir a tela do prompt escreva 'hostname' e ele irá devolver o nome do seu servidor, abra o SQL Menagement Studio para executar o código que irá criar o seu banco de dados e a tabela com as mesmas colunas do arquivo em excel que foi importado para o python 'Lotofacil.xlsx' utilize o seguinte código:

 CREATE DATABASE PotatoCore
USE PotatoCore
CREATE TABLE LOTOFACIL( 
    Concurso INT,
	Data_Sorteio DATE,
	Bola1 INT,
	Bola2 INT,
	Bola3 INT,
	Bola5 INT,
	Bola6 INT,
	Bola7 INT,
	Bola8 INT,
	Bola9 INT,
	Bola10 INT,
	Bola11 INT,
	Bola12 INT,
	Bola13 INT,
	Bola14 INT,
	Bola15 INT,
	Ganhadores_15_acertos INT,
	Cidade_UF VARCHAR(500),
	Rateio_15_acertos DECIMAL(10,2),
	Ganhadores_14_acertos INT,
	Rateio_14_acertos DECIMAL(10,2),
	Ganhadores_13_acertos INT,
	Rateio_13_acertos DECIMAL(10,2),
	Ganhadores_12_acertos INT,
	Rateio_12_acertos DECIMAL(10,2),
	Ganhadores_11_acertos INT,
	Rateio_11_acertos DECIMAL(10,2),
	Acumulado_15_acertos DECIMAL(10,2),
	Arrecadacao_Total DECIMAL(10,2),
	Estimativa_Prêmio DECIMAL (10,2),
	Acumulado_sorteio_especial_Lotofácil_da_Independência DECIMAL(10,2),
	Observação VARCHAR(500),
	Ano_do_Sorteio INT,
	Mês_do_Sorteio INT,
	Dia_do_Sorteio INT)

    ### Depois de executado o código no SQL você pode então executar o código em python no jupyter ou na extensão dele no VSCODE. Os arquivos tanto da tabela em excel quanto do código criado em python estão anexados no repositório.









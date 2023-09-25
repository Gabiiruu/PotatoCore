# PotatoCore
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

    Depois de executado o código no SQL você pode então executar o código em python no jupyter ou na extensão dele no VSCODE.

##### Código Python

    pip install pandas pyodbc

    
##### Importando a base de dados

import pandas as pd
import pyodbc 
import numpy as np
tabela_df = pd.read_excel('Lotofacil.xlsx')



##### os dados da coluna data estão sendo interpretados como um objeto e não como data sendo assim alterei o formato da coluna:


tabela_df['Data Sorteio'] = pd.to_datetime(tabela_df['Data Sorteio'], format='%d/%m/%Y')

##### para facilitar análises com datas acrescentei 3 colunas extraindo dia, mês e ano e não só a data completa

tabela_df['Ano do Sorteio'] = tabela_df['Data Sorteio'].dt.year
tabela_df['Mês do Sorteio'] = tabela_df['Data Sorteio'].dt.month
tabela_df['Dia do Sorteio'] = tabela_df['Data Sorteio'].dt.day

##### As colunas com valores monetários estavam sendo reconhecidas como objetos ao invés de float, sendo assim foi necessário alterar o formato dessas colunas.

tabela_df['Rateio 15 acertos'] = tabela_df['Rateio 15 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Rateio 15 acertos'] = tabela_df['Rateio 15 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Rateio 15 acertos'] = tabela_df['Rateio 15 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Rateio 15 acertos'] = tabela_df['Rateio 15 acertos'].astype (np.float32, copy = False)
tabela_df['Rateio 15 acertos'] = tabela_df['Rateio 15 acertos'].round(2)

tabela_df['Rateio 14 acertos'] = tabela_df['Rateio 14 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Rateio 14 acertos'] = tabela_df['Rateio 14 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Rateio 14 acertos'] = tabela_df['Rateio 14 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Rateio 14 acertos'] = tabela_df['Rateio 14 acertos'].astype (np.float32, copy = False)
tabela_df['Rateio 14 acertos'] = tabela_df['Rateio 14 acertos'].round(2)

tabela_df['Rateio 13 acertos'] = tabela_df['Rateio 13 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Rateio 13 acertos'] = tabela_df['Rateio 13 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Rateio 13 acertos'] = tabela_df['Rateio 13 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Rateio 13 acertos'] = tabela_df['Rateio 13 acertos'].astype (np.float32, copy = False)
tabela_df['Rateio 13 acertos'] = tabela_df['Rateio 13 acertos'].round(2)

tabela_df['Rateio 12 acertos'] = tabela_df['Rateio 12 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Rateio 12 acertos'] = tabela_df['Rateio 12 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Rateio 12 acertos'] = tabela_df['Rateio 12 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Rateio 12 acertos'] = tabela_df['Rateio 12 acertos'].astype (np.float32, copy = False)
tabela_df['Rateio 12 acertos'] = tabela_df['Rateio 12 acertos'].round(2)


tabela_df['Rateio 11 acertos'] = tabela_df['Rateio 11 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Rateio 11 acertos'] = tabela_df['Rateio 11 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Rateio 11 acertos'] = tabela_df['Rateio 11 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Rateio 11 acertos'] = tabela_df['Rateio 11 acertos'].astype (np.float32, copy = False)
tabela_df['Rateio 11 acertos'] = tabela_df['Rateio 11 acertos'].round(2)

tabela_df['Acumulado 15 acertos'] = tabela_df['Acumulado 15 acertos'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Acumulado 15 acertos'] = tabela_df['Acumulado 15 acertos'].apply(lambda x: str(x).replace('.',''))
tabela_df['Acumulado 15 acertos'] = tabela_df['Acumulado 15 acertos'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Acumulado 15 acertos'] = tabela_df['Acumulado 15 acertos'].astype (np.float32, copy = False)
tabela_df['Acumulado 15 acertos'] = tabela_df['Acumulado 15 acertos'].round(2)


tabela_df ['Arrecadacao Total'] = tabela_df['Arrecadacao Total'].apply(lambda x: str(x).replace('R$',''))
tabela_df ['Arrecadacao Total'] = tabela_df['Arrecadacao Total'].apply(lambda x: str(x).replace('.',''))
tabela_df ['Arrecadacao Total'] = tabela_df['Arrecadacao Total'].apply(lambda x: str(x).replace(',','.'))
tabela_df ['Arrecadacao Total'] = tabela_df['Arrecadacao Total'].astype (np.float32, copy = False)
tabela_df ['Arrecadacao Total'] = tabela_df['Arrecadacao Total'].round(2)

tabela_df['Estimativa Prêmio'] = tabela_df['Estimativa Prêmio'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Estimativa Prêmio'] = tabela_df['Estimativa Prêmio'].apply(lambda x: str(x).replace('.',''))
tabela_df['Estimativa Prêmio'] = tabela_df['Estimativa Prêmio'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Estimativa Prêmio'] = tabela_df['Estimativa Prêmio'].astype (np.float32, copy = False)
tabela_df['Estimativa Prêmio'] = tabela_df['Estimativa Prêmio'].round(2)


tabela_df['Acumulado sorteio especial Lotofácil da Independência'] = tabela_df['Acumulado sorteio especial Lotofácil da Independência'].apply(lambda x: str(x).replace('R$',''))
tabela_df['Acumulado sorteio especial Lotofácil da Independência'] = tabela_df['Acumulado sorteio especial Lotofácil da Independência'].apply(lambda x: str(x).replace('.',''))
tabela_df['Acumulado sorteio especial Lotofácil da Independência'] = tabela_df['Acumulado sorteio especial Lotofácil da Independência'].apply(lambda x: str(x).replace(',','.'))
tabela_df['Acumulado sorteio especial Lotofácil da Independência'] = tabela_df['Acumulado sorteio especial Lotofácil da Independência'].astype (np.float32, copy = False)
tabela_df['Acumulado sorteio especial Lotofácil da Independência'] = tabela_df['Acumulado sorteio especial Lotofácil da Independência'].round(2)


##### tratamento de valores vazios coluna 'Cidade / Uf' e 'Observação', troca do valor vazio pelo texto 'n/a' (não se aplica)



tabela_df['Cidade / UF'].fillna('N/A',inplace=True)
tabela_df['Observação'].fillna('N/A',inplace=True)


##### Remoção de duplicatas

tabela_df = tabela_df.drop_duplicates()

##### Identificação de tendências ou padrões nos números sorteados. (Análise exploratória)


display(tabela_df)


tabela_df.to_excel('Lotofacil.xlsx',index=False)


dados_conexao = (
    "Driver={SQL Server};"
    "Server=Virtooz;"
    "Database=PotatoCore;"
)

                          
conexao = pyodbc.connect (dados_conexao)

concurso  = tabela_df['Concurso']
data_sorteio = tabela_df['Data Sorteio']
Bola_1 = tabela_df['Bola1']
Bola_2 = tabela_df['Bola2']
Bola_3 = tabela_df['Bola3']
Bola_4 = tabela_df['Bola4']
Bola_5 = tabela_df['Bola5']
Bola_6 = tabela_df['Bola6']
Bola_7 = tabela_df['Bola7']
Bola_8 = tabela_df['Bola8']
Bola_9 = tabela_df['Bola9']
Bola_10 = tabela_df['Bola10']
Bola_11 = tabela_df['Bola11']
Bola_12 = tabela_df['Bola12']
Bola_13 = tabela_df['Bola13']
Bola_14 = tabela_df['Bola14']
Bola_15 = tabela_df['Bola15']
Ganhadores_15_acertos = tabela_df['Ganhadores 15 acertos']
cidade = tabela_df['Cidade / UF']
rateio_15_acertos = tabela_df['Rateio 15 acertos']
Ganhadores_14_acertos = tabela_df['Ganhadores 14 acertos'] 
rateio_14_acertos= tabela_df['Rateio 14 acertos']
Ganhadores_13_acertos = tabela_df['Ganhadores 13 acertos']
rateio_13_acertos= tabela_df['Rateio 13 acertos']
Ganhadores_12_acertos = tabela_df['Ganhadores 12 acertos']
rateio_12_acertos=tabela_df['Rateio 12 acertos']
Ganhadores_11_acertos = tabela_df['Ganhadores 11 acertos']
rateio_11_acertos=tabela_df['Rateio 11 acertos']
Acumulado_15_acertos= tabela_df['Acumulado 15 acertos']
Arrecadacao_Total = tabela_df['Arrecadacao Total']
Estimativa_Premio = tabela_df['Estimativa Prêmio'] 
Acumulado_independencia= tabela_df['Acumulado sorteio especial Lotofácil da Independência']
observacao = tabela_df['Observação']
ano_sorteio = tabela_df['Ano do Sorteio']
mes_do_sorteio = tabela_df['Mês do Sorteio']
dia_do_sorteio = tabela_df['Dia do Sorteio']

cursor = conexao.cursor()

comando = """INSERT INTO LOTOFACIL(Concurso, Data_Sorteio, Bola1, Bola2, Bola3, Bola5, Bola6, Bola7, Bola8, Bola9, Bola10, Bola11, Bola12, Bola13, Bola14, Bola15, Ganhadores_15_acertos, Cidade_UF, Rateio_15_acertos, Ganhadores_14_acertos, Rateio_14_acertos, Ganhadores_13_acertos, Rateio_13_acertos, Ganhadores_12_acertos, Rateio_12_acertos, Ganhadores_11_acertos, Rateio_11_acertos, Acumulado_15_acertos, Arrecadacao_Total, Estimativa_Prêmio, Acumulado_sorteio_especial_Lotofácil_da_Independência, Observação, Ano_do_Sorteio, Mês_do_Sorteio, Dia_do_Sorteio, ) VALUES
({Concurso},{data_sorteio},{Bola1}, {Bola2}, {Bola3}, {Bola4}, {Bola5}, {Bola6}, {Bola7}, {Bola8}, {Bola9}, {Bola10}, {Bola11}, {Bola12}, {Bola13}, {Bola14},{Bola15},{Ganhadores_15_acertos} , {cidade}, {rateio_15_acertos},{Ganhadores_14_acertos}, {rateio_14_acertos}, {Ganhadores_13_acertos}, {rateio_13_acertos}, {Ganhadores_12_acertos}, {rateio_12_acertos}, {Ganhadores_11_acertos}, {rateio_11_acertos}, {Acumulado_15_acertos},{Arrecadacao_Total}, {Estimativa_Premio}, {Acumulado_independencia}, {observacao}, {ano_do_sorteio}, {mes_do_sorteio}, {dia_do_sorteio})"""     

cursor.execute(comando)
cursor.commit







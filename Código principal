
from processamento_dados import Dados


path_json = 'pipeline_dados/data_raw/dados_empresaA.json'
path_csv = 'pipeline_dados/data_raw/dados_empresaB.csv'


#Extract

dados_empresaA = Dados(path_json, 'json')
print(f'Nomes Originais: {dados_empresaA.nome_colunas}')
print(f'A empresa A tem {dados_empresaA.qtd_linhas} linhas')

dados_empresaB = Dados(path_csv, 'csv')
print(f'Nomes Originais: {dados_empresaB.nome_colunas}')
print(f'A empresa B tem {dados_empresaB.qtd_linhas} linhas')

#Transform

key_mapping = {"Nome do Item": "Nome do Produto",
           'Classificação do Produto': 'Categoria do Produto',
            'Valor em Reais (R$)': 'Preço do Produto em reais',
            'Quantidade em Estoque': 'Quantidade em Estoque',
             'Nome da Loja': "Filial",
             'Data da Venda': 'Data da Venda'}

dados_empresaB.rename_coluns(key_mapping)
print(f'Nome Atualizado/Empresa B: {dados_empresaB.nome_colunas}')

dados_fusao = Dados.join(dados_empresaA, dados_empresaB)
print(f'Nome da Colunas/Dados Unidos: {dados_fusao.nome_colunas}')

print(f'Quantidade de Linhas/Dados Unidos: {dados_fusao.qtd_linhas}')


#Load
path_dados_combinados = 'pipeline_dados/data_processed/dados_combinados.csv'

dados_fusao.salvando_dados(path_dados_combinados)
print(path_dados_combinados)

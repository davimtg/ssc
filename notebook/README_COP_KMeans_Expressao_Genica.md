
# Análise de Expressão Gênica - Conjunto GSE75688

Este repositório contém um notebook (`COP_KMeans_Expressão_Gênica.ipynb`) que realiza a análise de expressão gênica do conjunto de dados GSE75688.

## Conteúdo do Notebook

1. **Download dos Dados**: Instruções para baixar os arquivos de expressão gênica (`GSE75688_GEO_processed_Breast_Cancer_raw_TPM_matrix.txt.gz`) e informações de amostra (`GSE75688_final_sample_information.txt.gz`) do NCBI GEO.
2. **Carregamento e Pré-Processamento**:
   - Carrega as tabelas de expressão gênica e informações de amostras usando `pandas`.
   - Filtra células de interesse (exemplo: células não tumorais).
   - Calcula genes altamente variáveis (HVGs).
   - Aplica normalização logarítmica (log1p) nos dados.
3. **Geração de Entradas para COP-KMeans**:
   - Cria o arquivo `genes.data` contendo a expressão normalizada para HVGs.
   - Gera restrições Must-Link (ML) e Cannot-Link (CL) com base nos rótulos das células (`index3`).
4. **Execução do COP-KMeans**:
   - Utiliza os scripts `cop_kmeans.py` e `run_ckm.py` para executar a clusterização com restrições.
   - Ajusta o número de clusters (`k`) e parâmetros de raíz (`seed`).
5. **Avaliação e Visualização**:
   - Avalia a qualidade dos clusters usando o índice de Informação Mútua Normalizada (NMI).
   - Projeta os dados em 2D usando PCA e UMAP, colorindo por clusters obtidos e rótulos reais para comparação.
   - Gera gráficos de dispersão para visualizar a separação dos clusters.

## Como Usar

1. **Pré-requisitos**:
   - Python 3.8+
   - Bibliotecas: `pandas`, `numpy`, `scikit-learn`, `umap-learn`, `matplotlib`, `seaborn`, `dataframe_image`
   - Scripts necessários: `cop_kmeans.py`, `run_ckm.py`

2. **Executando o Notebook**:
   - Abra o `COP_KMeans_Expressão_Gênica.ipynb` em um ambiente Jupyter.
   - Execute todas as células na ordem para reproduzir a análise completa.

3. **Adicionando ou Ajustando Parâmetros**:
   - Para alterar o número de clusters, modifique o parâmetro `k` na célula de execução do COP-KMeans.
   - Para mudar critérios de filtragem de células, ajuste a lógica em "Filtrar células de interesse".

## Estrutura de Arquivos

- `COP_KMeans_Expressão_Gênica.ipynb`: Notebook organizado com o pipeline de análise completo.
- `README.md`: Este arquivo, contendo descrições e instruções de uso.
- `cop_kmeans.py`: Implementação do algoritmo COP-KMeans.
- `run_ckm.py`: Script auxiliar para executar o COP-KMeans com parâmetros configuráveis.

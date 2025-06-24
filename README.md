
# Análise de Expressão Gênica com COP-KMeans

Este projeto explora a aplicação do algoritmo Constrained K-Means (COP-KMeans) para a análise de expressão gênica, utilizando o conjunto de dados GSE75688. O objetivo é demonstrar como a incorporação de restrições pode melhorar a qualidade da clusterização em dados biológicos complexos, como os de expressão gênica.



## Tabela de Conteúdo

- [Visão Geral do Projeto](#visão-geral-do-projeto)
- [Funcionalidades](#funcionalidades)
- [Estrutura de Diretórios](#estrutura-de-diretórios)
- [Instalação e Configuração](#instalação-e-configuração)
- [Uso](#uso)
- [Resultados e Exemplos](#resultados-e-exemplos)




## Visão Geral do Projeto

Este projeto se concentra na análise de expressão gênica do conjunto de dados GSE75688, que contém informações sobre amostras de câncer de mama. O principal objetivo é aplicar o algoritmo COP-KMeans para agrupar células com base em seus perfis de expressão gênica, incorporando restrições para guiar o processo de clusterização. Isso permite uma análise mais refinada e biologicamente relevante, superando algumas limitações do K-Means tradicional ao considerar conhecimentos prévios ou relações conhecidas entre as amostras.

O pipeline de análise inclui:
- Download e pré-processamento dos dados de expressão gênica.
- Identificação de genes altamente variáveis (HVGs).
- Geração de restrições Must-Link (ML) e Cannot-Link (CL) com base em metadados das amostras.
- Execução do COP-KMeans com os dados e restrições geradas.
- Avaliação da qualidade dos clusters utilizando métricas como o NMI (Normalized Mutual Information).
- Visualização dos resultados da clusterização em espaços de baixa dimensão (PCA e UMAP).




## Funcionalidades

- **Download e Pré-processamento de Dados**: Facilita o download e o carregamento de dados de expressão gênica do NCBI GEO, incluindo filtragem de células de interesse e normalização logarítmica.
- **Seleção de Genes Altamente Variáveis (HVGs)**: Implementa a identificação de HVGs para focar a análise nos genes mais informativos.
- **Geração de Restrições**: Capacidade de gerar restrições Must-Link (ML) e Cannot-Link (CL) a partir de metadados de amostras, essenciais para o COP-KMeans.
- **Implementação de COP-KMeans**: Inclui os scripts `cop_kmeans.py` e `run_ckm.py` para a execução do algoritmo COP-KMeans com restrições configuráveis.
- **Avaliação de Clusterização**: Avalia a qualidade dos clusters gerados usando métricas como o NMI (Normalized Mutual Information).
- **Visualização de Dados**: Permite a projeção de dados em 2D usando PCA e UMAP para visualização da clusterização e comparação com rótulos reais.
- **Notebooks Interativos**: Fornece notebooks Jupyter (`.ipynb`) para reprodução completa da análise, exploração de dados (EDA) e visualização de resultados.




## Estrutura de Diretórios

O projeto está organizado da seguinte forma:

```
.gitignore
LICENSE
README.md
ssc.ipynb
copkmeans/
├── cop_kmeans.py
├── run_ckm.py
└── __init__.py
examples/
├── iris.constraints
├── iris.data
├── iris_nmi.ipynb
└── runner.sh
notebook/
├── COP_KMeans_Expressao_Genica.ipynb
├── dataset.ipynb
├── eda_gse75688.ipynb
├── README_COP_KMeans_Expressao_Genica.md
└── results_images.ipynb
```

- `copkmeans/`: Contém a implementação do algoritmo COP-KMeans.
  - `cop_kmeans.py`: O algoritmo principal do COP-KMeans.
  - `run_ckm.py`: Script para executar o COP-KMeans.
- `examples/`: Exemplos de uso do COP-KMeans, incluindo dados e notebooks de demonstração.
- `notebook/`: Contém os notebooks Jupyter para análise de expressão gênica, exploração de dados e visualização de resultados.
  - `COP_KMeans_Expressao_Genica.ipynb`: Notebook principal com o pipeline de análise de expressão gênica.
  - `eda_gse75688.ipynb`: Notebook para Análise Exploratória de Dados (EDA) do conjunto GSE75688.
  - `dataset.ipynb`: Notebook relacionado ao processamento do dataset.
  - `results_images.ipynb`: Notebook para geração de imagens de resultados.
  - `README_COP_KMeans_Expressao_Genica.md`: README específico para o notebook de expressão gênica.
- `LICENSE`: Arquivo de licença do projeto.
- `README.md`: Este arquivo.
- `ssc.ipynb`: Um notebook adicional no diretório raiz do projeto.




## Instalação e Configuração

Para configurar o ambiente e executar o projeto, siga os passos abaixo:

### Pré-requisitos

- Python 3.8 ou superior
- `pip` (gerenciador de pacotes do Python)

### Instalação das Dependências

Recomenda-se criar um ambiente virtual para isolar as dependências do projeto:

```bash
python3 -m venv venv
source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
```

Com o ambiente virtual ativado, instale as bibliotecas necessárias. As principais bibliotecas utilizadas são:

```bash
pip install pandas numpy scikit-learn umap-learn matplotlib seaborn dataframe_image
```

Certifique-se de que os scripts `cop_kmeans.py` e `run_ckm.py` estejam acessíveis no seu `PYTHONPATH` ou no mesmo diretório de execução dos notebooks.




## Uso

O projeto é centrado nos notebooks Jupyter, que guiam o usuário através das diferentes etapas da análise.

### Executando a Análise de Expressão Gênica

O notebook principal para a análise de expressão gênica é o `notebook/COP_KMeans_Expressao_Genica.ipynb`. Para executá-lo:

1. Certifique-se de ter todos os pré-requisitos e dependências instalados (veja a seção [Instalação e Configuração](#instalação-e-configuração)).
2. Inicie o Jupyter Notebook ou JupyterLab a partir do diretório raiz do projeto:
   ```bash
   jupyter notebook
   # ou
   jupyter lab
   ```
3. Navegue até `notebook/COP_KMeans_Expressao_Genica.ipynb` e abra-o.
4. Execute todas as células em sequência para baixar os dados, pré-processá-los, gerar restrições, executar o COP-KMeans e visualizar os resultados.

### Outros Notebooks

- `notebook/eda_gse75688.ipynb`: Para uma análise exploratória detalhada do conjunto de dados GSE75688.
- `notebook/dataset.ipynb`: Contém scripts e exemplos relacionados ao processamento e manipulação do dataset.
- `notebook/results_images.ipynb`: Utilizado para gerar e visualizar imagens dos resultados da clusterização e outras análises.
- `examples/iris_nmi.ipynb`: Um exemplo de aplicação do COP-KMeans em um dataset mais simples (Iris) para cálculo de NMI.
- `ssc.ipynb`: Um notebook adicional que pode conter experimentos ou análises complementares.





## Resultados e Exemplos

Os resultados da clusterização e as visualizações geradas podem ser encontrados e reproduzidos nos notebooks, especialmente em `notebook/COP_KMeans_Expressao_Genica.ipynb` e `notebook/results_images.ipynb`.

O notebook `COP_KMeans_Expressao_Genica.ipynb` demonstra:
- A aplicação do COP-KMeans no conjunto de dados GSE75688.
- A geração de restrições Must-Link e Cannot-Link.
- A avaliação da qualidade dos clusters usando NMI.
- Visualizações 2D dos clusters obtidos, comparando-os com os rótulos reais das amostras, utilizando PCA e UMAP.

O notebook `examples/iris_nmi.ipynb` fornece um exemplo mais simples da aplicação do COP-KMeans e cálculo de NMI usando o conjunto de dados Iris, que pode ser útil para entender os conceitos básicos antes de mergulhar na análise de expressão gênica.
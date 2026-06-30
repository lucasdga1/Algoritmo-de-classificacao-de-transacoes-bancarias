# Algoritmo de classificação de transações bancárias
# Objetivo
* O objetivo principal deste projeto era criar um algoritmo de classificação que fosse capaz de detectar operações legítimas e fraudulentas, auxiliando a instituição bancária em questão a evitar perdas nas operações.

# Dataset
* O dataset foi fornecido pela EBAC como desafio acadêmico do último módulo do curso profissionalizante.
* A base de dados pode ser acessada pelo link abaixo:
* <a href="https://github.com/lucasdga1/Algoritmo-de-classificacao-de-transacoes-bancarias/tree/main/Bases%20de%20dados">Base de dados</a>
* O código para desenvolvimento do modelo pode ser acessado a partir do link abaixo:
* <a href="https://github.com/lucasdga1/Algoritmo-de-classificacao-de-transacoes-bancarias/blob/main/Classificacao_Fraude.ipynb">Código do modelo</a>

# Tecnologias Utilizadas
* Python: Linguagem de programação utilizada para análise de dados e machine learning.
* Pandas: Biblioteca para manipulação e análise de dados.
* NumPy: Biblioteca para operações numéricas.
* Plotly: Biblioteca para visualização de dados.
* Scikit-learn: Biblioteca para machine learning, utilizada para aplicação dos algoritmos.

# Metodologia
1. Os dados foram carregados como dataframe no Pandas e avaliados quanto à sua integridade e pré-processamento;
2. Foram feitas análises com gráficos para tentar obter grau de correlação entre as variáveis;
3. A maior parte das variáveis já estava vetorizada por PCA;
4. A base de dados foi separada em treino e teste;
5. A base de treino foi balanceada com SMOTE;
6. Foram treinados modelos de Regressão Logística, SVM, Random Forest e XGBoost;
7. Os modelos foram testados e avaliados.

# Cores utilizadas na análise
* As cores foram padronizadas para uma maior padronização e identidade visual;
* Cinza médio: #6B7280
* Cinza claro: #9CA3AF
* Preto: #1F2937
* Branco: #F3F4F6

# Análise de dados pré-modelagem
## Correlação entre Classes de operação e quantia movimentada
<img width="1314" height="450" alt="ClassesXQuantia" src="https://github.com/user-attachments/assets/9ca9804f-488e-4c66-9b51-ebccd73c028b" />
* Esse gráfico indica que a maioria das transações são legítimas, indicando não ter correlação com quantia movimentada necessariamente

## Correlação entre operações fraudulentas e quantia movimentada
<img width="1314" height="450" alt="FraudesXQuantia" src="https://github.com/user-attachments/assets/85f4a39c-deb4-4c27-a5cd-09062b6ca263" />
* O gráfico acima indica que a maioria das transações fraudulentas se encontram num espectro de pequeno valor (até 849 mais ou menos)

## Correlação em relação a movimentações de pequenas quantias
<img width="1314" height="450" alt="FraudesXPqQuantia" src="https://github.com/user-attachments/assets/98c4b461-2bd2-4afc-8297-d87c242e67aa" />
* A quantia de pequenas transações legítimas é mais alta que as fraudulentas

## Correlação entre variáveis
<img width="1314" height="450" alt="Correlacao" src="https://github.com/user-attachments/assets/76bda0bc-a6c6-4af5-8584-a9468455fd67" />
* Como a maioria das variáveis já foi vetorizada, a correlação com a variável target parece ser homogênea

# Treinamento
* Os modelos foram treinados com uma base balanceada com cerca de 80000 linhas e 28 colunas;
* Por causa da quantidade de dados, o número de interações do ajuste de hiperparâmetros foi definido como 15;
* Foi obtido o score dos modelos ajustados com cross-validation em 5 partes;
* A medida utilizada para avaliar foi o recall, por demonstrar a capacidade do modelo de classificar verdadeiros positivos.

# Teste
* Os modelos foram testados e, como medidas de avaliação, foram obtidos os relatórios de classificação, matriz de confusão e curva AUC_ROC

# Resultados
## Regressão Logística
* Regressão logística - errou somente 18 dados classificados como fraude (12%), mas classificou erroneamente 796 transações legítimas como fraudes (~1%).
<img width="1314" height="450" alt="Confusão_RL" src="https://github.com/user-attachments/assets/5e188d5e-bf1e-46df-a4f4-819a26b52988" />

## SVM
* SVM - igual à Regressão logística, porém com menos erros nas transações legítimas: 654(~1%).
<img width="1314" height="450" alt="Confusão_SVM" src="https://github.com/user-attachments/assets/c3770fa4-b5b0-4376-85d7-0783fa796305" />

## Random Forest
* Random Forest - 9 erros a mais nas classificações de fraudes (+6%), mas somente 24 classificações errôneas de transações legítimas (0.02%).
<img width="1314" height="450" alt="Confusao_RF" src="https://github.com/user-attachments/assets/fa477a55-efb7-4a80-8971-53554a8dcf2a" />

## XGBoost
* XGBoost - igual ao Random Forest, mas com acréscimo leve nas classificações erradas de transações legítimas +20(+ ~0.03%).
<img width="1314" height="450" alt="Confusao_XGB" src="https://github.com/user-attachments/assets/9db11b20-c2a6-4217-a1e0-5520a0f27635" />

## Curva AUC_ROC
<img width="1280" height="720" alt="AUC_ROC" src="https://github.com/user-attachments/assets/aad2f656-14e4-4ea6-8f61-f7b0987385c5" />

# Como o modelo pode auxiliar
* Levando em consideração a performance geral dos modelos, a capacidade de identificar classes corretamente e a capacidade de identificar operações fraudulentas, o modelo de XGBoost deve ajudar o banco a salvar cerca de 86,00 por operação e 100,00 por operação fraudulenta, em média. Isso representa um bom ganho para o banco nas suas operações diárias.
* Quantidade salva, em média, por operação geral: 86.58 / 88.35
* Quantidade salva, em média, por operação Fradudulenta: 100.21 / 122.21
* Quantidade monetária salva em termos gerais:  24659338.21
* Quantidade monetária salva com detecção de fraudes:  49304.94

# Próximos passos
* Aplicação do modelo nas operações da instituição;
* Futuro aprimoramento do modelo com deep learning e capacidade de processamento computacional maior.

# Como executar
* Clone o repositório.
* Instale as dependências listadas no `requirements.txt`.
* Execute o código "Classificacao_Fraude.ipynb" em sua base de dados

# Contribuições
* Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

# Autoria
Lucas Danziger Guimarães de Andrade

# Contato
<a href="mailto:lucas.dga1@gmail.com">Me envie um email<a/>

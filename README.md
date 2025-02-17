# Desafio de Projeto 1: Trabalhando com Machine Learning na Prática com Azure ML
# Entendendo o Desafio
Neste exercício, você usará o recurso de machine learning automatizado no Azure Machine Learning para treinar e avaliar um modelo de machine learning. Em seguida, você implantará e testará o modelo treinado. 

Para isso voicê deverá executar o seguinte passo a passo no Azure Machine Learning:

## 1 - Criar um espaço de trabalho do Azure Machine Learning
Para usar o Azure Machine Learning, você precisa provisionar um workspace do Azure Machine Learning na sua assinatura do Azure. Então você poderá usar o Azure Machine Learning Studio para trabalhar com os recursos no seu workspace.

Dica!: se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.

  1.1. Entre no portal do Azure usando https://portal.azure.comsuas credenciais da Microsoft.

  1.2. Selecione + Criar um recurso , pesquise por Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:
* __Assinatura__ : sua assinatura do Azure.
* __Grupo de recursos__ : crie ou selecione um grupo de recursos.
* __Nome__ : Insira um nome exclusivo para seu espaço de trabalho.
* __Região__ : Leste dos EUA.
* __Conta de armazenamento__ : observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho.
* __Cofre de chaves__ : observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho.
* __Insights do aplicativo__ : observe o novo recurso padrão de insights do aplicativo que será criado para seu espaço de trabalho.
* __Registro de contêiner__ : Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).

1.3. Selecione __Review + create__ e, em seguida, selecione __Create__ . Aguarde a criação do seu workspace (pode levar alguns minutos) e, em seguida, vá para o recurso implantado.

__Estúdio de lançamento__

No seu recurso de espaço de trabalho do Azure Machine Learning, selecione __Iniciar estúdio__ (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no estúdio do Azure Machine Learning usando sua conta da Microsoft). Feche todas as mensagens exibidas.

No Azure Machine Learning Studio, você deve ver seu workspace recém-criado. Caso contrário, selecione __All workspaces__ no menu à esquerda e, em seguida, selecione o workspace que você acabou de criar.

* No seu recurso de espaço de trabalho do Azure Machine Learning, selecione Iniciar estúdio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no estúdio do Azure Machine Learning usando sua conta da Microsoft). Feche todas as mensagens exibidas.

* No Azure Machine Learning Studio, você deve ver seu workspace recém-criado. Caso contrário, selecione All workspaces no menu à esquerda e, em seguida, selecione o workspace que você acabou de criar.
  
## 2 - Utilize o Azure ML Automatizado para treinar o modelo

O machine learning automatizado permite que você experimente vários algoritmos e parâmetros para treinar vários modelos e identificar o melhor para seus dados. Neste exercício, você usará um conjunto de dados de detalhes históricos de aluguel de bicicletas para treinar um modelo que prevê o número de aluguéis de bicicletas que devem ser esperados em um determinado dia, com base em características sazonais e meteorológicas.

__Citação__: Os dados usados ​​neste exercício são derivados do Capital Bikeshare e são usados ​​de acordo com o contrato de licença de dados publicado.

2.1. No Azure Machine Learning Studio , visualize a página __ML automatizado (em Criação)__.

2.2. Crie um novo trabalho de ML automatizado com as seguintes configurações, usando __Avançar__ conforme necessário para avançar pela interface do usuário:

* __Configurações básicas__:

  * __Nome do trabalho__ : O campo Nome do trabalho já deve estar preenchido previamente com um nome exclusivo. Mantenha-o como está.
  * __Novo nome do experimento__ :mslearn-bike-rental
  * __Descrição__ : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
  * __Tags__ : nenhuma

* __Tipo de tarefa e dados__ :

  * __Selecione o tipo de tarefa__ : Regressão  
  * __Selecionar conjunto de dados__ : Crie um novo conjunto de dados com as seguintes configurações:
  
* __Tipo de dados__ :
    
  * __Nome__ :bike-rentals
  * __Descrição__ :Historic bike rental data
  * __Tipo__ : Tabela (mltable)

* __Fonte de dados__ :
Selecione __De arquivos locais__
* __Tipo de armazenamento de destino__ :
  * __Tipo de armazenamento de dados__ : Azure Blob Storage
  * __Nome__ : workspaceblobstore
* __Seleção de MLtable__ :
  * __Pasta de upload__ : Baixe e descompacte a pasta que contém os dois arquivos que você precisa enviar https://aka.ms/bike-rentals
    
Selecione __Criar__ . Após a criação do conjunto de dados, selecione o conjunto de dados bike-rentals para continuar a enviar o trabalho de ML automatizado.

* __Configurações da tarefa__ :

  * __Tipo de tarefa__ : Regressão
  * __Conjunto de dados__ : aluguel de bicicletas
  * __Coluna de destino__ : aluguéis (inteiro)
    
* __Configurações adicionais__ :
  
  * __Métrica primária__ : NormalizedRootMeanSquaredError
  * __Explique o melhor modelo__ : Não selecionado
  * __Habilitar empilhamento de conjunto__ : Não selecionado
  * __Usar todos os modelos suportados__ : Não selecionado. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
  * __Modelos permitidos__ : Selecione apenas __RandomForest__ e __LightGBM__ — normalmente você tentaria o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
    
* __Limites__ : Expandir esta seção
  
  * __Máximo de ensaios__ :3
  * __Máximo de ensaios simultâneos__ :3
  * __Máximo de nós__ :3
  * __Limite de pontuação métrica__ : 0.085( para que se um modelo atingir uma pontuação métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termine. )
  * __Tempo limite do experimento__ :15
  * __Tempo limite de iteração__ :15
  * __Habilitar rescisão antecipada__ : Selecionado
    
* __Validação e teste__ :
  
  * __Tipo de validação__ : Divisão de validação de trem
  * __Porcentagem de dados de validação__ : 10
  * __Conjunto de dados de teste__ : Nenhum

* __Calcular__ :

  * __Selecione o tipo de computação__ : Sem servidor
  * __Tipo de máquina virtual__ : CPU
  * __Camada de máquina virtual__ : Dedicada
  * __Tamanho da máquina virtual__ : Standard_DS3_V2*
  * __Número de instâncias__ : 1
    
* Se sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

2.3. Envie o trabalho de treinamento. Ele inicia automaticamente.

2.4. Espere o trabalho terminar. Pode levar um tempo — agora pode ser uma boa hora para um coffee break!



# Desafio de Projeto 1: Trabalhando com Machine Learning na Prática com Azure ML
# Entendendo o Desafio
Neste exercício, você usará o recurso de machine learning automatizado no Azure Machine Learning para treinar e avaliar um modelo de machine learning. Em seguida, você implantará e testará o modelo treinado. 

Para isso voicê deverá executar o seguinte passo a passo no Azure Machine Learning:

## 1 - Criar um espaço de trabalho do Azure Machine Learning
Para usar o Azure Machine Learning, você precisa provisionar um workspace do Azure Machine Learning na sua assinatura do Azure. Então você poderá usar o Azure Machine Learning Studio para trabalhar com os recursos no seu workspace.

Dica : se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.

  1.1. Entre no portal do Azure usando https://portal.azure.comsuas credenciais da Microsoft.

  1.2. Selecione + Criar um recurso , pesquise por Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:
* Assinatura : sua assinatura do Azure.
* Grupo de recursos : crie ou selecione um grupo de recursos.
* Nome : Insira um nome exclusivo para seu espaço de trabalho.
* Região : Leste dos EUA.
* Conta de armazenamento : observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho.
* Cofre de chaves : observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho.
* Insights do aplicativo : observe o novo recurso padrão de insights do aplicativo que será criado para seu espaço de trabalho.
* Registro de contêiner : Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).
* Selecione Review + create e, em seguida, selecione Create . Aguarde a criação do seu workspace (pode levar alguns minutos) e, em seguida, vá para o recurso implantado.

1.3 Estúdio de lançamento

* No seu recurso de espaço de trabalho do Azure Machine Learning, selecione Iniciar estúdio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no estúdio do Azure Machine Learning usando sua conta da Microsoft). Feche todas as mensagens exibidas.

* No Azure Machine Learning Studio, você deve ver seu workspace recém-criado. Caso contrário, selecione All workspaces no menu à esquerda e, em seguida, selecione o workspace que você acabou de criar.

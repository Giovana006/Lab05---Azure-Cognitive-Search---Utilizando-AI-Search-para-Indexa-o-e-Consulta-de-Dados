## **Desafio: Utilizando AI Search para indexação e consulta de Dados**

![Static Badge](https://img.shields.io/badge/Inteligência_Artificial_(IA)-blue)
![Static Badge](https://img.shields.io/badge/AI_Search-blue)
![Static Badge](https://img.shields.io/badge/AI_Data_Indexing-blue)
![Static Badge](https://img.shields.io/badge/AI_Document_Intelligence-blue)
![Static Badge](https://img.shields.io/badge/AI_Knowledge_Mining-blue)

![Static Badge](https://img.shields.io/badge/Microsoft_Azure-orange)
![Static Badge](https://img.shields.io/badge/Azure_Cognitive_Search-orange)
![Static Badge](https://img.shields.io/badge/Azure_Storage_Account-orange)

### **Descrição do Projeto :**

Este repositório tem como finalidade armazenar o projeto desenvolvido no âmbito do módulo **"Inteligência de Documentos e Mineração de Conhecimento"** do Bootcamp **"Microsoft Azure AI Fundamentals"** da [DIO](https://www.dio.me/users/giovananascimentoferreira1) , sob orientação da professora [Valéria Baptista](https://www.linkedin.com/in/valeriabaptista/) .

Este projeto é um dos laboratórios do Bootcamp [Microsoft Azure AI Fundamentals](https://web.dio.me/track/microsoft-azure-ai-fundamentals), promovido através da parceria entre a Microsoft e a Dio.me.

Os alunos deste bootcamp tem, como principal objetivo, se prepararem para o exame de certificação Microsoft AI-900, dominando conceitos como visão computacional, classificação inteligente de imagem e inteligência de documentos com IA, enquanto se familiarizam com as tecnologias da Microsoft Azure.

Este desafio é o de número 5 do bootcamp e consiste na execução prática dos seguinte exercício:

- [Indexação no Azure AI](http://aka.ms/ai900-ai-search): explorar o serviço de índice de Pesquisa de IA do Azure.

O projeto é requisito essencial para aprovação no módulo “Inteligência Documental e Mineração de Conhecimento”, consolidando o aprendizado prático dos participantes e preparando-os para os desafios subsequentes.

O desenvolvimento deste projeto visa demonstrar como a mineração de conhecimento pode ser utilizada no Microsoft Azure, criando índices Azure AI Search juntamente com capacidades de IA. Para uma melhor compreensão, dividi todo o processo em etapas, desde a criação de recursos até a obtenção de insights com pesquisas cognitivas.

### ℹ️ Sobre o Objetivo do Desafio:

O objetivo deste desafio é `criar um serviço de AI Search para indexação e consulta de dados`.
Utilizando aprendizado de máquina e processamento de linguagem natural, ela permite uma busca intuitiva e contextual, melhorando a experiência do usuário e acelerando a tomada de decisões. A AI Search transforma dados brutos em conhecimento acessível e acionável.

Portanto, este projeto tem como objetivo mostrar como usar o recurso do "**Azure AI Search**" para indexação e consulta de dados.

Após concluir o projeto seguindo os passos pode se ter algumas ideias de aplicação para este recurso.

Uma delas seria para uso em uma rede de franquias, na qual pode se obter rapidamente através de uma breve busca varios dados das franquias de uma determinada localidade, saber quais franquias são melhores e piores avaliadas e o motivo. Entre outras aplicações. Ou seja o principal uso desse recurso seria por empresas independente do tamanho da mesma.

### **Introdução :**

O serviço de índice de Pesquisa de IA do Azure, conhecido como **Azure Cognitive Search**, oferece recursos de enriquecimento de IA para processar conteúdos que não são pesquisáveis em sua forma bruta.

Utilizando um conjunto de habilidades, ele pode traduzir textos, detectar idiomas, reconhecer entidades, extrair frases-chave e até realizar OCR em arquivos binários.

Além disso, o serviço suporta o enriquecimento incremental, que permite o uso de enriquecimentos em *cache* durante a execução do conjunto de habilidades, reduzindo assim os custos de processamento.

Para testar este serviço, utilizei uma base de avaliações de clientes de uma rede nacional de cafés (um dataset público que pode ser baixado [aqui](https://aka.ms/mslearn-coffee-reviews)).

Ao final, implementei uma solução de mineração de conhecimento que facilita a pesquisa de *insights* sobre as experiências do cliente, criando um índice de Pesquisa de IA do Azure.

Este experimento envolveu, entre outras, as seguintes etapas: extração de dados em um *datasource*, enriquecimento dos dados com habilidades de IA, utilização do indexador do Azure, consulta ao índice de pesquisa e revisão dos resultados salvos em uma base de conhecimento armazenada.

### **Contexto do problema :**
Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a criar uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes.

### ✅ Passos realizados:

> [!IMPORTANT]
>
> - [x] Ter um cadastro na [Azure](https://azure.microsoft.com) - realize o login na plataforma;
> - Baixe o [zipped coffee reviews](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html) - Será utilizado na etapa 3 - `Storage accounts`;
> 

> Para a realização deste desafio serão utilizados `3 recursos`. **Confira cada um abaixo**:

### **Aprovisionando os recursos necessários do Azure :**

Para realizar este laboratório, foi necessário aprovisionar, no [Portal do Azure](https://portal.azure.com/), os 3 serviços abaixo:

- ***Azure AI Search***: para gerenciará a indexação e a consulta;
- ***Azure AI services***: para enriquecer os dados na fonte de dados com *insights* gerados por IA;
- ***Storage Account***: para armazenar os documentos brutos.

> [!NOTE]
> Os 3 serviços precisaram ser aprovisionados no mesmo local (região), para permitir a integração entre eles.

#### **Passo 1: Criar um recurso _Azure AI Search_**

Inicialmente, precisamos acessar o [portal do Azure](https://portal.azure.com/) .

Depois vamos criar o recurso do **Azure AI Search** de acordo com os passos do vídeo a seguir:

<img src="Assets/Passo 1 - Criar o recurso Azure AI Search.gif">

#### **Passo 2: Criar um recurso _Azure AI Service_**

Agora vamos criar o recurso Azure AI Service de acordo com os passos do vídeo a seguir :

<img src="Assets/Passo 2 - Criar o recurso Azure AI Service.gif">

#### **Passo 3: Criando Conta de Armazenamento**

Precisamos criar uma conta de armazenamento porque ela nos fornecerá um namespace exclusivo para os dados, conterá todos os objetos de dados e a partir daí poderemos integrá-los à pesquisa cognitiva.

Vamos começar selecionando uma conta de armazenamento.

<img src="Assets/Passo 3 - Criando uma Conta de Armazenamento.gif">

#### **Passo 4: Configurar a Conta de Armazenamento Criada**

Precisaremos permitir o acesso anônimo ao Blob.

<img src="Assets/Passo 4 - Configurar a Conta de Armazenamento Criada.gif">

#### **Passo 5: Crie um Novo Contêiner em Nossa Conta de Armazenamento**

Você precisará criar um novo contêiner em nossa conta de armazenamento.

Siga de acordo com os passos do vídeo a seguir :

<img src="Assets/Passo 5 - Crie um Novo Contêiner em Nossa Conta de Armazenamento.gif">

#### **Passo 6: importe os dados para o contêiner**

Vamos acessar o container criado e fazer upload dos arquivos presentes no input do repositório para a pasta [review-coffee](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/tree/main/Inputs/review-coffee) .

Siga de acordo com os passos do vídeo a seguir :

<img src="Assets/Passo 6 - Importe os Dados para o Contêiner.gif">

**Arquivos Utilizados no Vídeo:**

[Arquivo em DOCX](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/tree/main/Inputs/review-coffee/Documentos%20Word%20(.docx))

[Arquivo em TXT](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/tree/main/Inputs/review-coffee/Documentos%20de%20Texto%20(.txt))

#### **Passo 7: Importe os dados para o Azure AI Search**

Agora você precisará importar os dados para o **Azure AI Search** por meio do **Azure Blop Storage**.

Siga de acordo com os passos do vídeo a seguir :

<img src="Assets/Passo 7 - Importe os Dados para o Azure AI Search.gif">

#### **Passo 8: Conecte-se aos Seus Dados**

Depois de ir para a página de importar os dados no recurso, agora você precisará preencher algumas informações para configurar a importação de dados para o Azure AI Search por meio do Azure Blob Storage.

De acordo com a imagem a seguir:

<img src="Assets/Configurações para a Importação de Dados para o Azure AI Search.png">

**Obs:** Depois de configurar e anexar o  serviços de IA.

**Formulário para Anexar a Storage Accounts e o Contêiner :**

<img src="Assets/Anexar o Contêiner - Link  para o Formulário.png">

**Passos para Anexar a Storage Accounts e o Contêiner :**

<img src="Assets/Anexar o Contêiner.png">

> [!NOTE]
>
> **Passo 1 :** Selecionar a **Storage Accounts** Criada.
>
> **Passo 2 :** Selecionar o **Contêiner** Criado (review-coffee).
>
> **Passo 3 :** Click no botão **SELECT**.

#### **Passo 9 - Configurações Adicionais :**

Preenchendo o campo ***“Attach AI Services”*** :

<img src="Assets/Anexar os serviços ou recursos de IA.png">

**Preenchendo o campo "Add enrichments" :**

<img src="Assets/Configurações da aba Add Enrichments - Parte 1.png">

<img src="Assets/Configurações da aba Add Enrichments - Parte 2.png">

**Preenchendo o campo "Save Enrichments to a Knowledge Store" :**

**Formulário para Anexar os Serviços de IA :**

<img src="Assets/Configurações da aba Save Enrichments to a Knowledge Store - Parte 1.png">

**Passos para Anexar os Serviços de IA :**

<img src="Assets/Configurações da aba Save Enrichments to a Knowledge Store - Parte 2.png">

> [!NOTE]
>
> **Passo 1 :** Selecionar a **Storage Accounts** Criada.
>
> **Passo 2 :** Selecionar o **Contêiner** Criado (review-coffee).
>
> **Passo 3 :** Click no botão **SELECT**.

Depois de selecionar o Contêiner podemos passar para a próxima etapa.

De acordo com os passos a seguir:

<img src="Assets/Configurações da aba Save Enrichments to a Knowledge Store - Parte 3.png">

<img src="Assets/Configurações da aba Save Enrichments to a Knowledge Store - Parte 4.png">

#### **Passo 10: Personalizar o Índice de Destino :**

Preenchendo a aba ***“Customize Target Index”*** :

<img src="Assets/Configurações da aba Customize Target Index - Parte 1.png">

<img src="Assets/Configurações da aba Customize Target Index - Parte 2.png">

> [!NOTE]
>
> **Passo 1 :** Mude o nome de **azureblob-indexer** para **coffee-indexer**.
>
> **Passo 2 :** Na barra **Key** , se não estiver selecionada, selecione **metadata_storage_path** .
>
> **Passo 3 :** Selecionar a Caixa da ***Coluna*** **Filterable** na ***Linha*** **Content** .
>
> **Passo 4 :** Click no botão **Next : Create an Intexer**.

#### **Passo 11: Crie um Indexador**

Preenchendo a aba ***"Create an indexer"*** :

<img src="Assets/Configurações da aba Create an Indexer.png">

> [!NOTE]
>
> **Passo 1 :** Mude o nome de **azureblob-indexer** para **coffee-indexer**.
>
> **Passo 2 :** Selecionar a palavra **ONCE** se não estiver selecionada.
>
> **Passo 3 :** Selecionar a Caixa **Base-64 Encode Keys** se não estiver selecionada.
>
> **Passo 4 :** Click no botão **SUBMIT**.

#### **Passo 12: Visualizar o Indexador**

<img src="Assets/Passo 12 - Visualizar o Indexador.gif">

**Arquivo JSON :** [visualizar_indexador.json](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/blob/main/Output/visualizar_indexador.json)

#### **Passo 13: Consulte o Índice :**

Use o Search Explorer para escrever e testar consultas. O explorador de pesquisa é uma ferramenta incorporada no portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Search Explorer para escrever consultas e revisar resultados em JSON.

<img src="Assets/Passo 13 - Consulte o Índice.gif">

+ **1° Pesquisa :**

Vamos começar analisando se a string de consulta está disponível.

No **Search Explorer** , inclua a query fornecida pela documentação `search=*&$count=true` , e clique em **"search"** .

**Arquivo JSON - Pesquisa :** [consulta_string_on.json]()

<img src="Inputs/Consulta String On - Pesquisa/Consulta String On - Pesquisa.png">

**Arquivo JSON - Resultado da Pesquisa :** [resultado_consulta_string_on.json]()

<img src="Output/Consulta String On - Resultado/Consulta String On - Resultado.png">

+ **2° Pesquisa :**

Agora vamos filtrar as consultas por localização em Chicago.

Filtramos pela localização `search=locations:'Chicago'` e ele vai trazer as reviews com os sentimentos de cada.

**Arquivo JSON - Pesquisa :** [consulta_localition_chicago.json]()

<img src="Inputs/Localização Chigaco - Pesquisa/Localização Chigaco - Pesquisa.png">

**Arquivo JSON - Resultado da Pesquisa :** [resultado_consulta_localition_chicago.json]()

<img src="Output/Localização Chigaco - Resultado/Localização Chigaco - Resultado.png">


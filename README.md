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

Vamos acessar o container criado e fazer upload dos arquivos presentes no input do repositório para a pasta [review-coffee](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html) .

<img src="Assets/Passo 6 - Importe os Dados para o Contêiner.gif">

**Arquivos Utilizados no Vídeo:**

[Arquivo em DOCX](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/tree/main/Inputs/review-coffee/Documentos%20Word%20(.docx))

[Arquivo em TXT](https://github.com/Giovana006/Lab05---Azure-Cognitive-Search---Utilizando-AI-Search-para-Indexa-o-e-Consulta-de-Dados/tree/main/Inputs/review-coffee/Documentos%20de%20Texto%20(.txt))


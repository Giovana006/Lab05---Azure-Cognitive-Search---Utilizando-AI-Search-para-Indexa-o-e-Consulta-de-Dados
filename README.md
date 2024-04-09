## **Desafio: Utilizando AI Search para indexação e consulta de Dados**

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

### ✅ Passos realizados:

> [!IMPORTANT]
>
> - [x] Ter um cadastro na [Azure](https://azure.microsoft.com) - realize o login na plataforma;
> - Baixe o [zipped coffee reviews](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html) - Será utilizado na etapa 3 - `Storage accounts`;
> 

> Para a realização deste desafio serão utilizados `3 recursos`. **Confira cada um abaixo**:

### **Introdução :**

O serviço de índice de Pesquisa de IA do Azure, conhecido como **Azure Cognitive Search**, oferece recursos de enriquecimento de IA para processar conteúdos que não são pesquisáveis em sua forma bruta.

Utilizando um conjunto de habilidades, ele pode traduzir textos, detectar idiomas, reconhecer entidades, extrair frases-chave e até realizar OCR em arquivos binários.

Além disso, o serviço suporta o enriquecimento incremental, que permite o uso de enriquecimentos em *cache* durante a execução do conjunto de habilidades, reduzindo assim os custos de processamento.

Para testar este serviço, utilizei uma base de avaliações de clientes de uma rede nacional de cafés (um dataset público que pode ser baixado [aqui](https://aka.ms/mslearn-coffee-reviews)).

Ao final, implementei uma solução de mineração de conhecimento que facilita a pesquisa de *insights* sobre as experiências do cliente, criando um índice de Pesquisa de IA do Azure.

Este experimento envolveu, entre outras, as seguintes etapas: extração de dados em um *datasource*, enriquecimento dos dados com habilidades de IA, utilização do indexador do Azure, consulta ao índice de pesquisa e revisão dos resultados salvos em uma base de conhecimento armazenada.

### **Aprovisionando os recursos necessários do Azure :**

Para realizar este laboratório, foi necessário aprovisionar, no [Portal do Azure](https://portal.azure.com/), os 3 serviços abaixo:

- ***Azure AI Search***: para gerenciará a indexação e a consulta;
- ***Azure AI services***: para enriquecer os dados na fonte de dados com *insights* gerados por IA;
- ***Storage Account***: para armazenar os documentos brutos.

> [!NOTE]
> Os 3 serviços precisaram ser aprovisionados no mesmo local (região), para permitir a integração entre eles.

### **Contexto do problema :**
Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a criar uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes.
# Laboratório 5 – Desenvolver um assistente de agente de viagem de AI da Contoso usando Azure OpenAI e o Semantic Kernel SDK

**Tempo estimado: 40 minutos**

## Objetivo

Neste laboratório, os participantes criarão um agente de viagens com
tecnologia de AI para a Contoso usando o Azure OpenAI e o Semantic
Kernel SDK. O objetivo é demonstrar como aproveitar as tecnologias de AI
para criar um agente de conversação capaz de entender as consultas dos
usuários, fornecer recomendações de viagens e executar tarefas como
reservar voos, hotéis e gerenciar itinerários. Ao final do laboratório,
os participantes terão experiência prática na integração de modelos de
AI com aplicativos do mundo real, utilizando o Semantic Kernel SDK para
aprimorar os recursos do agente de viagens e testando o desempenho do
agente em um ambiente simulado.

## Área de foco da solução

O laboratório se concentra na criação de um agente de viagens com
tecnologia de AI usando o Azure OpenAI e o Semantic Kernel SDK. Ele
permite o processamento de linguagem natural (NLP) para lidar com
consultas de usuários relacionadas ao planejamento de viagens, como
reservar voos, acomodações e fornecer recomendações de viagens.

O laboratório enfatiza a criação de uma interface de AI conversacional
que interage com os usuários, responde a perguntas e auxilia em tarefas
relacionadas a viagens. Usando o Semantic Kernel SDK, ele orquestra
tarefas como gerenciamento de itinerários e integra APIs para dados de
viagem em tempo real.

A solução visa aprimorar a experiência do usuário, fornecendo
assistência de viagem personalizada e responsiva. Automatiza tarefas
comuns de viagem para otimizar fluxos de trabalho e agilizar os
processos de planejamento de viagens.

## Exercício 1: Entender a VM e as credenciais

Neste exercício, identificaremos e entenderemos as credenciais que
usaremos em todo o laboratório.

1.  A guia **Instructions** contém o guia do laboratório com as
    instruções a serem seguidas em todo o laboratório.

2.  A guia **Resources** tem as credenciais necessárias para executar o
    laboratório.

- **URL** – URL para o portal do Azure

- **Subscription** – este é o **ID** **da** **assinatura** atribuída a
  você

- **Username** – o **ID de usuário** com a qual você precisa fazer
  **login** nos serviços do **Azure**.

- **Password** – **senha** para o **login no Azure**.

> Vamos chamar esse nome de usuário e senha como **credenciais de login
> no Azure**. Usaremos essas credenciais sempre que mencionarmos **as
> credenciais de login no Azure**.

- **Resource Group** – o **grupo de recursos** atribuído a você.

> **Importante**: certifique-se de criar todos os seus recursos neste
> grupo de recursos

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image1.png)

3.  A guia **Help** contém as informações de suporte. O valor do **ID**
    aqui é o **ID da** **instância do laboratório** que será usado
    durante a execução do laboratório.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image2.png)

## Exercício 2: Criar recursos e modelo de implementação do Azure OpenAI 

**Pré-requisitos:** uma conta do GitHub é necessária para concluir este
laboratório. Se você não tiver uma conta, crie uma aqui
+++**https://github.com/**+++ selecionando **Sign up**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image3.png)

1.  Faça login em +++**https://portal.azure.com**+++ usando as
    credenciais de login no Azure. Pesquise +++**Azure OpenAI**+++ na
    barra de pesquisa e selecione-o.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image4.png)

2.  Selecione **+ Create**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image5.png)

3.  Preencha os detalhes abaixo na guia **Basics** e selecione **Next**.

- Subscription – Selecione sua **assinatura atribuída**

- Resource group – Selecione o **grupo de recursos** atribuído a você

- Region – Selecione a **região** mais próxima (**East US 2** está sendo
  usado aqui)

- Name – +++AOAI\<ID da instância do laboratório\>+++ (substitua \<ID da
  instância do laboratório\> pela ID da VM)

- Pricing tier – **Standard**

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image6.png)

4.  Aceite os padrões nas páginas **Network** e **Tags** e clique em
    **Create** na página **Review + submit**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image7.png)

5.  Depois de criado, clique em **Go to resource**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image8.png)

6.  Selecione **Keys and Endpoint** em **Resource Management**. Copie os
    valores de **Key 1** e **Endpoint** para um bloco de notas para uso
    futuro neste laboratório.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

7.  Na página **Overview** do recurso do Azure OpenAI, selecione **Go to
    Azure AI Foundry portal**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image10.png)

8.  No painel esquerdo, selecione **Deployments**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image11.png)

9.  Selecione **+ Deploy model** -\> **Deploy base model**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image12.png)

10. Pesquise e selecione +++**gpt-35-turbo-16k**+++. Clique em
    **Confirm**.

![Uma captura de tela de um bate-papo Descrição gerada
automaticamente](./media/image13.png)

11. Aceite os padrões e selecione **Deploy**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image14.png)

## Exercício 3: Configurando o projeto do agente de viagens de AI com os serviços Azure OpenAI 

Neste exercício, você definirá sua pasta de projeto no Visual Studio
Code e a configurará para integração com os serviços Azure OpenAI.
Seguindo as etapas, você aprenderá a configurar um ambiente de
desenvolvimento local, modificar arquivos de projeto e preparar o
aplicativo para execução usando os detalhes de implementação do Azure
OpenAI.

1.  Abra o **Command Prompt.**

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image15.png)

2.  Execute os comandos abaixo um por um.

+++dotnet nuget list source+++

+++dotnet nuget add source [https://api.nuget.org/v3/index.json --name
nuget.org](https://api.nuget.org/v3/index.json%20--name%20nuget.org)+++

3.  Abra o **Visual Studio Code**. Selecione **File** -\> **Open
    Folder**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image16.png)

4.  Navegue até **C:\LabFiles** e selecione a pasta **AITravelAgent** e
    clique em **Select Folder**. A pasta será aberta no VS Code.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image17.png)

5.  No painel **EXPLORER**, navegue até a pasta
    **AITravelAgent/Starter**. Clique com o botão direito do mouse na
    pasta e selecione **Open in Integrated Terminal**.

> ![Uma captura de tela de um computador Descrição gerada
> automaticamente](./media/image18.png)

6.  No painel **EXPLORER**, expanda a pasta **Starter** e você verá a
    pasta **Plugins**, a pasta **Prompts** e o arquivo **Program.cs**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image19.png)

7.  Abra o arquivo **Starter/Program.cs** e atualize as variáveis a
    seguir com o nome de implementação do Azure OpenAI Services, a chave
    de API e o ponto de endpoint. Depois de fazer as alterações,
    pressione **Ctrl + S** para salvar o arquivo:

> string yourDeploymentName = +++**gpt-35-turbo-16k+++**
>
> string yourEndpoint = O valor do endpoint do recurso Azure OpenAI que
> salvamos anteriormente
>
> string yourKey = A Key 1 do recurso AOAI que salvamos anteriormente
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image20.png)

## Exercício 4: Criando e testando um plug-in conversor de moeda com Semantic Kernel

Neste exercício, você criará um plug-in conversor de moeda usando o
Semantic Kernel. Você escreverá e testará uma função que converte um
valor de uma moeda para outra usando taxas de câmbio predefinidas. Este
exercício ajudará você a entender como criar e chamar plug-ins
personalizados, utilizar decoradores para funcionalidade e descrições e
integrar plug-ins em um aplicativo maior.

1.  Crie um novo arquivo chamado +++**CurrencyConverter.cs**+++ na pasta
    **Stater/Plugins/ConvertCurrency**

> ![Uma captura de tela de um computador Descrição gerada
> automaticamente](./media/image21.png)

2.  No arquivo **CurrencyConverter.cs**, adicione o seguinte código para
    criar uma função de plug-in

> using Microsoft.SemanticKernel;
>
> using System.ComponentModel;
>
> using AITravelAgent;
>
> class CurrencyConverter
>
> {
>
> \[KernelFunction,
>
> Description("Convert an amount from one currency to another")\]
>
> public static string ConvertAmount(
>
> {
>
> var currencyDictionary = Currency.Currencies;
>
> }
>
> }

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

> Neste código, você usa o decorador KernelFunction para declarar sua
> função nativa. Você também usa o decorador Description para adicionar
> uma descrição do que a função faz. Você pode usar Currency.Currencies
> para obter um dicionário de moedas e suas taxas de câmbio. Em seguida,
> adicione alguma lógica para converter um determinado valor de uma
> moeda para outra.

3.  Modifique sua função **ConvertAmount**. Substitua o código existente
    pelo código abaixo:

> using Microsoft.SemanticKernel;
>
> using System.ComponentModel;
>
> using AITravelAgent;
>
> class CurrencyConverter
>
> {
>
> \[KernelFunction, Description(@"Converts an amount from one currency
> to another
>
> and returns a friendly message with the results")\]
>
> public static string ConvertAmount(
>
> \[Description("The starting currency code")\] string baseCurrencyCode,
>
> \[Description("The target currency code")\] string targetCurrencyCode,
>
> \[Description("The amount to convert")\] string amount)
>
> {
>
> var currencyDictionary = Currency.Currencies;
>
> Currency targetCurrency = currencyDictionary\[targetCurrencyCode\];
>
> Currency baseCurrency = currencyDictionary\[baseCurrencyCode\];
>
> if (targetCurrency == null)
>
> {
>
> return targetCurrencyCode + " was not found";
>
> }
>
> else if (baseCurrency == null)
>
> {
>
> return baseCurrencyCode + " was not found";
>
> }
>
> else
>
> {
>
> double amountInUSD = Double.Parse(amount) \* baseCurrency.USDPerUnit;
>
> double result = amountInUSD \* targetCurrency.UnitsPerUSD;
>
> return $"${amount} {baseCurrencyCode} is approximately
> {result.ToString("C")} in {targetCurrency.Name}s
> ({targetCurrencyCode})";
>
> }
>
> }
>
> }
>
> Neste código, você usa o dicionário **Currency.Currencies** para obter
> o objeto Currency para as moedas base e de destino. Em seguida, use o
> objeto **Currency** para converter o valor da moeda base para a moeda
> de destino. Por fim, você retorna uma string com o valor convertido.
> Em seguida, vamos testar seu plug-in.
>
> ![A screenshot of a computer program AI-generated content may be
> incorrect.](./media/image23.png)
>
> **Observação:** ao usar o Semantic Kernel SDK em seus próprios
> projetos, você não precisa codificar dados em arquivos se tiver acesso
> a APIs RESTful. Em vez disso, você pode usar o plug-in
> Plugins.Core.HttpClient para recuperar dados de APIs.

4.  No arquivo **Starter/Program.cs**, importe e chame sua nova função
    de plug-in com o código a seguir. (Exclua o código below var kernel
    = builder.Build(); e substitua-o pelo código abaixo.)

> kernel. ImportPluginFromType\<CurrencyConverter\>();
>
> kernel. ImportPluginFromType\<ConversationSummaryPlugin\>();
>
> var prompts = kernel. ImportPluginFromPromptDirectory("Prompts");
>
> var resultado = await kernel. InvokeAsync("CurrencyConverter",
>
> "ConvertAmount",
>
> novo() {
>
> {"targetCurrencyCode", "USD"},
>
> {"amount", "52000"},
>
> {"baseCurrencyCode", "VND"}
>
> }
>
> );
>
> Console.WriteLine(result);
>
> Neste código, você usa o método **ImportPluginFromType** para importar
> seu plug-in. Em seguida, você usa o método **InvokeAsync** para
> invocar sua função de plug-in. O método **InvokeAsync** usa o nome do
> plug-in, o nome da função e um dicionário de parâmetros. Por fim,
> imprima o resultado no console. Em seguida, execute o código para
> verificar se ele está funcionando.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image24.png)

5.  Vá em **File** na barra superior e selecione **Save All.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

6.  No terminal, insira **dotnet run**. Você deve ver a seguinte saída:

Output: $52000 VND is approximately $2.13 in US Dollars (USD)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

> Agora que seu plug-in está funcionando corretamente, vamos criar um
> prompt de linguagem natural que possa detectar quais moedas e valores
> o usuário deseja converter.

## Exercício 5: Configurando um prompt de moeda de destino para processamento semântico

Neste exercício, você configurará um sistema de prompt para identificar
moedas base, moedas de destino e valores da entrada do usuário. Ao criar
e configurar arquivos de configuração e prompt, você definirá como a AI
interpreta e processa solicitações de linguagem natural para conversões
de moeda.

1.  No **Visual Studio Code**, localize a pasta **Starter/Prompt**.
    Navegue até esta pasta para se preparar para as próximas etapas.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image27.png)

2.  Dentro da pasta **Starter/Prompt**, crie uma nova pasta chamada
    +++**GetTargetCurrencies**+++. Esta pasta conterá todos os arquivos
    relacionados a este exercício.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image28.png)

3.  Na pasta **GetTargetCurrencies**, crie um novo arquivo chamado
    +++**config.json**+++.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image29.png)

4.  Abra o arquivo **config.json** recém-criado no **Visual Studio
    Code**. Copie e cole o código a seguir no arquivo.

> {
>
> "schema": 1,
>
> "type": "completion",
>
> "description": "Identify the target currency, base currency, and
> amount to convert",
>
> "execution_settings": {
>
> "default": {
>
> "max_tokens": 800,
>
> "temperature": 0
>
> }
>
> },
>
> "input_variables": \[
>
> {
>
> "name": "input",
>
> "description": "Text describing some currency amount to convert",
>
> "required": true
>
> }
>
> \]
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image30.png)
>
> Salve o arquivo pressionando **Ctrl + S**. Essa configuração define
> como o sistema de AI deve interpretar e processar a entrada do
> usuário.

5.  Ainda dentro da pasta **GetTargetCurrencies**, crie outro novo
    arquivo chamado +++**skprompt.txt**+++.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image31.png)

6.  Abra o arquivo **skprompt.txt** em seu editor de texto e cole o
    seguinte conteúdo:

> \<message role="system"\>Identify the target currency, base currency,
> and
>
> amount from the user's input in the format
> target|base|amount\</message\>
>
> For example:
>
> \<message role="user"\>How much in GBP is 750.000 VND?\</message\>
>
> \<message role="assistant"\>GBP|VND|750000\</message\>
>
> \<message role="user"\>How much is 60 USD in New Zealand
> Dollars?\</message\>
>
> \<message role="assistant"\>NZD|USD|60\</message\>
>
> \<message role="user"\>How many Korean Won is 33,000 yen?\</message\>
>
> \<message role="assistant"\>KRW|JPY|33000\</message\>
>
> \<message role="user"\>{{$input}}\</message\>
>
> \<message role="assistant"\>target|base|amount\</message\>
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image32.png)
>
> Salve o arquivo pressionando **Ctrl + S**. Esse script define a lógica
> de prompt para processar solicitações de conversão de moeda.

## Exercício 6: Configurando um sistema de prompt para recomendações de atividades de viagem

Neste exercício, você configurará e personalizará um sistema de prompt
para sugerir atividades e pontos de interesse com base no destino de
viagem de um usuário. Ao editar os arquivos de configuração e prompt,
você definirá o comportamento, o tom e os requisitos de entrada do
sistema para gerar recomendações de viagem personalizadas e criativas.

1.  No **Visual Studio Code**, navegue até a pasta
    **Starter/Prompts/SuggestActivities**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

2.  Localize o arquivo **config.json** dentro da pasta
    **SuggestActivities** e abra-o.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image34.png)

3.  Substitua o código existente no arquivo **config.json** pelo
    seguinte:

> {
>
> "schema": 1,
>
> "type": "completion",
>
> "description": "Suggest activities and points of interest at a given
> destination",
>
> "execution_settings": {
>
> "default": {
>
> "max_tokens": 4000,
>
> "temperature": 0.5
>
> }
>
> },
>
> "input_variables": \[
>
> {
>
> "name": "history",
>
> "description": "Some background information about the user",
>
> "required": false
>
> },
>
> {
>
> "name": "destination",
>
> "description": "The destination a user wants to visit",
>
> "required": true
>
> }
>
> \]
>
> }
>
> ![A screenshot of a computer code AI-generated content may be
> incorrect.](./media/image35.png)
>
> Salve o arquivo depois de fazer as alterações pressionando **Ctrl +
> S**. Esse arquivo configura o sistema para processar entradas do
> usuário e gerar sugestões de atividades.

4.  Permaneça na pasta **SuggestActivities** e localize o arquivo
    **skprompt.txt**. Abra este arquivo no editor.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image36.png)

5.  Substitua o conteúdo existente do **skprompt.txt** pelo seguinte
    texto:

> You are an experienced travel agent.
>
> You are helpful, creative, and very friendly.
>
> Consider the traveler's background: {{$history}}
>
> The traveler would like some activity recommendations for their trip
> to {{$destination}}.
>
> Please suggest a list of things to do, see, and points of interest.
>
> ![A screenshot of a computer code AI-generated content may be
> incorrect.](./media/image37.png)
>
> Salve o arquivo pressionando **Ctrl + S**. Esse script define o
> comportamento e o tom do sistema ao gerar recomendações de atividades.

## Exercício 7: Configurando o programa principal para fluxo de trabalho de AI

Neste exercício, você configurará o arquivo Program.cs principal para
integração com os serviços Azure OpenAI e o Microsoft Semantic Kernel.
Ao personalizar o código, você habilitará funcionalidades como conversão
de moeda, sugestões de atividades e recomendações de viagem. Essa
configuração estabelece um fluxo de trabalho robusto com inteligência
artificial para interação do usuário e reconhecimento de intenção,
aproveitando plug-ins e lógica baseada em prompt.

1.  No projeto no **Visual Studio Code**, navegue até o arquivo
    **Starter/Program.cs** e abra-o para edição.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

2.  Substitua todo o conteúdo do arquivo **Program.cs** pelo código a
    seguir e pressione **Cntrl + S** para salvar o código.

**Observação:** depois de substituir o código, adicione novamente o
endpoint, a chave e o nome da implementação nas partes respectivas do
código.

[TABLE]

> O programa começa importando namespaces essenciais, como System.Text
> para manipulação de texto e Microsoft.SemanticKernel para fluxos de
> trabalho de conversação com tecnologia de AI. Ele integra os serviços
> Microsoft Azure OpenAI por meio do namespace
> Microsoft.SemanticKernel.Connectors.OpenAI, permitindo a comunicação
> com o modelo GPT (gpt-35-turbo-16k). A configuração envolve a
> configuração de variáveis como yourDeploymentName, yourEndpoint e
> yourApiKey para autenticar e se conectar ao ponto de extremidade do
> OpenAI do Azure.
>
> O **Semantic Kernel** é inicializado usando um padrão de construtor.
> Plug-ins para funcionalidades adicionais, como CurrencyConverter e
> ConversationSummaryPlugin, são importados. Além disso, os prompts
> armazenados em um diretório (Prompts) são carregados dinamicamente
> para facilitar o reconhecimento da intenção e a execução da tarefa.
>
> O loop principal do programa interage com o usuário solicitando
> entrada e determinando a intenção usando o prompt GetIntent. Com base
> na intenção, o programa se ramifica em diferentes funcionalidades:

1.  **Conversão de moeda**: se a intenção for converter moeda, o
    programa extrairá detalhes (moeda base, moeda de destino e valor)
    usando o prompt GetTargetCurrencies. Em seguida, ele chama o método
    ConvertAmount do plug-in CurrencyConverter e exibe o resultado.

2.  **Sugestões de destino**: se a intenção for sugerir destinos, o
    programa usará o método InvokePromptAsync do Semantic Kernel para
    fornecer recomendações com base na entrada do usuário.

3.  **Sugestões de atividades**: essa funcionalidade aproveita o resumo
    da conversa por meio do ConversationSummaryPlugin para fornecer
    sugestões de atividades contextualmente relevantes. O histórico de
    conversas é mantido usando um objeto StringBuilder para fluxo de
    diálogo contínuo.

4.  **Frases úteis e tradução**: para intenções como "HelpfulPhrases" ou
    "Translate", o kernel invoca automaticamente funções relevantes com
    base na entrada e nas configurações.

> Outras intenções do usuário são tratadas genericamente invocando o
> sistema de prompt, garantindo flexibilidade nas respostas. O loop de
> interação continua até que o usuário não forneça nenhuma entrada (uma
> cadeia de caracteres vazia).

## Exercício 8: Testando o aplicativo

Neste exercício, você testará a funcionalidade do seu aplicativo
executando consultas para conversão de moeda, sugestões de destino e
recomendações de atividades. Isso garantirá que seu sistema alimentado
por AI esteja funcionando conforme o esperado e fornecendo saídas
precisas e sensíveis ao contexto.

**Etapas para testar**

1.  **Execute o aplicativo**

    - Clique com o botão direito do mouse na pasta Starter e selecione
      **Open in Integrated Terminal**.

    - No terminal, digite o seguinte comando para executar o aplicativo:

> +++dotnet run+++

2.  **Testar conversão de moeda**

    - Quando solicitado, insira uma consulta de conversão de moeda,
      como:  
      *+++* How much is 60 USD in New Zealand dollars?*+++*

    - Saída esperada:  
      *$60 USD is approximately $97.88 in New Zealand Dollars (NZD)."*

3.  **Sugestões de destino de teste**

    - Insira uma consulta para sugestões de destino, fornecendo
      contexto. Por exemplo:  
      *+++* I'm planning an anniversary trip with my spouse, but they
      are currently using a wheelchair and accessibility is a must. What
      are some destinations that would be romantic for us?+++

    - Saída esperada: Uma lista de destinos românticos acessíveis, como:

      1.  Santorini, Greece: romantic sunsets and wheelchair-accessible
          paths in certain areas.

      2.  Venice, Italy: gondola rides with accessible boarding options.

      3.  Maui, Hawaii: stunning views and accessible resorts.

4.  **Sugestões de atividades de teste**

    - Insira uma consulta para recomendações de atividades em um destino
      específico. Por exemplo:  
      *+++* What are some things to do in Barcelona?+++

    - Saída esperada: recomendações adaptadas ao destino, como:

      1.  Visit the Sagrada Família: a Gaudí masterpiece with accessible
          facilities.

      2.  Explore Park Güell: unique mosaic designs with
          wheelchair-friendly routes.

      3.  Discover the Picasso Museum: a wheelchair-accessible art
          venue.

Exercício 7: Limpar os recursos

1.  No portal do Azure (+++https://portal.azure.com+++), selecione o
    grupo de recursos atribuído a você.

2.  Selecione os recursos abaixo dele e clique em **Delete**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

3.  Digite +++ **delete**+++ na caixa de confirmação de exclusão e
    clique em **Delete**.

4.  Selecione **Delete** na caixa de diálogo de confirmação.

5.  Procure uma notificação de confirmação de exclusão de recurso.

**Resumo:**

Neste laboratório, aprendemos a criar um agente usando o Semantic Kernel
e o serviço Azure OpenAI.

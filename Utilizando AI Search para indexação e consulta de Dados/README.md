# Passo a passo de como usar o Azure Cognitive Search.

Primeiramente criamos um recurso Azure Search, selecionando o a inscrição, o resource group, o nome escolhido do recurso, e o pricing tier Basic.

Após isso criamos novamente recurso do Azure AI services.

E por ultimo criamos um Storage.

Após isso configuramos o nosso storage, clicando na aba da esquerda configuração, e habilitamos a opção allow blob anonymous access.

Depois disso criamos um container. Para isso vamos em data storage, e depois na aba lateral esquerda clicamos em container, e na opção + Container.

Para a criação do container colocamos as seguintes opções:

- Name: coffee-reviews

- Public access level: Container (anonymous read access for containers and blobs)

E então dentro de nosso container podemos escolher um arquivo de nosso browser, o qual eu coloquei o arquivo review que está na pasta desse diretório.

## Importar e indexar os dados.

Após criarmos nosso container, podemos voltar no recurso do AI serach que criamos, e então clicamos na opção Import Data, onde teremos que conectar com o nosso Data Source, para isso selecionamos a opção Azure Blob Storage.

Teremos que completar a data store com os seguintes dados:

- Data Source: Azure Blob Storage

- Data source name: coffee-customer-data

- Data to extract: Content and metadata

- Connection string: Selecionamos nossa storage, e depois o nosso container.

Clicamos então para Add cognitive skills.

Dentro do Attach Cognitive Services colocamos os seguintes dados:

- Skillset name: coffee-skillset.

- Deixamos marcado a opção: Enable OCR.

- Enrichment granularity level: Pages (5000 character chunks).

Agora em Save enrichments to a knowledge store marcamos:

- Image projections
- Documents
- Pages
- Key phrases
- Entities
- Image details
- Image references

Então selecionamos Azure blob projections: Document. Clicamos em Next: Customize target index.

Dentro de Customize target index mudamos o Index name para coffee-index e selecionamos a opção filterable para todos os campos que jjá estão selecionados por padrão.

Clicamos em Next: Create an indexer.

Deixamos a opção Schedule marcado para Once. Clicamos em submit.

## Testando

Voltamos para o Azure AI Services e clicamos na opção Search Explorer para testarmos o nosso index.

Colocamos search=locations:'Chicago'. Isso irá nos fazer ver as ocirrencias em chicago. Me retornou o código o qual eu coloquei no documento message que esttá neste repositório.


Basicamente nos dando informações de uma cafeteria em Chicago.


## Conclusão

Esse recurso de pesquisa dentro de documentos, como a que nos foi apresentada, pode nos dar uma melhor organização dentro dos diversos arquivos de uma empresa seja ela qual for.










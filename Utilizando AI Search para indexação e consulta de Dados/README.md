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

Colocamos search=locations:'Chicago'. Isso irá nos fazer ver as ocirrencias em chicago. Me retornou o seguinte código:

{
  "@odata.context": "https://azureaiserach900.search.windows.net/indexes('coffee-index')/$metadata#docs(*)",
  "value": [
    {
      "@search.score": 3.5586636,
      "content": "\n\nReview: The coffee tastings every Wednesday afternoon are so fun. Each month there is a new drink theme. You do need to book a spot in advance to attend. It is very worth it! I also love their local music. Fourth Coffee brings in rising artists every weekend. I like to head over there mid-afternoon on weekdays when it’s not too busy and get a slice of pie or their seasonal baked goods.  \nDate: August 13, 2018\nLocation: Chicago, Illinois  \n\nimage1.png\n\n\n\nimage2.png\n\n\n\n",
      "metadata_storage_path": "aHR0cHM6Ly9zdG9yYWdldmVudHVyYWFpOTAwLmJsb2IuY29yZS53aW5kb3dzLm5ldC9jb2ZmZXJldmlld3MvcmV2aWV3LTQuZG9jeA2",
      "locations": [
        "Fourth Coffee",
        "Chicago",
        "Illinois"
      ],
      "keyphrases": [
        "new drink theme",
        "seasonal baked goods",
        "coffee tastings",
        "local music",
        "Fourth Coffee",
        "rising artists",
        "ierican Coffee",
        "Review",
        "afternoon",
        "spot",
        "advance",
        "weekdays",
        "slice",
        "pie",
        "Date",
        "August",
        "Location",
        "Chicago",
        "Illinois"
      ],
      "sentiment": "[\"positive\"]",
      "merged_content": "\n\nReview: The coffee tastings every Wednesday afternoon are so fun. Each month there is a new drink theme. You do need to book a spot in advance to attend. It is very worth it! I also love their local music. Fourth Coffee brings in rising artists every weekend. I like to head over there mid-afternoon on weekdays when it’s not too busy and get a slice of pie or their seasonal baked goods.  \nDate: August 13, 2018\nLocation: Chicago, Illinois  \n\nimage1.png\n ierican Coffee 114 10148/0034 \n\n\nimage2.png\n  \n\n\n",
      "text": [
        "ierican Coffee 114 10148/0034",
        ""
      ],
      "layoutText": [
        "{\"language\":\"en\",\"text\":\"ierican Coffee 114 10148/0034\",\"lines\":[{\"boundingBox\":[{\"x\":701,\"y\":284},{\"x\":649,\"y\":303},{\"x\":647,\"y\":297},{\"x\":699,\"y\":279}],\"text\":\"ierican Coffee\"},{\"boundingBox\":[{\"x\":682,\"y\":241},{\"x\":614,\"y\":263},{\"x\":611,\"y\":251},{\"x\":678,\"y\":228}],\"text\":\"114 10148/0034\"}],\"words\":[{\"boundingBox\":[{\"x\":701,\"y\":285},{\"x\":679,\"y\":293},{\"x\":676,\"y\":287},{\"x\":699,\"y\":279}],\"text\":\"ierican\"},{\"boundingBox\":[{\"x\":676,\"y\":294},{\"x\":652,\"y\":303},{\"x\":650,\"y\":297},{\"x\":674,\"y\":288}],\"text\":\"Coffee\"},{\"boundingBox\":[{\"x\":682,\"y\":242},{\"x\":672,\"y\":245},{\"x\":668,\"y\":232},{\"x\":678,\"y\":229}],\"text\":\"114\"},{\"boundingBox\":[{\"x\":669,\"y\":245},{\"x\":618,\"y\":262},{\"x\":615,\"y\":251},{\"x\":666,\"y\":233}],\"text\":\"10148/0034\"}]}",
        "{\"language\":\"en\",\"text\":\"\",\"lines\":[],\"words\":[]}"
      ],
      "imageTags": [
        "food",
        "chocolate",
        "table",
        "cup",
        "serveware",
        "indoor",
        "cocoa solids",
        "caffeine",
        "tableware",
        "sitting",
        "coffee",
        "dessert",
        "musical instrument",
        "music",
        "concert",
        "clothing",
        "person",
        "string instrument",
        "human face",
        "microphone",
        "plucked string instruments",
        "acoustic guitar",
        "guitar",
        "indoor",
        "woman"
      ],
      "imageCaption": [
        "{\"tags\":[\"cup\",\"coffee\",\"table\",\"indoor\",\"pastry\",\"beverage\",\"breakfast\",\"close\"],\"captions\":[{\"text\":\"a group of small cups with brown liquid in them\",\"confidence\":0.39556038379669189}]}",
        "{\"tags\":[\"person\",\"music\",\"guitar\",\"bowed instrument\",\"bass\"],\"captions\":[{\"text\":\"a person playing a guitar\",\"confidence\":0.54444891214370728}]}"
      ]
    },
    {
      "@search.score": 2.3650222,
      "content": "\nReview: I often make Fourth Coffee my meeting spot for my client meetings weekday mornings. I own a small business and the folks who work at Fourth Coffee are always very friendly. It leaves a good impression on my clients. There are also plenty of drink selections, good wi-fi, and seating. Some of my favorite coffees are the lavender honey latte and, in the winter, the apple-chai latte. There are delicious baked goods offered as well. \nDate: October 21, 2018\nLocation: Chicago, Illinois \n\nimage1.png\n\n\n\n",
      "metadata_storage_path": "aHR0cHM6Ly9zdG9yYWdldmVudHVyYWFpOTAwLmJsb2IuY29yZS53aW5kb3dzLm5ldC9jb2ZmZXJldmlld3MvcmV2aWV3LTUuZG9jeA2",
      "locations": [
        "meeting spot",
        "Chicago",
        "Illinois"
      ],
      "keyphrases": [
        "delicious baked goods",
        "lavender honey latte",
        "apple-chai latte",
        "Fourth Coffee",
        "meeting spot",
        "client meetings",
        "small business",
        "good impression",
        "drink selections",
        "good wi",
        "favorite coffees",
        "Review",
        "mornings",
        "folks",
        "clients",
        "plenty",
        "fi",
        "seating",
        "winter",
        "Date",
        "October",
        "Location",
        "Chicago",
        "Illinois"
      ],
      "sentiment": "[\"positive\"]",
      "merged_content": "\nReview: I often make Fourth Coffee my meeting spot for my client meetings weekday mornings. I own a small business and the folks who work at Fourth Coffee are always very friendly. It leaves a good impression on my clients. There are also plenty of drink selections, good wi-fi, and seating. Some of my favorite coffees are the lavender honey latte and, in the winter, the apple-chai latte. There are delicious baked goods offered as well. \nDate: October 21, 2018\nLocation: Chicago, Illinois \n\nimage1.png\n  \n\n\n",
      "text": [
        ""
      ],
      "layoutText": [
        "{\"language\":\"en\",\"text\":\"\",\"lines\":[],\"words\":[]}"
      ],
      "imageTags": [
        "clothing",
        "person",
        "furniture",
        "human face",
        "chair",
        "table",
        "woman",
        "indoor",
        "window",
        "desk",
        "sitting",
        "people",
        "restaurant"
      ],
      "imageCaption": [
        "{\"tags\":[\"person\",\"woman\",\"laptop\",\"dish\"],\"captions\":[{\"text\":\"a woman showing a woman something on a tablet\",\"confidence\":0.513512134552002}]}"
      ]
    },
    {
      "@search.score": 0.96866095,
      "content": "Review: Today I was truly disappointed with how long I had to wait for the pastries I ordered ahead of time. When I got my box, some of the pastries seemed stale. Terrible experience!  \nDate: October 23, 2018\nLocation: Chicago, Illinois \n\n",
      "metadata_storage_path": "aHR0cHM6Ly9zdG9yYWdldmVudHVyYWFpOTAwLmJsb2IuY29yZS53aW5kb3dzLm5ldC9jb2ZmZXJldmlld3MvcmV2aWV3LTguZG9jeA2",
      "locations": [
        "Chicago",
        "Illinois"
      ],
      "keyphrases": [
        "Terrible experience",
        "Review",
        "pastries",
        "time",
        "box",
        "Date",
        "October",
        "Location",
        "Chicago",
        "Illinois"
      ],
      "sentiment": "[\"negative\"]",
      "merged_content": "Review: Today I was truly disappointed with how long I had to wait for the pastries I ordered ahead of time. When I got my box, some of the pastries seemed stale. Terrible experience!  \nDate: October 23, 2018\nLocation: Chicago, Illinois \n\n",
      "text": [],
      "layoutText": [],
      "imageTags": [],
      "imageCaption": []
    }
  ]
}


Basicamente nos dando informações de uma cafeteria em Chicago.


## Conclusão

Esse recurso de pesquisa dentro de documentos, como a que nos foi apresentada, pode nos dar uma melhor organização dentro dos diversos arquivos de uma empresa seja ela qual for.










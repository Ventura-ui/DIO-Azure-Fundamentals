# Análise de Sentimentos com Language Studio no Azure AI

Aqui eu deixarei minha rápida experiência com os sistemas de linguagem do Azure AI.

## Speech Studio

Dentro do Speech Studio, após fazer login, vamos para a seção Conversão de fala em texto, e então selecionamos a opção Conversão de fala em texto em tempo real.

Dentro do Conversão de fala em texto em tempo real, podemos enviar arquivos de áudio, ou até mesmo gravarmos um áudio para que a IA identifique o que está sendo falado. 

Primeiramente selecionamos o idioma o qual o áudio está sendo falado, como no exemplo abaixo:

<img align="right" src="https://github.com/Ventura-ui/DIO-Azure-Fundamentals/blob/main/An%C3%A1lise%20de%20Sentimentos%20com%20Language%20Studio%20no%20Azure%20A/outputs/imagem1.png?raw=true" width=""/> 

Como podemos ver do lado direito ele escreve tudo que foi dito no áudio.

## Language Studio

Dentro do Language Studio, após fazer o login, vamos na aba Classify Text, e entramos em Analyze sentiment and mine opinions, essa seção irá definir o sentimento que está predominate no texto colocado.

Ao entramos na seção selecionamos o idioma que irá ser utilizado no texto, e então inserimos o texto.

Eu testei dois textos o primeiro em inglês e o segundo em português. Os textos são os seguintes:

1) Good Hotel and staff
 The Royal Hotel, London, UK
 3/2/2018
 Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey,
 and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which
 is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star.
 We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enormous bathroom. Thoroughly recommended.


2) Ontém fui no jogo de futebol num estádio aqui da cidade, foi super divertido meu time saiu campeão.

## Saídas dos textos:

Texto 1:

<img align="" src="https://github.com/Ventura-ui/DIO-Azure-Fundamentals/blob/main/An%C3%A1lise%20de%20Sentimentos%20com%20Language%20Studio%20no%20Azure%20A/outputs/imagem2.png?raw=true" width=""/> 

Texto 2:

<img align="" src="https://github.com/Ventura-ui/DIO-Azure-Fundamentals/blob/main/An%C3%A1lise%20de%20Sentimentos%20com%20Language%20Studio%20no%20Azure%20A/outputs/imagem3.png?raw=true" width=""/> 


Podemos observar que:

1 - No texto 1, a IA indentificou sentimentos negativos, a partir das palavras Tired e poor.

2 - No texto 2, a IA identificou sentimentos totalmente positivos.

## Conclusão

Penso que todos esses recursos são interessantissimos, e que os recursos de fala, como o mostrado primeiro, pode nos ajudar no dia a dia, assim como ja nos ajudam com aparelhos como a Alexa por exemplo. Já os recursos de Language para identificar padrões comportamentais e sentimentais através de textos, podem servir de ajuda em sistemas de suporte ao cliente por exemplo.

# Passo a passo no processo de desenvolvimento de um modelo de previsão

Antes de começar é necessário a criação de um workspace na Azure, e então podemos começar a criar o nosso ML automatizado.

Clicando na barra da esquerda em ML automatizado e em seguida + Novo trabalho ML automatizado.

ps: O modelo que criamos esta relacionado a um aluguel de bicicletas.

Seguindo teremos que especificar algumas configurações básicas as quais eu informei o seguinte:

* Nome do trabalho: mslearn-bike-automl
* Nome do Experimento: mslearn-bike-automl
* Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas

Após isso temos que especificar o tipo de tarefa o qual foi selecionado o tipo Regressão,
e então clicamos em criar para informarmos o tipo do ativo e o nome dos dados:

* Nome: alugueldebicicletas
* Descrição: dados históricos de aluguel de bicicletas
* Tipo: Tabular

Escolhemos uma fonte de dados de arquivos da web e insirimos o seguinte URL da Web:

https://aka.ms/bike-rentals

Verificamos se o URL esta correto e avançamos.

Dentro das configurações determinamos o seguinte:

* Formato do arquivo: Delimitado
* Delimitador: Virgula
* Codificação: UTF-8
* Cabeçalhos de coluna: Somente o primeiro arquivo tem Cabeçalhos

Após isso temos que examinar os tipos de dados, e podemos selecionar para ele criar, e então criamos com sucesso os dados de alugueldebicicletas.

Nas configurações de tarefas estão diversas configurações como:

* Coluna de destino: rentals(integer)

Configurações adicionais:

* Modelos Permitidos: RandomForest, LightGB.
* todas as outras configurações adcionais desmarcadas

Em limites:

* Máximo de avaliações: 3
* Máximo de avaliações simultaneas: 3
* Máximo de nós: 3
* Limite de pontuação da métrica: 0.085
* Tempo limite de emperimento: 15 minutos
* Tempo limite de iteração: 15 minutos
* Habilitamos o encerramento antecipado

Em Validar e testar:

* Tipo de validação: Divisão de validação e treinamento
* Tipo de teste: nenhum

Em Computação deixamos todas as configurações como ja estavam.

Então o trabalho de treinamento. Esperamos em torno de 15 minutos para que seja executado o treinamento.

Por fim, temos que testar o nosso modelo, para isso primeiramente temos que criar um, a partir da opção na barra lateral chamada Pontos de extremidade, onde eu criei meu modelo com as seguintes expecificações:

* Nome: predict-rentals
* Descrição: Predict cycle rentals
* Tipo de computação: Azure Container Instance

Demorou em torno de 10 minutos para ficar pronto, e então eu cliquei no meu modelo fui na aba Teste, e la eu troquei o template JSON que estava pelo que está na mesma pasta do meu repositório:

{  

    "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }

O resultado do teste foi o seguinte: 336.64448394959976.











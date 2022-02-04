# Projeto Scraping Learning - Um misto entre Web Scraping e Machine Learning

Projeto traz uma abordagem prática e intuitiva,  a aplicação de conceitos e técnicas adquiridos durante o curso de Python para Data Science da escola de tecnologia ALURA.

Através da prática de web scraping, a criação de uma modelo de machine laerning, foi possível prever com o intuito de trazer uma previsão dos casos de FEMENICÍDIO no estado de São Paulo, além de trazer algumas visualizações com plotly e seaborn.

Etapas resumidas - 'roadmap':

* i. **Questão do problema e Entendimento do problema** - ( FONTE: https://www.brazilianjournals.com/index.php/BJHR/article/view/9998 );

  A violência contra mulher é um problema de saúde pública que tem como consequência mais grave o feminicídio. Segundo dados da Organização Mundial de Saúde (OMS), cerca de 35% das mulheres sofrem violência sexual, seja por seus parceiros íntimos ou não. O início do ano de 2020 foi marcado pelo surgimento do novo Coronavírus e pela rápida disseminação da COVID-19 em diversos países e continentes, tendo sido declarado pela Organização Mundial de Saúde uma pandemia. Com base nos dados levantados das Secretarias de Segurança Pública dos estados brasileiros, pudemos observar que o estado de São Paulo teve um aumento de 138% nos casos de feminicídios comparado ao primeiro trimestre de 2018 e de 38% comparado ao mesmo período de 2019.

* ii. **Coleta de dados - WEB SCRAPING**;
 
  Coleta executada com as principais biblioteca para tal, como requests, BeautifulSoup e pandas.
  
  Primeiramente, o acesso a página do ssp.sp.gov, em seguinda a coleta do 'html.parser', e por fim os acessos <title> e extração do nome da tag.
  
  Em seguinda a mineração dos dados atráves de um loop, com objetivo de encontrar a página para fazer a extração, informando ao .find o período final.
  
  Criando listas para alocar os dados, em seguida a importação do dateutil.relativedelta para criação de uma função que auxiliara a busca de acordo com a última data de publicação no site.
  
  Criação de mais um loop e uma condição de verificação do rótulo == 'FEMINICÍDO'.
  
  A organizaçao do scraping com a criação de um dicionário com as listas criadas e por fim o a exportação para um arquivo do tipo CSV.
    
* iii. **Tratamento  e exploração dos dados**;

  Importação das bibliotecas para análise gráfica como plotly e seaborn, em seguinda um processo de ETL, a extração foi feita no script anterior, e os processos de transformação e carregamento nesse script. 
  
  Verificando dados nulos e tipos de dados que constituem o dataset, além de converter o Dtype da coluna periodo de: object para: datetime64[ns]
  
  Aplicando .describe para uma visualização inicial da contagem dos dados, média, desvio padrão, com valor consideravél baixo, representando assim uma menor dispersão dos dados e, outras métricas.  
  
 * iv. **Visualições**; 
 
 Plot 1, retrata um serie de acontecimentos ao longo do tempo, entre os anos de 2018 e 2021, com picos que variam entre o perído de JUL/2019.
  
 O plot2, é um boxplot com o objetivo de ter a nitidez e perceber à dispersão dos dados e visualização de outliers. Além  de auxiliar na escolha da medida de desempenho futuramente. 
  
 Observa-se que a dispersão dos dados representadada pelo intervalo interquatílico é de oito ocorrências, valor próximo a mediana dos dados. Já a simetria dos dados mostra que a distribuição é positiva, por conta da proximidade da linha com o primeiro quartil.
  
          * Média Móvel;
  
  A média móvel, plot 4, foi um recurso utilizado para  identificar a tendência do conjunto de dados dispostos na série de tempo, anos de 2018 a 2021. Embora seja muito difícil identificar exatamente os fatores que afetam o movimento dos dados do projeto, com aplicação do modelo de machine learning é possível prever uma tendência temporal para o próximo ano.
  
  A inclusão da média móvel junto ao plot 1, mostra que o modelo de média móvel atende as previsões um vez que, segue o fluxo dos dados, não se afasta dos dados no final da série, e como as previsões de média móvel são constantes, é observado que não há tendência nos dados antes da previsão final.
  
          * Divisão dos dados Treino e Teste;
  
 Foi optado por escolher 75% dos dados para treino, cerca de trinta e cinco registros e 25% para teste, cerca de doze registros. Em um modelo de machine learning é comum essa subdivisão dos dados para realizar os treinos e testes. Caso nós fizessemos um modelo de Machine Learning e treinássemos nossa rede com a totalidade de dados, poderia haver um Overfitting (ocorre quando o modelo se adaptou muito bem aos dados que foi treinado, mas não generaliza bem para novos dados, seria como se ele tivesse decorado mas não aprendido de fato).
  
  O plot 5, mostra bem como o modelo reage, de fato, existe a correlação entre os dados treinados e dados testados.
  
           * Criando o modelo de Machine Learning
  
  Utilizando a classe de modelos exponential smoothing, com objetivo de suavizar a time series, uma vez que, de acordo com o plot 1, não existe um padrão de sazonalidade ou tendência na série, por isso a escolha dessa classe.
  E utilizando seasonal_periods como 7, ou seja, um semestre.
  
  Plot 6, traz a representação gráfica do que o modelo será capaz de prever, com uma acentuada queda nos valores. Utilizando a métrica **RMSE** para validar o modelo, foi observado que o valor do erro, fica próximo do valor de teste, induzindo que não haverá discrepancia quando incluir novos dados no modelo desenvolvido. 
  
* v. **Comentários "insights" conclusivos**;
  
  Trata-se de um modelo de estudo e aprendizado, focado em aquisição de habilidades de programação e ciência de dados, não recomendado como argumentos justificativos para tal assunto.
  
  Uma melhora no modelo pode vir a existir uma vez que a base do governo do estado de São Paulo, sofre alterações ao passar dos meses.
  
  Os números podem ser ainda maiores, pois nem todos os crimes cometidos contra mulheres por atuais ou ex-parceiros são registrados como feminicídio. No caso de estupro em geral e de vulnerável, a subnotificação já era tema importante na análise dos dados, mas a falta de acesso aos órgãos para realizar a denúncia durante a pandemia pode ter contribuído para uma piora no cenário.
  
  Atenciosamente.
  
  
       

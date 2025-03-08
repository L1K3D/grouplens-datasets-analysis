# grouplens-datasets-analysis
# Grouplens Datasets Analysis

## Português 🇧🇷/Portuguese 🇧🇷

### Dados do Autor e Instituição
CEFSA - Centro Educacional da Fundação Salvador Arena
FESA - Faculdade Engenheiro Salvador Arena
São Bernardo do Campo, 08 de março de 2025
Heitor Santos Ferreira - RA: 081230042 - Engenharia de Computação - 6° Semestre - EC6
Eletiva II - Ambientes Inteligentes
Professor Elias Kento Tomiyama

### Introdução
Esse repositório contém a analise exploratória e explicativa sobre os dados contidos no DataSet 'small' do site Group Lens. É uma atividade verificada e que consta composição de nota para o modelo avaliativo N1 do primeiro bimestre (B1, podendo assim ser chamada também como 'atividade N1B1') da matéria 'Eletiva II - Ambientes Inteligentes', ministrada na FESA (Faculdade Engenheiro Salvador Arena), instituição de ensino superior que compoem o CEFSA (Centro Educacional da Fundação Salvador Arena) pelo professor Elias Kento Tomiyama.

### Descrição do DataSet
O *dataset* se compoem em quatro arquivos distintos que juntos trazem informações variadas de diversos filmes publicados, como seus links de acesso as criticas nos sites de rating como *'IMDB'* e *'TMDB'* para analises de notas e prêmios, trazendo também os nomes dos filmes com seus principais generos abordados durante os longas, rankings gerais com notas fornecidas por avaliações de usuários e os dias e horários nos quais essas notas e analises foram fornecidas e tags das quais os usuários classificaram os filmes, que podem variar entre nomes de atores, sentimentos ao visualizarem os longas, nomes de diretores e outros itens relevantes.

Seguindo a divisão explicada acima, os datasets estão divididos da seguinte maneira com seus respectivos tipos de dados:

***LINKS***
O dataset `links.csv` contém informações sobre filmes, incluindo identificadores exclusivos provenientes de duas das principais bases de dados de filmes online: IMDb e TMDb. 

Tabela com a descrição detalhada de cada coluna do dataset:

| Nome da Coluna | Descrição da Coluna                                      | Tipo de Dado | Exemplo    |
|----------------|----------------------------------------------------------|--------------|------------|
| movieId        | Identificador único para cada filme no dataset           | Integer      | 1          |
| imdbId         | Identificador único do filme na base de dados IMDb       | Integer      | 0114709    |
| tmdbId         | Identificador único do filme na base de dados TMDb       | Integer      | 862        |

*Analise realizada*
Durante a analise realizada perante a tabela de 'links', foi necessário corrigir os itens do campo 'tmdbId' pois os mesmos possiam números variaveis em float e com zeros a direita, o que dificultaria o entendimento durante as demais analises. Mesmo o número sendo registrado como *Integer*, foi necessário realizar essa informação, pois a importação considerou os itens presentes na coluna como 'float'.

A análise exploratória simples realizada sobre a tabela links revelou informações fundamentais sobre o dataset, sua composição e as características de seus atributos. Com um total de 9742 amostras, o dataset abrange uma ampla quantidade de filmes, cada um identificado por três colunas: movieId, imdbId e tmdbId. Esses identificadores correspondem, respectivamente, ao ID interno do filme dentro do dataset, ao identificador único no IMDb (Internet Movie Database) e ao identificador único no TMDb (The Movie Database). A uniformidade nos registros, sem a presença de valores ausentes, demonstra que o dataset está completo e adequado para análises.

Ao examinar a estrutura do dataset, foi possível constatar que as colunas movieId e imdbId estão configuradas como inteiros de 64 bits (int64), enquanto a coluna tmdbId está no formato de inteiro de 32 bits (int32), o que resulta em um menor consumo de memória. No total, o dataset ocupa aproximadamente 190.4 KB, um tamanho relativamente pequeno e eficiente para análise em ferramentas como Python.

As estatísticas descritivas fornecem insights valiosos sobre a distribuição dos valores. O movieId possui valores que variam de 1 a 193609, enquanto o imdbId está na faixa de 417 a 8391976 e o tmdbId varia entre 0 e 525662. Os valores médios das colunas destacam as diferenças entre os identificadores, com o imdbId apresentando uma média de 677183.9, muito superior à média do tmdbId, que é de 55116.82. O movieId, por sua vez, possui uma média de 42200.35. Essas discrepâncias refletem os padrões numéricos distintos das plataformas IMDb e TMDb, além de possíveis inconsistências, como valores 0 em tmdbId, que podem indicar a ausência de mapeamento ou informações incompletas para certos filmes.

Os quartis complementam a análise, demonstrando a distribuição dos valores em cada coluna. Por exemplo, o valor mediano (50º percentil) do movieId é 7300, enquanto o do imdbId é 167260.5 e o do tmdbId é 16497.5. Essas informações ajudam a identificar a concentração de registros e como os dados estão distribuídos ao longo da faixa de valores. Já o desvio padrão das colunas destaca a variação significativa dos dados, especialmente para o imdbId, que possui um desvio de 1107228, indicando uma dispersão considerável em torno da média.

De maneira geral, o dataset demonstra-se robusto e organizado, sem valores ausentes e com metadados claros sobre os filmes. A análise aponta para sua adequação em estudos que exigem o cruzamento com outras tabelas, como informações detalhadas de filmes ou avaliações de usuários. Os identificadores imdbId e tmdbId servem como chaves valiosas para integrar o dataset links

###---###---###---###---###---###---###---###---###---###---###---###---###

***MOVIES***
O dataset `movies.csv` contém informações detalhadas sobre uma coleção de filmes, cada um identificado por um ID único, acompanhado do título e de seus gêneros associados.

Tabela com a descrição detalhada de cada coluna do dataset:

| Nome da Coluna | Descrição da Coluna                                    | Tipo de Dado | Exemplo                                     |
|----------------|--------------------------------------------------------|--------------|---------------------------------------------|
| movieId        | Identificador único para cada filme no dataset         | Integer      | 1                                           |
| title          | Título do filme, incluindo o ano de lançamento         | String       | Toy Story (1995)                            |
| genres         | Gêneros associados ao filme, separados por "|"         | String       | Adventure|Animation|Children|Comedy|Fantasy |

*Analise Realizada*
A análise exploratória realizada sobre a tabela movies fornece uma visão geral abrangente de sua estrutura e conteúdo. Este dataset apresenta um total de 9742 exemplos, cada um representando um filme único. Ele é composto por três atributos principais: movieId, title e genres. A coluna movieId serve como identificador único para cada filme no dataset, enquanto a coluna title contém os títulos dos filmes, incluindo os anos de lançamento, e a coluna genres descreve os gêneros associados a cada filme, utilizando um formato onde os gêneros estão separados por um delimitador.

Não foram identificados valores ausentes em nenhuma das colunas, evidenciado pelo fato de que todas possuem 9742 valores não nulos. Isso reforça a consistência e integridade dos dados, que estão prontos para serem analisados sem a necessidade de tratamentos adicionais para lidar com dados ausentes. Em relação aos tipos de dados, a coluna movieId é do tipo inteiro (int64), enquanto title e genres são do tipo objeto (object). Esse formato é adequado para a representação de identificadores numéricos, texto e categorias dentro do dataset. Em termos de espaço de memória, o dataset ocupa aproximadamente 228.5 KB, o que o torna eficiente para manipulação e processamento em ferramentas de análise de dados.

As estatísticas descritivas da coluna movieId revelam a distribuição dos identificadores numéricos dentro do dataset. O valor mínimo é 1, enquanto o máximo é 193609. A média dos valores é de 42200.35, com um desvio padrão de 52160.49, indicando uma ampla dispersão entre os identificadores. Os valores dos quartis mostram que 25% dos registros possuem um identificador abaixo de 3248.25, 50% (mediana) possuem valores iguais ou inferiores a 7300 e 75% dos registros possuem valores abaixo de 76232. Essa análise reflete a forma como os identificadores estão distribuídos de maneira não uniforme.

Por último, a coluna genres, que originalmente apresentava os gêneros separados por |, foi ajustada para utilizar o delimitador |. Essa mudança aprimora a legibilidade, permitindo que os gêneros sejam mais facilmente interpretados. A distribuição dos gêneros representa uma diversidade significativa de categorias cinematográficas, incluindo combinações de gêneros como Adventure | Animation | Children | Comedy | Fantasy e Comedy | Drama | Romance. Essa variedade sugere que o dataset é valioso para a análise de tendências em gêneros de filmes e oferece um rico potencial para estudos sobre a popularidade de combinações de gêneros.

De maneira geral, o dataset movies demonstra-se limpo, estruturado e bem preparado para análises subsequentes, como exploração de tendências, agrupamento de gêneros e cruzamento com outras tabelas do mesmo conjunto de dados. Ele fornece uma base sólida para a realização de investigações aprofundadas no campo da análise de dados cinematográficos

###---###---###---###---###---###---###---###---###---###---###---###---###

***RATINGS***
O dataset `ratings.csv` armazena dados das avaliações realizadas por usuários para diversos filmes, incluindo a nota atribuída e o momento em que a avaliação foi feita. As informações podem ser cruzadas com outros datasets, como `movies.csv`, para análises mais detalhadas.

Tabela com a descrição detalhada de cada coluna do dataset:

| Nome da Coluna | Descrição da Coluna                                   | Tipo de Dado | Exemplo     |
|----------------|-------------------------------------------------------|--------------|-------------|
| userId         | Identificador único para cada usuário                 | Integer      | 1           |
| movieId        | Identificador único do filme avaliado                 | Integer      | 47          |
| rating         | Nota atribuída ao filme, em uma escala numérica       | Float        | 5.0         |
| timestamp      | Momento da avaliação, no formato Unix (Epoch time)    | Integer      | 964983815   |

*Analise Realizada*
Foi necessário converter o campo 'timestamp' que estava com valores no formato Integer para data e hora real, além de transformar os nomes das colunas para melhor compreensão.

A análise exploratória realizada sobre a tabela ratings oferece uma visão detalhada e interessante sobre os dados de avaliações de filmes fornecidos pelos usuários. O dataset possui 100836 linhas, representando diferentes instâncias de avaliação, e 4 colunas: userId, movieId, rating e timestamp. O campo userId identifica os usuários de forma única, enquanto movieId refere-se ao identificador dos filmes avaliados. A coluna rating contém a nota atribuída pelos usuários aos filmes, variando entre 0.5 (nota mínima) e 5.0 (nota máxima). Já a coluna timestamp foi convertida para um formato de data e hora legíveis, facilitando análises temporais relacionadas ao momento em que as avaliações foram realizadas.

O dataset está completo, sem valores ausentes em nenhuma das colunas, evidenciado pela contagem total de 100836 valores não nulos em cada uma. Em termos de estrutura, as colunas userId e movieId são do tipo inteiro (int64), enquanto rating é do tipo float (float64). O campo timestamp, após a conversão, passou a ser representado como datetime64[ns], permitindo o acesso direto às datas e horários. O dataset ocupa aproximadamente 3.1 MB de memória, o que o torna suficientemente leve para análises em ferramentas padrão de ciência de dados.

As estatísticas descritivas fornecem uma visão mais aprofundada sobre os dados. A média das notas atribuídas pelos usuários aos filmes é de aproximadamente 3.50, com um desvio padrão de 1.04, indicando uma concentração das avaliações em torno de valores intermediários da escala. A mediana (50% dos registros) das notas também é de 3.5, reforçando a ideia de centralidade. Além disso, 25% das avaliações possuem notas iguais ou inferiores a 3.0, enquanto 75% têm notas iguais ou superiores a 4.0.

Quanto às datas das avaliações, as análises mostram que o intervalo de tempo cobre um período amplo, com a avaliação mais antiga registrada em 29 de março de 1996 e a mais recente em 24 de setembro de 2018. A média dos timestamps é equivalente a uma data em torno de 19 de março de 2008, sugerindo que o conjunto de dados reflete um histórico abrangente de avaliações ao longo de mais de duas décadas. O valor do primeiro quartil indica que 25% das avaliações ocorreram antes de abril de 2002, enquanto 75% ocorreram antes de julho de 2015.

A distribuição de identificadores para userId e movieId também merece destaque. O campo userId varia entre 1 e 610, com uma média de aproximadamente 326, sugerindo que o dataset abrange uma comunidade relativamente limitada de usuários altamente engajados. Já o campo movieId possui identificadores que vão de 1 a 193609, com uma média de 19435.29, refletindo a diversidade do catálogo de filmes avaliados.

De maneira geral, o dataset ratings é robusto e bem estruturado, contendo informações ricas para análises detalhadas de tendências, comportamentos de avaliação e preferências do público. A diversidade das notas e o amplo intervalo de datas possibilitam estudos interessantes sobre a evolução das avaliações ao longo do tempo e o impacto de períodos específicos na recepção dos filmes. Além disso, sua estrutura bem organizada facilita o cruzamento com outros datasets, como movies e tags, para enriquecer ainda mais as análises.

###---###---###---###---###---###---###---###---###---###---###---###---###

***TAGS***
O dataset `tags.csv` fornece informações sobre as tags (palavras-chave ou descritores) associadas a filmes por diferentes usuários. Cada registro inclui o identificador do usuário, o identificador do filme, a tag atribuída e o momento em que a tag foi aplicada.

Tabela com a descrição detalhada de cada coluna do dataset:

| Nome da Coluna | Descrição da Coluna                                 | Tipo de Dado | Exemplo              |
|----------------|-----------------------------------------------------|--------------|----------------------|
| userId         | Identificador único para cada usuário               | Integer      | 2                    |
| movieId        | Identificador único do filme associado à tag        | Integer      | 60756                |
| tag            | Tag (palavra-chave) atribuída ao filme pelo usuário | String       | funny                |
| timestamp      | Momento da criação da tag, no formato Unix (Epoch)  | Integer      | 1445714994           |

*Analise Realizada*
A análise exploratória realizada sobre a tabela tags revelou informações importantes e detalhadas sobre este dataset, que contém 3683 registros, representando interações entre usuários e filmes por meio de atribuição de tags. O dataset é composto por quatro colunas principais: userId, movieId, tag e timestamp, que fornecem insights sobre como os filmes são descritos e categorizados pelos usuários.

A coluna userId identifica exclusivamente os usuários que atribuem as tags, enquanto movieId refere-se ao identificador único dos filmes aos quais essas tags estão associadas. A coluna tag, contendo palavras-chave atribuídas pelos usuários para descrever os filmes, foi convertida para letras maiúsculas para garantir maior uniformidade nos dados. Por exemplo, tags como "funny", "Highly quotable" e "Boxing story" foram padronizadas para "FUNNY", "HIGHLY QUOTABLE" e "BOXING STORY". Essa transformação aumenta a consistência e facilita análises futuras.

O campo timestamp, originalmente registrado em formato Unix, foi convertido para um formato de data e hora legível, como "2015-10-24 19:29:54". Essa conversão possibilita análises temporais mais claras, permitindo identificar tendências sobre quando os usuários estão mais engajados na atribuição de tags. A avaliação do período coberto pelo dataset mostra que as tags foram registradas entre 13 de janeiro de 2006 e 16 de setembro de 2018. A data média para os registros é aproximadamente 31 de outubro de 2011, sugerindo que o dataset abrange mais de uma década de interações.

A análise estatística das colunas também oferece percepções valiosas. A coluna userId apresenta valores que variam de 2 a 610, com uma média de 431.15, indicando uma comunidade de usuários consistentemente ativa na atribuição de tags. Já a coluna movieId cobre uma ampla gama de identificadores de filmes, com valores que variam de 1 a 193565 e uma média de 27252.01, refletindo a diversidade do catálogo de filmes ao qual essas tags foram aplicadas.

A padronização e transformação dos dados tornam este dataset altamente funcional para análises qualitativas e categóricas. Ele pode ser utilizado para identificar as tags mais populares, analisar a relação entre filmes e gêneros representados pelas tags, ou mesmo explorar padrões de comportamento dos usuários ao longo do tempo. Essa estrutura bem organizada e rica em informações abre caminho para investigações mais aprofundadas no âmbito da categorização e preferências no universo cinematográfico.


## Inglês 🇺🇸/English 🇺🇸
This repository contains exploratory and explanatory analysis of the data included in the 'small' dataset from the Group Lens website.

### Author and Institution Data
CEFSA - Centro Educaional da Fundação Salvador Arena
FESA - Faculdade Engenheiro Salvador Arena
São Bernardo do Campo, March 8, 2025 
Heitor Santos Ferreira - RA: 081230042 - Computer Engineering - 6th Semester - EC6 
Elective II - Intelligent Environments 
Professor Elias Kento Tomiyama

### Introduction
This repository contains exploratory and explanatory analyses of the data from the 'small' dataset on the Group Lens website. It is a verified activity that contributes to the grading composition of the N1 evaluation model for the first term (B1, also referred to as 'activity N1B1') of the course 'Elective II - Intelligent Environments', taught at FESA (Salvador Arena Engineer College), a higher education institution under CEFSA (Salvador Arena Foundation Educational Center), led by Professor Elias Kento Tomiyama.

### Dataset Description
The dataset comprises four distinct files that collectively provide various pieces of information about a wide range of published movies. This includes links to reviews on rating websites like 'IMDB' and 'TMDB' for analysis of scores and awards. It also features the names of the movies with their main genres, general rankings based on user evaluations, timestamps of when these ratings and reviews were provided, and tags that users assigned to the movies. These tags can include actor names, emotions experienced while watching the movies, director names, and other relevant elements.

Following the division explained above, the datasets are organized as follows with their respective data types:

***LINKS*** 
The links.csv dataset contains information about movies, including unique identifiers from two of the most prominent online movie databases: IMDb and TMDb.

Table with a detailed description of each column in the dataset:

| Column Name   | Column Description                                       | Data Type | Example    |
|---------------|----------------------------------------------------------|-----------|------------|
| movieId       | Unique identifier for each movie in the dataset          | Integer   | 1          |
| imdbId        | Unique identifier for the movie in the IMDb database     | Integer   | 0114709    |
| tmdbId        | Unique identifier for the movie in the TMDb database     | Integer   | 862        |

*Exploratory Analysis*
Analysis Performed During the analysis of the links table, it was necessary to correct the items in the tmdbId field, as they contained variable numbers in float format and trailing zeros, which could complicate understanding in further analyses. Even though the numbers were stored as Integer, this correction was necessary because the initial data import treated the values in the column as 'float'.

The simple exploratory analysis of the links table revealed fundamental information about the dataset, its composition, and the characteristics of its attributes. With a total of 9742 samples, the dataset covers a broad range of movies, each identified by three columns: movieId, imdbId, and tmdbId. These identifiers correspond to the movie's internal ID within the dataset, the unique ID from the IMDb (Internet Movie Database), and the unique ID from the TMDb (The Movie Database), respectively. The uniformity of the records, without missing values, demonstrates that the dataset is complete and suitable for analysis.

Examining the dataset structure, it was found that the movieId and imdbId columns are configured as 64-bit integers (int64), while the tmdbId column is in the 32-bit integer format (int32), resulting in lower memory consumption. Overall, the dataset occupies approximately 190.4 KB, a relatively small and efficient size for analysis in tools like Python.

The descriptive statistics provide valuable insights into the value distributions. The movieId column ranges from 1 to 193609, while the imdbId ranges from 417 to 8391976, and the tmdbId ranges between 0 and 525662. The average values for the columns highlight the differences among the identifiers, with the imdbId having an average of 677183.9, significantly higher than the tmdbId average of 55116.82. The movieId has an average of 42200.35. These discrepancies reflect the distinct numerical patterns of the IMDb and TMDb platforms, as well as potential inconsistencies, such as 0 values in the tmdbId, which may indicate missing mappings or incomplete information for certain movies.

The quartiles complement the analysis, showing the distribution of values within each column. For instance, the median (50th percentile) of the movieId is 7300, while the imdbId median is 167260.5, and the tmdbId median is 16497.5. These insights help identify the concentration of records and how the data is distributed across the range of values. The standard deviation further highlights the significant variation in the data, especially for the imdbId, which has a standard deviation of 1107228, indicating considerable dispersion around the mean.

Overall, the dataset is robust and well-organized, with no missing values and clear metadata about the movies. The analysis suggests its suitability for studies requiring integration with other tables, such as detailed information on movies or user ratings. The imdbId and tmdbId identifiers serve as valuable keys for linking the links dataset to external data sources.

###---###---###---###---###---###---###---###---###---###---###---###---###

***MOVIES***
The `movies.csv` dataset contains detailed information about a collection of movies, each identified by a unique ID, along with its title and associated genres.

Below is a detailed table describing each column in the dataset:

| Column Name   | Column Description                                    | Data Type | Example                                     |
|---------------|-------------------------------------------------------|-----------|---------------------------------------------|
| movieId       | Unique identifier for each movie in the dataset       | Integer   | 1                                           |
| title         | Movie title, including the release year               | String    | Toy Story (1995)                            |
| genres        | Genres associated with the movie, separated by "|"    | String    | Adventure|Animation|Children|Comedy|Fantasy |

*Exploratory Analysis*
The exploratory analysis conducted on the `movies` table provides a comprehensive overview of its structure and content. This dataset consists of a total of **9742 entries**, each representing a unique movie. It is composed of three primary attributes: `movieId`, `title`, and `genres`. The `movieId` column serves as the unique identifier for each movie in the dataset, while the `title` column contains the titles of the movies, including their release years. The `genres` column describes the associated genres of each movie, using a delimiter to separate the genres.

No missing values were identified in any of the columns, as evidenced by all columns containing **9742 non-null values**. This highlights the consistency and integrity of the data, which is ready for analysis without the need for additional cleaning to handle missing values. Regarding data types, the `movieId` column is of type integer (`int64`), while `title` and `genres` are of type object (`object`). This format is well-suited for representing numerical identifiers, text, and categories within the dataset. In terms of memory usage, the dataset occupies approximately **228.5 KB**, making it efficient for manipulation and processing in data analysis tools.

Descriptive statistics for the `movieId` column reveal the distribution of numerical identifiers within the dataset. The minimum value is **1**, while the maximum is **193609**. The average value is **42200.35**, with a standard deviation of **52160.49**, indicating a wide dispersion among the identifiers. The quartile values show that 25% of the records have an identifier below **3248.25**, 50% (median) have values equal to or less than **7300**, and 75% of the records have values below **76232**. This analysis reflects the uneven distribution of the identifiers.

Lastly, the `genres` column, which originally used "|" to separate genres, was adjusted to use the delimiter " | ". This change improves readability, allowing the genres to be more easily interpreted. The genre distribution represents a significant diversity of cinematic categories, including combinations such as `Adventure | Animation | Children | Comedy | Fantasy` and `Comedy | Drama | Romance`. This variety suggests that the dataset is valuable for analyzing trends in movie genres and offers rich potential for studies on the popularity of genre combinations.

In summary, the `movies` dataset is clean, well-structured, and well-prepared for subsequent analyses, such as exploring trends, clustering genres, and cross-referencing with other tables within the same dataset collection. It provides a solid foundation for conducting in-depth investigations in the field of cinematic data analysis.

###---###---###---###---###---###---###---###---###---###---###---###---###

***RATINGS***
The `ratings.csv` dataset stores data on user evaluations for various movies, including the rating given and the time the evaluation was made. This information can be cross-referenced with other datasets, such as `movies.csv`, for more detailed analyses.

Below is a detailed table describing each column in the dataset:

| Column Name   | Column Description                                   | Data Type | Example     |
|---------------|------------------------------------------------------|-----------|-------------|
| userId        | Unique identifier for each user                     | Integer   | 1           |
| movieId       | Unique identifier for the rated movie               | Integer   | 47          |
| rating        | Rating given to the movie on a numerical scale       | Float     | 5.0         |
| timestamp     | Time of evaluation in Unix (Epoch time) format       | Integer   | 964983815   |

*Exploratory Analysis*
It was necessary to convert the `timestamp` field, initially recorded as Integer values, into a real date and time format. Additionally, column names were adjusted for better understanding.

The exploratory analysis conducted on the `ratings` table provides detailed and intriguing insights into the movie evaluations provided by users. The dataset contains **100836 rows**, representing different instances of evaluations, and **4 columns**: `userId`, `movieId`, `rating`, and `timestamp`. The `userId` column uniquely identifies users, while `movieId` refers to the identifiers of the evaluated movies. The `rating` column contains the ratings given by users, ranging from 0.5 (minimum score) to 5.0 (maximum score). The `timestamp` column was converted to a readable date and time format, facilitating temporal analyses of when the evaluations were conducted.

The dataset is complete, with no missing values in any column, as evidenced by a total count of **100836 non-null values** in each. In terms of structure, the `userId` and `movieId` columns are of type integer (`int64`), while `rating` is of type float (`float64`). After conversion, the `timestamp` field is represented as `datetime64[ns]`, allowing direct access to dates and times. The dataset occupies approximately **3.1 MB** of memory, making it lightweight and manageable for standard data science tools.

Descriptive statistics provide deeper insights into the data. The average rating given by users is approximately **3.50**, with a standard deviation of **1.04**, indicating a concentration of evaluations around the mid-range of the scale. The median rating (50th percentile) is also **3.5**, reinforcing this central tendency. Additionally, 25% of the ratings are **3.0** or lower, while 75% are **4.0** or higher.

Regarding the evaluation dates, the analysis shows a broad time range, with the earliest evaluation recorded on **March 29, 1996**, and the most recent on **September 24, 2018**. The average timestamp corresponds to a date around **March 19, 2008**, suggesting that the dataset reflects an extensive history of evaluations spanning over two decades. The first quartile indicates that 25% of the evaluations occurred before **April 2002**, while 75% were recorded before **July 2015**.

The distribution of identifiers for `userId` and `movieId` is also noteworthy. The `userId` field ranges between **1** and **610**, with an average of approximately **326**, indicating that the dataset covers a relatively small, highly engaged user community. Meanwhile, the `movieId` field contains identifiers ranging from **1** to **193609**, with an average of **19435.29**, reflecting the diversity of the evaluated movie catalog.

Overall, the `ratings` dataset is robust and well-structured, containing rich information for detailed analyses of trends, evaluation behaviors, and audience preferences. The diversity of ratings and the wide time span enable fascinating studies on the evolution of evaluations over time and the impact of specific periods on movie reception. Additionally, its well-organized structure makes it easy to cross-reference with other datasets, such as `movies` and `tags`, to further enrich the analyses.

###---###---###---###---###---###---###---###---###---###---###---###---###

***TAGS***
The `tags.csv` dataset provides information about tags (keywords or descriptors) associated with movies by different users. Each record includes the user's unique identifier, the movie identifier, the tag applied, and the moment the tag was created.

Below is a detailed table describing each column in the dataset:

| Column Name   | Column Description                                 | Data Type | Example              |
|---------------|----------------------------------------------------|-----------|----------------------|
| userId        | Unique identifier for each user                   | Integer   | 2                    |
| movieId       | Unique identifier for the movie associated with the tag | Integer   | 60756                |
| tag           | Tag (keyword) assigned to the movie by the user   | String    | funny                |
| timestamp     | Moment of tag creation, in Unix (Epoch) format    | Integer   | 1445714994           |

*Exploratory Analysis*
The exploratory analysis of the `tags` table revealed significant and detailed insights about this dataset, which contains **3683 records**, representing interactions between users and movies through the assignment of tags. The dataset consists of four main columns: `userId`, `movieId`, `tag`, and `timestamp`, which offer insights into how movies are described and categorized by users.

The `userId` column uniquely identifies the users who assign the tags, while `movieId` refers to the unique identifier of the movies to which these tags are associated. The `tag` column, containing keywords assigned by users to describe the movies, was converted to uppercase to ensure greater uniformity in the data. For example, tags such as "funny", "Highly quotable," and "Boxing story" were standardized to "FUNNY," "HIGHLY QUOTABLE," and "BOXING STORY." This transformation enhances consistency and facilitates future analyses.

The `timestamp` field, originally recorded in Unix format, was converted into a readable date and time format, such as "2015-10-24 19:29:54." This conversion enables clearer temporal analyses, allowing trends to be identified regarding when users were more engaged in tagging. An evaluation of the time period covered by the dataset shows that the tags were recorded between **January 13, 2006**, and **September 16, 2018**. The average date for the records is approximately **October 31, 2011**, suggesting that the dataset spans more than a decade of interactions.

Statistical analysis of the columns also provides valuable insights. The `userId` column presents values ranging from 2 to 610, with an average of **431.15**, indicating a community of users consistently active in assigning tags. Meanwhile, the `movieId` column covers a wide range of movie identifiers, with values ranging from 1 to 193565 and an average of **27252.01**, reflecting the diversity of the movie catalog to which these tags were applied.

The standardization and transformation of the data make this dataset highly functional for qualitative and categorical analyses. It can be used to identify the most popular tags, analyze the relationship between movies and genres represented by the tags, or even explore user behavior patterns over time. This well-organized and information-rich structure paves the way for more in-depth investigations into categorization and preferences within the cinematic universe.
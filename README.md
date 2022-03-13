# Mapa da Água
Scripts e metodologia do projeto [Mapa da Água](https://mapadaagua.reporterbrasil.org.br/)

O Mapa da Água revela resultados de testes feitos na água tratada que detectaram substâncias químicas e radioativas que podem oferecer risco à saúde. Destacamos os casos em que o volume dessas substâncias estava acima da concentração máxima permitida, que é quando elas passam a oferecer risco, segundo parâmetros do Ministério da Saúde. Cada país define o seu limite de segurança para a concentração máxima permitida de cada substância na água.

É esse o controle que define a potabilidade da água. As amostras que contém substâncias fora deste padrão são consideradas impróprias para o consumo, da mesma forma como um alimento pode estar fora da validade ou fora dos padrões sanitários.

O Mapa destaca quais municípios tiveram ao menos um teste com substâncias acima do limite permitido no Brasil entre 2018 e 2020. Criamos um “alerta máximo” para os locais onde a mesma substância esteve acima da concentração máxima permitida ao menos uma vez em cada um dos 3 anos . A contaminação contínua é quando os riscos são maiores devido à presença de substâncias químicas e radioativas que podem gerar doenças crônicas, como câncer e problemas endócrinos.

Para chegar a esse retrato, fizemos a leitura dos dados de controle do Sistema de Informação de Vigilância da Qualidade da Água para Consumo Humano, o Sisagua, do Ministério da Saúde. Esse banco de dados reúne os testes feitos pelas instituições responsáveis pelo abastecimento.

A lei brasileira determina que os fornecedores são responsáveis por testar a água e por apresentar os resultados à autoridade de saúde local, o que na prática se dá por meio do registro desses dados no Sisagua. Como esse banco traz informações classificadas em termos técnicos, a reportagem consultou o Ministério da Saúde e especialistas para deixar os dados mais acessíveis ao público não especializado.

A ferramenta foi construída a partir de dados de 2018 a 2020 obtidos em novembro de 2021. Ela não abarca atualizações e retificações feitas desde então. [Baixe aqui](https://dados.gov.br/dataset/controle-semestral) a base atualizada. As informações do banco utilizado (os dados de controle do Sisagua) são enviadas pelas instituições responsáveis pelo abastecimento de cada região - que podem ser empresas, autarquias ou governos locais.

É importante entender que cada município tem diferentes estações onde a água é tratada. Assim, um resultado acima do limite não significa necessariamente que a água de todo o município tem problemas, mas sim os locais abastecidos por aquela estação. Em termos de alerta para a saúde da população, porém, um local com problema pode afetar pessoas de diferentes partes do mesmo município, já que elas circulam e estão sujeitas a consumir água em diferentes locais.

O mapa traz todos os resultados computados no Sisagua para agrotóxicos, substâncias orgânicas, inorgânicas, parâmetros radioativos e, o grupo que se revelou mais problemático: os subprodutos da desinfecção, que são substâncias indesejáveis geradas a partir do processo de tratamento da água.

São 65 substâncias no total.

Todas as substâncias destacadas pelo Mapa oferecem algum risco à saúde humana se estiverem acima da concentração máxima permitida

Este especial da Repórter Brasil é resultado de um esforço interdisciplinar de pesquisadores, jornalistas de dados, programadores e designers que contou ainda com a valiosa colaboração de especialistas com experiência no banco de dados do Sisagua e na vigilância da qualidade da água (leia mais em “equipe”).

O mapa é uma versão atualizada e revisada de um primeiro mapa [publicado em abril de 2019](https://portrasdoalimento.info/agrotoxico-na-agua/#), quando a Repórter Brasil trabalhou em colaboração com a ONG suíça Public Eye e com a Agência Pública. É o resultado de um processo de amadurecimento da versão de 2019, que foi a primeira experiência no Brasil de tradução dos dados do Sisagua para o público não especializado. Essa primeira experiência revelou o grande interesse público sobre a qualidade da água, assim como a demanda por mais transparência ativa na divulgação dos resultados destes testes.

### Como os dados foram trabalhados
Os arquivos do Sisagua estão em CSV e cada ano tem mais de um milhão de linhas – cada linha é um teste feito em algum munícipio do Brasil. No total, somando 2018, 2019 e 2020, são 5.126.181 linhas. Os dados originais estão [aqui](https://drive.google.com/drive/folders/1_s52ZWGvoXFz4CjRnRnFccMNVF8keEKc?usp=sharing), e foram baixados em 2 de novembro de 2021.

Foram analisadas todas essas linhas para criar as quatro novas colunas de avaliação, que indicam se o teste é Consistente ou Inconsistente e se está dentro ou acima do VMP (Valor Máximo Permitido) para uma substância danosa à saúde.

Esse grande tratamento de dados, que foi feito com a orientação e regras do Ministério da Saúde, não pode ser feito em programas normais de planilha, que têm uma limitação de linhas para processamento. Usamos então a linguagem de programação Python, rodando no Google Colab com aumento de memória RAM.

A metodologia geral do projeto e do site Mapa da Água está [aqui](https://mapadaagua.reporterbrasil.org.br/metodologia). E a metodologia específica do tratamento dos dados está neste Github, na pasta **metodologia** em um PDF. 

Por fim, os scripts em Python criados estão na pasta **scripts**, com essa divisão:

- 01_sisagua_novas_colunas.ipynb – cria as colunas de avaliação de cada ano nos testes originais do Sisagua e cria três arquivos

- 02_sisagua_criabancodedados.ipynb – une os três anos de testes na água dos três arquivos e faz a descrição dos testes em categorias de gravidade (tipo_cor). É esse arquivo final que abastece o Mapa da Água

### Equipe
COORDENAÇÃO: Ana Aranha e Piero Locatelli<br>
REPORTAGEM: Ana Aranha, Hélen Freitas e André Cabette<br>
EDIÇÃO: Ana Aranha, Ana Magalhães, Mariana Della Barba e Gisele Lobato<br>
PROCESSAMENTO DE DADOS: Reinaldo Chaves<br>
ANÁLISE DE DADOS: Marina Gama Cubas e Reinaldo Chaves<br>
CONSULTORIA: Tiago Magalhães (interpretação dos dados do Sisagua) e Fábio Kummrow (descrição das substâncias)<br>
CRIAÇÃO E PROJETO GRÁFICO: Fernanda Segabinassi e Alexandre Macedo Costa<br>
COMUNICAÇÃO ESTRATÉGICA: Gota no Oceano<br>
PROGRAMAÇÃO: Paulo Campos e André Mota (Studio Cubo Web)

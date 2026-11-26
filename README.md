<div align="center">

# 🎬 Streaming de Filmes — Projetos de Análise de Dados

**Desafio 1 · Google Sheets** · **Desafio 2 · Estatística com Python** · **Desafio 3 · Excel e Dashboard**

Três desafios de análise de dados com o mesmo tema: integração, estatística descritiva e visualização de indicadores de streaming de filmes.

[![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
[![Google Sheets](https://img.shields.io/badge/Google%20Sheets-API-34A853?logo=googlesheets&logoColor=white)](https://developers.google.com/workspace/sheets/api)
[![Pandas](https://img.shields.io/badge/Pandas-An%C3%A1lise-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Excel](https://img.shields.io/badge/Microsoft%20Excel-Dashboard-217346?logo=microsoftexcel&logoColor=white)](https://www.microsoft.com/pt-br/microsoft-365/excel)
[![Desafio 3 — Excel](https://img.shields.io/badge/Desafio%203-Baixar%20Excel-217346?logo=microsoftexcel&logoColor=white)](api/Desafio_03_Streaming_Filmes.xlsx)
[![Dados fictícios](https://img.shields.io/badge/Dados-fict%C3%ADcios-9B87C4)](#dados)
[![Abrir Desafio 1 no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/beatrisAS/Desafio1_API_Streaming_Filmes_Python/blob/main/api/Desafio1_API_Python.ipynb)
[![Abrir Desafio 2 no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/beatrisAS/Desafio1_API_Streaming_Filmes_Python/blob/main/api/Desafio2_Estatistica_Python.ipynb)

</div>

---

## Sobre o projeto

Este repositório reúne **três desafios de análise de dados sobre streaming de filmes**, desenvolvidos no bootcamp de Analista de Dados da Generation Brasil. Os projetos exploram etapas complementares da análise: geração e integração de dados, investigação estatística e comunicação de resultados por meio de um dashboard no Excel.

### Desafio 1 — Integração com Google Sheets

O notebook gera **10 registros fictícios de filmes**, grava-os em uma planilha e lê os valores novamente para conferir a escrita. O foco é praticar autenticação, organização de dados e validações básicas de uma carga.

### Desafio 2 — Estatística descritiva

O notebook do segundo desafio usa `filmes.csv` (dimensão) e `visualizacoes.csv` (fato) para investigar em qual dispositivo ocorre a maior proporção de visualizações não concluídas. Também compara essa proporção por gênero e analisa `tempo_assistido_min` com medidas de tendência central, dispersão, outliers, distribuição e gráficos.

### Desafio 3 — Relatório e dashboard no Excel

O terceiro desafio explora a construção de um relatório analítico no Excel Web, com fórmulas, tabelas dinâmicas, indicadores, gráficos e segmentação por dispositivo. O objetivo é compreender o volume de visualizações, comparar o tempo médio assistido com a duração média dos filmes e acompanhar a evolução mensal do consumo.

> **Importante:** os desafios compartilham o tema, mas possuem objetivos próprios. O Desafio 2 utiliza os CSV fornecidos no repositório oficial do desafio, não a base pequena de 10 filmes gerada no Desafio 1. Os dados são didáticos e não representam usuários reais.

## Desafio 3 · Dashboard de streaming no Excel

### Visão geral

O projeto utiliza 55.000 registros fictícios de visualização e uma dimensão com 10.300 filmes.

**Pergunta de negócio:** Qual dispositivo concentra mais visualizações e como o tempo médio assistido se compara à duração média dos filmes?

**Métrica principal:** `tempo_assistido_min`. **Grupo:** `dispositivo`. **Coluna complementar:** `duracao_dim`, obtida por meio do PROCX. **Decisão:** priorizar melhorias na experiência dos dispositivos mais utilizados e investigar a diferença entre tempo assistido e duração dos filmes.

<p align="center">
  <img src="assets/dashboard-streaming-excel.jpg"
       alt="Dashboard de Streaming de Filmes"
       width="750">
  <br>
  <sub><i>Figura 1 — Dashboard interativo de análise de streaming de filmes desenvolvido no Microsoft Excel.</i></sub>
</p>

### Indicadores principais

| Indicador | Resultado |
| --- | ---: |
| Total de visualizações | 55.000 |
| Total de minutos assistidos | 5.000.899 |
| Média de minutos por visualização | 90,9 min |
| Dispositivo com mais visualizações | Smart TV (aprox. 40%) |
| Maior média de tempo assistido | Tablet (92,1 min) |

### Relatório por dispositivo

| Dispositivo | Visualizações | Minutos assistidos | Média assistida (min) | Participação (aprox.) | Duração média dos filmes (min, aprox.) |
| --- | ---: | ---: | ---: | ---: | ---: |
| Smart TV | 21.994 | 1.998.273 | 90,9 | 40% | 131 |
| Celular | 16.503 | 1.501.129 | 91,0 | 30% | 130 |
| Computador | 8.188 | 738.649 | 90,2 | 15% | 130 |
| Tablet | 5.581 | 513.894 | 92,1 | 10% | 131 |
| Console | 2.734 | 248.954 | 91,1 | 5% | 130 |
| **Total** | **55.000** | **5.000.899** | **90,9** | **100%** | — |

As durações médias foram arredondadas conforme os rótulos do gráfico. A média geral da duração deve ser consultada na planilha, pois seu valor exato não está disponível na captura.

### Organização da planilha

| Aba | Finalidade |
| --- | --- |
| `Leitura` | Contexto e orientações do exercício. |
| `Relatorio` | Consolidação dos indicadores por dispositivo. |
| `Dinamica` | Agregações e tabelas dinâmicas para análise. |
| `Conferencia` | Área de conferência dos resultados. |
| `fato` | Registros de visualização, incluindo `duracao_dim` e `ano_mes`. |
| `dimensao` | Dados descritivos dos filmes. |
| `Dashboard` | Painel visual com indicadores, gráficos, segmentação e tabelas de apoio. |

### Cálculos e recursos do Excel

- **Quantidade:** contagem de `visualizacao_id`, em vez da soma dos identificadores.
- **Tempo total:** soma de `tempo_assistido_min`.
- **Média:** média do tempo assistido por registro; a média geral considera todos os registros, não uma média simples das médias dos dispositivos.
- **Participação percentual:** quantidade do dispositivo dividida pelo total geral. Na estrutura do relatório, a fórmula `=B3/$B$8` é aplicada na coluna de participação e formatada como porcentagem.
- **Evolução mensal:** soma do tempo assistido agrupada pelo campo `ano_mes`.

### Integração entre fato e dimensão com PROCX

A coluna `duracao_dim` traz a duração original do filme da tabela dimensão para cada registro da tabela fato, utilizando `filme_id` como chave de relacionamento. Isso permite comparar a duração dos filmes com o tempo efetivamente assistido por dispositivo.

```excel
=PROCX([@[filme_id]];tbl_dimensao[filme_id];tbl_dimensao[duracao_min];"Sem cadastro";0)
```

No relatório, a duração média por dispositivo é calculada com:

```excel
=SEERRO(MÉDIASE(tbl_fato[dispositivo];A3;tbl_fato[duracao_dim]);"-")
```

A conferência de registros sem correspondência utiliza:

```excel
=CONT.SE(tbl_fato[duracao_dim];"Sem cadastro")
```

O resultado esperado é zero. A média geral da duração considera todos os registros numéricos (`=MÉDIA(tbl_fato[duracao_dim])`), não a média simples das médias por dispositivo.

### Visualizações do dashboard

| Gráfico | Objetivo |
| --- | --- |
| Barras horizontais | Comparar a quantidade de visualizações por dispositivo. |
| Colunas agrupadas | Comparar o tempo médio assistido com a duração média dos filmes por dispositivo. |
| Pizza | Mostrar a participação percentual das visualizações por dispositivo. |
| Linha | Acompanhar a evolução mensal do tempo assistido, de janeiro de 2025 a julho de 2026. |

O painel reúne quatro tabelas dinâmicas e uma segmentação por dispositivo. A tabela dinâmica de médias utiliza `dispositivo` em Linhas e as médias de `tempo_assistido_min` e `duracao_dim` em Valores. A identidade visual combina grafite, vermelho, dourado e tons neutros, com ícones discretos e hierarquia de informações.

> A participação percentual foi calculada sobre a quantidade de visualizações. Por isso, o título do gráfico de pizza deve indicar **Participação percentual das visualizações**, e não do tempo assistido.

### Insights e recomendações

- Smart TV e celular concentram aproximadamente 70% das visualizações, sendo canais relevantes para priorizar investigações sobre a experiência de uso.
- O tablet possui a maior média de minutos assistidos, apesar de representar uma parcela menor das visualizações. A diferença entre as médias dos dispositivos é pequena e não comprova maior engajamento por si só.
- A série mensal apresenta oscilações no consumo; o gráfico permite investigar períodos de maior e menor volume, sem atribuir causas que não estejam demonstradas na base.
- A duração média dos filmes fica entre aproximadamente 130 e 131 minutos por dispositivo, enquanto o tempo médio assistido varia de 90,2 a 92,1 minutos. Em todos os dispositivos, o tempo médio assistido é inferior à duração média dos filmes.
- Maio de 2026 registrou o maior tempo assistido na série apresentada, com 274.610 minutos.
- Recomenda-se priorizar melhorias na Smart TV e no celular e investigar a diferença entre duração e tempo assistido, sem interpretar essa diferença isoladamente como prova de abandono.

Os resultados descrevem exclusivamente uma base didática, não uma plataforma comercial real.

### Como consultar o projeto

- [Acessar a planilha completa do Desafio 3 (Excel)](api/Desafio_03_Streaming_Filmes.xlsx)
- [Visualizar o dashboard desenvolvido no Excel](assets/dashboard-streaming-excel.jpg)
- [Consultar o repositório oficial do Desafio 03](https://github.com/rafaelq80/desafios_tecnicos_ad/tree/03_Desafio_03/desafio_03)

Abra a planilha `.xlsx` no Excel ou Excel Web para consultar as abas, fórmulas, tabelas dinâmicas, gráficos e segmentações. A imagem apresenta uma prévia do dashboard.

## O que você vai praticar

- Autenticar uma aplicação com uma conta de serviço e acessar o Google Sheets pelo ID.
- Gerar registros fictícios, organizar colunas e validar uma carga de dados.
- Reconhecer tabelas dimensão e fato e conferir chaves primárias e estrangeiras.
- Carregar CSV no pandas e verificar tipos, ausências e duplicatas.
- Comparar visualizações não concluídas por dispositivo e gênero.
- Interpretar média, mediana, desvio padrão, outliers e distribuição do tempo assistido.
- Consolidar indicadores no Excel, calcular participações percentuais e construir tabelas dinâmicas.
- Relacionar tabelas fato e dimensão com PROCX e tratar erros de cálculo com SEERRO.
- Comunicar resultados com gráficos, segmentação e um dashboard analítico.

## Tecnologias

| Tecnologia | Uso |
| --- | --- |
| Microsoft Excel / Excel Web | Relatórios, PROCX, SEERRO, tabelas dinâmicas, segmentação e dashboard do Desafio 3. |
| Python 3 | Geração, organização e conferência dos dados. |
| Google Colab | Execução do notebook e armazenamento do segredo usado na autenticação. |
| Google Cloud | Configuração do projeto, APIs e conta de serviço. |
| Google Sheets API | Acesso e escrita na planilha. |
| Google Drive API | API incluída na preparação indicada pelo notebook do Desafio 1. |
| `pandas` | Carrega e analisa os CSV do Desafio 2. |
| Seaborn e Matplotlib | Criam os gráficos do Desafio 2. |
| `gspread` | Integração de Python com Google Sheets. |
| `Faker` | Geração de nomes fictícios para a direção. |
| `random` | Seleção de categorias e geração de números. |
| `json` | Leitura do conteúdo JSON da credencial no Colab. |

## Estrutura do repositório

```text
Desafio1_API_Streaming_Filmes_Python/
├── README.md
├── assets/
│   └── dashboard-streaming-excel.jpg
└── api/
    ├── Desafio1_API_Python.ipynb
    ├── Desafio2_Estatistica_Python.ipynb
    ├── Desafio_01_Streaming_Filmes.xlsx
    └── Desafio_03_Streaming_Filmes.xlsx
```

| Arquivo | Descrição |
| --- | --- |
| [`Desafio1_API_Python.ipynb`](api/Desafio1_API_Python.ipynb) | **Desafio 1:** preparação, autenticação, geração e conferência de registros na planilha. |
| [`Desafio2_Estatistica_Python.ipynb`](api/Desafio2_Estatistica_Python.ipynb) | **Desafio 2:** conferência dos CSV, análise da taxa de visualizações não concluídas e estatística descritiva do tempo assistido. |
| [`Desafio_01_Streaming_Filmes.xlsx`](api/Desafio_01_Streaming_Filmes.xlsx) | Exemplo em Excel com a aba `filmes`, o cabeçalho e 10 registros fictícios do Desafio 1. |
| [`Desafio_03_Streaming_Filmes.xlsx`](api/Desafio_03_Streaming_Filmes.xlsx) | **Desafio 3:** planilha Excel com relatório, fórmulas, tabelas dinâmicas, gráficos e dashboard interativo. |
| [`dashboard-streaming-excel.jpg`](assets/dashboard-streaming-excel.jpg) | Prévia visual do dashboard do Desafio 3. |
| `README.md` | Documentação dos três desafios. |

> O Desafio 3 é disponibilizado em formato `.xlsx`, acompanhado de uma imagem de prévia do dashboard.

> O Excel é uma cópia local de exemplo do Desafio 1. O notebook trabalha com uma planilha online do Google Sheets e não atualiza esse arquivo automaticamente.

## Desafio 2 · Análise estatística das visualizações

A análise estatística trabalha com duas tabelas relacionadas por `filme_id`:

| Tabela | Tipo | Conteúdo |
| --- | --- | --- |
| `filmes.csv` | Dimensão | Cadastro e características dos filmes, como gênero, ano e duração. |
| `visualizacoes.csv` | Fato | Registros de visualização, incluindo dispositivo, conclusão e tempo assistido. |

O notebook verifica tipos, campos ausentes, duplicatas e a integridade da chave estrangeira antes de analisar os dados.

**Pergunta de negócio:** Em qual dispositivo há maior proporção de visualizações não concluídas?

`concluido=False` é tratado como indicador de visualização não concluída; isso não confirma que a pessoa tenha abandonado definitivamente o filme. O notebook também compara taxas por gênero e descreve o tempo assistido.

**Resultado nesta base didática:** computador tem a maior taxa de visualizações não concluídas (**83,50%**, 6.837 de 8.188). Por gênero, animação apresenta 84,28% e ação 82,30%. Os números descrevem apenas a base fornecida para o exercício.

## Fluxo do Desafio 1 · integração com Google Sheets

```text
Credencial da conta de serviço no Colab
                  ↓
        Autenticação com gspread
                  ↓
   Abertura da planilha pelo ID
                  ↓
  Seleção e renomeação da primeira aba
                  ↓
   Escrita do cabeçalho com 7 colunas
                  ↓
      Geração de 10 registros fictícios
                  ↓
        Envio das linhas à planilha
                  ↓
       Leitura e conferência dos dados
```

1. **Preparação e autenticação:** o notebook instala `gspread` e `faker`, lê o segredo `GCP_SA_JSON` no Colab e usa o JSON para autenticar a conta de serviço.
2. **Acesso à planilha:** abre a planilha com `gc.open_by_key(SHEET_ID)`, seleciona a primeira aba (`sh.sheet1`) e tenta renomeá-la para `filmes`.
3. **Escrita do esquema:** escreve os nomes das sete colunas a partir de `A1` e compara o cabeçalho com a lista `COLUNAS`.
4. **Geração e envio:** `gerar_linha(i)` cria cada registro. O notebook organiza os valores na ordem do cabeçalho e envia as linhas com `append_rows`, usando `value_input_option="RAW"`.
5. **Leitura e conferência:** usa `get_all_values()` e verifica se a aba tem 11 linhas (cabeçalho mais 10 registros) e se o cabeçalho corresponde ao esquema esperado.

> A verificação de 11 linhas pressupõe que a aba esteja vazia antes da primeira execução. Ela não valida individualmente todos os campos nem confirma uma relação com uma tabela de fatos.

## Esquema dos dados

A aba `filmes` representa uma **tabela dimensão**: cada registro descreve um filme fictício.

| Coluna | Descrição | Exemplo | Regra de geração |
| --- | --- | --- | --- |
| `filme_id` | Identificador do registro. | `1` | Inteiro de 1 a 10 em cada execução. |
| `titulo` | Título fictício. | `Distante Vale 01` | Combinação de um adjetivo, um substantivo e o número do registro. |
| `genero` | Gênero atribuído ao filme. | `documentário` | Selecionado da lista `GENEROS`. |
| `ano_lancamento` | Ano de lançamento fictício. | `2000` | Inteiro entre 1985 e 2024, inclusive. |
| `duracao_min` | Duração fictícia, em minutos. | `103` | Inteiro entre 75 e 184, inclusive. |
| `classificacao_indicativa` | Classificação atribuída ao registro. | `10` | Um dos valores `L`, `10`, `12`, `14`, `16` ou `18`. |
| `diretor_ficticio` | Nome fictício da pessoa responsável pela direção. | `Brenda Alves` | Gerado com `Faker("pt_BR").name()`. |

Gêneros disponíveis: `ação`, `comédia`, `drama`, `terror`, `documentário`, `animação`, `ficção científica` e `romance`.

## Dados

- Os registros são sintéticos e não representam um catálogo real nem pessoas reais associadas às obras.
- Os nomes são gerados pelo Faker em português do Brasil; semelhanças com pessoas reais são coincidência.
- `Faker.seed(42)` e `random.seed(42)` favorecem a reprodutibilidade. Versões diferentes das bibliotecas ou do ambiente podem alterar os resultados.
- Os IDs de 1 a 10 recomeçam em cada execução e não são automaticamente únicos entre execuções.
- O arquivo Excel do Desafio 1 é apenas uma amostra de uma execução; não está sincronizado com a planilha online. A planilha do Desafio 3 reúne o relatório e o dashboard.

## Como executar

Os dois notebooks têm requisitos diferentes; o Desafio 3 utiliza o Excel. O **Desafio 1** exige configurar uma conta de serviço e uma planilha. O **Desafio 2** roda no Colab usando os CSV baixados do repositório oficial do desafio.

### Desafio 3 — Consulta dos dados no Excel

1. Baixe o arquivo [Desafio_03_Streaming_Filmes.xlsx](api/Desafio_03_Streaming_Filmes.xlsx).
2. Abra a planilha no Excel ou Excel Web e consulte as abas `Relatorio`, `Dinamica`, `Conferencia` e `Dashboard`.
3. Consulte a [imagem do dashboard](assets/dashboard-streaming-excel.jpg) para visualizar o resultado do projeto.

> Utilize o arquivo `.xlsx` para explorar os gráficos e as segmentações do painel.

### Desafio 2 — Análise estatística no Colab

1. Baixe `filmes.csv` e `visualizacoes.csv` da pasta **Streaming de filmes** no repositório oficial do desafio.
2. Abra o notebook [`Desafio2_Estatistica_Python.ipynb`](api/Desafio2_Estatistica_Python.ipynb) no Colab.
3. Envie os dois arquivos CSV quando a célula de carga solicitar, ou coloque-os na pasta do Drive esperada pelo notebook.
4. Execute as células em ordem e confira as tabelas, comparações e gráficos.

> O Desafio 2 não usa os 10 registros criados no Desafio 1: use os CSV oficiais indicados no guia do desafio.

### Desafio 1 — Google Sheets

#### Pré-requisitos

Você precisa de:

1. Uma conta Google com acesso ao Google Colab, Google Cloud e Google Sheets.
2. Um projeto do Google Cloud com permissão para configurar APIs e uma conta de serviço.
3. Uma planilha Google que possa ser compartilhada com a conta de serviço.
4. A credencial JSON da conta de serviço, armazenada com segurança em **Secrets** no Colab.

> O notebook usa `google.colab.userdata` e foi preparado para o Google Colab. Para executá-lo localmente, a autenticação precisa ser adaptada.

#### 1. Abra o notebook

Acesse [Abrir no Google Colab](https://colab.research.google.com/github/beatrisAS/Desafio1_API_Streaming_Filmes_Python/blob/main/api/Desafio1_API_Python.ipynb). Para editar sua própria versão, faça uma cópia no Colab e conecte um ambiente de execução.

#### 2. Configure o Google Cloud

No [Google Cloud Console](https://console.cloud.google.com/):

1. Crie ou selecione um projeto.
2. Ative a **Google Sheets API** e a **Google Drive API**, conforme a preparação do notebook.
3. Crie uma conta de serviço e gere uma chave JSON, se permitido pelas políticas da sua organização.
4. Guarde a credencial com segurança: ela contém informações sensíveis.

> Algumas organizações restringem a criação de chaves de conta de serviço. Siga as políticas aplicáveis e use um método de autenticação autorizado.

#### 3. Prepare uma planilha de teste

1. Crie uma planilha no [Google Sheets](https://sheets.google.com/). O nome sugerido é `Desafio_01_Streaming_Filmes`.
2. Use uma planilha de teste cuja primeira aba esteja vazia; o notebook tenta renomeá-la para `filmes`.
3. Compartilhe a planilha com o endereço `client_email` da conta de serviço, com permissão de **Editor**.
4. Copie o ID da planilha, localizado entre `/d/` e `/edit` no endereço:

```text
https://docs.google.com/spreadsheets/d/SEU_ID_AQUI/edit
```

> O nome da planilha é apenas organizacional; o notebook abre a planilha pelo ID. O ID que já está no notebook é o do exemplo: substitua-o pelo da sua planilha de teste.

#### 4. Cadastre o segredo no Colab

1. Abra **Secrets** pela chave na barra lateral do Colab.
2. Crie um segredo chamado exatamente `GCP_SA_JSON`.
3. Cole nele o conteúdo completo do arquivo JSON da conta de serviço.
4. Permita que o notebook acesse o segredo e autorize o acesso quando solicitado.

🔐 **Nunca cole a credencial JSON em uma célula, no README, em comentários, no histórico do Git ou em um repositório.** Trate-a como uma senha.

#### 5. Configure o ID da planilha

Na célula **“Célula 3 — abrir a planilha”**, substitua `SHEET_ID` pelo ID da sua própria planilha:

```python
SHEET_ID = "SEU_ID_AQUI"
NOME_TABELA = "filmes"
```

Revise as permissões da planilha antes de compartilhar: o ID não é uma senha, mas não torna privado o conteúdo de uma planilha pública.

#### 6. Execute as células na ordem

| Etapa | Ação |
| --- | --- |
| Célula 1 | Instala `gspread` e `faker`. |
| Célula 2 | Lê o segredo e autentica a conta de serviço. |
| Célula 3 | Abre a planilha e renomeia a primeira aba. |
| Célula 4 | Escreve e confere o cabeçalho. |
| Célula 5 | Gera e acrescenta 10 filmes fictícios. |
| Célula 6 | Lê a aba e executa as verificações finais. |

Na primeira execução, o Colab pode pedir autorização para acessar o segredo. Se solicitado, execute novamente a célula de autenticação.

## Resultado esperado

Se a primeira aba estava vazia e as células foram executadas uma única vez, o resultado esperado é:

- Uma aba chamada `filmes`.
- Uma linha de cabeçalho com os sete nomes de coluna, na ordem definida.
- Dez linhas de dados fictícios.
- Uma saída semelhante a:

```text
10 linhas enviadas
Linhas (cabeçalho + dados): 11
Cabeçalho confere: True
```

O notebook também exibe uma amostra. Os valores retornados por `get_all_values()` aparecem como texto, inclusive os campos numéricos.

### Exemplo de saída

| filme_id | titulo | genero | ano_lancamento | duracao_min | classificacao_indicativa | diretor_ficticio |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Distante Vale 01 | documentário | 2000 | 103 | 10 | Brenda Alves |
| 2 | Distante Cidade 02 | comédia | 2022 | 129 | L | Sra. Isabelly Câmara |
| 3 | Sombra Destino 03 | terror | 1999 | 139 | 16 | Cauã Rocha |

## Cuidados importantes

### Executar novamente pode duplicar registros

A função `append_rows` acrescenta linhas; ela não substitui os dados existentes. Como os IDs recomeçam em 1, uma nova execução pode gerar IDs repetidos. A validação de 11 linhas também pode falhar se a aba já tiver dados.

Para testar novamente, use uma planilha ou aba de teste vazia. Antes de limpar, renomear ou sobrescrever qualquer dado, faça uma cópia e confirme que pode alterá-lo.

### O notebook usa a primeira aba

O notebook seleciona `sh.sheet1`, não procura uma aba existente pelo nome. Assim, tentará renomear a primeira aba para `filmes`; se já existir outra aba com esse nome, pode ocorrer conflito. A escrita do cabeçalho a partir de `A1` também pode substituir valores nas células correspondentes.

### Proteja credenciais e dados

- Nunca publique a chave JSON ou o valor de `GCP_SA_JSON`.
- Revise as células, saídas e links antes de compartilhar o notebook.
- Saídas salvas podem exibir o e-mail da conta de serviço e o endereço da planilha: confira se são adequados para publicação.
- Se uma chave for exposta, revogue-a ou exclua-a no Google Cloud e siga as orientações de segurança aplicáveis.
- Use dados fictícios para testes e respeite as regras de acesso da sua organização.

## Solução de problemas

| Problema | O que conferir |
| --- | --- |
| O segredo `GCP_SA_JSON` não é encontrado | Nome exato no painel Secrets e acesso do notebook habilitado. |
| Erro ao interpretar o JSON | Se o segredo contém o arquivo completo e válido; não compartilhe seu conteúdo. |
| Erro de permissão na planilha | Se ela foi compartilhada com o `client_email` correto e com permissão de Editor. |
| Planilha não encontrada | ID, conta usada na autenticação e permissões de compartilhamento. |
| API desativada | Se as APIs indicadas estão ativas no projeto certo do Google Cloud. |
| Erro ao renomear a aba | Se já existe uma aba `filmes` e qual é a primeira aba da planilha. |
| A verificação de 11 linhas falha | Se a aba já tinha dados ou se o envio foi executado mais de uma vez. |
| Falha fora do Colab | `google.colab.userdata` depende do Colab; adapte a autenticação para execução local. |

## Melhorias futuras

As ideias abaixo não estão implementadas no notebook atual:

- Validar tipos, limites de ano e duração, categorias permitidas e campos vazios.
- Evitar duplicações em reexecuções com uma estratégia explícita de identificadores e atualização.
- Permitir configurar a quantidade de registros e os parâmetros da geração.
- Selecionar a aba pelo nome e tratar sua criação ou conflitos.
- Separar geração, autenticação, escrita e validação em funções menores e incluir testes.
- Fixar versões das dependências para aumentar a reprodutibilidade.
- Se solicitado, criar uma tabela relacionada e validar as chaves entre as tabelas.
- Preparar uma alternativa de autenticação local que não exponha credenciais.

## Referências

- [Desafio 03 — repositório oficial](https://github.com/rafaelq80/desafios_tecnicos_ad/tree/03_Desafio_03/desafio_03)
- [Documentação do Python em português](https://docs.python.org/pt-br/3/)
- [Primeiros passos com o Google Colab](https://colab.research.google.com/)
- [Google Sheets API](https://developers.google.com/workspace/sheets/api)
- [Documentação do gspread](https://docs.gspread.org/)
- [Documentação do Faker](https://faker.readthedocs.io/)

## 👩‍💻 Autoria

**Beatris Antunes Silva**

---

<div align="center">

  Projeto de estudo desenvolvido no contexto do bootcamp de Analista de Dados da Generation Brasil.

</div>

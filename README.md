<div align="center">

# 🎬 Streaming de Filmes — Python e Google Sheets

**Geração de dados fictícios e integração com a Google Sheets API**

Uma prática de análise de dados que conecta Python a uma planilha, cria registros de filmes e confere a escrita e a leitura dos dados.

[![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
[![Google Sheets](https://img.shields.io/badge/Google%20Sheets-API-34A853?logo=googlesheets&logoColor=white)](https://developers.google.com/workspace/sheets/api)
[![Dados fictícios](https://img.shields.io/badge/Dados-fict%C3%ADcios-9B87C4)](#-sobre-os-dados)
[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/beatrisAS/Desafio1_API_Streaming_Filmes_Python/blob/main/api/Desafio1_API_Python.ipynb)

</div>

---

## 📌 Visão geral

Este repositório apresenta uma prática de integração entre **Python e Google Sheets** no contexto de um catálogo fictício de streaming de filmes. A partir de um notebook no Google Colab, são gerados **10 registros de teste**, que depois são gravados e lidos novamente em uma planilha.

O objetivo é exercitar um fluxo comum na área de dados: preparar um ambiente, autenticar uma aplicação, organizar informações em um esquema definido, enviar os registros a uma fonte externa e conferir o resultado.

> **Escopo atual:** o projeto usa a Google Sheets API para manipular dados. Ele **não implementa uma API própria de streaming**, não reproduz vídeos e não coleta dados de um serviço real de filmes. O notebook corresponde à etapa de teste com 10 registros; a carga completa não está implementada nesta versão.

---

## 🎯 Objetivos de aprendizagem

- Compreender o uso de uma **conta de serviço** para autenticar uma aplicação no Google Cloud.
- Acessar uma planilha do Google Sheets pelo **ID** usando Python e a biblioteca `gspread`.
- Criar dados fictícios com `Faker` e com o módulo `random`.
- Organizar os registros de acordo com um esquema de colunas pré-definido.
- Escrever os dados em uma aba e ler os valores novamente para conferência.
- Praticar cuidados com credenciais e validações básicas de uma carga de dados.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Papel no projeto |
| --- | --- |
| **Python 3** | Linguagem usada para gerar, organizar e conferir os dados. |
| **Google Colab** | Ambiente de execução do notebook e armazenamento do segredo utilizado no exemplo. |
| **Google Cloud** | Plataforma usada para criar a conta de serviço e ativar as APIs. |
| **Google Sheets API** | Permite acessar e modificar os dados da planilha. |
| **Google Drive API** | Faz parte da preparação indicada no notebook. |
| **gspread** | Biblioteca Python que facilita a interação com o Google Sheets. |
| **Faker** | Gera nomes fictícios para a coluna de direção. |
| **random** | Seleciona valores e gera números para os registros de teste. |
| **json** | Converte o conteúdo da credencial armazenada no Colab em um dicionário Python. |

---

## 📁 Estrutura do repositório

```text
Desafio1_API_Streaming_Filmes_Python/
│
├── README.md
│
└── api/
    ├── Desafio1_API_Python.ipynb
    └── Desafio_01_Streaming_Filmes.xlsx
```

| Arquivo | Conteúdo |
| --- | --- |
| [`Desafio1_API_Python.ipynb`](api/Desafio1_API_Python.ipynb) | Notebook com preparação, autenticação, geração, escrita e conferência dos dados. |
| [`Desafio_01_Streaming_Filmes.xlsx`](api/Desafio_01_Streaming_Filmes.xlsx) | Cópia em Excel de uma saída de exemplo, com a aba `filmes`, um cabeçalho e 10 registros fictícios. |
| `README.md` | Documentação do projeto. |

> O arquivo `.xlsx` é uma **cópia local de exemplo**. O notebook opera sobre uma planilha do **Google Sheets**; não atualiza automaticamente o arquivo Excel do repositório.

---

## 🔄 Como funciona

```text
Conta de serviço + segredo no Colab
                │
                ▼
     Autenticação com gspread
                │
                ▼
     Abertura da planilha pelo ID
                │
                ▼
   Primeira aba renomeada para filmes
                │
                ▼
  Escrita do cabeçalho de sete colunas
                │
                ▼
 Geração de 10 registros fictícios
                │
                ▼
   Inclusão das linhas no Google Sheets
                │
                ▼
    Leitura e conferência dos dados
```

### 1. Preparação e autenticação

O notebook instala `gspread` e `faker`, importa as bibliotecas e acessa o segredo `GCP_SA_JSON` no Colab. O conteúdo é interpretado como JSON e utilizado para autenticar a conta de serviço.

### 2. Acesso à planilha

A planilha é aberta com `gc.open_by_key(SHEET_ID)`. O código seleciona **a primeira aba** (`sh.sheet1`) e tenta renomeá-la para `filmes`.

### 3. Escrita do esquema

Os nomes das sete colunas são escritos a partir da célula `A1`. Em seguida, o notebook compara a primeira linha com a lista `COLUNAS`.

### 4. Geração e envio

A função `gerar_linha(i)` cria um dicionário para cada filme. As linhas são colocadas na ordem definida pelo cabeçalho e enviadas com `append_rows`, usando `value_input_option="RAW"`.

### 5. Leitura e conferência

O notebook usa `get_all_values()` para ler a aba e verifica, com `assert`, se há **11 linhas** no total e se o cabeçalho corresponde ao esquema esperado.

> A conferência pressupõe que a aba esteja vazia antes da primeira execução. Ter 11 linhas não comprova, por si só, a validade individual de cada campo ou a existência de uma tabela de fatos relacionada.

---

## 🗂️ Dicionário de dados

A aba utilizada pelo notebook representa a tabela dimensão **`filmes`**. Cada linha gerada corresponde a um filme fictício.

| Coluna | Descrição | Exemplo | Regra usada na geração |
| --- | --- | --- | --- |
| `filme_id` | Identificador do registro. | `1` | Números inteiros de 1 a 10 em cada execução. |
| `titulo` | Título fictício do filme. | `Distante Vale 01` | Combinação de uma palavra da lista `ADJETIVOS`, uma da lista `SUBSTANTIVOS` e o número do registro. |
| `genero` | Gênero atribuído ao filme. | `documentário` | Selecionado da lista `GENEROS`. |
| `ano_lancamento` | Ano de lançamento fictício. | `2000` | Inteiro entre **1985 e 2024**, incluindo os limites. |
| `duracao_min` | Duração fictícia em minutos. | `103` | Inteiro entre **75 e 184**, incluindo os limites. |
| `classificacao_indicativa` | Classificação atribuída ao registro. | `10` | Selecionada entre `L`, `10`, `12`, `14`, `16` e `18`. |
| `diretor_ficticio` | Nome fictício da pessoa responsável pela direção. | `Brenda Alves` | Gerado com `Faker("pt_BR").name()`. |

Os gêneros definidos no notebook são: `ação`, `comédia`, `drama`, `terror`, `documentário`, `animação`, `ficção científica` e `romance`.

---

## 🎲 Sobre os dados

- Os registros são **sintéticos**: não representam um catálogo real de filmes nem pessoas reais associadas às obras.
- Os nomes são produzidos pela biblioteca Faker em português do Brasil. Eventual semelhança com nomes reais é coincidência.
- As sementes `Faker.seed(42)` e `random.seed(42)` são usadas para favorecer a **reprodutibilidade**. Diferenças de versão das bibliotecas e do ambiente podem alterar os resultados.
- A geração inclui identificadores de 1 a 10 em **cada execução**. Eles não são automaticamente únicos entre execuções.
- O arquivo Excel do repositório mostra uma saída de exemplo; não é uma tabela dinâmica vinculada à planilha online.

---

## 🚀 Como executar

### Pré-requisitos

Você precisará de:

1. Uma conta Google com acesso ao **Google Colab**, ao **Google Cloud** e ao **Google Sheets**.
2. Um projeto no Google Cloud no qual você tenha permissão para configurar as APIs e uma conta de serviço.
3. Uma planilha Google que você possa compartilhar com essa conta de serviço.
4. A credencial JSON da conta de serviço, armazenada com segurança no recurso **Secrets** do Colab.

> O notebook foi preparado para o **Google Colab**, pois usa `google.colab.userdata`. Em um ambiente local, a autenticação precisa ser adaptada; simplesmente executar o notebook como está fora do Colab pode falhar.

### Passo 1 — Abra o notebook

Clique em **[Abrir no Google Colab](https://colab.research.google.com/github/beatrisAS/Desafio1_API_Streaming_Filmes_Python/blob/main/api/Desafio1_API_Python.ipynb)**.

Para editar sua própria versão, faça uma cópia do notebook no Colab. Quando solicitado, conecte um ambiente de execução.

### Passo 2 — Configure o Google Cloud

No [Google Cloud Console](https://console.cloud.google.com/):

1. Crie ou selecione um projeto.
2. Ative a **Google Sheets API** e a **Google Drive API**, conforme a preparação do notebook.
3. Crie uma conta de serviço e gere uma chave em formato JSON, se sua organização permitir esse tipo de chave.
4. Guarde a credencial com segurança. O JSON contém informações sensíveis de autenticação.

> Contas organizacionais podem restringir a criação de chaves de serviço. Nesse caso, siga as políticas da organização e use um método de autenticação permitido.

### Passo 3 — Prepare a planilha

1. Crie uma planilha no [Google Sheets](https://sheets.google.com/). O nome sugerido no notebook é `Desafio_01_Streaming_Filmes`.
2. Use uma **planilha de teste**, com a primeira aba vazia. O código vai renomear essa primeira aba para `filmes`.
3. Compartilhe a planilha com o endereço `client_email` da conta de serviço, concedendo acesso de **Editor** para permitir a escrita.
4. Copie o ID da planilha no endereço entre `/d/` e `/edit`:

```text
https://docs.google.com/spreadsheets/d/SEU_ID_AQUI/edit
```

> O nome da planilha ajuda na organização, mas a abertura é feita pelo **ID**. O ID já preenchido no notebook aponta para a planilha usada no exemplo: substitua-o pelo ID da sua própria planilha de teste.

### Passo 4 — Cadastre o segredo no Colab

1. No Colab, abra **Secrets** pelo ícone de chave na barra lateral.
2. Crie um segredo chamado exatamente `GCP_SA_JSON`.
3. Cole **o conteúdo completo** do arquivo JSON da conta de serviço no campo do segredo.
4. Habilite o acesso do notebook ao segredo e autorize a solicitação quando o Colab pedir.

🔐 **Não cole o JSON em uma célula de código, no README, em comentários, no histórico do Git ou em um repositório.** Trate a chave como uma senha.

### Passo 5 — Informe o ID da sua planilha

Na célula **“Célula 3 — abrir a planilha”**, substitua o valor de `SHEET_ID`:

```python
SHEET_ID = "SEU_ID_AQUI"
NOME_TABELA = "filmes"
```

O ID de uma planilha não é, sozinho, uma senha, mas não torna seguro divulgar conteúdo privado: revise sempre as permissões de compartilhamento.

### Passo 6 — Execute as células em ordem

| Etapa no notebook | O que acontece |
| --- | --- |
| **Célula 1** | Instala `gspread` e `faker`. |
| **Célula 2** | Lê o segredo e autentica a conta de serviço. |
| **Célula 3** | Abre a planilha pelo ID e renomeia a primeira aba. |
| **Célula 4** | Escreve e confere o cabeçalho. |
| **Célula 5** | Gera e acrescenta 10 filmes fictícios. |
| **Célula 6** | Lê a aba e executa as verificações finais. |

Na primeira execução, o Colab pode solicitar acesso ao segredo. O próprio notebook orienta executar novamente a célula de autenticação se necessário.

---

## ✅ Conferência do resultado

Se você começou com uma primeira aba vazia e executou as células uma única vez, o resultado esperado é:

- Uma aba chamada **`filmes`**.
- **1 linha de cabeçalho** com os sete nomes de coluna, na ordem definida.
- **10 linhas de dados fictícios** abaixo do cabeçalho.
- Mensagens como estas ao final da execução:

```text
10 linhas enviadas
Linhas (cabeçalho + dados): 11
Cabeçalho confere: True
```

O notebook também mostra uma amostra das primeiras linhas. Os valores lidos por `get_all_values()` aparecem como texto na saída exibida, inclusive para campos numéricos.

### Amostra de uma execução registrada

| filme_id | titulo | genero | ano_lancamento | duracao_min | classificacao_indicativa | diretor_ficticio |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Distante Vale 01 | documentário | 2000 | 103 | 10 | Brenda Alves |
| 2 | Distante Cidade 02 | comédia | 2022 | 129 | L | Sra. Isabelly Câmara |
| 3 | Sombra Destino 03 | terror | 1999 | 139 | 16 | Cauã Rocha |

---

## ⚠️ Cuidados importantes

### Reexecução pode duplicar os dados

A célula de geração usa **`append_rows`**, portanto acrescenta novos registros em vez de substituir os anteriores. Como os identificadores recomeçam em 1, executar essa célula novamente pode criar **IDs repetidos**. Em uma aba que já contenha dados, a verificação de 11 linhas pode falhar.

Para testar novamente, use uma **nova planilha ou uma aba de teste vazia** e confira qual é a primeira aba antes de executar. Não limpe, renomeie ou sobrescreva dados importantes sem uma cópia e autorização.

### A primeira aba será renomeada

O notebook usa `sh.sheet1`, não uma busca pela aba chamada `filmes`. Assim, a primeira aba será selecionada e renomeada. Se já existir outra aba chamada `filmes`, a operação pode falhar por conflito de nome. A escrita do cabeçalho a partir de `A1` também pode **substituir valores existentes nas células correspondentes**.

### Proteja credenciais e dados

- Nunca publique a chave JSON ou valores do segredo `GCP_SA_JSON`.
- Antes de compartilhar o notebook, revise as células, as saídas e os links exibidos.
- A saída salva no notebook pode mostrar o endereço da conta de serviço e a URL da planilha usada no exemplo; confira se essas informações e as permissões de acesso são adequadas para publicação.
- Se uma chave for exposta, revogue-a ou exclua-a no Google Cloud e siga as políticas de segurança aplicáveis.
- Use dados fictícios para testes e respeite as regras de acesso da organização.

---

## 🧩 Solução de problemas

| Situação | O que verificar |
| --- | --- |
| O segredo `GCP_SA_JSON` não é encontrado | Confira o nome exato no painel Secrets e se o acesso do notebook foi habilitado. |
| Erro ao interpretar o JSON | Verifique se o segredo contém o conteúdo completo e válido do arquivo JSON, sem compartilhá-lo. |
| Erro de permissão ao abrir ou editar a planilha | Confira se a planilha foi compartilhada com o `client_email` correto e se a conta possui acesso de Editor. |
| Planilha não encontrada | Revise o valor de `SHEET_ID`, a conta usada na autenticação e o compartilhamento. |
| Falha relacionada a API desativada | Confira se as APIs indicadas estão ativas no projeto do Google Cloud correspondente. |
| Erro ao renomear a aba | Verifique se já existe uma aba chamada `filmes` e qual é a primeira aba da planilha. |
| A verificação de 11 linhas falha | Veja se a aba já tinha dados ou se a célula que acrescenta os registros foi executada mais de uma vez. |
| O notebook falha fora do Colab | `google.colab.userdata` depende do ambiente Colab; a autenticação precisa ser adaptada para execução local. |

---

## 💡 Possíveis melhorias

As ideias abaixo são **sugestões futuras**, não funcionalidades implementadas no notebook atual:

- Adicionar verificações por coluna: tipos, limites de ano e duração, valores permitidos e campos vazios.
- Evitar duplicação ao reexecutar a carga, por exemplo com uma estratégia explícita de identificadores e atualização.
- Tornar configuráveis a quantidade de registros e os parâmetros de geração.
- Selecionar a aba pelo nome de forma explícita e tratar sua criação ou conflito de nomes.
- Separar geração, autenticação, escrita e validação em funções menores e incluir testes automatizados.
- Fixar versões das dependências para aumentar a reprodutibilidade.
- Desenvolver, se o desafio solicitar, uma segunda tabela relacionada e a carga completa, validando as chaves entre as tabelas.
- Incluir uma alternativa de autenticação para execução local, sem salvar credenciais no repositório.

---

## 📚 Referências

- [Documentação do Python em português](https://docs.python.org/pt-br/3/)
- [Primeiros passos com o Google Colab](https://colab.research.google.com/)
- [Documentação da Google Sheets API](https://developers.google.com/workspace/sheets/api)
- [Documentação do gspread](https://docs.gspread.org/)
- [Documentação do Faker](https://faker.readthedocs.io/)
- [Contas de serviço no Google Cloud](https://cloud.google.com/iam/docs/service-account-overview?hl=pt-br)

---

## 👩‍💻 Autoria

**Beatris Antunes Silva** 
---

<div align="center">
  Projeto de estudo desenvolvido no contexto de um bootcamp de Análise de Dados. 
</div>


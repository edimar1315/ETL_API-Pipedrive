
```markdown
# 🚀 Pipedrive API Data Extraction and Transformation

![Python](https://img.shields.io/badge/Python-3.6%2B-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-1.x-orange.svg) ![Requests](https://img.shields.io/badge/requests-2.x-green.svg)

Este projeto realiza a extração, desaninhamento e transformação de dados da API do Pipedrive, incluindo a formatação e limpeza de dados sobre negócios e organizações. Utilizamos bibliotecas como `requests`, `pandas`, `numpy` e `matplotlib` para processar os dados.

## 📋 Pré-requisitos

Antes de executar o script, certifique-se de ter os seguintes requisitos instalados:

- **Python 3.6+**
- Bibliotecas Python:
  - `requests`
  - `pandas`
  - `numpy`
  - `matplotlib`

Instale as dependências executando:

```bash
pip install requests pandas numpy matplotlib
```

## 🚀 Como Executar o Projeto

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/seu-usuario/pipedrive-api-data-extraction.git
   ```

2. **Acesse o diretório do projeto**:
   ```bash
   cd pipedrive-api-data-extraction
   ```

3. **Edite o script para incluir seu token da API do Pipedrive**:
   Substitua o valor do `api_token` nas URLs pelas suas credenciais da API.

4. **Execute o script**:
   Se estiver utilizando Jupyter Notebook, basta executar as células. Caso contrário, você pode rodar o script Python diretamente:
   ```bash
   python script.py
   ```

## 📊 Descrição das Tarefas

### Task 1: Obtenção e Desaninhamento dos Dados de Negócios da API do Pipedrive

1. **Requisição à API do Pipedrive para obter dados de negócios**:
   - Utilizamos a biblioteca `requests` para fazer uma chamada à API e obter um JSON contendo os negócios.

2. **Transformação dos Dados em DataFrame**:
   - Os dados retornados são convertidos em um DataFrame utilizando `pandas`.

3. **Desaninhamento das Colunas Aninhadas**:
   - Utilizamos uma função personalizada `desanexar_listas` que expande as colunas que contêm listas de dicionários.

4. **Limpeza de Colunas Aninhadas Restantes**:
   - Removemos colunas que ainda contêm listas ou dicionários para deixar o DataFrame limpo.

5. **Filtragem dos Negócios**:
   - Filtramos os dados para mostrar apenas o negócio com `id` 45805.

### Task 2: Obtenção e Desaninhamento dos Dados de Organizações da API do Pipedrive

1. **Requisição à API para Organizações**:
   - Requisição à API para obter informações sobre as organizações associadas aos negócios.

2. **Desaninhamento das Colunas de Organizações**:
   - Aplicamos a mesma função de desaninhamento utilizada nos negócios para expandir as colunas aninhadas das organizações.

3. **Filtragem das Organizações**:
   - Filtramos os dados para exibir a organização com `id` 30673.

### Task 3: Renomeação e Formatação de Colunas

1. **Renomeação de Colunas**:
   - As colunas são renomeadas para nomes mais amigáveis utilizando o dicionário de renomeação.

   Exemplo:
   ```python
   renomear_colunas = {
       'deal_id': 'id_negocio',
       'deal_value': 'valor_negocio',
       'deal_date': 'data_negocio',
       'Person_id_email': 'email_pessoa',
       'Person_id_phone': 'telefone_pessoa',
       'User_id_name': 'nome_usuario',
       'Org_id_name': 'nome_organizacao',
   }
   ```

2. **Formatação de Valores e Datas**:
   - Colunas numéricas (como `valor_negocio`) são formatadas com separadores de milhar, e colunas de datas são formatadas para `DD/MM/AAAA`.

   Exemplo de formatação:
   ```python
   df_desanexado['valor_negocio'] = df_desanexado['valor_negocio'].apply(lambda x: f"{x:,.2f}".replace(",", "X").replace(".", ",").replace("X", "."))
   df_desanexado['data_negocio'] = pd.to_datetime(df_desanexado['data_negocio']).dt.strftime('%d/%m/%Y')
   ```

## 🛠 Estrutura do Projeto

```plaintext
├── README.md               # Documentação do projeto
├── script.py               # Script Python principal para extração e transformação de dados
└── requirements.txt        # Arquivo opcional para gerenciamento de dependências
```

## 🎯 Funcionalidades Futuras

- [ ] Integração com o Airflow para automatizar o processo de ETL.
- [ ] Salvar os dados processados diretamente em um banco de dados SQL.
- [ ] Melhorar o tratamento de erros nas requisições à API.

## 📄 Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👥 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

---

Feito com 💙 por [Edimar Silva](https://github.com/edimar1315)
```

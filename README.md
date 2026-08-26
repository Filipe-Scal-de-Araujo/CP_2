# Checkpoint 01 — Listas, Tuplas e Dicionários com APIs

Avaliação prática da disciplina **Computational Thinking of Engineering** (Engenharia Mecatrônica — 1º ano), que utiliza duas APIs públicas para resolver situações envolvendo estruturas de dados em Python (listas, tuplas e dicionários).

**Autores:**
- Filipe Scal de Araujo — RM 569175
- Francisco Antonio Garcia Saia — RM 571541

## 📋 Sobre o projeto

O notebook consome dados de duas APIs públicas:

- **[AwesomeAPI](https://economia.awesomeapi.com.br/)** — cotações de moedas (USD, EUR, GBP em relação ao Real);
- **[OpenWeather](https://openweathermap.org/api)** — dados meteorológicos de quatro cidades (São Paulo, Campinas, Santos e São José dos Campos).

A partir desses dados, o notebook resolve duas situações-problema simuladas:

1. **Componentes para um protótipo mecatrônico** — cálculo do custo em reais de componentes importados, usando as cotações de câmbio.
2. **Teste de campo** — decisão sobre em quais cidades um teste externo pode ser realizado, com base em critérios de temperatura, umidade e velocidade do vento.

## 🧩 Estrutura das questões

| Questão | Descrição | Pontos |
|---|---|---:|
| 1 | Extrai as cotações de câmbio da AwesomeAPI e monta uma lista de tuplas `(moeda, valor_de_venda)`, identificando a maior cotação | 2,0 |
| 2 | Monta um dicionário de componentes e calcula o custo de cada um em reais, o custo total e o componente mais caro | 3,0 |
| 3 | Organiza os dados brutos da OpenWeather em uma lista de dicionários (`dados_clima`) | 2,0 |
| 4 | Filtra as cidades aptas para o teste de campo (temperatura, umidade e vento dentro dos limites) e gera um relatório | 3,0 |
| **Total** | | **10,0** |

## ⚙️ Pré-requisitos

- Conta Google (para rodar no Google Colab);
- Chave de API gratuita da OpenWeather ([obter aqui](https://openweathermap.org/api));
- Biblioteca `requests` (já disponível por padrão no Colab).

## ▶️ Como executar

1. Abra o notebook `CHECKPOINT_01_1EMA_2SEM.ipynb` no [Google Colab](https://colab.research.google.com/).
2. No menu lateral, clique no ícone de **chave (Secrets)** e crie um segredo chamado:
   ```
   OPENWEATHER_API_KEY
   ```
   com sua chave da OpenWeather como valor, e habilite o acesso ao notebook.
3. Execute as células na ordem, de cima para baixo:
   - Primeiro as células de **conexão com as APIs** (não alterar);
   - Depois as células de cada questão.

## ⚠️ Observações e pontos de atenção

Ao revisar o notebook, alguns pontos merecem atenção antes da entrega:

- **Chave da OpenWeather:** a célula de conexão apresentou erro `401 Unauthorized` na última execução registrada — o valor colado em `OPENWEATHER_API_KEY` parece conter a chave duplicada/quebrada em duas linhas. Verifique se o Secret está configurado com uma chave válida e em uma única linha.
- **Questão 2:** o cálculo de `custo_brl` usa `cotacoes[0][1]` (sempre a cotação da primeira moeda da lista) para todos os componentes, em vez de buscar a cotação correspondente à moeda de cada componente. Vale conferir se isso está de acordo com o enunciado, que pede o uso da cotação específica de cada moeda.
- **Questão 3:** a célula final faz `dados = [dados_clima_ap1]`, mas essa variável não é definida em nenhum lugar do notebook (o nome usado nas demais células é `dados_clima_api`), o que gera `NameError`. É necessário corrigir esse nome de variável.
- Por conta dos pontos acima, as **Questões 3 e 4** dependem de `dados_clima`, que não chega a ser criado com sucesso na versão atual do notebook — vale rodar tudo novamente do início após os ajustes.

## 📦 Estrutura de dados esperada

```python
# Questão 1
cotacoes = [("USD", 5.44), ("EUR", 6.34), ("GBP", 7.33)]

# Questão 3
dados_clima = [
    {"cidade": "São Paulo", "temperatura": 22.5, "umidade": 70, "vento": 3.2},
    # ...
]

# Questão 4
relatorio_operacao = {
    "cidades_avaliadas": 4,
    "cidades_aprovadas": ["São Paulo", "Campinas"],
    "quantidade_aprovada": 2
}
```

## 🛠️ Tecnologias

- Python 3
- [Google Colab](https://colab.research.google.com/)
- [requests](https://docs.python-requests.org/)

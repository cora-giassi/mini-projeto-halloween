# Festa em Cena - Análise de Pedidos de Halloween
## Descrição do Projeto

O projeto é sobre uma rede fictícia que vende fantasias e acessórios para o Halloween pelos canais Mercado, Loja física e Web. A gestão precisa de um relatório para comparar os períodos de venda, mas os dados estão desorganizados, trocados e até mesmo incompletos. O programa vai tratar os dados e resolver essas inconsistências para conseguir fornecer um relatório coerente.

Uma linha é um pedido de um único produto (que pode ter várias unidades).

**Quatro colunas:**

- categoria: tipo do produto (Fantasia ou Acessorio)
- canal_venda: onde o pedido foi feito (Mercado, Loja física ou Web)
- data_venda: data e hora do pedido, formato AAAA-MM-DD HH:MM:SS.
- data_entrega: data das entregas (vazia quando não há entrega)

### Regras adotadas

- **Textos:** Na categoria, usei strip() para tirar os espaços antes e depois das palavras, lower() para deixar tudo minúsculo e re.sub() para apagar o que não é letra nem espaço. Se a categoria está vazia, ela vira "sem categoria". Os canais foram padronizados para Mercado, Loja física e Web.

- **Valores:** A quantidade é válida quando o inteiro for maior que zero. O preço unitário é válido quando estiver preenchido e não negativo. Os registros com problema foram marcados e não apagados, para não inventar valores. Um pedido com os dois problemas conta uma vez só no total.

- **Datas:** A data_venda foi convertida com datetime.strptime. Se a data é inválida ou vazia, ficam marcadas em com_data_invalida, aparecem como "Data Inválida" e não entram nas contagens por ano/mês e o processamento continua. O texto original (data_venda) foi preservado.

## Guia de Execução

1. Instale o pandas: `pip install pandas`
2. Coloque `projeto.ipynb` e `halloween_vendas.csv` na mesma pasta.
3. Abra o `projeto.ipynb` no VS Code e clique em **Run All**.

## Resultados

- Total de linhas lidas: 1500
- Categorias vazias preenchidas: 18
- Categorias não vazias alteradas: 1482
- Quantidade inválida: 7
- Preço inválido ou ausente: 12
- Problemas numéricos (pedidos afetados): 19
- Datas inválidas: 4
- Total de cancelados: 109
- Sem entrega e cancelados: 109
- Sem entrega e outros status: 34

### Entrega sem data

Dos pedidos sem data de entrega, 109 são cancelados e 34 têm outro status (todos Concluídos). Por isso, a hipótese de que todo pedido sem entrega é cancelado é **falsa** nessa base. Nenhum status e data de entrega foram alterados.

### Descoberta 1: Canal

- **Evidência:** Web teve 666 pedidos, Loja física 551 e Mercado 283. Nenhum pedido foi excluído por canal não reconhecido.
- **Interpretação:** o site é o canal com mais pedidos registrados (cerca de 44% do total).
- **Limitação:** são pedidos registrados, incluindo cancelados e devolvidos. Não representam receita nem vendas concluídas.

### Descoberta 2: Período (ano-mês)

- **Evidência:** outubro teve 393 pedidos em 2024 e 410 em 2025. Novembro teve 174 em 2024 e 182 em 2025. Quatro pedidos foram excluídos por data inválida.
- **Interpretação:** os pedidos se concentram em outubro, antes do Halloween e caem em novembro.
- **Limitação:** a base cobre só agosto a novembro de cada ano e é fictícia, então não reflete o mercado real.

## Reflexão: ML e qualidade de dados

Dados com categorias vazias, textos inconsistentes, quantidades inválidas e datas erradas prejudicam as análises e os modelos de Machine Learning. Mas limpar os dados não é o suficiente para evitar overfitting ou underfitting. A representatividade da base, a escolha do modelo certo e a avaliação também importam!
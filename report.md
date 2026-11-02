# Relatório e Insights – Festa em Cena

A base fictícia tem 1.500 pedidos de agosto a novembro de 2024 e 2025. Cada linha é um pedido de um único produto, que pode ter várias unidades. 
Todas as contagens abaixo são de pedidos registrados, não de receita nem de vendas concluídas.

## Qualidade dos dados
- 18 categorias vazias foram preenchidas com "sem categoria".
- 1.482 categorias não vazias foram padronizadas com strip, lower e re.sub. A maioria só mudou de maiúscula para minúscula, e algumas tinham espaços extras ou pontuação, como "FANTASIA!!!".
- 7 pedidos têm quantidade inválida e 12 estão sem preço. Somados, 19 pedidos são afetados e nenhum valor foi inventado: esses registros só foram marcados.
- 4 datas de venda são inválidas e ficaram fora das contagens por período.

## Entrega sem data
São 143 pedidos sem data de entrega: 109 são Cancelados e 34 estão como Concluídos. A hipótese de que todo pedido sem entrega é cancelado é falsa nesta base. Esses 34 casos indicam uma possível falha de registro e nenhum status foi alterado e nenhuma data foi inventada.

## Descoberta 1 – Canal
A Web lidera com 666 pedidos (cerca de 44%), seguida de Loja física com 551 e Mercado com 283. Isso sugere que o site é o principal ponto de entrada de pedidos. 
Limitação: a contagem inclui cancelados e devolvidos, então o canal líder pode não ser o de maior receita.

## Descoberta 2 – Período
Outubro concentra a demanda: 393 pedidos em 2024 e 410 em 2025. Em setembro foram 104 e 94, e em novembro 174 e 182. Isso mostra que a procura se concentra antes do Halloween. 
Limitação: a base cobre só quatro meses por ano e não mostra o restante do ano.

## Reflexão
Limpar e tratar os dados melhora a análise, mas não é o suficiente para evitar o overfitting ou underfitting. A representatividade da base, a escolha do modelo certo e a avaliação também importam!
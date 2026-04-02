# Inteligência Logística: Dashboard de Performance e Saúde Financeira

<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Solicita%C3%A7%C3%A3o%20por%20email%20do%20Projeto%20Log%C3%ADstica.JPG?raw=true">
Projeto surgiu da necessidade do gestor da logística que está com dificuldade para acompanhar o desempenho logístico das
operações que atualmente não tem uma visão consolidada e acessível dos Centros de Distribuição
(CDs), o que tem dificultado a tomada de decisões estratégicas.<br><br>

Objetivos principais:<br>
- Acompanhar a performance logística de forma consolidada entre todos os CDs;<br>
- Ter a possibilidade de analisar cada CD individualmente;<br>
- Acompanhar os principais KPIs logísticos como OTIF (Entrega no prazo e completa), INFULL ( Entrega completa) e ONTIME (Entrega no prazo);<br>
- Visualizar o volume de pedidos entregues no prazo e os atrasados;<br>
- Ter uma visão clara das ocorrências logísticas (como mercadoria errada, cliente ausente etc);<br>
- Verificar a distribuição de pedidos por tipo de veículo utilizado;<br>
- Avaliar o desempenho mensal dos KPIs;<br>
- Ter uma visão financeira dos custos logísticos, receita bruta, margem e ticket médio;<br>
- Visualizar os dados por cidade e por tipo de ocorrência..

<br><br>
##

## Ferramentas e Tecnologias:

- Microsoft Excel: Armazenamento das bases de dados históricas (2022-2025).<br>

- Power Query (M): Utilizado para todo o processo de limpeza, tratamento de erros e consolidação (ETL).<br>

- Linguagem DAX: Desenvolvimento de métricas de performance e inteligência de tempo.<br>

- Power BI Desktop: Construção do modelo de dados, dashboards interativos e design de interface (UX/UI).

<br>

##

## Tratamento de Dados (ETL)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tratamento%20de%20Dados%20aplicado.JPG?raw=true">
Nesta fase, utilizei o Power Query para realizar o processo de ETL (Extração, Transformação e Carga). 
<br><br>

Processos Realizados:

- Acrescentar Consultas (Append): Uni as tabelas anuais de 2022, 2023, 2024 e 2025 em uma única tabela mestre. Isso permitiu uma análise histórica contínua sem fragmentação.<br>

- Limpeza de Delimitadores: Ajustei o tratamento de arquivos CSV/Excel para garantir que as colunas de "Custo" e "Receita" fossem lidas corretamente, removendo caracteres especiais desnecessários.<br>

- Tipagem de Dados: Configurei cada coluna com seu formato ideal (Data para prazos, Decimal Fixo para valores financeiros e Texto para categorias de CDs).<br>

- Criação de Colunas Condicionais: Desenvolvi lógicas simples no Power Query para pré-classificar ocorrências, otimizando o processamento que seria feito posteriormente via DAX.
<br>

##

## Modelagem de Dados e Inteligência de Tempo
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tabela%20criada%20Dim%20Calend%C3%A1rio.JPG?raw=true">

Desenvolvi uma tabela de dimensões de tempo (dCalendário) utilizando Linguagem DAX. Esta etapa permite:

- Análises Comparativas: Evolução mensal e anual (YoY).<br>

- Filtros Temporais: Segmentação por Ano, Mês, Trimestre e Semanas.<br>

- Continuidade: Garante que o dashboard não tenha "buracos" em meses sem movimentação operacional.
<br>

##

## Arquitetura Star Schema (Esquema Estrela)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Relacionamento%20da%20Dim%20Calendario%20com%20a%20Fato%20Pedidos.JPG?raw=true">


Organizei o modelo seguindo as melhores práticas de Business Intelligence:


- Tabela Fato: Centralizei todos os pedidos e eventos logísticos de 2022 a 2025.<br>

- Tabelas Dimensões: Separei as informações de CDs, Transporte, Status e Calendário.<br>

- Relacionamentos: Estabeleci conexões do tipo 1:N (Um para Muitos), garantindo integridade referencial e filtros que se propagam corretamente por todas as páginas do dashboard.

<br>

##

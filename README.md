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

---

## Ferramentas e Tecnologias:

- Microsoft Excel: Armazenamento das bases de dados históricas (2022-2025).<br>

- Power Query (M): Utilizado para todo o processo de limpeza, tratamento de erros e consolidação (ETL).<br>

- Linguagem DAX: Desenvolvimento de métricas de performance e inteligência de tempo.<br>

- Power BI Desktop: Construção do modelo de dados, dashboards interativos e design de interface (UX/UI).

---

## Tratamento de Dados (ETL)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tratamento%20de%20Dados%20aplicado.JPG?raw=true">
Nesta fase, utilizei o Power Query para realizar o processo de ETL (Extração, Transformação e Carga). 
<br><br>

Processos Realizados:

- Acrescentar Consultas (Append): Uni as tabelas anuais de 2022, 2023, 2024 e 2025 em uma única tabela mestre. Isso permitiu uma análise histórica contínua sem fragmentação.<br>

- Limpeza de Delimitadores: Ajustei o tratamento de arquivos CSV/Excel para garantir que as colunas de "Custo" e "Receita" fossem lidas corretamente, removendo caracteres especiais desnecessários.<br>

- Tipagem de Dados: Configurei cada coluna com seu formato ideal (Data para prazos, Decimal Fixo para valores financeiros e Texto para categorias de CDs).<br>

- Criação de Colunas Condicionais: Desenvolvi lógicas simples no Power Query para pré-classificar ocorrências, otimizando o processamento que seria feito posteriormente via DAX.

---

## Modelagem de Dados e Inteligência de Tempo
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tabela%20criada%20Dim%20Calend%C3%A1rio.JPG?raw=true">

Desenvolvi uma tabela de dimensões de tempo (dCalendário) utilizando Linguagem DAX. Esta etapa permite:

- Análises Comparativas: Evolução mensal e anual (YoY).<br>

- Filtros Temporais: Segmentação por Ano, Mês, Trimestre e Semanas.<br>

- Continuidade: Garante que o dashboard não tenha "buracos" em meses sem movimentação operacional.

---

## Configurações de Parâmetros e Inteligência de Tempo
<img align="right" width="300"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Par%C3%A2metros%20Criados.JPG?raw=true">
Nesta seção, detalho os bastidores técnicos que permitem a automatização das datas do dashboard e a clareza visual para a tomada de decisão.
<br><br>

Parâmetros Dinâmicos (MinDate e MaxDate)<br>
Para que a tabela de calendário fosse inteligente e dinâmica, criei parâmetros de tempo no Power BI.<br>

- MinDate (Data Mínima): Uma medida que localiza automaticamente a data mais antiga na tabela Fato_Pedidos (ex: 01/01/2022).<br>

- MaxDate (Data Máxima): Uma medida que localiza a data de pedido mais recente na base (ex: 31/12/2025).<br>

Objetivo: Esta configuração garante que, ao adicionar novos arquivos à pasta de dados, o intervalo de tempo do dashboard se ajuste sozinho, sem intervenção manual. É a base para uma solução escalável.
<br>
##

<img align="right" width="300"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Regra%20de%20cores%20para%20o%20gr%C3%A1fico%20de%20%C3%A1rea.JPG?raw=true">

Implementei uma regra visual (Formatação Condicional) no gráfico de velocímetro do KPI principal (OTIF).<br>

Utilizei a lógica DAX e as configurações de "Cor - Série" para definir uma meta de 65%:<br>

- Se o valor for >= 0,65 (65%), a cor do KPI muda automaticamente para preto/verde, sinalizando meta atingida.

- Se o valor for < 0,65 (65%), a cor muda para vermelho, alertando o gestor sobre o desempenho abaixo do esperado.

Objetivo: Melhorar a experiência do usuário (UX), permitindo uma leitura rápida e clara do status operacional ("Atenção" ou "Sucesso").

---

## Arquitetura Star Schema (Esquema Estrela)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Relacionamento%20da%20Dim%20Calendario%20com%20a%20Fato%20Pedidos.JPG?raw=true">


Organizei o modelo seguindo as melhores práticas de Business Intelligence:


- Tabela Fato: Centralizei todos os pedidos e eventos logísticos de 2022 a 2025.<br>

- Tabelas Dimensões: Separei as informações de CDs, Transporte, Status e Calendário.<br>

- Relacionamentos: Estabeleci conexões do tipo 1:N (Um para Muitos), garantindo integridade referencial e filtros que se propagam corretamente por todas as páginas do dashboard.

---

## Inteligência de Dados (Cálculos DAX)
<img align="right" width="200"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Medidas%20Criadas.JPG?raw=true">


Para transformar os dados brutos em insights acionáveis, desenvolvi uma camada de inteligência utilizando Linguagem DAX. O foco foi criar indicadores de performance (KPIs) e métricas financeiras que respondem diretamente às necessidades do gestor.<br><br>

- Organizei o modelo com mais de 10 medidas calculadas, divididas entre:<br>

- KPIs de Performance: OTIF, OnTime e InFull.<br>

- Volumetria: Contagem total de pedidos, pedidos no prazo, atrasados e com ocorrências.<br>

Saúde Financeira: Receita Bruta, Custo Total, Margem e Ticket Médio.<br>
##

### Exemplos de Lógica Aplicada (Fórmulas DAX)

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%201%20de%20Medidas%20criadas%20usando%20DAX.JPG?raw=true" width="32%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%202%20Medidas%20criadas%20Usando%20DAX.JPG?raw=true" width="32%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%203%20Medidas%20criadas%20usando%20DAX.JPG?raw=true" width="32%">
</div>

<br>

Apresento três exemplos técnicos de como a lógica foi implementada no Power BI para garantir precisão e performance na tomada de decisão:

1. **Eficiência de Prazo (% ONTIME):** Utilizei a função `DIVIDE` para calcular a proporção de pedidos entregues no prazo. Esta função é considerada uma boa prática em BI, pois trata automaticamente erros de divisão por zero, garantindo que o dashboard nunca exiba valores de erro e mantenha a integridade visual.

2. **Segmentação Dinâmica (CALCULATE):** Através da função `CALCULATE`, criei métricas específicas que filtram a tabela fato diretamente na medida. Neste exemplo, a medida isola apenas os pedidos cujo status é "No Prazo", permitindo comparações rápidas entre o volume total e a performance ideal do negócio.

3. **Qualidade Logística (Pedidos SEM Ocorrência):** Para medir a qualidade operacional, apliquei um filtro na dimensão de status (`idOcorrencia = "1"`). Isso permite identificar os pedidos que foram entregues sem qualquer tipo de avaria, reclamação ou problema de comunicação, fundamental para o cálculo do indicador mestre: o **OTIF**.

---

## Design de Experiência (UX) e Interatividade

Nesta etapa, foquei em transformar dados complexos em uma interface intuitiva. O objetivo foi garantir que o gestor pudesse navegar entre diferentes visões e obter detalhes sem sobrecarregar a tela principal.

### Navegação e Identidade Visual

Desenvolvi botões de navegação interativos que separam o dashboard em duas visões estratégicas:
-   **KPIs de Performance:** Visão operacional focada no OTIF.
-   **Saúde Financeira:** Visão de faturamento, custo e margem.

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20de%20Bot%C3%B5es%20de%20navega%C3%A7%C3%A3o%20de%20p%C3%A1ginas.JPG?raw=true" width="45%">
</div>

<br>

### Tooltips Personalizadas (Dicas de Ferramenta)

As Tooltips foram configuradas para fornecer um "mergulho nos dados" sem a necessidade de trocar de página. Ao passar o mouse sobre os gráficos, janelas flutuantes detalham as informações.

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20Tool%20Tip%202.JPG?raw=true" width="48%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20Tool%20Tip%203.JPG?raw=true" width="48%">
</div>

---

## Entrega Final e Insights de Negócio
O objetivo final deste projeto foi transformar dados brutos em uma ferramenta de apoio à decisão. Com o dashboard concluído, é possível identificar gargalos operacionais e oportunidades de economia financeira.

### Painel de KPIs (Visão Operacional)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/P%C3%A1gina%20KPI%C2%B4s.JPG?raw=true">

Principais Insights Operacionais:

- Gargalo de Ocorrências: Identificamos que "Mercadoria Errada" e "Cliente Ausente" são as maiores causas de insucesso nas entregas. Isso sugere uma revisão no processo de conferência no carregamento e uma melhoria na comunicação de agendamento com o cliente.<br>

Performance de Frota: O uso de Tooltips permite visualizar que determinados tipos de veículos, como a Fiorino, possuem um volume maior de entregas no prazo em comparação a carretas de grande porte em áreas urbanas.<br>

OTIF Geográfico: O mapa destaca cidades onde o índice OTIF está abaixo da meta (65%), permitindo uma atuação direta nos Centros de Distribuição dessas regiões.

##

### Painel Financeiro (Visão de Rentabilidade)
<img align="right" width="500"  src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/P%C3%A1gina%20Financeiro.JPG?raw=true">

Principais Insights Financeiros:

- Análise de Margem: Através das medidas DAX de % Margem e Ticket Médio, conseguimos isolar rotas que, apesar de alto faturamento, possuem custos logísticos que corroem o lucro.<br>

- Impacto das Ocorrências: Calculamos o custo do "retrabalho" gerado por entregas com ocorrência, quantificando a perda financeira direta por mercadorias recusadas.

---

##
##

## Conclusão Estratégica: Inteligência de Dados na Operação Logística
Este projeto não se limitou à criação de gráficos, mas sim ao desenvolvimento de uma solução de Business Intelligence voltada para a eficiência da malha logística. Através da integração de dados de pedidos e ocorrências, o dashboard permite uma transição da gestão reativa para a gestão preditiva.

Valor Agregado à Operação:
Otimização de Custos (Bottom Line): Através das métricas financeiras como Custo Total e Margem, o gestor consegue identificar rotas onde o frete está consumindo a rentabilidade, permitindo renegociações ou trocas de modais.

Melhoria no Nível de Serviço (SLA): Acompanhar o % OTIF e o % ONTIME em tempo real permite que a operação identifique imediatamente quais Centros de Distribuição ou transportadoras estão performando abaixo da meta de 65% estabelecida nas regras de negócio.

Redução de Ineficiências (Ocorrências): Ao mapear motivos como "Mercadoria Errada" ou "Pedido Faltando", a operação pode atuar na causa raiz dentro do armazém, reduzindo o custo de logística reversa e aumentando a satisfação do cliente final.

Decisões Baseadas em Evidências: O uso de parâmetros dinâmicos e filtros de data permite análises históricas precisas para planejar picos de demanda e sazonalidade.

### Resultado Final
A entrega deste dashboard proporciona à liderança logística uma "Torre de Controle" capaz de monitorar a saúde financeira e a performance de entrega em um único local, eliminando planilhas manuais e garantindo que a decisão seja sempre pautada em dados íntegros e atualizados.







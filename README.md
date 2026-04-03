# Inteligência Logística: Dashboard de Performance e Saúde Financeira

Este projeto surgiu da necessidade de consolidar o acompanhamento do desempenho logístico. O gestor enfrentava dificuldades para visualizar as operações dos Centros de Distribuição (CDs) de forma integrada, o que impactava a tomada de decisões estratégicas devido à falta de uma visão consolidada e acessível.

| Objetivos do Projeto | Contexto da Solicitação |
| :--- | :--- |
| - Monitorar a performance logística consolidada entre todos os CDs. <br> - Analisar o desempenho individualizado por unidade operativa. <br> - Acompanhar KPIs fundamentais: OTIF, InFull e OnTime. <br> - Quantificar o volume de pedidos no prazo versus atrasados. <br> - Mapear ocorrências logísticas (mercadoria errada, cliente ausente). <br> - Avaliar a saúde financeira: custos, receita bruta, margem e ticket médio. | <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Solicita%C3%A7%C3%A3o%20por%20email%20do%20Projeto%20Log%C3%ADstica.JPG?raw=true" width="500"> |

---

## Ferramentas e Tecnologias

- **Microsoft Excel:** Repositório das bases de dados históricas (2022-2025).
- **Power Query (Linguagem M):** Utilizado para todo o processo de limpeza, tratamento de erros e consolidação (ETL).
- **Linguagem DAX:** Desenvolvimento de métricas complexas de performance e inteligência de tempo.
- **Power BI Desktop:** Construção do modelo de dados, dashboards interativos e interface de usuário (UX/UI).

---

## Tratamento de Dados (ETL)

Nesta fase, utilizei o Power Query para realizar o processo de Extração, Transformação e Carga (ETL), garantindo que os dados estivessem prontos para uma análise precisa.

| Processos Realizados | Evidência Técnica |
| :--- | :--- |
| **Acrescentar Consultas (Append):** Unificação das tabelas anuais (2022 a 2025) em uma única tabela mestre, permitindo análise histórica contínua. <br><br> **Limpeza e Padronização:** Ajuste de delimitadores em arquivos CSV/Excel e tratamento de colunas financeiras (Custo e Receita) para leitura correta. <br><br> **Tipagem e Colunas Condicionais:** Configuração de formatos de dados e criação de lógicas para pré-classificar ocorrências operacionais. | <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tratamento%20de%20Dados%20aplicado.JPG?raw=true" width="500"> |

---

## Modelagem de Dados e Arquitetura

A estrutura do modelo foi desenhada seguindo as melhores práticas de Business Intelligence para suportar filtros dinâmicos e garantir a integridade referencial.

| Arquitetura Star Schema | Relacionamentos do Modelo |
| :--- | :--- |
| **Tabela Fato:** Centralização de todos os pedidos e eventos logísticos de 2022 a 2025. <br><br> **Tabelas Dimensões:** Separação clara de informações sobre CDs, Transportes, Status e Tempo. <br><br> **Integridade:** Conexões do tipo 1:N (Um para Muitos), garantindo que os filtros se propaguem corretamente por todo o painel. | <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Relacionamento%20da%20Dim%20Calendario%20com%20a%20Fato%20Pedidos.JPG?raw=true" width="500"> |

### Inteligência de Tempo (Tabela dCalendário)

Desenvolvi uma tabela de dimensões de tempo dedicada utilizando Linguagem DAX. Esta etapa é fundamental para permitir análises comparativas e garantir a continuidade histórica do dashboard.

| Funcionalidades da dCalendário | Visualização do Código DAX |
| :--- | :--- |
| **Análises Comparativas:** Evolução mensal e anual (YoY), essencial para identificar sazonalidade. <br><br> **Filtros Temporais:** Segmentação por Ano, Mês, Trimestre e Semanas. <br><br> **Consistência:** Garante que o dashboard não apresente lacunas em meses sem movimentação operacional. | <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Tabela%20criada%20Dim%20Calend%C3%A1rio.JPG?raw=true" width="500"> |

---

## Configurações de Parâmetros e Automação

Implementação de bastidores técnicos que garantem a escalabilidade do painel e o monitoramento visual de metas.

**Parâmetros Dinâmicos (MinDate e MaxDate)**
Desenvolvi parâmetros que identificam automaticamente o intervalo de datas na base. Isso assegura que, ao inserir novos dados, o dashboard se ajuste sozinho, sem necessidade de ajuste manual no modelo.

**Formatação Condicional de Metas**
Apliquei regras visuais no KPI de OTIF com meta de 65%. A cor do indicador alterna automaticamente entre verde (meta atingida) e vermelho (atenção), otimizando o tempo de leitura do gestor.

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Par%C3%A2metros%20Criados.JPG?raw=true" width="45%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Regra%20de%20cores%20para%20o%20gr%C3%A1fico%20de%20%C3%A1rea.JPG?raw=true" width="45%">
</div>

---

## Inteligência de Dados (Cálculos DAX)

Criação de uma camada de medidas robustas para transformar volume de pedidos em indicadores de rentabilidade e serviço.

| Gestão de Medidas | Inventário de Métricas |
| :--- | :--- |
| O modelo conta com mais de 10 medidas calculadas, separadas por contexto: <br> - **Performance:** OTIF, OnTime, InFull. <br> - **Volume:** Pedidos Totais, Atrasos, Ocorrências. <br> - **Financeiro:** Margem Bruta, Receita, Ticket Médio. | <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Medidas%20Criadas.JPG?raw=true" width="250"> |

### Exemplos de Lógica Aplicada (Fórmulas DAX)

Abaixo, apresento a construção técnica de três métricas fundamentais para a operação:

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%201%20de%20Medidas%20criadas%20usando%20DAX.JPG?raw=true" width="32%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%202%20Medidas%20criadas%20Usando%20DAX.JPG?raw=true" width="32%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Exemplo%203%20Medidas%20criadas%20usando%20DAX.JPG?raw=true" width="32%">
</div>

1. **Eficiência de Prazo (% ONTIME):** Utilização da função `DIVIDE` para garantir segurança matemática e evitar erros de divisão por zero.
2. **Segmentação Dinâmica (CALCULATE):** Aplicação de filtros contextuais para isolar o volume de pedidos entregues rigorosamente no prazo.
3. **Qualidade Operacional:** Lógica para contabilizar entregas sem ocorrências, servindo de base para o indicador OTIF.

---

## Design de Experiência (UX) e Interatividade

O foco do design foi a usabilidade, permitindo que o usuário realize o detalhamento dos dados de forma intuitiva.

- **Navegação:** Menu lateral com botões para alternar entre a visão operacional e financeira.
- **Detalhamento (Tooltips):** Configuração de janelas flutuantes que detalham ocorrências por tipo de veículo ou região sem a necessidade de sair da tela principal.

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20de%20Bot%C3%B5es%20de%20navega%C3%A7%C3%A3o%20de%20p%C3%A1ginas.JPG?raw=true" width="40%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20Tool%20Tip%202.JPG?raw=true" width="28%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/Cria%C3%A7%C3%A3o%20Tool%20Tip%203.JPG?raw=true" width="28%">
</div>

---

## Entrega Final e Insights de Negócio

O resultado final é uma ferramenta de suporte à decisão que permite identificar oportunidades de melhoria na malha logística.

<div align="center">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/P%C3%A1gina%20KPI%C2%B4s.JPG?raw=true" width="48%">
  <img src="https://github.com/JCarlosGN/Projeto_Logistica_Portfolio/blob/main/Imagens%20Projeto%20Logistica/P%C3%A1gina%20Financeiro.JPG?raw=true" width="48%">
</div>

**Insights Extraídos:**
- **Gargalos Operacionais:** "Mercadoria Errada" e "Cliente Ausente" são os principais detratores do OTIF, exigindo revisão nos processos de checkout e agendamento.
- **Eficiência de Frota:** Veículos leves possuem melhor performance de prazo em áreas urbanas, enquanto veículos pesados demandam maior atenção no planejamento de rotas.
- **Saúde Financeira:** Identificação de rotas com alto faturamento, porém com margem reduzida devido aos custos de reentrega e ocorrências.

---

## Conclusão Estratégica

Este projeto entregou uma solução de Business Intelligence que transforma a gestão logística de reativa em preventiva. A centralização dos dados em uma torre de controle automatizada permite a otimização de custos e o monitoramento rigoroso do nível de serviço (SLA), garantindo decisões baseadas em evidências e integridade total das informações.

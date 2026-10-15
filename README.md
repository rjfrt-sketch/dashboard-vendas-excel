# Dashboard de Vendas — Xbox Game Pass (Excel)

Dashboard em Excel que transforma a base bruta de assinaturas do Xbox Game Pass em indicadores e gráficos para apoiar decisões de venda.

## Arquivos
- `dashboard_xbox.xlsx` — workbook com o dashboard concluído.
- `README.md` — este documento.

## Dados utilizados
Base `base.xlsx` do desafio (aba **Bases**, tabela `Tabela1`): **295 assinaturas**, com início entre jan e dez/2024.

| Coluna | Descrição |
|---|---|
| Subscriber ID, Name | identificação do assinante |
| Plan | Core, Standard ou Ultimate |
| Start Date | data de início da assinatura |
| Auto Renewal | Yes / No |
| Subscription Type | Monthly, Quarterly ou Annual |
| Subscription Price | preço da assinatura |
| EA Play Season Pass (+ Price) | adicional EA Play |
| Minecraft Season Pass (+ Price) | adicional Minecraft |
| Coupon Value | desconto aplicado |
| Total Value | valor da venda = preço + EA Play + Minecraft − cupom |

Validação: a regra de `Total Value` foi conferida linha a linha e não há divergências. A coluna de preço do EA Play traz `-` quando não há compra; as fórmulas `SUMIFS` ignoram esse texto.

## Estrutura do workbook
- **Assets** — paleta de cores e logos usados no visual.
- **Bases** — dados brutos.
- **Cálculos** — todas as métricas, em fórmulas (`SUMIFS`, `COUNTIFS`, `EDATE`) sobre a aba Bases.
- **Dashboard** — painel final.

## Perguntas de negócio respondidas
1. Faturamento total de planos anuais: **R$ 1.754**
2. Faturamento de planos anuais por auto renovação: **R$ 1.537** com e **R$ 217** sem
3. Total de vendas do EA Play Season Pass: **R$ 2.940**
4. Total de vendas do Minecraft Season Pass: **R$ 3.880**

Indicadores gerais: faturamento total de **R$ 7.633**, 295 assinantes e ticket médio de cerca de R$ 25,87.

## Principais insights
- O plano **Ultimate** responde por cerca de 70% do faturamento (R$ 5.388 de R$ 7.633).
- O faturamento mensal fica estável perto de R$ 800 entre mar e nov/2024; jan e fev têm poucas vendas e dez é parcial.
- Entre os planos anuais, ~88% do faturamento vem de assinantes com auto renovação.

## Como usar
1. Abra `dashboard_xbox.xlsx` no Excel 2016 ou superior.
2. Na aba **Dashboard**, use o menu da célula **D5** (Todos / Monthly / Quarterly / Annual) para filtrar a Seção 1. A Seção 2 trata sempre de planos anuais.
3. Para atualizar com novos dados, adicione linhas na tabela da aba **Bases**; as fórmulas cobrem até a linha 1000.

## Como reproduzir do zero
1. Importe `base.xlsx` e mantenha a aba Bases como Tabela (`Ctrl+T`).
2. Na aba **Cálculos**, crie as métricas com `SUMIFS`/`COUNTIFS` (ou Tabelas Dinâmicas) e a série mensal com `EDATE`.
3. Na aba **Dashboard**, monte cartões de KPI e gráficos apontando para a aba Cálculos, usando a paleta da aba Assets (`#22C55E`, `#9BC848`, `#E8E6E9`).
4. Adicione a validação de dados (lista) na célula D5 para o filtro.

## Observação técnica
Em vez de Tabelas Dinâmicas e segmentação de dados (como no exemplo da DIO), este dashboard usa fórmulas e um filtro por lista suspensa, que se recalculam automaticamente sem precisar atualizar pivôs.

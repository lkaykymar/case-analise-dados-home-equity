# case-analise-dados-home-equity
# BZR Group — Case de Análise de Dados: Home Equity

## Sobre o projeto

Este repositório apresenta a análise de dados desenvolvida para um case da **BZR Group**, com foco em operações de **Home Equity**.

O objetivo foi explorar a base disponibilizada, identificar padrões e inconsistências, calcular indicadores de desempenho e gerar insights relacionados ao volume de crédito, fechamento das operações, tipos de imóvel e canais de aquisição.

## Objetivos da análise

- Analisar a evolução do crédito aprovado ao longo do período;
- Avaliar o volume e o percentual de crédito das operações fechadas;
- Analisar o desempenho por tipo de imóvel;
- Avaliar o desempenho dos canais de aquisição;
- Identificar inconsistências e valores ausentes na base;
- Propor um processo operacional simplificado e seus principais KPIs;
- Apresentar possíveis oportunidades de distribuição de investimento entre os canais.

## 1. Visão geral da base

A base analisada contém **1.185 registros e 14 variáveis**, relacionadas às operações de crédito Home Equity.

Antes das análises, foi realizada uma verificação da estrutura, dos tipos de dados, dos valores ausentes e de possíveis inconsistências.

Entre os principais pontos identificados:

- `closed_at` apresentou **68,10% de valores ausentes**;
- `credit_score` apresentou **41,43% de valores ausentes**;
- `loan_term` apresentou **41,01% de valores ausentes**;
- As demais variáveis apresentaram menos de 2% de valores ausentes;
- Foram identificadas operações com data de fechamento anterior à data de aprovação;
- Observou-se um registro com idade de 9 anos, considerado como possível erro de digitação;
- Foram constatadas operações em que o valor financiado era superior ao valor do imóvel;
- Foram detectadas inconsistências na nomenclatura da variável `property_type`.

A variável `property_type` foi padronizada para reduzir inconsistências de nomenclatura, resultando nas categorias `apartment`, `house`, `commercial` e `land`.

As inconsistências foram avaliadas de acordo com o objetivo da análise. Para registros inconsistentes, a primeira alternativa seria validar e corrigir os dados a partir da fonte original. Caso não seja possível confirmar a informação, os registros poderiam ser excluídos da análise, evitando que valores potencialmente incorretos influenciem os resultados. Para os valores ausentes, podem ser utilizadas técnicas de imputação, considerando a distribuição dos dados disponíveis, medidas estatísticas de tendência central e dispersão ou modelos estatísticos, como regressão linear, para estimar valores aproximados.

Como as variáveis analisadas, com exceção de closed_at, apresentaram baixa quantidade de valores ausentes, optou-se por mantê-los sem imputação. Os valores ausentes em closed_at foram interpretados como operações ainda não fechadas, e não como operações que não serão fechadas. Por esse motivo, também foram mantidos.

---

## 2. Métricas analisadas

Para responder às questões propostas no case, foram calculadas e analisadas as seguintes métricas:

- **Volume financeiro de crédito aprovado por trimestre**;
- **Volume financeiro e percentual de crédito aprovado por tipo de imóvel e trimestre**;
- **Volume financeiro e percentual de crédito aprovado para operações sem tipo de imóvel informado, por trimestre**;
- **Volume financeiro e percentual de fechamento do crédito aprovado, por trimestre**;
- **Percentual de fechamento por tipo de imóvel**;
- **Volume financeiro de crédito aprovado por canal**;
- **Conversão financeira por canal.**

---

## 3. Principais conclusões

### Evolução do crédito aprovado

<img width="986" height="490" alt="image" src="https://github.com/user-attachments/assets/ac7253e4-60db-4360-b9dc-d09fa104cfb3" />

O volume de crédito aprovado apresentou forte crescimento ao longo do período analisado, passando de aproximadamente **R$ 9 milhões no terceiro trimestre de 2024 para R$ 62,9 milhões no quarto trimestre de 2025**, aproximadamente sete vezes o valor observado no início do período.

O crescimento se intensificou principalmente ao longo de 2025, com destaque para o período entre o segundo e o quarto trimestre.

### Crédito aprovado e fechamento

<img width="986" height="490" alt="image" src="https://github.com/user-attachments/assets/8ec344d5-69e6-4c9e-b7a8-92c0fb1bb38c" />

<img width="986" height="490" alt="image" src="https://github.com/user-attachments/assets/87603b28-7fc0-454e-8d2a-e940f8ac09b8" />

Embora o percentual de crédito aprovado que chegou ao fechamento tenha apresentado redução, passando de **23% no Q3-2024 para 16% no Q4-2025**, o crescimento do volume aprovado também elevou o volume absoluto de crédito fechado, de aproximadamente **R$ 2,0 milhões para R$ 10,2 milhões**.

O maior volume de crédito fechado ocorreu no **Q3-2025**, com aproximadamente **R$ 12,7 milhões**.

No Q4-2025, entretanto, o crédito aprovado continuou crescendo enquanto o volume de crédito fechado diminuiu, indicando que o crescimento das aprovações não foi acompanhado na mesma proporção pelos fechamentos.

### Crédito por tipo de imóvel

<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/fcf8cea9-a388-43e8-aa07-e035936f6d9f" />

O crédito aprovado esteve concentrado principalmente em **apartamentos e casas** durante todo o período analisado.

Os apartamentos apresentaram o maior volume de crédito aprovado em todos os trimestres, com destaque para o período entre Q2-2025 e Q4-2025. As casas também representaram uma parcela significativa do crédito aprovado, enquanto imóveis comerciais e terrenos apresentaram participação reduzida.

O crescimento do crédito aprovado observado ao longo de 2025 ocorreu principalmente pelo aumento dos volumes destinados a apartamentos e casas.

### Fechamento por tipo de imóvel

<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/976a9efb-1de1-4ccb-9b27-ef6332512943" />

Apesar de os apartamentos concentrarem o maior volume de crédito aprovado, as casas apresentaram um percentual de fechamento ligeiramente superior:

- **Casas: 27,70%**
- **Apartamentos: 25,48%**

Imóveis comerciais e terrenos apresentaram percentuais de fechamento consideravelmente menores, indicando diferenças no comportamento de fechamento entre os tipos de imóvel.

### Completude da informação sobre o tipo de imóvel

<img width="984" height="490" alt="image" src="https://github.com/user-attachments/assets/c3a4474c-0ed6-4059-b854-00a319f67d12" />

A quantidade de registros sem informação sobre o tipo de imóvel apresentou uma pequena alta no Q1-2025. A partir desse período, houve redução contínua, chegando a **zero no Q4-2025**.

Esse comportamento indica uma melhora na completude dos dados referentes ao tipo de imóvel ao longo do período analisado.

### Volume de crédito por canal

<img width="889" height="490" alt="image" src="https://github.com/user-attachments/assets/3e1c6665-5b2e-4585-bc77-cb4d36b40389" />

O canal **Organic** concentrou o maior volume financeiro entre os canais analisados, com aproximadamente **R$ 126,1 milhões em crédito**.

O segundo maior volume foi observado no canal **Offline**, com aproximadamente **R$ 34,7 milhões**, enquanto os demais canais apresentaram volumes significativamente menores.

### Conversão por canal

<img width="889" height="490" alt="image" src="https://github.com/user-attachments/assets/4fa32477-9523-4a08-8aed-d61c7d9268bb" />

Os canais apresentaram diferenças relevantes entre o volume de crédito aprovado e a proporção desse volume que chegou ao fechamento.

Em termos de conversão financeira, os maiores percentuais observados foram:

- **Other: 48,37%**
- **Social Media: 39,67%**

O menor percentual observado foi:

- **Remarketing: 24,71%**

Esses resultados mostram que o canal com maior volume financeiro aprovado não necessariamente apresenta a mesma proporção de conversão em crédito fechado, tornando importante analisar **volume e conversão conjuntamente**.

## 4. Possíveis Distribuições de Investimento entre os Canais

A estratégia deve considerar conjuntamente volume financeiro e conversão, buscando equilibrar escala e eficiência. Como proposta inicial, seria possível destinar 35% do orçamento para Organic, devido ao elevado volume financeiro observado, 20% para Social Media e 20% para Other, canais que apresentaram percentuais de conversão superiores. Os 25% restantes seriam distribuídos entre Offline, Affiliates e Remarketing, com menor investimento inicial e acompanhamento contínuo dos resultados.

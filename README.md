
## 📊 Painel de Vendas

### 1. Objetivo

Este arquivo (`Entrega_9_-_Dashboard___PowerQuery.xlsx`) é um dashboard construído a partir de uma base de dados de vendas, aplicando os conceitos trabalhados na capacitação: importação e tratamento de base no Power Query, modelagem de dados no Power Pivot, construção de indicadores (medidas DAX), tabelas dinâmicas e estruturação de um mini dashboard analítico.

O arquivo é `.xlsx` — não utiliza macros/VBA; toda a automação de tratamento de dados foi feita via Power Query (consultas) e Power Pivot (modelo de dados e medidas).

### 2. Estrutura do arquivo (abas)

| Aba | Visibilidade | Descrição |
|---|---|---|
| **Base de Dados** | Visível | Base tratada e enriquecida, resultado das consultas do Power Query (merge com `Marca` e `Tabelas Auxiliares`). É a fonte de todas as tabelas dinâmicas e do modelo de dados. 33.545 linhas. |
| **Tabelas Auxiliares** | Oculto | Tabela de apoio com a hierarquia vendedor → supervisor → gerente → equipe de vendas, além de categoria. Consultada no Power Query. |
| **Marca** | Oculto | Tabela de apoio com o de-para de `ID_Marca` → `Marca`. Consultada no Power Query e também carregada no Modelo de Dados. |
| **Tabelas Dinâmicas** | Visível | Tabelas dinâmicas que alimentam o dashboard (faturamento por vendedor, por mês, por categoria, por equipe de vendas). |
| **Dashboard** | Visível | Aba principal — KPIs, gráficos e segmentação de dados (slicer), para visualização executiva. |

*Abas ocultas guardam as tabelas de apoio usadas no tratamento — foram ocultadas para não poluir a navegação, mas continuam ativas e recalculando normalmente.*

### 3. Importação e tratamento da base (Power Query)

Três consultas foram criadas no Power Query:
- **`Base de Dados`**: consulta principal, com o merge (mesclagem) das tabelas `Marca` e `Tabelas Auxiliares`, trazendo já resolvidas as colunas `Vendedor`, `Supervisor`, `Gerente`, `Equipe Vendas`, `Marca`, `Subcategoria` e `Categoria`.
- **`Marca`**: consulta de apoio com o de-para de marca.
- **`Tabelas Auxiliares`**: consulta de apoio com a hierarquia de vendas e categorias.

Todo o tratamento (junção das tabelas, tipagem de colunas, tratamento de nulos) foi feito na camada do Power Query, e o resultado é carregado tanto para a planilha `Base de Dados` quanto para o Modelo de Dados (Power Pivot).

### 4. Modelo relacional (quando aplicável)

Como as tabelas auxiliares já foram mescladas na `Base de Dados` durante o tratamento no Power Query, um modelo relacional não se fez estritamente necessário para a construção das medidas e do dashboard — a informação de marca, categoria e hierarquia de vendas já está disponível como coluna única na tabela tratada.

Ainda assim, foi criado um relacionamento entre a tabela **`Marca`** e a **`Base de Dados`** (via `Id_Marca` ↔ `ID_Marca`) no Modelo de Dados do Power Pivot, para demonstrar a técnica de modelagem relacional. Esse relacionamento não é utilizado nas medidas nem no dashboard final, já que a coluna `Marca` mesclada cumpre a mesma função sem redundância de modelo.

### 5. Indicadores (medidas DAX)

Medidas criadas no Power Pivot, usadas nas tabelas dinâmicas e nos cartões do dashboard:

- **Faturamento Total:** R$ 1.221.063.833,19
- **Ticket Médio:** R$ 36.400,77
- **Desconto Médio:** 8,01%
- **Quantidade de Vendas (Qtde):** 436.570
- **Quantidade de Pedidos:** 33.545

### 6. Tabelas dinâmicas e gráficos

**4 tabelas dinâmicas** na aba `Tabelas Dinâmicas`:
- Faturamento por vendedor
- Quantidade por mês
- Faturamento por categoria/subcategoria
- Quantidade por equipe de vendas

Essas tabelas alimentam **4 gráficos** na aba `Dashboard`:
- Faturamento por mês (linha)
- Faturamento por vendedor (barras)
- Faturamento por categoria (barras)
- Distribuição por equipe de vendas (rosca)

Há uma **segmentação de dados (slicer) por Ano** conectada às tabelas dinâmicas, permitindo filtrar o painel de forma interativa.

## 👩‍💻 Autora

Desenvolvido por **Ana Beatriz Mendes de Sousa**
[LinkedIn](https://www.linkedin.com/in/ana-beatriz-mendes-de-sousa) · [GitHub](https://github.com/beatrizzmendees)


Quer que eu salve isso como uma aba "Leia-me" dentro do próprio arquivo .xlsx, ou como um arquivo .md separado pra você anexar na entrega?

# 🚗 Dashboard de Locação de Veículos — Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen?style=for-the-badge)

## 📋 Sobre o Projeto

Dashboard analítico desenvolvido no **Power BI** para monitoramento e análise de uma empresa fictícia de locação de veículos. O projeto centraliza informações de faturamento, perfil de clientes e previsão de receita em um painel interativo com navegação por abas, slicers dinâmicos e visuais customizados.

---

## 📊 Estrutura do Dashboard

O relatório é composto por **4 páginas**:

### 🏠 Capa
Página de apresentação com identidade visual do projeto e botão de navegação para o dashboard principal.

### 📦 Locação de Veículo
Visão operacional das locações, contendo:
- **Faturamento por Ano** — gráfico de colunas com drill-down por trimestre, mês e dia
- **Participação % no Faturamento** — gráfico de colunas com % sobre o total por ano/mês
- **Faturamento por Dia da Semana** — gráfico de barras para identificar padrões semanais
- **Cards de KPIs:** Total de Clientes, Média de KM rodados, Total de Vendas
- **Tabela detalhada** com ID do cliente, marca, modelo, placa, dia da semana, cadastro, valor de venda e status
- **Filtro de busca por placa** (visual customizado)
- **Slicers:** Situação Cadastral, Ano, Modelo, Dia da Semana

### 👤 Cliente
Análise do perfil e comportamento dos clientes:
- **Cards de KPIs:** Total de Cidades, Total de Clientes, Faturamento Total, Ticket Médio (salário)
- **Rosca por Situação Cadastral** — distribuição de clientes ativos/inativos
- **Rosca por Categorias** — segmentação dos clientes por categoria
- **Tabela INNER JOIN** — clientes que possuem locação ativa (ID, Nome, Marca, Modelo, Status, Valor Gasto)
- **Tabela LEFT JOIN** — todos os clientes, incluindo os sem locação (ID, Placa, Marca, Dia, Modelo, Status)
- **Slicers:** ID do Cliente, Marca, Data

### 📈 Previsão
Projeção de receita futura:
- **Gráfico de Linha com Previsão** — série temporal de faturamento com forecast por ano/trimestre/mês
- **Cards de KPIs:** Total de Clientes, Ticket Médio, Total de Vendas
- **Slicers:** Situação Cadastral, Ano, Modelo, Dia da Semana

---

## 🗄️ Modelagem de Dados

### Tabelas utilizadas

| Tabela | Descrição |
|--------|-----------|
| `tb_km` | Tabela fato principal — registros de locação com dados de veículo, cliente, KM, datas e valores |
| `tb_cli` | Tabela dimensão de clientes — ID, nome, cidade e informações cadastrais |
| `MEDIDAS` | Tabela de medidas DAX centralizadas |

### Principais colunas — `tb_km`

| Coluna | Tipo |
|--------|------|
| ID_CLIENTE | Chave estrangeira |
| PLACA | Texto |
| MARCA | Texto |
| MODELO | Texto |
| DATA / ANO | Data / Hierarquia de datas |
| SITUAÇÃO CADASTRAL | Texto |
| CATEGORIAS | Texto |
| Total Venda | Numérico |
| Media de KM | Numérico |
| Nome do Dia | Texto calculado |
| ICONE | Numérico |

### Principais colunas — `tb_cli`

| Coluna | Tipo |
|--------|------|
| ID | Chave primária |
| NOME | Texto |
| Cidade | Texto |

### Relacionamentos
O modelo utiliza relacionamentos entre `tb_km[ID_CLIENTE]` → `tb_cli[ID]`, com consultas **INNER JOIN** (clientes com locação) e **LEFT JOIN** (todos os clientes) para análises comparativas na página de clientes.

---

## 📐 Medidas DAX

| Medida | Descrição |
|--------|-----------|
| `FAT` | Faturamento total |
| `Fat Medida` | Faturamento com contexto de filtro |
| `%GT Fat Medida` | Participação percentual sobre o total de faturamento |
| `MEDIA DE KM` | Média de quilometragem por locação |
| `TOTAL CLIENTES` | Contagem distinta de clientes |
| `TOTAL CIDADES` | Contagem distinta de cidades |
| `ticket médio salario` | Ticket médio relacionado ao salário dos clientes |
| `MEDIA SLR` | Média salarial dos clientes |

---

## 🛠️ Tecnologias e Recursos

- **Power BI Desktop**
- **DAX** — medidas e colunas calculadas
- **Power Query (M)** — transformação e tratamento de dados
- Visual customizado: **Text Filter** (filtro de busca por placa)
- Hierarquia de datas nativa do Power BI (Ano → Trimestre → Mês → Dia)
- Drill-down habilitado nos gráficos temporais
- Tema visual customizado (CY26SU04)
- Imagens de fundo customizadas por página

---

## 📁 Estrutura do Repositório

```
📦 locacao-veiculos-powerbi
 ┣ 📊 LOCAÇÃO_DE_VEÍCULOS.pbix
 ┗ 📄 README.md
```

---

## 🚀 Como Visualizar

1. Faça o download do arquivo `LOCAÇÃO_DE_VEÍCULOS.pbix`
2. Abra com o **Power BI Desktop** (gratuito — [download aqui](https://powerbi.microsoft.com/pt-br/desktop/))
3. Navegue pelas abas: **Capa → Locação de Veículo → Cliente → Previsão**
4. Utilize os slicers para filtrar por ano, modelo, situação cadastral e dia da semana

---

## 👨‍💻 Autor

Feito com 💙 por **[Seu Nome]**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/juanvictor-cmd/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/JuanVictor-cmd)

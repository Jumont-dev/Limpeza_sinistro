## 🧹 Limpeza e Pré-processamento de Dados de Sinistros

Este projeto tem como objetivo preparar um conjunto de dados de sinistros para análises futuras, garantindo maior qualidade, consistência e confiabilidade das informações.

### 📂 Etapas Realizadas

#### 🔹 Carregamento Inicial

O conjunto de dados foi carregado a partir do arquivo **`SINISTROS.xlsx`**, servindo como base para todas as etapas subsequentes.

#### 🔹 Remoção de Colunas

Foram removidas colunas consideradas irrelevantes, redundantes ou com baixo valor analítico, incluindo:

* Informações temporais derivadas: `ano_sinistro`, `mes_sinistro`, `dia_sinistro`, `ano_mes_sinistro`, `dia_da_semana`, `turno`
* Localização e administração: `tipo_local`, `cod_ibge`, `regiao_administrativa`, `administracao`, `conservacao`, `circunscricao`
* Indicadores específicos: `qtd_gravidade_ileso` e múltiplas colunas relacionadas a `tp_sinistro`

#### 🔹 Agregação de Dados de Veículos

As colunas:

* `qtd_veic_outros`
* `qtd_veic_nao_disponivel`

foram combinadas em uma nova coluna:

* `qtd_veic_outros_não_dispo`

Após a agregação, as colunas originais foram removidas para evitar redundância.

#### 🔹 Tratamento de Valores Implausíveis

* Valores negativos em `numero_logradouro` foram considerados inválidos e convertidos para `NaN`
* Valores iguais a `0.0` em `latitude` e `longitude` foram tratados como dados ausentes (`NaN`)

#### 🔹 Conversão de Tipos de Dados

A coluna `hora_sinistro` foi convertida para o tipo `datetime.time`, com tratamento robusto para valores inválidos, que foram convertidos para `NaT`.

#### 🔹 Tratamento de Valores Ausentes

Todas as colunas iniciadas por `qtd_` tiveram seus valores ausentes (`NaN`) preenchidos com `0`, assumindo que a ausência de registro representa quantidade nula.

#### 🔹 Verificação Final

Foi realizada uma checagem completa para identificar valores ausentes remanescentes, permitindo decisões adicionais de tratamento, se necessário.

### 💾 Exportação dos Dados

Após o processamento, os dados foram exportados em dois formatos:

* `SINISTRO_limpo.csv` → formato leve e amplamente compatível
* `SINISTRO_limpo.xlsx` → versão em Excel para fácil visualização

---

✨ O resultado é um dataset estruturado, limpo e pronto para análises exploratórias, modelagem e geração de insights.

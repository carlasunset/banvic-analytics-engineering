# 🏦 Banvic Analytics Engineering

Projeto desenvolvido durante a **Formação em Analytics Engineering da Indicium Academy**, utilizando **dbt** e **Databricks** para construir uma camada analítica baseada em modelagem dimensional, seguindo boas práticas de Analytics Engineering.

A estrutura inicial do repositório e os datasets utilizados como *seeds* foram disponibilizados durante a formação. A implementação da camada analítica, incluindo modelagem dos dados, transformações, documentação e testes de qualidade, foi desenvolvida por mim ao longo do curso.

---

# 📖 Contexto

O projeto simula a construção de uma plataforma analítica para uma instituição financeira fictícia chamada **Banvic**.

A partir de dados operacionais disponibilizados como *seeds* no dbt, foi desenvolvida uma camada analítica organizada em diferentes níveis de transformação, permitindo estruturar os dados para consumo analítico utilizando uma arquitetura em camadas.

Durante o desenvolvimento foram aplicados conceitos modernos de **Analytics Engineering**, incluindo modelagem dimensional, documentação, testes automatizados e organização de projetos dbt.

---

# 🎯 Objetivos

- Construir uma arquitetura analítica utilizando dbt;
- Implementar modelos organizados em camadas (*staging*, *intermediate* e *marts*);
- Desenvolver um modelo dimensional para análise das transações;
- Aplicar boas práticas de organização e documentação;
- Implementar testes para garantir a qualidade e integridade dos dados;
- Utilizar Databricks como ambiente de execução.

---

# 🛠 Tecnologias Utilizadas

- dbt Core
- Databricks
- SQL
- YAML
- Git
- GitHub
- dbt Packages

---

# 🏗 Arquitetura do Projeto

O projeto foi desenvolvido seguindo a arquitetura em camadas recomendada pelo dbt.

```text
Seeds
   │
   ▼
Sources
   │
   ▼
Staging
   │
   ▼
Intermediate
   │
   ▼
Marts
   │
   ▼
Camada Analítica
```

Cada camada possui responsabilidades específicas, facilitando manutenção, reutilização dos modelos e evolução do projeto.

---

# 📁 Estrutura do Projeto

```text
.
├── analyses/
├── macros/
│   └── generate_schema_name.sql
│
├── models/
│   ├── staging/
│   │   ├── erp_banvic/
│   │   └── schema/
│   │
│   ├── intermediate/
│   │   └── schema/
│   │
│   └── marts/
│       └── schema/
│
├── seeds/
│   └── banvic/
│
├── snapshots/
├── tests/
│   └── tst_soma_transacoes_2018.sql
│
├── dbt_project.yml
├── packages.yml
└── README.md
```

---

# 🔄 Fluxo ELT

```text
  CSV (Seeds)
      │
      ▼
   dbt seed
      │
      ▼
   Sources
      │
      ▼
   Staging
      │
      ▼
Intermediate
      │
      ▼
    Marts
      │
      ▼
Modelo Dimensional
      │
      ▼
Testes e Documentação
```

---

# 📊 Camadas Implementadas

## 🔹 Staging

A camada **staging** é responsável pela padronização inicial dos dados provenientes das *seeds*.

Nesta etapa foram realizadas transformações para preparar os dados para as próximas camadas, mantendo os modelos simples, reutilizáveis e consistentes.

Modelos implementados:

- Agências
- Clientes
- Colaboradores
- Contas
- Localidades
- Transações

---

## 🔹 Intermediate

A camada **intermediate** concentra as regras de transformação e integração entre diferentes entidades do negócio.

Nessa etapa foram criados modelos intermediários utilizados posteriormente na construção das dimensões e da tabela fato.

Modelos implementados:

- Dimensão Agências
- Dimensão Clientes
- Dimensão Colaboradores
- Dimensão Contas
- Dimensão Datas
- Fato Transações

---

## 🔹 Marts

A camada **marts** disponibiliza os modelos finais para consumo analítico utilizando modelagem dimensional.

Foram desenvolvidas as seguintes tabelas:

### Dimensões

- dim_agencias
- dim_clientes
- dim_colaboradores
- dim_contas
- dim_datas

### Fato

- fct_transacoes

---

# ⭐ Modelo Dimensional

O modelo dimensional foi estruturado utilizando uma tabela fato central relacionada às dimensões de negócio.

```text
             dim_datas
                 │
                 │
dim_clientes ────┤
                 │
dim_contas ──────┤
                 │
dim_agencias ────┤
                 │
dim_colaboradores│
                 │
                 ▼
          fct_transacoes
```

Essa estrutura facilita consultas analíticas, reduz a complexidade das transformações e segue práticas amplamente utilizadas em projetos de Data Warehouse.

---

# ✅ Testes Implementados

Para garantir a qualidade dos dados foram utilizados testes nativos do dbt e testes personalizados.

## Generic Tests

- Relationships
- Accepted Values

Os testes garantem a integridade referencial entre dimensões e tabela fato, além da validação de valores esperados em colunas específicas.

## Singular Test

Foi desenvolvido um teste personalizado para validar a consistência do valor total das transações auditadas de 2018.

```sql
Total esperado:
822.808,44
```

Esse teste garante que os dados transformados permanecem consistentes em relação ao valor de referência disponibilizado.

---

# 📚 Documentação

Os modelos foram documentados utilizando arquivos YAML.

Foram documentados:

- modelos;
- colunas;
- sources;
- descrições das tabelas;
- descrições dos campos.

Além da documentação, também foram implementados testes diretamente na definição dos modelos, aproximando o projeto das boas práticas recomendadas pelo dbt.

---

# 🚀 Aprendizados

Durante o desenvolvimento deste projeto foi possível aplicar na prática conceitos fundamentais de Analytics Engineering, incluindo:

- arquitetura em camadas utilizando dbt;
- modelagem dimensional;
- organização de projetos analíticos;
- documentação de modelos;
- testes automatizados de qualidade dos dados;
- utilização de packages do dbt;
- desenvolvimento em ambiente Databricks;
- versionamento utilizando Git e GitHub.

---

# 👩‍💻 Autora

**Carla Lira Rodrigues**

Analytics Engineering | SQL | dbt | Databricks | Data Modeling

- 💼 LinkedIn: https://www.linkedin.com/in/carla-lira-rodrigues/
- 💻 GitHub: https://github.com/carlasunset

# Students Performance – Data Pipeline (Databricks + PySpark)

Este repositório contém o desenvolvimento completo de um pipeline de dados em nuvem utilizando **Databricks Community Edition**, **PySpark** e **SQL**, com base no dataset público _Students Performance_.  
O objetivo é construir um MVP que envolva: busca e coleta, modelagem, carga, processamento (ETL) e análise dos dados.

---

## Objetivo do Projeto

Identificar quais fatores influenciam o desempenho escolar dos estudantes, analisando notas de matemática, leitura e escrita a partir de características socioeconômicas e pessoais.

### **Perguntas de negócio**
1. Há diferença de desempenho entre gêneros?  
2. A escolaridade dos pais influencia as notas?  
3. Alunos que completaram curso preparatório possuem desempenho melhor?  
4. Existem diferenças de desempenho entre grupos raciais?  
5. Quais variáveis explicam melhor a performance em matemática?  
6. Existem padrões ou correlações entre as três notas (math, reading, writing)?  
7. Há desigualdade consistente entre grupos?

---

## Arquitetura do Pipeline (Bronze → Prata → Ouro)

### **Camada Bronze (Raw)**
1) Upload do dataset original (`StudentsPerformance.csv`) para o Data Bricks  
2) Tabela: `bronze_students`

### **Camada Prata  (Tratado)**
Transformações:
1) renomear colunas  
2) padronizar valores  
3) criar IDs  
4) variáveis dos tipos (inteiro, string)

Tabela: `silver_students_performance`

### **Camada Ouro Layer (Curado e Analítico)**
1) Métricas por gênero  
2) métricas por escolaridade dos pais  
3) Métricas por etnia  
4) médias gerais e estatísticas descritivas  
5) dataset final para análise e visualização  

Tabela: `ouro_performance_insights`

---

## Modelagem Dimensional (Esquema Estrela)

### **Fato: Fato_Performance**
- student_id  
- nota_mat  
- nota_leitutra  
- nota_escrita  

### **Dimensões**
- Estudante  
- Gênero  
- Etnia 
- Educacao_dos_pais  
- Preparacao_Teste  

> O diagrama completo está disponível na pasta `docs/`.

---

## Catálogo de Dados

Documento localizado em: `docs/catalogo_de_dados.md`

Inclui:
- Descrição das variáveis  
- tipo de dado  
- domínios  
- valores mínimos/máximos  
- categorias   

---

## Como Reproduzir no Databricks

### **1. Criar cluster**
- Cluster Mode: Single Node  
- Runtime: Databricks Runtime 13+ (ou versão mais recente)  
- Autoscaling: OFF  
- Termination: 120 min  

### **2. Upload do dataset**
No menu lateral:  
`Data` → `Add Data` → `Upload File`

Caminho final no DBFS:/FileStore/tables/StudentsPerformance.csv

### **Importando notebooks**
Baixe os arquivos da pasta `/notebooks` deste repositório e importe para o Workspace do Databricks.

### **3. Executar na ordem**
1. `01_bronze_ingest.ipynb`  
2. `02_prata_transform.ipynb`  
3. `03_ouro_curated.ipynb`  
4. `04_anal[itico.ipynb`













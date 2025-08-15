# 📊 Análise e Modelagem Preditiva de Evasão de Clientes - Telecom X

## 🧭 1. Introdução
Este projeto tem como objetivo analisar e prever a evasão de clientes (Churn) da empresa fictícia **DeleconX**.  
A evasão de clientes é um dos maiores desafios de empresas de telecomunicações e serviços contínuos, afetando diretamente a receita e a retenção no longo prazo.

A análise utiliza **Python**, **Pandas**, **Scikit-learn** e bibliotecas de visualização para identificar fatores que influenciam o churn e construir modelos preditivos capazes de estimar a probabilidade de um cliente cancelar o serviço.

---

## 🛠️ 2. Pipeline do Projeto
1. **ETL (Extract, Transform, Load)**  
   - Leitura do dataset original (`.json`).
   - Limpeza e tratamento de dados.
   - Criação de novas variáveis.
   - Padronização e conversão de tipos.

2. **Análise Exploratória de Dados (EDA)**  
   - Distribuição do churn.
   - Análises por variáveis categóricas e numéricas.
   - Visualizações com gráficos interativos.

3. **Modelagem Preditiva**  
   - Correlação e seleção de variáveis.
   - Separação em treino e teste.
   - Modelos utilizados: Regressão Logística, Random Forest e Gradient Boosting.
   - Avaliação com métricas: Acurácia, Precisão, Recall e F1-Score.

4. **Interpretação e Conclusão**  
   - Principais fatores de churn identificados.
   - Recomendações estratégicas.

---

## 📥 3. Processo de ETL - Extração, Transformação e Carga de Dados
**Etapas realizadas:**
1. **Extração**: Carregamento do dataset em formato JSON diretamente de URL pública.
2. **Transformação**:
   - Normalização da estrutura.
   - Conversão de tipos de dados (`account_Charges_Total` para `float64`).
   - Padronização de valores categóricos (`Yes/No` → `1/0`).
   - Substituição de valores vazios na coluna `Churn` por `"Nao_informado"`.
   - Criação da coluna `Contas_Diarias` para análise de gastos médios.
3. **Carga**: Armazenamento dos dados tratados para uso na modelagem.

📌 *Tabela exemplo após limpeza:*

| customer_ID | customer_gender | customer_tenure | account_Contract | account_Charges_Total | Churn |
|-------------|----------------|-----------------|------------------|-----------------------|-------|
| 0001        | Male           | 12              | Monthly          | 68.5                  | Yes   |
| 0002        | Female         | 36              | Two year         | 120.4                 | No    |

---

## 📊 4. Análise Exploratória de Dados (EDA)

### 4.1 Distribuição de Churn
- **71,2%** dos clientes permaneceram na empresa.
- **25,7%** cancelaram o serviço.
![Gráfico Distribuição de Churn]([imagens/churn_distribution.png](https://github.com/BrunoRomeu/TelecomX-An-lise-de-Churn-e-Modelagem-Preditiva/blob/main/TelecomX_assets/Distribui%C3%A7%C3%A3o%20de%20Churn.png))

### 4.2 Gênero (customer_gender)
- Diferença irrelevante na taxa de churn entre gêneros.

### 3.3 Tipo de Contrato (account_Contract)
- Contratos **mensais** apresentam maior evasão.
- Contratos **anuais/bianuais** mostram maior fidelização.
![Gráfico Contrato vs Churn](imagens/contract_churn.png)

### 4.4 Método de Pagamento (account_PaymentMethod)
- Pagamento eletrônico automático apresentou taxas mais altas de churn.

### 4.5 Tempo de Permanência (customer_tenure)
- Clientes com **menos de 10 meses** apresentam maior probabilidade de cancelamento.
![Gráfico Tenure vs Churn](imagens/tenure_churn.png)

### 4.6 Total de Gastos (account_Charges_Total)
- Clientes com **gastos mais baixos** tendem a cancelar com mais frequência.
![Gráfico Gastos vs Churn](imagens/spend_churn.png)

---

## 🤖 5. Modelagem Preditiva

### 5.1 Seleção de Variáveis
- Foram selecionadas variáveis relevantes com base em **correlação** e importância para o modelo:
  - `customer_tenure`
  - `account_Contract`
  - `account_PaymentMethod`
  - `account_Charges_Total`
  - `Contas_Diarias`

### 5.2 Modelos Utilizados
1. **Logistic Regression**
2. **Random Forest Classifier**
3. **Gradient Boosting Classifier**

📌 *Tabela de desempenho:*

| Modelo                     | Acurácia | Precisão | Recall | F1-Score |
|----------------------------|----------|----------|--------|----------|
| Logistic Regression        | 0.82     | 0.78     | 0.70   | 0.74     |
| Random Forest Classifier   | 0.88     | 0.85     | 0.82   | 0.83     |
| Gradient Boosting          | 0.90     | 0.88     | 0.84   | 0.86     |

### 5.3 Interpretação
- **Gradient Boosting** foi o modelo com melhor desempenho, com maior equilíbrio entre precisão e recall.
- Variáveis mais influentes:
  1. Tempo de permanência (`customer_tenure`)
  2. Tipo de contrato (`account_Contract`)
  3. Total de gastos (`account_Charges_Total`)

---

## ✅ 6. Conclusões
- Contratos **curtos** e **pagamentos automáticos** estão mais associados à evasão.
- Clientes **novos** e com **gastos menores** são mais propensos a cancelar.
- Modelos preditivos atingiram bons níveis de acurácia, permitindo ações preventivas.

---

## 💡 7. Recomendações
1. Incentivar contratos anuais ou bianuais com benefícios extras.
2. Criar programas de **onboarding** e suporte especial para clientes novos (0–6 meses).
3. Monitorar clientes com **baixa média de gastos** e contratos mensais.
4. Revisar experiência de clientes que usam **pagamento eletrônico automático**.
5. Utilizar o modelo de **Gradient Boosting** para prever churn e aplicar estratégias personalizadas.

---

## 🚀 8. Tecnologias Utilizadas
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

---

## 📌 9. Execução
Para rodar este projeto no Google Colab:
1. Fazer upload do `.ipynb`.
2. Garantir que o dataset esteja no caminho correto.
3. Executar célula por célula.

---

---
## 📚 10. Reprodutibilidade & Contribuição

Contribuições, issues e PRs são bem-vindos — siga o padrão:

1. Fork → branch feature → PR.
2. Documente mudanças no `CHANGELOG.md` (se aplicável).
3. Para dados sensíveis, use `.env` e nunca comite credenciais.

---

## 🧾 11. Licença

**Creative Commons BY-NC-SA 4.0** — ver `LICENSE` para detalhes.

---

## ✉️ 12. Autor & Contato

**Autor:** Bruno Romeu  
**Contato:** [LinkedIn](https://www.linkedin.com/in/bruno-celestino-romeu/) | [GitHub](https://github.com/BrunoRomeu)  
**Licença:** Creative Commons BY-NC-SA 4.0  

> "Dados são apenas números até que sejam transformados em decisões" - Adaptado de W. Edwards Deming

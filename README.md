# Manutenção Preditiva Industrial com Machine Learning

**Dataset:** [AI4I 2020 Predictive Maintenance (UCI)](https://archive.ics.uci.edu/ml/datasets/AI4I+2020+Predictive+Maintenance+Dataset)

## Sobre o Projeto
Este projeto explora a aplicação de técnicas de Machine Learning para prever falhas em equipamentos industriais utilizando dados reais (Gêmeo Digital). Diferente de simulações ideais, enfrentamos aqui os desafios do mundo real: dados ruidosos e, principalmente, **desbalanceamento de classes** (apenas ~3% de falhas).

## Objetivo de Negócio
O objetivo não é apenas ter uma acurácia alta, mas evitar paradas não planejadas. Na indústria, deixar uma máquina quebrar (Falso Negativo) é muito mais custoso do que realizar uma inspeção preventiva desnecessária (Falso Positivo). O foco deste projeto foi otimizar o **Recall** (Capacidade de Detecção).

## Tecnologias Utilizadas
* **Linguagem:** Python
* **Análise de Dados:** Pandas, Numpy
* **Visualização:** Seaborn, Matplotlib
* **Machine Learning:** Scikit-Learn (Random Forest)
* **Tratamento de Desbalanceamento:** Imbalanced-Learn (SMOTE)

## Metodologia e Resultados

O projeto foi dividido em duas fases para demonstrar o impacto do tratamento de dados:

### Fase 1: Modelo com Dados Originais (Desbalanceados)
* **Acurácia:** 98% (Enganosa!)
* **Recall (Detecção de Falhas):** **0.40**
* **Diagnóstico:** O modelo era extremamente conservador. Deixava passar 60% das falhas reais, tornando-o pouco útil para proteção de ativos críticos.

### Fase 2: Aplicação de SMOTE (Synthetic Minority Over-sampling Technique)
Aplicamos o SMOTE para gerar dados sintéticos da classe de falha no conjunto de treino, equilibrando o aprendizado do algoritmo.

* **Acurácia:** 96%
* **Recall (Detecção de Falhas):** **0.66** 
* **Conclusão:** Aceitamos uma leve queda na precisão (mais alertas preventivos) em troca de um aumento significativo na segurança operacional, detectando 66% das falhas contra apenas 40% anteriormente.

## Insights de Engenharia (A Física por trás dos Dados)
A análise de *Feature Importance* revelou que o modelo aprendeu sozinho conceitos fundamentais de mecânica. As variáveis mais importantes para a decisão foram:
1.  **Rotação [rpm]**
2.  **Torque [Nm]**

Isso valida a relação física de Potência ($P = \tau \cdot \omega$). O algoritmo identificou que a quebra da correlação padrão entre Torque e Rotação é o maior indicativo de falha iminente, seguido pelo **Desgaste da Ferramenta (Tool Wear)**.

---

*Desenvolvido por Davi Cucco | [LinkedIn](https://www.linkedin.com/in/davi-duarte-cucco-8b272a238/)*

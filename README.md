# Trabalho Prático: Estatística e Probabilidade Aplicada à Astronomia

**Alunos:** Cláudio Lozeá Feijó Soares  
**Docentes:** Sérgio Monteiro, D.Sc. e Manuel Martins, D.Sc.  
**Instituição:** UNICARIOCA - Pós-Graduação em Ciência de Dados  


---


## 1.  Enunciado do Problema: Calibração de Brilho em Estrelas Variáveis

Em astronomia, a medição do brilho de astros (magnitude aparente) é frequentemente afetada por ruídos instrumentais e atmosféricos. Imagine que uma equipe de astrofísicos está monitorando uma estrela específica e sabe que, devido às propriedades físicas do astro, as medições de brilho tendem a seguir uma Distribuição Gaussiana (Normal) em torno de um valor central (μ), com uma variabilidade inerente (σ).

**O Problema**: O objetivo é simular um conjunto de 1.000 observações de brilho para esta estrela, realizar uma análise de inferência para estimar se a média observada condiz com o valor teórico esperado e identificar possíveis anomalias nos dados captados.

---

## 2. Objetivos

O desenvolvimento do código e da análise estatística foi dividido em quatro etapas fundamentais:

1. **Simulação de Dados:** : Gerar um vetor de 1.000 observações utilizando a função rnorm(), configurando uma média de brilho específica e um desvio padrão que represente o ruído do telescópio.


2. **Análise Descritiva e Visualização:** Criar um histograma das medições sobreposto por uma curva de densidade teórica para verificar visualmente a aderência à distribuição normal. Utilizar pacotes como ggplot2 para garantir a qualidade visual.


3. **Inferência Estatística:** Implementar o cálculo de um Intervalo de Confiança (IC) de 95% para a média do brilho da estrela e realizar um Teste de Hipótese (Z-test ou T-test) para verificar se a média amostral difere significativamente de um valor padrão pré-estabelecido.


4. **Diagnóstico de Outliers:** Utilizar boxplots ou regras de desvios padrão para identificar e destacar medições que fogem do esperado (possíveis falhas instrumentais), quantificando o impacto dessas medidas na estimativa final.

---

## 3. Conclusão dos Resultados Obtidos

Após a execução da simulação e dos cálculos analíticos no R, chegamos às seguintes conclusões estatísticas:

### 3.1. Inferência e Teste de Hipótese
A partir dos dados simulados, o Teste de Hipótese gerou um *Z-score* de **-0,8169** e um *p-valor* aproximado de **0,414**.

* **Conclusão:** Como o *Z-score* está contido na zona segura do nível de confiança de 95% (entre -1,96 e +1,96) e o *p-valor* é confortavelmente maior que o nível de significância de 0,05, **não rejeitamos a hipótese nula**.

* **Impacto Prático:** Isso significa que não há diferença estatisticamente significativa entre a média simulada nos nossos dados e o valor teórico original ($\mu=15.5$). A pequena flutuação observada se deve estritamente à variabilidade aleatória e aos ruídos instrumentais esperados para a medição do telescópio, não caracterizando uma alteração no comportamento real da estrela.

### 3.2. Diagnóstico e Impacto dos Outliers
Utilizando o critério matemático da Amplitude Interquartílica (IQR), mapeado graficamente pelo *Boxplot*, o diagnóstico revelou a presença de **11 outliers** (medições atípicas que representam falhas pontuais) no conjunto de 1.000 observações.

Para **quantificar o impacto** desses valores discrepantes, as estimativas amostrais foram comparadas antes e após a remoção dos outliers:

* **Efeito na Dispersão (Ruído):** Os outliers estavam inflando artificialmente o erro de medição do telescópio. Com a sua remoção, o desvio padrão caiu de **0.802 para 0.764**, e a amplitude de variação superior encolheu de **18.30 para 17.60**.


* **Efeito na Tendência Central:** A **Mediana** provou ser uma estatística robusta, mantendo-se inalterada em **15.49** antes e após a limpeza dos dados. A **Média Aritmética** final (15.48) também não sofreu distorção significativa.


* **Conclusão Geral:** O fato da média continuar praticamente igual à mediana demonstra que a distribuição dos erros do telescópio foi simétrica (ocorrendo falhas tanto em brilhos muito altos quanto muito baixos). O principal benefício da limpeza dos dados foi garantir o isolamento adequado do ruído e o estreitamento da dispersão em torno da magnitude natural observada da estrela.

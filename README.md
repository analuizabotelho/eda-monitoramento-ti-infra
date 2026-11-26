# Monitoramento de infraestrutura de TI: a CPU explica a latência?

Análise exploratória de 500 registros de monitoramento de servidores (latência, uso de CPU e uso de memória) para responder a uma pergunta de negócio: **vale investir em mais hardware para reduzir a latência?**

Projeto individual da disciplina Exploratory Data Analysis (Prof. Kyung Moo Kim), Unimpacta.

## Dados
- Base `monitoramento_ti_infra.csv`, fornecida pelo professor da disciplina.
- 500 registros com latência (ms), uso de CPU (%), uso de memória (GB), tipo de serviço (`database`, `api_gateway` e `web_server`), servidor e código de status.
- Sem valores ausentes e sem registros duplicados.

## O que foi feito
1. Limpeza e preparação dos dados.
2. Estatística descritiva (média, mediana, desvio padrão, mínimo e máximo) para latência, CPU e memória.
3. Visualizações: histograma da latência, boxplots de CPU e memória por tipo de serviço e heatmap de correlação.
4. Conclusão voltada para o negócio.

## Principais achados
- **Latência:** média de cerca de 50 ms, com distribuição próxima do formato normal (em sino) e sem grande assimetria.
- **CPU por serviço:** a mediana de uso de CPU cresce do `database` para o `api_gateway` e o `web_server`, que é o mais alto dos três.
- **Outliers:** nenhum grupo apresentou pontos fora dos limites nos boxplots de CPU e memória.
- **Correlação:** CPU x latência ≈ 0,00 e memória x latência = 0,02. Não há relação relevante entre o uso de CPU ou memória e a latência.

## Conclusão para o negócio
Nestes dados, não há motivo para comprar mais servidores ou fazer upgrade de CPU agora, já que a CPU não explica a latência. O `web_server` merece acompanhamento por ter o uso de CPU mais alto e poder virar gargalo se a demanda crescer. Antes de investir em hardware, a recomendação é investigar outras causas de lentidão, como rede, banco de dados ou a própria aplicação.

## Limitações
- Análise exploratória: correlação baixa não exclui relações não lineares nem causas que não estão na base (rede, banco, aplicação).
- Apenas 500 registros e três métricas.

## Arquivos
- `monitoramento_ti_eda.ipynb`: notebook com a análise (Python, Pandas, NumPy, Matplotlib e Seaborn)

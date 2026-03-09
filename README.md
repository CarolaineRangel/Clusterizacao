🎯 Objetivo
Este projeto visa identificar grupos de clientes com características semelhantes por meio da técnica de clusterização K-Prototypes, permitindo uma segmentação mais inteligente da base de clientes ativos. O objetivo é gerar insights que apoiem decisões estratégicas de engajamento, retenção e personalização de atendimento.

Código

⚙️ Etapas do Processo
1. Coleta e Preparação dos Dados
Os dados foram extraídos do BigQuery e processados para garantir consistência e qualidade.

Etapas realizadas:

Correção de tipos e formatos.

Tratamento de valores ausentes.

Conversão de variáveis categóricas para formatos apropriados ao modelo.

2. Clusterização com K-Prototypes
Utilizou-se o algoritmo K-Prototypes, adequado para bases com variáveis mistas (numéricas e categóricas).

Foi definido um número fixo de 4 clusters, com base em testes exploratórios e análise de coerência dos agrupamentos.

Os rótulos dos clusters foram adicionados ao DataFrame original.

3. Análise dos Clusters
Foram calculadas estatísticas descritivas (médias e frequências) por cluster.

Geração de gráficos:

Gráficos de dispersão (ex: faturamento vs. tempo de vida).

Radar plot (gráfico de aranha) para comparar o perfil médio dos clusters em múltiplas variáveis.

Gráfico 3D com Plotly, combinando ‘faixa_faturamento’, ‘tempo de vida’ e ‘has_nitro’.

🧠 Método K-Prototypes – Explicação
O K-Prototypes é uma extensão dos algoritmos:

K-Means (para variáveis numéricas).

K-Modes (para variáveis categóricas).

Ele permite calcular uma distância mista:

Numéricas: distância euclidiana.

Categóricas: número de categorias diferentes (dissimilaridade).

Um fator de peso γ equilibra a influência entre os dois tipos.

✅ Vantagens:
Suporte a dados mistos.

Fácil implementação via kmodes em Python.

⚠️ Limitações:
Requer definição prévia de K.

Sensível à escala dos dados numéricos (normalização recomendada).

📌 Resultados
O gráfico apresenta a distribuição de clientes ativos segmentados por clusters, com base em duas variáveis principais:

Eixo X: Faixa de faturamento mensal.

Eixo Y: Tempo de vida do cliente (em meses).

Cores: Representam os clusters identificados.

image-20250411-182739.png
🟪 Cluster 0 – Pequenas empresas heterogêneas
Faturamento até 30k (incluindo "sem vendas").

Variação ampla de tempo de vida (até >80 meses).

Representa um perfil mais heterogêneo de pequenas empresas ou em estágio inicial.

🟡 Cluster 3 – Empresas em crescimento
Faturamento entre 30k e 100k.

Tempo de vida mais longo (>40 meses).

Indica empresas médias, mais consolidadas e engajadas.

🟢 Cluster 2 – Grandes e maduras
Faturamento entre 100k e 250k.

Forte uso da plataforma e presença funcional.

Tempo de vida entre 10 e 50 meses.

Perfil de empresas grandes, já integradas ao ecossistema.

🔵 Cluster 1 – Estratégicos em início de jornada
Faturamento acima de 250k.

Baixo tempo de vida (clientes mais recentes).

Forte presença de funcionalidades tecnológicas.

Indica clientes estratégicos com alto potencial, mas ainda em fase de adaptação.

 

🕸️ Radar Plot – Perfil Funcional dos Clusters
O gráfico abaixo é um Radar Plot (ou gráfico de aranha) que apresenta um retrato mais detalhado dos 4 clusters de clientes ativos identificados via K-Prototypes. Cada linha colorida representa a média normalizada das variáveis para os clientes de cada cluster.

image-20250411-183409.png
🟪 Cluster 0:
Alta demanda por suporte (tickets).

Baixo uso de funcionalidades como pix, KDS, integração com pagamentos.

Perfil mais básico e reativo com alta demanda de suporte.

image-20250411-183555.png
 

🔵 Cluster 1:
Destaque em uso de tecnologias avançadas (zapiturbo, chatbot, whatsapp bot).

Alta presença de funcionalidades mais avançadas, mas com menor engajamento em tempo de vida e pedidos.

Pode representar clientes tecnologicamente sofisticados, porém ainda com 

image-20250411-183624.png
 

🟢 Cluster 2:
Altos valores em quase todas as variáveis.

Clientes mais engajados, com uso amplo de recursos da plataforma (fiscal, emissão, pagamentos).

Perfil de cliente maduro, engajado e com forte ativação funcional — provavelmente empresas grandes ou bem integradas à plataform

image-20250411-183642.png
 

🟡 Cluster 3:
Forte ativação nos primeiros dias (onboarding).

Uso de vendas online e meios de pagamento modernos.

Potencial para engajamento, mas ainda em fase inicial.

image-20250411-183649.png
✅ Conclusões
A clusterização revelou perfis distintos de clientes ativos, permitindo uma segmentação estratégica.

A faixa de faturamento, tempo de vida e uso de funcionalidades foram os principais eixos de diferenciação.

Clientes com maior engajamento funcional e tempo de vida tendem a estar nos clusters 2 e 3.

Clusters 0 e 1 podem demandar ações específicas de engajamento ou suporte, por estarem em fases iniciais ou apresentarem baixa ativação.

🚀 Próximos Passos
Aprofundar a análise temporal:

Verificar evolução de métricas por cluster ao longo do tempo.

Analisar transição de clientes entre clusters.

Conectar com métricas de churn e retenção:

Avaliar quais clusters têm maior risco de churn.

Integrar com modelos de previsão de cancelamento.

Aplicar modelo em clientes novos:

Usar os centróides dos clusters como referência para classificar novos clientes e prever comportamentos esperados.


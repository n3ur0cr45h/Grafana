<div align="Center"> 
<br>

<h4>

░██████╗░██████╗░░█████╗░███████╗░█████╗░███╗░░██╗░█████╗░
██╔════╝░██╔══██╗██╔══██╗██╔════╝██╔══██╗████╗░██║██╔══██╗
██║░░██╗░██████╔╝███████║█████╗░░███████║██╔██╗██║███████║
██║░░╚██╗██╔══██╗██╔══██║██╔══╝░░██╔══██║██║╚████║██╔══██║
╚██████╔╝██║░░██║██║░░██║██║░░░░░██║░░██║██║░╚███║██║░░██║
░╚═════╝░╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░░░░╚═╝░░╚═╝╚═╝░░╚══╝╚═╝░░╚═╝
</h4>
</div>

----
  
<details>
  <summary><b> 1. Fundamentos</b></summary>
<div align="Left">  
<br>  
    
  G1.1 - O que é o Grafana?  
  > - Grafana é uma plataforma de observabilidade e visualização de Dados;  
  > - Permite:  
  >   - Criação de gráficos, tabelas e painéis personalizados;  
  >   - Conexão com diversas fontes de dados (Como Prometheus, ElasticSearch, InfluxDB, CloudWatch, Azure Monitor...);  
  >   - Configuração de alertas e notificações em canais (Microsoft Teams, e-mail, etc...);    
  >   - Suporte a métricas, logs e traces / rastreios.
  
  G1.2 - Componentes da Arquitetura Básica do Grafana
  >  - Os principais componenetes de uma arquitetura básica do Grafana, são:
  >    - Data Sources: Fontes de Dados de onde o Grafana busca os dados para exibição;
  >    - Dashboards: Painéis personalizados com gráficos, tabelas, gauges, heatmaps, etc;
  >    - Alerting: Sistema de alertas baseado em condições configuradas; 
  >    - Users & Permissions: Controle de acesso; 
  >    - Plugins: Para novas fontes de dados, visualizações personalizadas, painéis prontos da comunidade.
  >
  >  - Resumidamente: Fontes de Dados -> Servidor Grafana -> Dashboards + Alerting + API

 G1.3 - Grafana Open Source, Enterprise e Cloud 
  > | Tipo        | Recursos                                                  |
  > |-------------|-----------------------------------------------------------|
  > | Open Source | Gratuito, Recursos Básicos de Visualização e Alertas      |
  > | Enterprise  | Suporte Oficial, Recursos de Segurança Avançada, Auditoria, Gestão empresarial de Usuários, Integrações Premium |
  > | Cloud       | SaaS, Hospedagem de Dashes, Coleta e Armazenamento de Métricas, Logs e Traces, Inclui Stack Completa            |

 G1.4 - Stack LGTM: Loki, Grafana, Tempo, Mimir 
  > - Conjunto de Ferramentas Open Source criadas e mantidas pela Grafana Labs;
  > - Voltadas para Observabilidade Completa - Logs, Métricas e Rastreios.
  >    
  > | Ferramenta  | Função                                                         |
  > |-------------|----------------------------------------------------------------|
  > | Loki        | Armazenamento e Consulta de Logs                               |
  > | Grafana     | Interface central para visualizar métricas, logs e raastreios  | 
  > | Tempo       | Armazena e consulta rastreios distribuídos                     |
  > | Mimir       | Backend escalável para métricas (Pode substituir o Prometheus) |
  >
  > - LGTM é uma stack de observabilidade moderna, com foco em leveza, performance e integração fácil;
  > - Normalmente usada junto de microsserviços, Kubernetes, etc.

 G1.5 - Métricas e Séries Temporais 
  > - Métricas são valores números que representam o comportamento ou estado de um sistema ao longo do tempo;
  > - As métricas são usadas para monitorar, visualizar e alertar sobre a saúde e o desempenho de sistemas.  
  > - Exemplo de Métricas:
  >   - Uso de CPU de um Servidor;
  >   - Quantidade de Requisições HTTP por Segundo;
  >   - Tempo de resposta de uma API;
  >   - Número de erros registrados.
  >  
  > - Séries Temporais são sequências de dados onde cada ponto é um par (timestamp, valor);
  > - Para cada métrica, temos uma série de valores medidos ao longo do tempo.

G1.6 - Conceitos Básicos: Labels, Jobs, Targets
  > - "Labels" são pares "chave-valor", que descrevem a origem ou contexto de uma métrica:
  >   - Exemplo: http_requests_total{method="GET", status="200", job="api-server"}
  > - "Job" é um labem usado para identificar qual serviço ou componente está sendo monitorado:
  >   - Exemplo: job="database"
  > - "Target" é uma instância específica de onde as métricas estão sendo coletadas;
  > - Pode ser um host ou endpoint
  > - Cada job pode ter vários targets.

G1.7 - Exporters 
  > - Exporters são aplicações intermediárias que exponibilizam métricas de sistemas, serviçous ou hardwares;
  > - As métricas são expostas ao Prometheus, num formato que ele consegue entender e coletar.
  > - Fluxo de Monitoramento:
  >   - Exporters expõem as métricas de serviços / sistemas em um endpoint HTTP;
  >   - Prometheus coleta / faz scraping desses endpoints periodicamente;
  >   - As métricas são armazenadas internamente no Prometheus;
  >   - Grafana se conecta ao Prometheus como Fonte de Dados, e cria painéis em cima disso.

G1.8 - Data Sources | Fontes de Dados
  > - Sistemas externos de onde o Grafana obtém os dados para visualização;
  > - Ao invés do Grafana armazenar esses dados, ele atua como Interface: Consultando e Exibindo os Resultados;
  > - É necessário informar a URL do serviço, o tipo de fonte, e credenciais (Se necessário);
  > - Cada painel pode usar uma ou mais fontes de dados para exibição de informações.
  > - Tipos mais comuns de Data Sources:
  >   - Prometheus (Métricas);
  >   - Grafana Mimir (Métricas em Larga Escala);
  >   - Loki (Logs);
  >   - Tempo (Traces / Rastreamento Distribuído).

</div> 
</details>

----

<details>
  <summary><b> 2. Intermediário</b></summary>
<div align="Left">  
<br>  

  G2.1 - Scrape (Prometheus)
  > - Processo onde o Prometheus puxa as métricas expostas por serviços (targets), via HTTP;
  > - Os serviços precisam expor suas métricas em um endpoint HTTP, geralmente /metrics.
  >   - O Prometheus possui um arquivo de configuração - prometheus.yml;
  >   - Nesse arquivo, definimos os "targets" e o intervalo de scrape;
  >   - Cada coleta é armazenada com um timestamp e labels, formando séries temporais.   

  G2.2 - Armazenamento Local de Métricas e Retenção (Prometheus)
  > - Prometheus armazena os dados coletados em Disco, usando o formato TSDB - Time Series Database;
  > - Cada métrica é armazenada como uma série tempora, com valores associados a timestamps e labels.
  > - Por padrão, o Prometheus mantém as métricas por 15 dias, mas é customizável;
  >   - Como o armazenamento do Prometheus é local, a retenção de longo prazo não é indicada;
  >   - Para isso, existem existem algumas opções para ambientes distribuídos e backends de longo prazo:
  >     - Thanos;
  >     - Cortex;
  >     - VictoriaMetrics;
  >     - Mimir.  

 G2.3 - PromQL 
  > - Prometheus Query Language é a linguagem de consulta do Prometheus;
  > - Usada para:
  >   - Buscar séries temporais;
  >   - Agregar dados (sum, avg, max, etc.);
  >   - Filtrar métricas por labels;
  >   - Criar expressões derivadas.
  > - O Grafana usa o PromQL para consultar dados do Prometheus;
  >   - Quando é criado um painel no Grafana com o Prometheus como fonte de dados, você escreve consultas em PromQL nos painéis;
  >   - Grafana não processa dados, ele envia apenas a consulta ao Prometheus e renderiza o resultado.

 G2.4 - Alloy
  > - Agente unificado de Observabilidade;
  > - Coleta os dados de telemetria (logs, métricas e traces) - centralizando tudo em apenas 1 agente;
  > - Simplifca a coleta, realiza transformação e encaminha os dados aos backends: Mimir, Loki e Tempo.
  > - Principais Funções:
  >   - Scrape de Métricas - como Prometheus;
  >   - Colega de Logs - como Promtail;
  >   - Coleta de Traces - como OTEL Collector;
  >   - Aplica transformações e Roteamento de Dados;
  >   - Envia os dados para Diferentes Destinos.
  > - Usa linguagem YAML ou Flow (mais modular).

 G2.5 - Mimir
  > - Time-Series Database (TSDB), distrbuído e altamente escalável - comppatível com Prometheus.
  > - Características: 
  >   - Recebe métricas via remote_write;
  >   - Armazena grandes volumes de dados com alta retenção;
  >   - Permite consultas rápidas e em larga escala;
  >   - Suporta múltiplos tenants (multiusuário).
  > - Evolução do "Cortex".
  >   
  > - Foi projetado com uma arquitetura baseada em microsserviços;
  > - Permite escalar horizontalmente cada parte da pipeline de ingestão e consulta;
  > - Componentes escaláveis:
  >   - Distributors: Recebem as métricas via remote_write;
  >   - Ingesters: Processam e armazenam os dados;
  >   - Querier / Query Frontend: Tratam as requisições PromQL;
  >   - Store Gateway: Lida com acesso ao armazenamento de longo prazo (ex: S3, GCS);
  >   - Compactor: Otimiza chunks e reduz redundância.
  >     
  > - O Mimir distribui o trabalho em vários nós (instâncias), que desempenham funções específicas;
  > - Usa técnicas como "consistent hashing" para espalhar séries temporais entre vários ingesters;
  > - Assim, mantém a disponibilidade e balanceamento de carga.
  >   
  > - Shards
  >   - Cada série temporal é shardeada (dividida) com base em uma hash key derivada dos labels;
  >   - Isso garante que diferente séries vão para diferentes ingesters (Evita gargalos e permite paralelismo de escrita / leitura);
  >   - Querier também shardeia as queries, enviando partes da consulta para múltiplos nós ao mesmo tempo.
  >
  > - Chunks
  >   - Métricas no Mimir são armazenadas em Chunks: pedaços compactos de séries temporais que agrupam valores e timestamps juntos;
  >   - Exemplo: um chunk pode conter as amostras de uma métrica a cada 15s por 2 horas.
  >   - O armazenamento deles pode ser:
  >     - Temporariamente na memória dos ingesters;
  >     - Persistidos no Object Storage: (ex: S3, GCS), para retenção de longo prazo.
  >   - Chunking reduz o uso de disco e melhora o desempenho de leitura.

 G2.6 - Loki | Logs Estruturados 
  > - Loki é a solução de gerenciamento de logs do Grafana;
  > - Se rtrata de um sistema de agregação de logs, escalável e otimizado;
  > - Foi projetado para armazenar logs em forma de logs estruturados - facilita a busca e análise.
  >   - Logs Estruturados são entradas de log que possuem formato específico e padronizado - como JSON;
  >   - A estruturação contêm campos predefinidos, como testamps, níveis de log, IDs de correlação, mensagem, etc.
  > - Após coletar e armazenar logs, o Grafana pode visualizá-los, com queries semelhantes a BDs - usando LogQL;
  > - É possível criar dashboards no Grafana para exibir os logs;
  > - Em relação a alertas, o Grafana permite configuração para disparo de notificações, em casos de logs específicos.

 G2.7 - Tempo | Tracing Distribuído 
  > - Serve para rastrear o fluxo de uma requisição em sistemas distribuídos;
  > - Permite analisar a requisição em diferentes serviços e componentes da arquitetura;
  > - Nisso, temos o mapeamento do caminho, para cada requisição, com detalhes de tempo, falhas, e interação;
  >   - Cada requisição é tratada como "trace", e é subdividido em "spans", representando cada parte por onde passou;
  >   - Os spans possuem informações como tempo de execução, status, e outros detalhes.    

 G2.8 - Painéis 
  > - Unidades de visualização de dados;
  > - Cada painel mostra um gráfico, tabela, status de métrica, ou outra forma de visualização.
  > - Tipos de Painéis:
  >   - Gráficos de Linhas (Time Series): Ideal para visualização de métricas ao longo do tempo;
  >   - Gráficos de Barras: Para comparações diretas entre diferentes métricas ou instâncias;
  >   - Gráficos de Área: Para mostrar a magnitude de uma métrica ao longo do tempo;
  >   - Tabelas: Dados em formato tabular;
  >   - Indicadores (Single Stat / Stat): Valor numérico grande, como taxa de erro, latência média, etc;
  >   - Discos (Gauge): Valores de métricas em intervalos de referência;
  >   - Heatmaps: Distribuição de dados em uma grade de coler, com base na intensidade de uma métrica.

 G2.9 - Variáveis
  > - As variáveis permitem tornar os painéis mais dinâmicos, interativos e também criar templates;
  > - São parâmetros que podem ser usados em consultas para filtrar ou ajustar dados nos painéis;
  > - Extremamente útil quando deseja criar um painel genérico, para ser utilizado em várias instâncias sem duplicar configurações.
  > - As variáveis podem funcionar de 3 maneiras:
  >   - Datasource (Fonte de Dados);
  >   - Consultas;
  >   - Interatividade.
  > - Então, para um painel, nós escolhemos o data source, e qual query será usada para puxar os dados. 

 G2.10 - Alertas e Notificações
  > - Alertas baseados em métricas, são configurações para monitoramento em tempo real;
  > - Definimos uma condição de alerta para monitorar métricas específicas de fontes de dados;
  > - Assim, há o disparo de notificações quando essas condições são atendidas.
  >   - Para alertas, é necessário definir um threshold (limiar), que será o valor de referência;
  >   - Quando a métrica monitorada atinge ou ultrapassa esse valor, o alerta é acionado.
  >   - Também é importante definir uma condição de alerta, que envolve comparação entre valores ou comportamento temporal;
  >   - As condições podem ser valores estáticos ou valores dinâmicos - como média, máximo, mínimo, desvio, etc.
  >   - Tipos de condições:
  >     - Trigger (Disparo): Último Valor, Média de Intervalo ou Percentis.
  >     - State (Estado): Ok, Alerta ou No Data.
  > - O Grafana possui opção de enviar notificações por meio de canais externos - os mais comuns:
  >   - E-mail;
  >   - Slack;
  >   - Webhook;
  >   - Teams;
  >   - SMS;
  >   - Entre outros.      

</div> 
</details>

----

<details>
  <summary><b> 3. Avançado</b></summary>
<div align="Left">  
<br>  

G3.1 - Fluxo de Dados 
  
  > | Processo | Ferramenta  | Função                                           |
  > |----------|-------------|--------------------------------------------------|
  > | 1        | Alloy       | Coleta de Logs, Métricas e Traces                |
  > | 2        | Mimir, Loki e Tempo | Armazena o respectivo dado               |
  > | 3        | Grafa       | Consulta usando PromQL, LogQL e TraceQL          |

G3.2 - Sistemas Escaláveis | Sistemas Distribuídos
  > - Sistemas Escaláveis: conseguem aumentar a sua própria capacidade conforme demanada;
  > - Sistemas Distribuídos: são compostos por múltiplos nós, para execução de tarefas, como se fosse apenas um.

G3.3 - Modelos de Multi-Cluster (Observabilidade Federada)
  > - Coleta Centralizada: Vários Clusters enviam métricas | Logs| Traces para um Mimir | Loki | Tempo central;
  > - Agregação Federada: Cada Cluster roda sua própria instância local do Mimir | Loki | Tempo - Um Grafana global é usado para todos.
  > - Benefícios:
  >   - Resiliência Regional;
  >   - Escalabilidade Global;
  >   - Isolamento de ruído e limites por Tenant.       

G3.4 - Conceitos Gerais de Performance | Otimização
  > - Em sistemas de observabilidade, existem três pilares para performance e otimização:
  >   - Latência: Tempo de resposta das consultas;
  >   - Custo | Armazenamento: Volume de dados retidos e custo de operação;
  >   - Escalabilidade: Capacidade de crescer horizontalmente conforme volume de dados.
  > - A performance depende dos hábitos de coleta, retenção e modelagem de dados.
  >
  > - Boas Práticas de Retenção e Armazenamento
  >   - A retenção deve equilibrar custo x necessidade de análise histórica;
  >     - Métricas: 15 - 90 dias;
  >     - Logs: 7 - 30 Dias;
  >     - Traces: 7 - 14 Dias.
  > - Usar Object Storage (S3, GCS, Azure Blob) para dados frios;
  > - Compactar e deduplicar blocos periodicamente;
  > - Configurar retenções diferentes por tenant, namespace ou tipo de métrica.         

G3.5 - Redução de Cardinalidade de Métricas
  > - Cadinalidade é o número de combinações únicas de labels (chaves + valores), em séries temporais;
  > - Alta cardinalidade = explosão de memória, CPU e Armazenamento.
  > - Práticas para redução de Cardinalidade:
  >   - Evitar Labels Dinâmicos: Não usar IDs únicos, timestamps ou hashes como labels;
  >   - Usar Labels Fixos e Agregadores: Agrupar por Recursos Estáveis (Serviço, Região, Pod);
  >   - Agrupar Métricas: Preferência de uma métrica com label "type", ao invés de várias diferentes;
  >   - Usar Histogram e Summary com Moderação: Criam séries internas (Buckets) - evitar o excesso de buckets;
  >   - Downsampling e Rollups: Agregar métricas antigas para reduzir volume.  

</div> 
</details>

----

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

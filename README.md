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
  
  G1.2 - O que é a stack "LGTM" / Stack do Grafana?  
  >  - Pelo Grafana Labs, o conjunto oficial de ferramentas usadas recomendado pelo Grafana se chama "LGTM":
  >    - Loki: Sistema de logs;  
  >    - Grafana: Visualização e dashboards;  
  >    - Tempo: Rastreamento Distribuído - Compatível com OpenTelemetry;  
  >    - Mimir: Armazenamento escalável de métricas Prometheus.   
  >      - Adições:
  >        - Prometheus: Coleta de métricas PromQL;
  >        - Alloy: Coleta métricas, logs e traces, e envia ao Loki, Mimir ou Tempo;
  >        - Grafana Cloud: Versão SaaS da Stack, sem precisar gerenciar a Infra.

  G1.3 - Exporters  
  >  - Os "exportadores" expõem as métricas para serem coletadas pelo Alloy ou Prometheus;  
  >  - Exportadores comuns:  
  >    - kube-state-metrics: Objetos do Kubernetes; 
  >    - cAdvisor: Métricas de Contêineres; 
  >    - Node Exporter: Métricas do Sistema Operacional; 
  >    - Kubelet / Metrics-server: Métricas básicas dos Pods / Nós.
  >      - Exportadores de Infra e Serviços:
  >        - Blackbox Exporter: Teste de Endpoints;
  >        - MySQL Exporter: Métricas do Banco MySQL / MariaDB;
  >        - Postgre Exporter;
  >        - Redis Exporter;
  >        - Kafka Exporter;
  >        - NGINX Exporter.  

</div> 
</details>

----

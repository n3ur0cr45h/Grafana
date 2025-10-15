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
</div> 
</details>

----

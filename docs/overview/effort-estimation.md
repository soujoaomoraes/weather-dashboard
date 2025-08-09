# Estimativa de Esforço - Backend Weather Dashboard

Este documento detalha a estimativa de esforço para o desenvolvimento da infraestrutura de backend do projeto, com base nos requisitos definidos.

A estimativa é medida em **dias de desenvolvimento** para um engenheiro sênior.

| # | Feature | Tarefas | Estimativa (dias) |
|---|---|---|---|
| 1 | **Setup & Arquitetura** | - Definição da arquitetura de microsserviços<br>- Setup do monorepo (se aplicável)<br>- Configuração do ambiente de desenvolvimento<br>- Definição do contrato da API (OpenAPI/Swagger) | 2-3 |
| 2 | **API Gateway** | - Implementação do gateway<br>- Configuração de rate limiting<br>- Roteamento para os serviços internos | 2-3 |
| 3 | **Serviço de Dados Meteorológicos** | - Integração com OpenWeatherMap e WeatherAPI<br>- Normalização e processamento dos dados<br>- Criação dos endpoints principais (`/weather/now`, `/weather/forecast`) | 3-4 |
| 4 | **Sistema de Cache** | - Configuração do Redis<br>- Implementação da estratégia de cache para os endpoints de dados<br>- Estratégia de invalidação | 2-3 |
| 5 | **Serviço de Geolocalização** | - Implementação do endpoint de busca de cidades (`/location/search`)<br>- Integração com API de geocodificação (se necessário) | 2-3 |
| 6 | **Serviço de Histórico de Usuário** | - Modelagem do banco de dados (PostgreSQL)<br>- Endpoints para salvar e consultar histórico de buscas<br>- Relacionamento com usuários (se houver autenticação) | 2-3 |
| 7 | **Sistema de Alertas** | - Lógica para definir e acionar alertas (ex: chuva nas próximas horas)<br>- Mecanismo de notificação (Webhook ou similar)<br>- Endpoints para gerenciamento de alertas | 3-4 |
| 8 | **Observabilidade** | - Implementação de logs estruturados<br>- Configuração de monitoramento básico (health checks) | 1-2 |
| 9 | **Testes** | - Cobertura de testes unitários (>85%)<br>- Testes de integração para os principais fluxos | 4-5 |
| 10 | **Documentação & Deploy** | - Documentação final dos endpoints<br>- Criação de scripts de deploy (Dockerfile, CI/CD) | 2-3 |
| | | **Total Estimado** | **23 - 33 dias** |

## Premissas

- A equipe já possui familiaridade com as tecnologias propostas (Node.js/TypeScript, Redis, PostgreSQL).
- As chaves de API para os serviços externos (OpenWeatherMap, etc.) estão disponíveis.
- O escopo de "autenticação de usuário" não está incluído nesta estimativa inicial. Se necessário, adicionará 3-5 dias ao projeto.
- A estimativa considera um único desenvolvedor focado no backend.

## 🗺️ Mapa de Tecnologias

A seguir, apresentamos o mapa de tecnologias definido para o desenvolvimento do aplicativo. Ele foi elaborado com base nas necessidades funcionais e não funcionais do projeto, considerando boas práticas de desenvolvimento, viabilidade técnica e alinhamento com a arquitetura adotada (MVC + Camadas no app móvel e Client-Server para comunicação com o backend). O objetivo é garantir uma base tecnológica estável, escalável e adequada à realidade de um MVP voltado à saúde pública municipal.

### Legenda e Estrutura do Mapa de Tecnologias
- O mapa está organizado de forma a representar os principais blocos de desenvolvimento do sistema, divididos em:

[![DoeVida.png](https://i.postimg.cc/hPFPGTbP/DoeVida.png)](https://postimg.cc/G9Q17B5Z)

## 📋 Tabela de Tecnologias 

|Tecnologia|Camada|Justificativa|
|----------|------|-------------|
|**Flutter / React Native**|Frontend Mobile|Permitem desenvolvimento multiplataforma (Android/iOS) com desempenho nativo e interface moderna.|
|**REST + JSON**|API|Leve, simples e amplamente suportado para comunicação entre frontend e backend.|
|**Firebase Auth**|Autenticação|Fácil de integrar, seguro e com suporte a login por e-mail, número de telefone e mais.|
|**Node.js + Express**|	Backend	|Rápido, escalável e com grande comunidade — ideal para APIs leves e serviços REST.|
|**Spring Boot (alternativa)**|	Backend Java |Indicado se o time já tem familiaridade com Java e deseja um framework robusto.|
|**PostgreSQL**| Banco de Dados  Relacional|	Confiável, gratuito e com excelente suporte a dados estruturados como usuários e agendamentos.|
|**Firebase Functions**|	Agendamento|	Para lidar com agendamentos, lembretes e verificações periódicas de forma automatizada.|
|**Heroku**|	Hospedagem|	Solução prática e de baixo custo para hospedagem de frontend ou backend.|
|**Firebase Cloud Messaging (FCM)**|	Notificações Push|	Ideal para enviar lembretes de doação, alertas sobre campanhas e status de exames.|
|**JWT + HTTPS**|	Segurança|	Garante autenticação segura e comunicação criptografada entre cliente e servidor.|
|**Regra de Acesso / Firebase Rules**	|Segurança / LGPD|	Controla o acesso aos dados sensíveis com base no papel do usuário e conformidade legal.|
|**Git + GitHub**|	Controle de Versão|	Versionamento de código e colaboração eficiente entre a equipe de desenvolvimento.|
|**GitHub Actions**|	CI/CD	|Automatiza testes e deploys a cada alteração, aumentando a produtividade e segurança.|
|**GitHub Projects**| Gerenciamento de Tarefas	|Integra tarefas e backlog diretamente no repositório, com suporte a quadros Kanban.|

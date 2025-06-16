## 📌 Diagrama de Containers

O **Diagrama de Containers** divide o sistema em grandes partes lógicas chamadas **containers**, como **aplicativos**, **APIs**, **bancos de dados** e **serviços**. Ele mostra os **containers internos do sistema** e foca em como o sistema é **dividido tecnicamente** (**front-end**, **back-end**, **banco de dados**, etc).

--- 

### Diagrama de Containers 

[![C-pia-do-Diagrama-de-containers-1-drawio.png](https://i.postimg.cc/qMVTXLkR/C-pia-do-Diagrama-de-containers-1-drawio.png)](https://postimg.cc/9zpKcyw5)

### ▪️Containers 

|**Container** | **Tecnologia** |	**Função** |
|-|-|-|
|Aplicativo Móvel|	FlutterFlow|	Interface principal para doadores acessarem funcionalidades do app|
|API Backend REST|	.NET |	Responsável por regras de negócio, controle de fluxo e integrações|
|Banco de Dados	|PostgreSQL|	Armazena dados de usuários, doações, agendamentos, exames etc.|
|Painel Web para Funcionários|	React.js|	Interface para que o hospital gerencie doações e acompanhe os dados|
|Sistema Hospitalar Legado|	Sistema externo	|Plataforma existente para coleta/exames, se for usado pelo hospital|
|Serviço de Notificações|	Firebase Cloud Messaging | Envia alertas e lembretes para doadores|
|API de CEP	|ViaCEP / Correios|	Valida e completa endereços durante o cadastro|

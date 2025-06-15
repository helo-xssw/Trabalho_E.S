## 📌 Diagrama de Componentes

O **Diagrama de Componentes**, também baseado no Modelo C4, detalha a organização interna do aplicativo móvel DoeVida, destacando os principais componentes de software e suas responsabilidades. Ele mostra como as partes do sistema se comunicam entre si e com serviços externos, oferecendo uma visão mais técnica e aprofundada da estrutura do aplicativo, essencial para o planejamento e desenvolvimento da solução.

--- 

### Diagrama de Componentes

[![Diagrama-Componentes-drawio-1.png](https://i.postimg.cc/9F2H4hk4/Diagrama-Componentes-drawio-1.png)](https://postimg.cc/DmxMDtnF)

### ▪️ Interfaces Externas
|**Componente**|	**Descrição**|
|-|-|
|Aplicativo Mobile DoeVida|	Fornece uma interface amigável e acessível para doadores realizarem cadastro, agendarem doações, visualizarem histórico e receberem notificações.|
|Painel Web para Funcionários|	Ferramenta acessada por profissionais de saúde (enfermeiros, atendentes) para consultar, registrar e gerenciar as doações no sistema.|

### ▫️ Componentes da Aplicação API

|**Componente**|	**Descrição**|
|-|-|
|Controlador de Cadastro|Responsável por processar cadastros de novos usuários e suas informações. Faz validações básicas e utiliza a API de CEP para completar o endereço.|
|Controlador de Doações	|Gerencia o agendamento, histórico e status de doações dos usuários. Também permite que funcionários registrem coletas e exames.|
|Controlador de Notificações|	Componente que dispara mensagens de alerta e lembretes para os usuários cadastrados, como confirmação de agendamento e campanhas de doação.|
|Componente de CEP|Realiza integração com a API do ViaCEP para completar automaticamente os dados de endereço durante o cadastro.|

### ▪️ Serviços e Recursos Externos

|**Componente**|**Descrição**|
|-|-|
|Banco de Dados (PostgreSQL)|Armazena informações dos usuários, dados de doações, exames, históricos, notificações enviadas, etc.|
|Firebase Cloud Messaging	|Serviço de mensagens usado para enviar notificações push aos dispositivos móveis dos doadores.|
|API de CEP (ViaCEP)|	Serviço externo que retorna dados de endereço a partir de um CEP, usado para facilitar o preenchimento de formulários.|
|Sistema Hospitalar Legado|Plataforma já existente nos hospitais que pode ser consultada pela API para verificar coletas e exames realizados fora do app.|

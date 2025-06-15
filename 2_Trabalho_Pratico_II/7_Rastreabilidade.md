## 🔎 Rastreabilidade

A rastreabilidade tem como objetivo demonstrar como os requisitos do sistema, expressos por meio das histórias de usuário, foram considerados no desenho da arquitetura do aplicativo DoeVida. A tabela a seguir estabelece uma relação direta entre cada história de usuário, os componentes do sistema que a suportam (incluindo as tecnologias utilizadas) e os diagramas nos quais esses elementos estão representados. Esse mapeamento facilita o entendimento do alinhamento entre as necessidades dos usuários e as decisões arquiteturais adotadas.

---

### Tabela de Mapeamento

|**História do Usuário**|**Componentes Envolvidos**|**Diagramas de Referência**|
|-|-|-|
|H1: Como enfermeira responsável pela UBS, quero acessar a lista de agendamentos de doadores, para planejar e organizar os atendimentos de doação de sangue no dia.|Painel Web para Funcionários (React), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)| Contexto, Containers, Componentes|
|H3: Como enfermeira responsável pela triagem, eu quero ter acesso às informações de histórico médico do doador, para realizar a triagem com mais precisão e garantir a segurança durante a doação.|Painel Web para Funcionários (React), Banco de Dados (PostgreSQL)|Contexto, Containers|
|H6:  Como um doador em potencial, eu quero me cadastrar facilmente no app, para começar o processo de doação e receber orientações iniciais.|Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Cadastro (Node.js), API de CEP (ViaCEP) Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|
|H7: Como um doador em potencial, eu quero responder a um questionário de triagem no app, para saber se estou apto a doar sangue antes de agendar.|Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|
|H8: Como um doador em potencial, eu quero agendar meus exames iniciais diretamente pelo app, para confirmar minha elegibilidade para doar sangue.|Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|
|H11: Como doador de sangue, desejo acessar uma lista atualizada de horários disponíveis para doação, para que eu possa escolher o melhor horário e agendar minha doação de forma prática.|Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|
|H12: Como doador de sangue, desejo receber notificações sobre a campanha vigente do mês, para me manter atualizado e participar ativamente.|Aplicativo Mobile DoeVida (Flutter/React Native), Serviço de Notificações (Firebase), Controlador de Notificações (Node.js)|Contexto, Containers, Componentes|
|H13: Como doador de sangue, desejo ter acesso aos resultados dos exames realizados na pré-doação, para que eu possa acompanhar minha saúde e estar ciente da minha aptidão para futuras doações.| Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|
|H15: Como doador de sangue, quero poder alterar facilmente o horário ou a data do meu agendamento, para ajustar a doação caso aconteça algum imprevisto em minha agenda.|Aplicativo Mobile DoeVida (Flutter/React Native), Controlador de Agendamentos (Node.js), Banco de Dados (PostgreSQL)|Contexto, Containers, Componentes|

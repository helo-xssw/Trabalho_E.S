## 👩‍💻 Casos de Teste com Classes de Equivalência

> H6: Como um doador em potencial, quero me cadastrar no aplicativo e receber por e-mail um guia com orientações de uso, para iniciar o processo de doação de forma segura e informada.

#### ✅ Critérios de Aceitação 

- O usuário deverá preencher obrigatoriamente os campos: nome completo, e-mail, senha, CEP e CNS (Cartão Nacional de Saúde) para concluir o cadastro no aplicativo.

- O sistema deve validar o endereço do usuário e permitir o cadastro apenas se o CEP informado estiver incluído na lista de CEPs previamente cadastrados como pertencentes ao município de Itacoatiara-AM.

- Se o CEP for válido, o cadastro é concluído com sucesso.

- Se o CEP for de outro município, o sistema exibe uma mensagem informando que o app é restrito à região e impede o cadastro.


#### 📋 Regras de Negócio

|**Regra de Negócio**| Descrição|
|------------------------|-----------|
|**RN01**|Apenas usuários com CEP pertencente ao município atendido poderão concluir o cadastro e acessar as funcionalidades principais do sistema como, cadastro de usuários, login, visualização de conteúdo e acesso ao suporte..|
|**RN02**| O sistema deve impedir o cadastro de usuários cujo CEP não esteja na base de cobertura do município.|
|**RN03**| Todos os dados pessoais e sensíveis dos usuários devem ser protegidos conforme a Lei Geral de Proteção de Dados (LGPD).|
|**RN04**|  sistema deve exigir autenticação segura (CPF ou e-mail + senha) para acesso às informações pessoais e funcionalidades privadas.| 

#### 📑 Classes de Equivalência - Cadastro de Usuário

| **Condição de Entrada** | Classes Válidas | Classes Inválidas | Classes Inválidas |
|-|-|-|-|
|E-mail informado corretamente|E-mail no formato correto (ex: user@exemplo.com) (1)	|E-mail sem “@” ou domínio (ex: usuario.com) (2) |Campo de e-mail em branco (3)|
|CEP pertence ao município de Itacoatiara-AM|	CEP válido de Itacoatiara (ex: 69100-000)| (4)	CEP de outro município (ex: 69000-000 – Manaus) | (5)	Campo de CEP em branco (6)|
|Senha válida segundo critérios mínimos de segurança	|Senha com ao menos 8 caracteres, contendo letras e números | (7)	Senha com menos de 8 caracteres |(8)	Senha apenas com letras ou números simples (9)|
|CNS preenchido corretamente| 15 dígitos numéricos (10) |	Menos de 15 dígitos (11)	| Campo de CNS em branco (12)|

#### 💻 Casos de Teste - Cadastro de Usuário

| **Casos de Teste** | **Classes de Equivalência** | **Entradas**                                                  | **Resultado Esperado**                  |
|--------------------|-----------------------------|---------------------------------------------------------------|------------------------------------------|
| CT01             | 1, 4, 7, 10                  | usuario@exemplo.com, 69100-000, Senha123, 123456789012345     | Cadastro permitido                       |
| CT02             | **2**, 4, 7, 10                  | usuario.com, 69100-000, Senha123, 123456789012345             | Cadastro inválido (e-mail mal formatado) |
| CT03             | 1, **5**, 7, 10                  | usuario@exemplo.com, 69000-000, Senha123, 123456789012345     | Cadastro inválido (CEP fora da área)     |
| CT04             | 1, 4, **8**, 10                  | usuario@exemplo.com, 69100-000, 12345, 123456789012345        | Cadastro inválido (senha fraca)          |
| CT05             | 1, 4, 7, **11**                  | usuario@exemplo.com, 69100-000, Senha123, 12345               | Cadastro inválido (CNS inválido)         |
| CT06             | **3**, **5**, **8**, **12**                  | "", 69000-000, abcdefg, ""                                     | Cadastro inválido (vários campos inválidos) |

----
> H7: Como um doador em potencial, eu quero responder a um questionário de triagem no app, para saber se estou apto a doar sangue antes de agendar.

#### ✅ Critérios de Aceitação 

- A triagem só está disponível após a validação da localidade no cadastro.

- O usuário tem acesso a um questionário baseado nas diretrizes nacionais de doação.

- O sistema deve informar se o usuário está apto ou não a seguir com os exames. Em caso de reprovação, deve apresentar mensagem explicando que o agendamento estará bloqueado por 7 dias, salvo apresentação de justificativa médica para liberação antecipada.


#### 📋 Regras de Negócio

|**Regra de Negócio**| Descrição|
|------------------------|-----------|
|**RN05**| Somente usuários com cadastro completo e endereço validado poderão iniciar a triagem de doador.|
|**RN06**| Usuários reprovados na triagem não poderão agendar exames ou coletas até que passem por nova avaliação, a ser liberada automaticamente após 7 dias ou mediante apresentação de justificativa médica.|
|**RN07**| A triagem deve seguir os critérios estabelecidos na Resolução RDC nº 36/2013 da Anvisa e na Portaria nº 204/2007 do Ministério da Saúde, garantindo padronização e conformidade com o atendimento no SUS.|

#### 📑 Classes de Equivalência - Triagem do Doador

| **Condição de Entrada**                             | **Classes Válidas**                     | **Classes Inválidas**                            | **Classes Inválidas**                          |
|-----------------------------------------------------|-----------------------------------------|--------------------------------------------------|------------------------------------------------|
| Respostas estão dentro dos critérios da triagem     | Todas as respostas indicam aptidão (1)  | Resposta que indica inaptidão temporária (2)     | Resposta que indica inaptidão definitiva (3)   |
| Acesso ao agendamento de exames                     | Usuário aprovado na triagem (4)         | Usuário reprovado e ainda dentro dos 7 dias (5)  | Usuário sem justificativa após reprovação (6)  |
| Reavaliação após reprovação                         | Passaram 7 dias após reprovação (7)     | Tentativa antes de 7 dias sem justificativa (5)  | Justificativa médica inválida (8)              |

#### 💻 Casos de Teste - Triagem do Doador

| **Casos de Teste** | **Classes de Equivalência** | **Entradas (Situação)**                                                                 | **Resultado Esperado**                               |
|--------------------|-----------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------|
| CT01            | 1, 4                        | Respostas indicam saúde apta, nenhum critério impeditivo                                | Triagem aprovada. Acesso ao agendamento liberado     |
| CT02             | **2**, 5                        | Resposta indica febre nos últimos dias (inaptidão temporária), tentativa em 2 dias      | Triagem reprovada. Agendamento bloqueado             |
| CT03            | **3**, **6**                        | Resposta indica hepatite (inaptidão definitiva), tentativa de seguir para exames         | Triagem reprovada. Agendamento permanentemente negado|
| CT04            | **2**, 7                        | Reprovado anteriormente por gripe, tenta após 8 dias                                     | Triagem liberada automaticamente após 7 dias         |
| CT05            | **2**, **8**                        | Reprovado por motivo temporário, apresenta justificativa médica inválida                 | Triagem continua reprovada. Acesso negado            |
| CT06            | **2**, 4                        | Reprovado anteriormente por motivo temporário, apresenta justificativa médica aceita     | Triagem liberada antecipadamente. Acesso autorizado  |

---

> H8: Como um doador apto, eu quero agendar meus exames iniciais diretamente pelo app, para confirmar minha elegibilidade para doar sangue.

#### ✅ Critérios de Aceitação

- Disponível apenas para usuários aptos na triagem e residentes no município.

- O usuário visualiza datas e locais de coleta apenas do hospital municipal.

- O agendamento é confirmado com data, hora e local, e aparece na conta do usuário.


#### 📋 Regras de Negócio

|**Regra de Negócio**| Descrição|
|------------------------|-----------|
|**RN08**| Os locais disponíveis para coleta de sangue e exames devem estar vinculados exclusivamente ao hospital municipal.|
|**RN09**| A funcionalidade de agendamento deve estar disponível apenas para usuários aprovados na triagem.|
|**RN10**| O sistema deve permitir que o usuário ou um administrador realizem o reagendamento manual em casos de ausência, cancelamento ou indisponibilidade. O reagendamento automático deve ocorrer apenas se houver cancelamento por parte da unidade de saúde, com sugestão de nova data dentro de 48 horas.|
|**RN11**| O sistema deve enviar notificações automáticas via push, e-mail e SMS, sendo: lembretes de agendamento 24 horas antes da consulta, confirmação imediata após o agendamento, alertas no início de campanhas de doação, e notificações de resultados assim que forem disponibilizados no sistema.|

#### 📑 Classes de Equivalência - Agendamento de Exames

| **Condição de Entrada**               | **Classes Válidas**                    | **Classes Inválidas**                         | **Classes Inválidas**                            |
|--------------------------------------|----------------------------------------|-----------------------------------------------|--------------------------------------------------|
| Aprovação na triagem                 | Usuário aprovado na triagem (1)        | Usuário reprovado na triagem (2)              | Usuário ainda não realizou triagem (3)           |
| Disponibilidade de data/horário      | Horário com vagas disponíveis (4)      | Horário com todas as vagas preenchidas (5)    | Data inválida (feriado ou fora do calendário) (6)|

#### 💻 Casos de Teste - Agendamento de Exames

| **Casos de Teste** | **Classes de Equivalência** | **Condições de Entrada**                                        | **Resultado Esperado**                                                 |
|-------|------------------------------|------------------------------------------------------------------|------------------------------------------------------------------------|
| CT01  | 1, 4                         | Usuário aprovado + horário com vagas                             | Agendamento confirmado com data, hora e local                         |
| CT02  | 1, **5**                         | Usuário aprovado + horário esgotado                              | Sistema bloqueia agendamento e informa que o horário está indisponível|
| CT03  | 1, **6**                         | Usuário aprovado + data inválida                                 | Agendamento recusado com mensagem de "data indisponível"             |
| CT04  | **2**, 4                         | Usuário reprovado + horário com vagas                             | Sistema impede agendamento com aviso de reprovação na triagem        |
| CT05  | **3**, 4                         | Usuário sem triagem + horário com vagas                           | Sistema impede agendamento e solicita conclusão da triagem            |

---

> H9: Como um doador em potencial ou reavaliado, quero acompanhar o status dos meus exames no app, para saber quando poderei doar efetivamente.

#### ✅ Critérios de Aceitação 

- O usuário pode acompanhar o status da triagem e dos exames, visualizando uma das seguintes situações: 'Pendente', 'Em análise', 'Aprovado' ou 'Reprovado'. A exibição será feita por meio de mensagens textuais e ícones coloridos no painel de acompanhamento.
- O app exibe notificações sobre aprovação ou rejeição com base nos resultados.

- Após aprovação, o usuário ganha acesso às funções de agendamento e histórico de doações.

#### 📋 Regras de Negócio

|**Regra de Negócio**| Descrição|
|------------------------|-----------|
|**RN12**|Usuários aprovados nos exames terão o status alterado para 'doador ativo' e acesso a funcionalidades completas. Esse status será válido por 12 meses, podendo ser renovado automaticamente mediante nova avaliação, ou revogado em caso de inaptidão temporária ou definitiva identificada em exames subsequentes.|
|**RN13**|Usuários não aprovados nos exames terão seu acesso restrito a conteúdos informativos e orientações.|

#### 📑 Classes de Equivalência - Acompanhamento de Exames

| **Condição de Entrada**                | **Classes Válidas**                | **Classes Inválidas**                    | **Classes Inválidas**                  |
|---------------------------------------|------------------------------------|------------------------------------------|----------------------------------------|
| Status dos exames                     | Status 'Pendente', 'Em análise', 'Aprovado', 'Reprovado' (1) | Status inexistente ou corrompido (2) | Status vazio/nulo (3)                  |
| Resultado dos exames                  | Exames aprovados (4)               | Exames reprovados (5)                    | Exames ainda não iniciados (6)         |

#### 💻 Casos de Teste - Acompanhamento de Exames

| **Casos de Teste** | **Classes de Equivalência** | **Condições de Entrada**                                               | **Resultado Esperado**                                                                 |
|--------|------------------------------|------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| CT01   | 1, 4                         | Status 'Aprovado' e exames com resultado positivo                      | Exibe mensagem e ícone verde + libera funções de agendamento e histórico              |
| CT02   | 1, **5**                         | Status 'Reprovado' e exames com resultado negativo                     | Exibe mensagem e ícone vermelho + bloqueia funcionalidades, exceto informativos       |
| CT03   | 1, **6**                         | Status 'Pendente' e exames não iniciados                               | Exibe ícone amarelo e texto informando que o exame está pendente                      |
| CT04   | **2**, 4                         | Status com valor inválido e exames aprovados                           | Exibe erro de sistema ou mensagem padrão de falha                                     |
| CT05   | **3**, 4                         | Status ausente (nulo) com exames aprovados                             | Exibe erro de carregamento e impede acesso às funções dependentes                     |
| CT06   | 1, 4                         | Status 'Aprovado' com validade expirada (após 12 meses)                | Exibe aviso de expiração e solicita nova avaliação para manter status de doador ativo |

--- 

> H10: Como um doador em potencial, eu gostaria de acessar conteúdos educativos e motivacionais sobre doação, para tirar dúvidas e ganhar confiança no processo.

#### ✅ Critérios de Aceitação

- A seção educativa com conteúdos sobre doação de sangue estará disponível para todos os usuários, incluindo não cadastrados. No entanto, funcionalidades como salvar conteúdos favoritos ou receber recomendações personalizadas estarão disponíveis apenas para usuários registrados.

- Os conteúdos são direcionados ao público local, com informações específicas sobre o hospital vinculado ao usuário, incluindo horários, campanhas e localização, podendo ser hospital municipal, regional, estadual ou conveniado.

- O conteúdo é acessível mesmo para usuários que ainda não completaram o cadastro.

#### 📋 Regras de Negócio

|**Regra de Negócio**| Descrição|
|------------------------|-----------|
|**RN14**| O módulo informativo do app deve estar acessível a todos os usuários, inclusive os que não finalizaram o cadastro.|
|**RN15**| O conteúdo educacional e informativo deve estar adaptado à realidade e necessidades do hospital e da população do município.|

#### 📑 Classes de Equivalência

| **Condição de Entrada**             | **Classes Válidas**                                 | **Classes Inválidas**                         | **Classes Inválidas**                         |
|------------------------------------|-----------------------------------------------------|------------------------------------------------|------------------------------------------------|
| Tipo de usuário                    | Visitante, cadastrado, cadastrado incompleto (1)    | Tipo de usuário desconhecido (2)              | Dados de sessão inválidos (3)                 |
| Conteúdo adaptado ao município     | Conteúdo do hospital vinculado (4)                  | Conteúdo não carregado (falha) (5)            | —                                              |
| Acesso a funcionalidades extras    | Usuário cadastrado completo (6)                     | Usuário não cadastrado (7)                    | Cadastrado parcial sem permissão (8)          |



#### 💻 Casos de Teste

| **Casos de Teste** | **Classes de Equivalência** | **Condições de Entrada**                                               | **Resultado Esperado**                                                                 |
|--------|------------------------------|------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| CT01   | 1, 4                         | Visitante acessa a seção educativa com conteúdo do hospital local      | Conteúdo exibido normalmente com informações locais                                    |
| CT02   | **3**, **5**                         | Sessão expirada e conteúdo não carregado                               | Mensagem de erro e solicitação de recarregamento                                      |
| CT03   | 1, 6                         | Usuário cadastrado completo acessa e salva conteúdo como favorito      | Conteúdo é salvo com sucesso                                                          |
| CT04   | 1, **7**                         | Usuário visitante tenta favoritar conteúdo                             | Sistema exibe mensagem solicitando cadastro                                           |
| CT05   | 1, **8**                         | Usuário com cadastro incompleto tenta acessar recomendações            | Acesso negado com mensagem indicando necessidade de completar cadastro                |


---

> H11: Como doador de sangue, desejo acessar uma lista atualizada de horários disponíveis para doação, para que eu possa escolher o melhor horário e agendar minha doação de forma prática.

#### ✅ Critérios de Aceitação

- O sistema exibe uma lista atualizada de horários disponíveis para doação no hemonúcleo.
- A lista de horários é mantida atualizada pelo sistema, seja em tempo real ou em períodos pré-definidos.
- O usuário pode visualizar os dias e horários disponíveis para agendamento de forma clara e acessível.
- O sistema agenda o horário selecionado, sem verificar limite de vagas ou conflitos.
- Caso o horário escolhido esteja indisponível, o sistema notifica o usuário e sugere alternativas.

#### 📋 Regras de Negócio

| **Regra de Negócio** | Descrição |
|----------------------|-----------|
| **RN14** | O módulo informativo do aplicativo deve permitir acesso irrestrito, estando disponível para todos os usuários, inclusive aqueles que ainda não concluíram o cadastro.|
| **RN15** | O conteúdo educacional e informativo do aplicativo deve ser personalizado de acordo com as necessidades do hospital e com as características da população do município.|
| **RN16** | Os horários disponíveis para doação devem ser definidos e atualizados pelo hemonúcleo local, de acordo com sua capacidade de atendimento. |
| **RN17** | Cada horário de doação deve ter um limite máximo de vagas, definido pelo administrador do hemonúcleo. |
| **RN18** | O agendamento só poderá ser realizado com pelo menos 24 horas de antecedência da data desejada. |
| **RN19** | O sistema deve impedir que um mesmo usuário agende dois horários no mesmo dia, exceto em casos de reagendamento por ausência ou cancelamento.|
| **RN20** | O agendamento de horário será permitido apenas para usuários que estejam aptos segundo os requisitos mínimos de saúde (idade, peso, estado geral de saúde e intervalo entre doações). |
| **RN21** | Horários que atingirem o limite de agendamentos devem ser automaticamente ocultados ou marcados como indisponíveis. |
| **RN22** | O cancelamento de agendamento deve ser permitido até 12 horas antes do horário marcado. Após esse prazo, o cancelamento só poderá ser feito por contato direto com o hemonúcleo. |
| **RN23** | Usuários que faltarem ao agendamento sem aviso prévio serão temporariamente bloqueados de novos agendamentos, pelo período estabelecido pelo hemonúcleo. |

#### 📑 Classes de Equivalência

| **Condição de Entrada**                   | **Classes Válidas**                                           | **Classes Inválidas**                                        | **Classes Inválidas**                                 |
|------------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|--------------------------------------------------------|
| Usuário apto a doar (passou nos exames)  | Aprovado nos exames médicos (1)                              | Reprovado nos exames médicos (2)                             | Sem resultado ou avaliação pendente (3)               |
| Antecedência do agendamento              | Agendamento feito com 24h ou mais de antecedência (4)         | Agendamento feito com menos de 24h (5)                        | Tentativa de agendamento retroativo (6)               |
| Disponibilidade de horário               | Horário disponível com vagas (7)                              | Horário sem vagas (lotado) (8)                                | Horário já agendado pelo próprio usuário (9)          |
| Conflito de agendamento                  | Sem conflito no mesmo dia (10)                                | Duplo agendamento no mesmo dia (11)                           | Tentativa de burlar limite com contas diferentes (12) |


#### 💻 Casos de Teste

| **Casos de Teste** | **Classes de Equivalência** | **Condições de Entrada**                                                         | **Resultado Esperado**                                                                      |
|--------|-----------------------------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| CT01   | 1, 4, 7, 10                 | Usuário apto tenta agendar com 2 dias de antecedência em horário disponível     | Agendamento confirmado com sucesso                                                          |
| CT02   | **2**, 4, 7, 10                 | Usuário reprovado nos exames tenta agendar                                      | Sistema exibe mensagem de inaptidão e bloqueia o agendamento                               |
| CT03   | 1, **5**, 7, 10                 | Usuário apto tenta agendar para o mesmo dia                                     | Sistema bloqueia a ação e informa o tempo mínimo necessário                                 |
| CT04   | 1, 4, **8**, 10                 | Usuário tenta agendar em horário lotado                                         | Sistema exibe alerta e sugere alternativas                                                  |
| CT05   | 1, 4, 7, **11**                 | Usuário tenta agendar dois horários no mesmo dia                                | Sistema bloqueia segundo agendamento e alerta sobre conflito                               |
| CT06   | 1, 4, **9**, 10                 | Usuário tenta agendar no mesmo horário já marcado por ele                       | Sistema informa que o horário já está agendado pelo próprio usuário                        |
| CT07   | **3**, 4, 7, 10                 | Usuário com exames pendentes tenta agendar                                      | Sistema solicita que aguarde conclusão dos exames                                           |
| CT08   | 1, **6**, 7, 10                 | Usuário tenta agendar um horário passado                                        | Sistema exibe erro e impede o agendamento                                                  |
| CT09   | 1, 4, 7, **12**                 | Usuário tenta reagendar fora do prazo permitido                                 | Sistema bloqueia reagendamento e orienta contato com o hemonúcleo                          |


---

> H12: Como doador de sangue, desejo receber notificações sobre a campanha vigente do mês, para me manter atualizado e participar ativamente.

## ✅ Critérios de Aceitação

- O sistema envia notificações aos usuários sobre a campanha vigente do mês.
- As notificações destacam informações relevantes como tema, período, metas e benefícios (quando houver).
- As notificações são enviadas por meio de push (aplicativo) e/ou e-mail, conforme preferência do usuário.
- O usuário pode acessar um histórico ou seção fixa com informações da campanha atual e anteriores.
- O usuário pode configurar a frequência das notificações (diária, semanal, quinzenal ou mensal) e o tipo de recebimento desejado (push, e-mail, ambos ou nenhum).

## 📋 Regras de Negócio

| **Regra de Negócio** | Descrição |
|----------------------|-----------|
| **RN24** | O sistema deve enviar notificações mensais sobre campanhas vigentes aos usuários cadastrados. |
| **RN25** | O conteúdo das notificações será elaborado pelo hemonúcleo, considerando a campanha vigente e alinhado às diretrizes estabelecidas pelo Ministério da Saúde e/ou pela Secretaria Municipal de Saúde, respeitando eventuais atualizações ou orientações complementares desses órgãos. |
| **RN26** | As notificações devem conter informações claras e relevantes sobre a campanha, como tema, período, metas e benefícios (quando aplicável). |
| **RN27** | O usuário poderá configurar suas preferências de notificação no aplicativo (tipo, canal e frequência), sendo possível desativá-las, respeitando um limite mínimo definido pelo sistema. |
| **RN28** | O sistema deve respeitar as configurações de privacidade e não enviar notificações a usuários que desativaram esse recurso. |
| **RN29** | As notificações devem obrigatoriamente informar o tema e o período da campanha. Informações adicionais, como metas e benefícios, podem ser incluídas quando aplicável. |

#### 📑 Classes de Equivalência

| **Classe** | **Descrição**                                                 |
| ---------- | ------------------------------------------------------------- |
| 1          | Usuário cadastrado e ativo                                    |
| 2          | Usuário inativo ou não cadastrado                             |
| 3          | Preferência de recebimento configurada como push              |
| 4          | Preferência de recebimento configurada como e-mail            |
| 5          | Preferência configurada para ambos                            |
| 6          | Preferência configurada como nenhum                           |
| 7          | Frequência configurada (diária, semanal, quinzenal ou mensal) |
| 8          | Notificação enviada com sucesso                               |
| 9          | Acesso ao histórico de campanhas                              |
| 10         | Notificação não enviada por ausência de configuração          |


#### 💻 Casos de Teste

| **ID** | **Classes de Equivalência** | **Condições de Entrada**                                                             | **Resultado Esperado**                                                                 |
|--------|-----------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| CT01   | 1, 3, 7, 8                  | Usuário ativo com preferência de push e frequência semanal                          | Notificação é enviada via push semanalmente                                           |
| CT02   | 1, 4, 7, 8                  | Usuário ativo com preferência de e-mail e frequência mensal                         | Notificação é enviada por e-mail mensalmente                                          |
| CT03   | 1, 5, 7, 8                  | Usuário ativo com preferência de push e e-mail com frequência diária                | Notificação é enviada por ambos os meios diariamente                                  |
| CT04   | 1, 6, 7, 10                 | Usuário ativo com opção de não receber notificações                                 | Sistema não envia notificação                                                         |
| CT05   | 2, 3, 7, 10                 | Usuário inativo ou não cadastrado com preferência de push                           | Notificação não enviada; sistema bloqueia envio                                       |
| CT06   | 1, 3, 7, 9                  | Usuário ativo acessa histórico de campanhas                                         | Histórico da campanha vigente e anteriores é exibido com sucesso                     |
| CT07   | 1, 3, -, 10                 | Usuário ativo configurou tipo de recebimento mas não configurou frequência          | Sistema não envia notificação e exibe alerta solicitando configuração de frequência   |

---

> H13: Como doador de sangue, desejo ter acesso aos resultados dos exames realizados na pré-doação, para que eu possa acompanhar minha saúde e estar ciente da minha aptidão para futuras doações.

#### ✅ Critérios de Aceitação

- O sistema permite que o usuário visualize os resultados dos exames realizados na pré-doação.
- Os resultados incluem informações sobre aptidão, hemoglobina, pressão, doenças triadas e outras métricas relevantes.
- Os dados são apresentados de forma clara, segura e acessível.
- Os resultados são disponibilizados somente após validação e liberação por parte do hemonúcleo.
- O usuário recebe uma notificação quando os exames forem liberados para consulta.
- O histórico de exames fica disponível para visualização futura dentro do perfil do usuário.

#### 📋 Regras de Negócio

| **Regra de Negócio** | Descrição |
|----------------------|-----------|
| **RN30** |O sistema deve disponibilizar os resultados dos exames da pré-doação em até 7 dias úteis após validação técnica e liberação pelo hemonúcleo. |
| **RN31** | Os dados de exames devem ser protegidos por autenticação e criptografia, garantindo sigilo médico e segurança da informação. |
| **RN32** | Os resultados exibidos devem conter explicações simples ou links para informações complementares sobre os indicadores apresentados. |
| **RN33** | O usuário deve ser notificado assim que os resultados estiverem disponíveis no sistema, por meio de push, e-mail ou SMS, conforme preferência configurada no perfil do usuário. |
| **RN34** | O histórico de resultados deve ser armazenado no perfil do doador por até 12 meses, e ser acessível a qualquer momento pelo próprio usuário. |
| **RN35** | O sistema deve destacar se o usuário está apto ou inapto para futuras doações, com base nas informações mais recentes. |
| **RN36** | Resultados críticos (ex: doenças infecciosas detectadas) devem ser tratados com sigilo e orientações específicas, podendo exigir contato direto do hemonúcleo com o doador. |

#### 📑 Classes de Equivalência

Preencher

#### 💻 Casos de Teste

Preencher

---

> H14: Como doador de sangue, eu quero receber orientações de cuidado após a doação pelo app, para garantir minha recuperação adequada e saber o que evitar.

#### ✅ Critérios de Aceitação

- O app exibe orientações claras e objetivas sobre cuidados pós-doação assim que o procedimento for registrado como concluído.
- As orientações incluem recomendações como repouso, hidratação, alimentação e atividades a evitar.
- O conteúdo é adaptado ao perfil do doador, quando necessário (ex: primeira doação, doação por aférese).
- “O usuário recebe uma notificação por push e e-mail, com link direto para o conteúdo assim que o procedimento for registrado como concluído.”
- O conteúdo permanece disponível no histórico do usuário para consulta posterior.

#### 📋 Regras de Negócio

| **Regra de Negócio** | Descrição |
|----------------------|-----------|
| **RN37** |O sistema deve enviar uma notificação push ao identificar que o procedimento foi concluído, permitindo acesso às orientações pós-doação por link direto. |
| **RN38** | As orientações devem seguir a Portaria GM/MS nº XXXX, com revisões semestrais baseadas nas atualizações do Ministério da Saúde. |
| **RN39** | O conteúdo deve abordar recomendações de hidratação, alimentação, repouso e restrições (ex: evitar esforço físico, dirigir motos). |
| **RN40** | O sistema deve notificar o usuário com um lembrete e acesso direto às orientações pós-doação. |
| **RN41** | As orientações devem ser acessíveis a qualquer momento no perfil ou histórico do usuário. |

#### 📑 Classes de Equivalência

Preencher

#### 💻 Casos de Teste

Preencher

---

> H15: Como doador de sangue, desejo alterar a data ou o horário do meu agendamento com antecedência mínima de 12 horas, por meio de um fluxo simples no aplicativo, para reagendar a doação caso ocorra um imprevisto.

#### ✅ Critérios de Aceitação

- O usuário pode visualizar seus agendamentos futuros no aplicativo.
- O sistema permite alterar a data e/ou o horário de um agendamento ativo, desde que respeitado o prazo mínimo de antecedência.
- As opções disponíveis para reagendamento devem considerar apenas os horários ainda livres.
- O usuário recebe uma confirmação da alteração e uma notificação com os novos dados do agendamento.
- O histórico deve registrar a alteração feita, mantendo a rastreabilidade.

#### 📋 Regras de Negócio

| **Regra de Negócio** | Descrição |
|----------------------|-----------|
| **RN42** | O sistema deve permitir a alteração de agendamentos com no mínimo 12 horas de antecedência da data agendada. |
| **RN43** | O usuário só pode alterar agendamentos futuros — não é possível modificar datas já expiradas. |
| **RN44** | O novo horário selecionado deve estar entre os horários disponíveis e com vagas abertas. |
| **RN45** | Após a alteração, o sistema deve atualizar o registro de agendamento e gerar uma nova confirmação para o usuário. |
| **RN46** | O sistema deve registrar todas as alterações no histórico do usuário, incluindo data, horário anterior e novo horário. |
| **RN47** | Em caso de indisponibilidade nos horários desejados, o sistema deve sugerir opções alternativas próximas à original. |

#### 📑 Classes de Equivalência

Preencher

#### 💻 Casos de Teste

Preencher

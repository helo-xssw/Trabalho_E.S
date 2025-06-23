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


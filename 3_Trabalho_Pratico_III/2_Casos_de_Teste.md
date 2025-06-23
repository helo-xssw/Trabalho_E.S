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

#### 📑 Classes de Equivalência 

| **Condição de Entrada** | Classes Válidas | Classes Inválidas | Classes Inválidas |
|-|-|-|-|
|E-mail informado corretamente|E-mail no formato correto (ex: user@exemplo.com) (1)	|E-mail sem “@” ou domínio (ex: usuario.com) (2) |Campo de e-mail em branco (3)|
|CEP pertence ao município de Itacoatiara-AM|	CEP válido de Itacoatiara (ex: 69100-000)| (4)	CEP de outro município (ex: 69000-000 – Manaus) | (5)	Campo de CEP em branco (6)|
|Senha válida segundo critérios mínimos de segurança	|Senha com ao menos 8 caracteres, contendo letras e números | (7)	Senha com menos de 8 caracteres |(8)	Senha apenas com letras ou números simples (9)|
|CNS preenchido corretamente| 15 dígitos numéricos (10) |	Menos de 15 dígitos (11)	| Campo de CNS em branco (12)|

#### 💻 Casos de Teste 

| **Casos de Teste** | **Classes de Equivalência** | **Entradas**                                                  | **Resultado Esperado**                  |
|--------------------|-----------------------------|---------------------------------------------------------------|------------------------------------------|
| Caso 1             | 1, 4, 7, 10                  | usuario@exemplo.com, 69100-000, Senha123, 123456789012345     | Cadastro permitido                       |
| Caso 2             | **2**, 4, 7, 10                  | usuario.com, 69100-000, Senha123, 123456789012345             | Cadastro inválido (e-mail mal formatado) |
| Caso 3             | 1, **5**, 7, 10                  | usuario@exemplo.com, 69000-000, Senha123, 123456789012345     | Cadastro inválido (CEP fora da área)     |
| Caso 4             | 1, 4, **8**, 10                  | usuario@exemplo.com, 69100-000, 12345, 123456789012345        | Cadastro inválido (senha fraca)          |
| Caso 5             | 1, 4, 7, **11**                  | usuario@exemplo.com, 69100-000, Senha123, 12345               | Cadastro inválido (CNS inválido)         |
| Caso 6             | **3**, **5**, **8**, **12**                  | "", 69000-000, abcdefg, ""                                     | Cadastro inválido (vários campos inválidos) |

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

#### 📑 Classes de Equivalência 

| **Condição de Entrada**                             | **Classes Válidas**                     | **Classes Inválidas**                            | **Classes Inválidas**                          |
|-----------------------------------------------------|-----------------------------------------|--------------------------------------------------|------------------------------------------------|
| Respostas estão dentro dos critérios da triagem     | Todas as respostas indicam aptidão (1)  | Resposta que indica inaptidão temporária (2)     | Resposta que indica inaptidão definitiva (3)   |
| Acesso ao agendamento de exames                     | Usuário aprovado na triagem (4)         | Usuário reprovado e ainda dentro dos 7 dias (5)  | Usuário sem justificativa após reprovação (6)  |
| Reavaliação após reprovação                         | Passaram 7 dias após reprovação (7)     | Tentativa antes de 7 dias sem justificativa (5)  | Justificativa médica inválida (8)              |

#### 💻 Casos de Teste 

| **Casos de Teste** | **Classes de Equivalência** | **Entradas (Situação)**                                                                 | **Resultado Esperado**                               |
|--------------------|-----------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------|
| Caso 1             | 1, 4                        | Respostas indicam saúde apta, nenhum critério impeditivo                                | Triagem aprovada. Acesso ao agendamento liberado     |
| Caso 2             | **2**, 5                        | Resposta indica febre nos últimos dias (inaptidão temporária), tentativa em 2 dias      | Triagem reprovada. Agendamento bloqueado             |
| Caso 3             | **3**, **6**                        | Resposta indica hepatite (inaptidão definitiva), tentativa de seguir para exames         | Triagem reprovada. Agendamento permanentemente negado|
| Caso 4             | **2**, 7                        | Reprovado anteriormente por gripe, tenta após 8 dias                                     | Triagem liberada automaticamente após 7 dias         |
| Caso 5             | **2**, **8**                        | Reprovado por motivo temporário, apresenta justificativa médica inválida                 | Triagem continua reprovada. Acesso negado            |
| Caso 6             | **2**, 4                        | Reprovado anteriormente por motivo temporário, apresenta justificativa médica aceita     | Triagem liberada antecipadamente. Acesso autorizado  |

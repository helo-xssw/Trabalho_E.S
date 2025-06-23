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

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
| | | | |

----

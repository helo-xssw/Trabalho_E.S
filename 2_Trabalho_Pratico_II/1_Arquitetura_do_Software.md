## 📐 Arquitetura do Software 

 Os padrões de arquitetura escolhidos foram o **Modelo MVC** (Model-View-Controller), a **Arquitetura em Camadas** e a **Arquitetura Cliente-Servidor**, definidos com base na proposta do aplicativo de doação de sangue, que exige organização, escalabilidade e uma comunicação eficiente entre cliente e servidor.

- A seguir, temos uma imagem representando a interação entre os principais componentes dessas arquiteturas, evidenciando o fluxo de dados entre o usuário, o aplicativo e o backend.

---

###  Arquitetura MVC

[![Inserir-um-t-tulo-3.png](https://i.postimg.cc/1RFBrg7C/Inserir-um-t-tulo-3.png)](https://postimg.cc/149D9zQw)

### ▪️ Visão

A **Visão** é responsável pela interface com o usuário no aplicativo móvel.
Essa camada apresenta as telas de **login, cadastro, agendamento de doação, histórico, informações sobre sangue, entre outras funcionalidades**.
Toda a interação do usuário acontece aqui.

### ▫️Controlador 

O **Controlador** é responsável por mediar a comunicação entre a Visão (as telas do app) e o restante do sistema.
No app, ele é responsável por **capturar ações do usuário** (como “agendar uma doação” ou “editar perfil”), enviar esses dados ao backend por meio de **requisições HTTP (API REST)** e exibir as respostas adequadas (mensagem de sucesso, dados atualizados, etc.).

### ▪️ Modelo

O **Modelo** representa a lógica e os dados do sistema.
No backend, ele se conecta com o banco de dados para realizar operações como:

- Salvar novo usuário
- Verificar agendamentos existentes
- Validar reagendamentos
- Consultar histórico de doações
- Essa camada é onde ficam as regras de negócio (ex: “só pode reagendar com 24h de antecedência”) e a manipulação direta dos dados.

###  ▫️Banco de Dados

Armazena todas as informações da aplicação, como:

- Dados dos usuários (nome, CPF, localidade, status de doador)
- Agendamentos realizados
- Regras de restrição para doação
- Mensagens de notificação

--- 

### Arquitetura Cliente-Servidor

[![C-pia-de-Inserir-um-t-tulo-2.png](https://i.postimg.cc/1zgDBtr5/C-pia-de-Inserir-um-t-tulo-2.png)](https://postimg.cc/zLrLXqQ9)

### ▪️Comunicação Client-Server

Todo o sistema segue a **arquitetura Client-Server**, onde:

- O **cliente** é o aplicativo móvel que roda no dispositivo do doador
- O **servidor** é responsável por processar as requisições (API REST) e acessar o banco de dados

Essa separação garante:

- Flexibilidade na evolução de front e back-end
- Segurança e controle centralizado
- Possibilidade de integração futura com outros sistemas de saúde

--- 

## 📊 Tabela de Justificativa 

|Arquitetura|Aplicada em|Motivo da Escolha|
|-|-|-|
|MVC (Model-View-Controller)|Aplicativo móvel (frontend)|Organiza melhor a estrutura do app; separa visual (UI), lógica (controller) e dados (model); facilita manutenção e testes.|
|Arquitetura em Camadas|	Aplicativo móvel (frontend)|	Torna o código mais modular e reutilizável; cada camada tem responsabilidade única: apresentação, lógica, comunicação externa, etc.|
|Client-Server|Comunicação geral|O app (cliente) envia requisições ao servidor por meio de APIs; o backend processa e responde. Escalável, seguro e de fácil manutenção.|

## 🔍 Rastreabilidade Diagramas C4

> **Funcionalidade:** Login do Usuário
- **Diagrama de Classes:** A funcionalidade de login está associada à classe Usuario, que contém atributos como email, senha, nomeCompleto e CNS. Esses atributos permitem a verificação de credenciais no momento da autenticação. A estrutura da classe representa os dados persistidos e validados durante o login.

- **Diagrama C4 (Container):** O usuário realiza o login pelo Aplicativo Mobile DoeVida. As informações são enviadas para a API Backend REST, que consulta o banco de dados e verifica se os dados estão corretos. Se estiverem, o acesso é liberado.
-  **Diagrama C4 (Componentes):** O processo de login é tratado pelo Controlador de Cadastro, que valida os dados inseridos e verifica se existe um registro correspondente no banco de dados. Após a verificação, o resultado é retornado ao app.

---

> **Funcionalidade:** Cadastro do Usuário
- **Diagrama de Classes:** Utiliza a classe Usuário, que contém atributos como nome, e-mail, senha, CEP e CNS. Esses dados são armazenados no sistema após a validação.

- **Diagrama C4 (Container):** O usuário preenche os dados no Aplicativo Mobile DoeVida. As informações são enviadas para a API Backend REST, que realiza as validações e armazena os dados no banco de dados.

- **Diagrama C4 (Componentes):** O cadastro é processado pelo Controlador de Cadastro, que valida os campos preenchidos e utiliza o Componente de CEP para buscar e completar o endereço com base no CEP informado. Após as validações, os dados são registrados no banco de dados.

---

> **Funcionalidade:** Agendamento de Doação

- **Diagrama de Classes:** A classe AgendarDoacao contém atributos como data, horário e local da doação, e está associada à classe Doador, que representa quem realizou o agendamento.
  
- **Diagrama C4 (Container):** O doador realiza o agendamento pelo Aplicativo Mobile DoeVida, enviando os dados para a API Backend REST. O backend, por meio do Controlador de Doações, valida e registra o agendamento no banco de dados.
  
- **Diagrama C4 (Componentes):** O Controlador de Doações valida e salva o agendamento. Após a confirmação, o Controlador de Notificações envia a mensagem de confirmação para o doador.

  

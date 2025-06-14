# Arquitetura utilizada: Arquitetura em camadas

A **arquitetura em camadas** é um modelo de organização de software que divide o sistema em camadas separadas por responsabilidade, como:

- **Apresentação:** Interface com o usuário.
- **Aplicação:** Controle e regras de uso.
- **Domínio:** Regras de negócio.
- **Infraestrutura:** Banco de dados, APIs externas, etc.

## Justificativa da utilização da arquitetura em camadas no desenvolvimento do aplicativo DoeVida

A **arquitetura em camadas** é ideal para o sistema **DoeVida** por ser **simples**, **organizada** e **adequada a um prazo curto (6 meses)** com uma **equipe pequena (5 pessoas)**.

Essa arquitetura permite:

- Separação clara de responsabilidades, facilitando o desenvolvimento e a manutenção.
- Um backend limpo e reutilizável, essencial para um sistema que, por enquanto, será apenas um aplicativo móvel.
- Boa escalabilidade vertical, suportando picos de acesso durante campanhas de doação.
- Facilidade na aplicação de regras de segurança em pontos estratégicos do sistema.

Em resumo, a Arquitetura em Camadas oferece um **bom equilíbrio entre produtividade, segurança e estruturação**, sendo **perfeita para um MVP** com **potencial de evolução futura**.

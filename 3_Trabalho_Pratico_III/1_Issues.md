## ✍️ Correção do Backlog (Issues)

Após a inspeção realizada por uma equipe externa, foi recebida uma tabela contendo os defeitos identificados no produto. Cada um desses defeitos foi registrado como uma issue no GitHub, utilizando labels específicas para facilitar a categorização e o acompanhamento. Com base nessas issues, as correções necessárias foram realizadas diretamente no backlog do produto, tornando-o mais completo, coerente e alinhado com os critérios de qualidade esperados.

A seguir, destacamos as issues mais relevantes identificadas nesse processo. Para cada uma, apresentamos um comparativo entre a situação anterior e o resultado após a correção, demonstrando as melhorias implementadas no backlog.

[Link para o acesso completo das Issues](https://github.com/helo-xssw/Trabalho_E.S/issues)

---
### ▫️ H7 - Critério de Aceitação - Item 3: Inconsistência entre triagem e bloqueio de agendamento. 

> O critério de aceitação diz que o sistema informa se o usuário está apto a seguir com os exames, enquanto a RN06 impede o agendamento se o
usuário for reprovado. O sistema pode precisar de uma mensagem explicativa para que usuários entendam claramente as razões da reprovação e eventuais alternativas.

- **Antes da Correção**

[![H7-ANTES-CR.jpg](https://i.postimg.cc/YSsG6Pbb/H7-ANTES-CR.jpg)](https://postimg.cc/8FLzDZ86)

Reformular o critério para refletir as consequências da reprovação, conforme a regra de negócio RN06:

> "O sistema deve informar se o usuário está apto ou não a seguir com os exames. Em caso de reprovação, deve apresentar mensagem explicando que o agendamento estará bloqueado por 7 dias, salvo apresentação de justificativa médica para liberação antecipada."

- **Depois da Correção**
  
[![Captura-de-tela-2025-06-24-142057.png](https://i.postimg.cc/tTs68bYK/Captura-de-tela-2025-06-24-142057.png)](https://postimg.cc/fthk067C)
---

### ▪️ H9 - Critério de Aceitação - Item 01: Falta de detalhamento nos status de triagem e exames.

> O item 1 do critério de aceitação afirma que "O usuário pode acompanhar o status da triagem e dos exames", mas não especifica quais são os possíveis status nem como essa visualização será feita no sistema (por ícones, mensagens, cores, etc.).

Essa omissão pode gerar interpretações diferentes entre a equipe de desenvolvimento e dificultar os testes de aceitação.

- **Antes da Correção**
  
[![H9-CR-Antes.jpg](https://i.postimg.cc/pLDtQ02J/H9-CR-Antes.jpg)](https://postimg.cc/BjQy4BPj)

Reformular o critério de aceitação incluindo os possíveis status e a forma de apresentação. Por exemplo:
> "O usuário pode acompanhar o status da triagem e dos exames, visualizando uma das seguintes situações: 'Pendente', 'Em análise', 'Aprovado' ou 'Reprovado'. A exibição será feita por meio de mensagens textuais e ícones coloridos no painel de acompanhamento."

- **Após correção**
  
[![Captura-de-tela-2025-06-23-232417.png](https://i.postimg.cc/2800sh0N/Captura-de-tela-2025-06-23-232417.png)](https://postimg.cc/RNn1f6rg)

---

### ▫️H11 - Regras de Negócio, RN20: Omissão dos pré-requistos de saúde. 

> A equipe avaliadora apontou que a regra de negócio RN20 não específica quais os pré-requisitos de saúde poderão agendar um horário.
Reformular a regra de negócio:

- **Antes da Correção**

[![Whats-App-Image-2025-06-23-at-01-33-58.jpg](https://i.postimg.cc/Kz8fzC4f/Whats-App-Image-2025-06-23-at-01-33-58.jpg)](https://postimg.cc/t18WvS3n)

> RN20: O agendamento de horário será permitido apenas para usuários que estejam aptos segundo os requisitos mínimos de saúde (idade, peso, estado geral de saúde e intervalo entre doações).

- **Depois da Correção**

[![Captura-de-tela-2025-06-24-144631.png](https://i.postimg.cc/50XPgZ10/Captura-de-tela-2025-06-24-144631.png)](https://postimg.cc/XG0c71rS)

### ▪️ H12 - Critério de aceitação, item 05: Não específica as opções de frequência das notificações.

> A equipe avaliativa apontou que o item 05 do Critério de aceitaçao está ambiguo pois não especifica as opções disponíveis de frequência de notificações.

- **Antes da Correção**

[![H12-ANTES-CR.jpg](https://i.postimg.cc/9Mg6FdX4/H12-ANTES-CR.jpg)](https://postimg.cc/nj7R3QDZ)

Reformular o Critério de aceitação:
> Item 05: O usuário pode configurar a frequência das notificações (diária, semanal, quinzenal ou mensal) e o tipo de recebimento desejado (push, e-mail, ambos ou nenhum).

- **Depois da Correção**

[![Captura-de-tela-2025-06-24-145659.png](https://i.postimg.cc/bv3M3xt6/Captura-de-tela-2025-06-24-145659.png)](https://postimg.cc/cKtXJ8TY)

  

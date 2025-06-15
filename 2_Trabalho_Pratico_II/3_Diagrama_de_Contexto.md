## 📌  Diagrama de Contexto

O nível de contexto oferece uma **visão geral do sistema**, identificando os **principais atores externos** (como usuários e sistemas externos) e mostrando como eles interagem com o sistema. O **Diagrama de Contexto** ajuda a entender o **escopo do sistema**, seus **limites** e **interfaces com o ambiente externo**.
- A seguir temos o Diagrama de Contexto, baseado no Modelo C4 de Simon Brown. Este diagrama oferece uma visão geral do sistema, identificando os atores externos e como eles interagem com o aplicativo DoeVida. 
---

### Diagrama de Contexto 

[![C-pia-do-Diagrama-de-contexto-drawio.png](https://i.postimg.cc/Qx9SNhz7/C-pia-do-Diagrama-de-contexto-drawio.png)](https://postimg.cc/KRbtJSxc)

### ▪️ Atores Externos (Usuários e Sistemas Externos)

|**Ator Externo**|**Descrição**|
|-|-|
|Doador|	Pessoa física que utiliza o app para se cadastrar, agendar doações, receber notificações e visualizar informações sobre doação de sangue.|
|Funcionário do Hospital|	Responsável por validar dados de agendamento, registrar doações e atualizar o status dos doadores no sistema interno.|
|Sistema Hospitalar Interno|Sistema legado usado pelo hospital para registrar coletas, exames e disponibilidade de bolsas de sangue. Pode ser integrado via API ou interface manual.|
|API de CEP (Correios ou ViaCEP)|	Utilizada para validação de endereço durante o cadastro do doador.|
|Serviço de Notificação (Firebase/OneSignal)|	Envia notificações para lembrar o doador sobre sua doação ou reagendamento.|

### ▫️Principais Interações

**Doador** interage com o aplicativo para:
- Realizar cadastro
- Agendar doação
- Reagendar/cancelar
- Verificar histórico
- Acessar orientações educativas

**Funcionário do hospital** usa sistema interno para:

- Confirmar presença
- Informar status do sangue coletado
- Atualizar prontuário

**App** se comunica com:

- Sistema hospitalar interno (para atualização de status)
- Serviços externos de CEP (durante cadastro)
- Serviços de push notification (para lembretes e alertas)

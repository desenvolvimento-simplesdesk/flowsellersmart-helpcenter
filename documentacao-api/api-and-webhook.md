---
description: Aprenda a integrar via API  WEBHOOK URL na Smart 2.0 Flowseller
icon: webhook
---

# API & WEBHOOK

### Configuração de envio API

Aqui será apresentado o uso do PUSH na Flowseller Smart 2.0\
Efetue o login na plataforma Flowseller > **Configurações > API/WEBHOOK**\\

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
PUSH: Esta função permite o envio de mensagens via API\
Cada envio, abrirá um novo ticket na fila de pendente, se não houver um ticket aberto para o contato na conexão(canal) escolhido para envio a ação após o envio permitirá fechar automaticamente ou manter o ticket aberto.\
A URL e o token podem ser gerados na plataforma. Para utilizar a URL (endpoint), basta clicar em ADICIONAR para criar a configuração para a API e preencher os campos de dados API (PUSH) como mostramos nas imagens abaixo
{% endhint %}

### Campos para preenchimento

<figure><img src="../.gitbook/assets/aqui (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

**Nome da API:** descrição do sistema externo

**Enviar por:** nome do canal do WhatsApp por onde as mensagens vão ser enviadas para o WhatsApp dos clientes.

**Ação no atendimento após o envio:**

* **Fechar:** manter na aba de fechados após o envio
* **Manter aberto:** ficar na aba de pendentes sem departamento vinculado **Redirecionar para fila:** ficar na aba de pendentes com um departamento vinculado
* **Redirecionar para usuário:** enviar para a aba de ativos de um atendente

{% hint style="info" %}
**Ação no atendimento após o envio:** essas ações só vão funcionar quando o cliente estiver na aba de fechados no atendimento ou se o contato do cliente estiver chegando pela primeira vez na plataforma. Se o cliente estiver na aba de pendentes ou na aba de ativos e for disparada uma mensagem ele vai permanecer no mesmo local, apenas receberá a mensagem do sistema externo.
{% endhint %}

### Copie o token clicando no ícone de link

<figure><img src="../.gitbook/assets/aqui (2).png" alt=""><figcaption></figcaption></figure>

Metódo POST:

```html
// Metodo post
https://URL_COPIADA_COM_TOKEN
```

### Headers

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |

### Exemplo de requisição

Para enviar apenas texto ao usuário

```json
{
   "body": "MENSAGEM", //Mensagem de texto
   "number": "5511999999999", //Celular com DDI e DDD
   "externalKey": "123456", //Valor obrigatório para possibilitar o rastreamento da mensagem
}
```

Para enviar imagens, vídeo, áudio ou documentos gerais

```json
{
   "number":"5511999999999", //Celular com DDI e DDD
   "externalKey":"123456", //Valor obrigatório para possibilitar o rastreamento da mensagem
   "body":"", //Mensagem de texto que será enviada como legenda/caption. Para não enviar deixe em branco
   "mediaUrl":"https://exemplo.com/img.png" //url da mídia > vídeo, imagem, áudio, documentos gerais
}
```

A mensagem é inicialmente adicionada em uma fila para a mensagem ser processada sequencialmente

```json
{
   "message": "Message add queue"   
}   
```

O JSON padrão e completo para o body da requisição por **WhatsApp Business:**

```json
{
  "number": "5511999999999", //número do WhatsApp do cliente (obrigatório!!!)
  "body": "seu texto aqui", //texto a ser enviado para o cliente (obrigatório!!!)
  "externalKey": "123456", //para possibilitar o rastreamento da mensagem (obrigatório!!!)
  "mediaUrl": "https://", //link de mídia. O sistema converte para arquivo e envia
  "userId": 183, //id do atendente
  "onlyNote": true, // Caso deseje enviar somente a nota interna, sem mensagem.
  "forceTicketToUser": true, // forçar ticket  para usuário (deve ser usado junto de userId)
  "forceTicketToDepartment": true, /* deve ser utilizado junto à chave queueId, se
o cliente estiver na aba de fechados ou ativos, ele vai para a aba de pendetes.
Conseguimos alternar ou adicionar o departamento ao ticket. Pode ser usado em
consjunto com as chaves forceTicketToUser e userId, forçando um ticket para um
departamento e movendo para os ativos de um atendente*/
  "queueId": "435", //id do departamento
  "forceTicketToClosed": true, /* força ticket para aba de fechado. Pode ser usado
só ou em cojunto com um motivo de fechamento através do parâmetro closingReasonId*/
  "closingReasonId": 123 // id do motivo de fechamento
  "note": { //disparar nota interna (visível apenas para o atendente)
    "body": "seu texto aqui", //texto da nota interna
    "mediaUrl": "https://" // link da mídia para nota interna
  }
}
```

**API Oficial do WhasApp (WABA):**

A url autenticada você vai encontrar no mesmo local, só que agora no item "**Enviar por",** você vai adicionar uma canal com API oficial e o **body** a ser utilizado será esse:

```json
{
  "number": "5511999999999", //número do cliente
  "templateId": "uuid-template", //hsmId
  "params": ["variavel1", "variavel2"], //caso o template tenha variáveis
  "externalKey": "valor para rastreamento",
  "userId": 123, //id do atendente
  "onlyNote": true, // Caso deseje enviar somente a nota interna, sem mensagem.
  "forceTicketToUser": true, // forçar ticket  para usuário
  "forceTicketToDepartment": true, /* deve ser utilizado junto à chave queueId, se
o cliente estiver na aba de fechados ou ativos, ele vai para a aba de pendetes.
Conseguimos alternar ou adicionar o departamento ao ticket. Pode ser usado em
consjunto com as chaves forceTicketToUser e userId, forçando um ticket para um
departamento e movendo para os ativos de um atendente*/
  "queueId": "435", //id do departamento
  "forceTicketToClosed": true, /* força ticket para aba de fechado. Pode ser usado
só ou em cojunto com um motivo de fechamento através do parâmetro closingReasonId*/
  "closingReasonId": 123 // id do motivo de fechamento
  "note": { //disparar nota interna (visível apenas para o atendente)
    "body": "seu texto aqui", //texto da nota interna
    "mediaUrl": "https://" // link da mídia para nota interna
  }
}
```

[Como encontro o hsmId?](https://ajuda.simplesdesk.com.br/documentacao-api/api-de-templates)

{% hint style="info" %}
Os itens obrigatórios para qualquer dos exemplos sempre serão o **number, o body e o externalKey.**
{% endhint %}

{% hint style="info" %}
**forceTicketToClosed** possui precedência sobre todos os outros parâmetros, o que forçará a mudança do ticket para fechado, mesmo que o ticket não tenha como origem da criação via API.

Caso **forceTicketToUser** seja utilizado com **forceTicketToDepartment**, garanta que o usuário informado possua acesso ao departamento informado.
{% endhint %}

O **Id do departamento (queueId)** é encontrado em Configurações -> Departamentos

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FwpUwDExR24R46ZvOlVd3%252Fimage.png%3Falt%3Dmedia%26token%3D23e94138-e716-4fd9-aac0-713ab50a5b11&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=fec12141&#x26;sv=2" alt=""><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FqQHQQ6g9tn8vHWgZbOQz%252Fimage.png%3Falt%3Dmedia%26token%3Dfae5d861-59ac-435d-8935-40b170fb4f92&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=7308729a&#x26;sv=2" alt=""><figcaption></figcaption></figure>

O **Id do Motivo de Fechamento (closingReasonId)** é encontrado em Configurações -> Motivos de fechamento

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FivVG36dbm93BSn2vHI4q%252Fimage.png%3Falt%3Dmedia%26token%3D3298926f-e7ba-4af4-94eb-373f3773deff&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=88f510a6&#x26;sv=2" alt=""><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FusEgFio3UNMSSnKz4hBW%252Fimage.png%3Falt%3Dmedia%26token%3Ddb70afe9-8e54-4960-b6cd-1c6e8fc4437d&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ff93199b&#x26;sv=2" alt=""><figcaption></figcaption></figure>

## Configurações do Webhook

Aqui será apresentado os demais usos do WEBHOOK na Flowseller Smart 2.0, como eventos, payloads e logs.\
Efetue o login na plataforma Flowseller > **Configurações > API/WEBHOOK**

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Esta função permite o envio de dados do contato/atendimento a partir de um determinado evento (gatilho) que ocorre na plataforma
{% endhint %}

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Dúvidas sobre o payload? Clique no ícone de "?" para obter um exemplo de Payload para cada evento disponível

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

### LOGS

É possível fazer uma pesquisa pelos logs de requisição para API (PUSH) ou envio de dados para o Webhook

<figure><img src="../.gitbook/assets/aqui (3).png" alt=""><figcaption></figcaption></figure>

### Detalhe do evento Webhook URL:

| Campo  | Descrição                         |
| ------ | --------------------------------- |
| #      | Id de identificação da requisição |
| Nome   | Nome da Api                       |
| Evento | Nome do evento na plataforma      |
| Tipo   | Webhook ou API (Push)             |
| Status | Falha ou sucesso (200)            |
| Data   | Data e hora da requisição         |
| Ação   | Detalhe do evento                 |

### Envio: Payload / Header

### Retorno: Status / Body / Header

```json
  //Payload
{
  "contact": {
  "id": 4200,
  "name": "John Doe",
  "number": "5511999999999",
  "email": "flowseller@flowseller.com.br",
  "profilePicUrl": null,
  "tags": [
    "Proposta"
    ],
    "extrainfo": [],
    "leadStatus": {
    "id": 6,
    "status": "Quente",
    }

}

//Header
{
   "Accept": "application/json, text/plain, */*,
   "Content-Type": "application/json,
   "User-Agent": "axios/0.21.4",
}

```

### Contato criado

```json
// ("event": "NewContact")

{
  "contact": {
    "id": 17256,
    "name": "Nome do Contato",
    "number": "559999009900",
    "email": "",
    "profilePicUrl": "https://pps.whatsapp.net/v/...",
    "tags": [
      "Cliente",
      "OutraTag"
    ],
    "extraInfo": [],
    "leadStatus": {
      "id": 2,
      "status": "Em atendimento ",
      "color": "#0000d6",
      "active": true,
      "createdAt": "2023-03-20T17:31:12.723Z",
      "updatedAt": "2023-03-20T17:31:12.723Z"
    }
  },
  "userId": 1,
  "tenantId": 1,
  "wallets": [
    {
      "id": 1,
      "name": "Administrador",
      "ContactWallet": {
        "id": 44,
        "contactId": 17256,
        "walletId": 1,
        "tenantId": 1,
        "createdAt": "2023-06-05T12:07:48.557Z",
        "updatedAt": "2023-06-05T12:07:48.557Z"
      }
    }
  ],
  "tenantId": 1,
  "event": "NewContact"
}
```

### Atendimento iniciado ("event":"StartedTicket")

```json
{
  "ticket": {
    "id": 9902,
    "status": "open",
    "unreadMessages": 0,
    "lastMessage": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta",
    "channel": "whatsapp",
    "answered": true,
    "isGroup": false,
    "isActiveDemand": false,
    "isCreatedAtAPI": false,
    "lastInteractionBot": "2023-06-05T12:06:38.486Z",
    "botRetries": 0,
    "closedAt": null,
    "lastMessageAt": "1685966800307",
    "startedAttendanceAt": 1685966800307,
    "userId": 1,
    "contactId": 17256,
    "whatsappId": 1,
    "autoReplyId": null,
    "setUpAutoReplyId": null,
    "chatFlowId": null,
    "stepChatFlow": null,
    "queuedId": 2,
    "closingReasonId": null,
    "tenantId": 1,
    "apiConfigId": null,
    "createdAt": "2023-06-01T13:25:05.089Z",
    "updatedAt": "2023-06-05T12:07:09.586Z",
    "contact": {
      "id": 17256,
      "name": "Nome do contato",
      "number": "559999009900",
      "email": "",
      "profilePicUrl": "https://pps.whatsapp.net/v.../",
      "pushname": "Nome do contato",
      "observations": null,
      "telegramId": null,
      "messengerId": null,
      "instagramPK": null,
      "isUser": true,
      "isWAContact": true,
      "isGroup": false,
      "leadStatusId": null,
      "tenantId": 1,
      "customFields": {
        "cpf": "12312312311"
      },
      "tags": [],
      "createdAt": "2023-05-21T21:15:15.480Z",
      "updatedAt": "2023-06-05T12:06:24.474Z",
      "extraInfo": [],
      "leadStatus": null,
      "wallets": []
    },
    "user": null,
    "tenantId": 1,
    "event": "StartedTicket"
  }
}
```

### Atendimento transferido ("event":"TransferOfTicket")

```json
{
  "ticket": {
    "id": 9902,
    "status": "open",
    "unreadMessages": 0,
    "lastMessage": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta",
    "channel": "whatsapp",
    "answered": true,
    "isGroup": false,
    "isActiveDemand": false,
    "isCreatedAtAPI": false,
    "lastInteractionBot": "2023-06-05T12:06:38.486Z",
    "botRetries": 0,
    "closedAt": null,
    "lastMessageAt": "1685966800307",
    "startedAttendanceAt": 1685966829586,
    "userId": 1,
    "contactId": 17256,
    "whatsappId": 1,
    "autoReplyId": null,
    "stepAutoReplyId": null,
    "chatFlowId": null,
    "stepChatFlow": null,
    "queuedId": 2,
    "closingReasonId": null,
    "tenantId": 1,
    "apiConfigId": null,
    "createdAt": "2023-06-01T13:25:05.089Z",
    "updatedAt": "2023-06-05T12:07:09.586Z",
    "contact": {
      "id": 17256,
      "name": "Nome do contato",
      "number": "559999099900",
      "email": "",
      "profilePicUrl": "https://pps.whatsapp.net/v/.../",
      "pushname": "Nome do contato",
      "observations": null,
      "telegramId": null,
      "messengerId": null,
      "instagramPK": null,
      "isUser": true,
      "isWAContact": true,
      "isGroup": false,
      "leadStatusId": null,
      "tenantId": 1,
      "customFields": {
        "cpf": "12312312311"
      },
      "tags": [],
      "createdAt": "2023-05-21T21:15:15.480Z",
      "updatedAt": "2023-06-05T12:06:24.474Z",
      "extraInfo": [],
      "leadStatus": null,
      "wallets": []
    },
    "user": null
  },
  "tenantId": 1,
  "event": "TransferOfTicket"
}

```

### Atualização da conexão ("event":"ConnectionStatusUpdate")

```json
{
  "connection": {
    "UrlWabaWebHook": "",
    "UrlMessengerWebHook": "",
    "id": 1,
    "name": "Linha 2",
    "qrcode": "",
    "status": "CONNECTED",
    "battery": "20",
    "plugged": false,
    "isActive": true,
    "isRejectCall": true,
    "callRejectedMessage": null,
    "isDeleted": false,
    "retries": 0,
    "isDefault": true,
    "instagramUser": null,
    "fbPageId": null,
    "type": "whatsapp",
    "number": "5599999999999",
    "phone": {},
    "tenantId": 1,
    "createdAt": "2021-03-12T02:23:17.000Z",
    "updatedAt": "2023-06-05T12:46:57.643Z",
    "chatFlowId": 1,
    "defaultQueueId": 6
  },
  "tenantId": 1,
  "event": "ConnectionStatusUpdate"
}

```

### Contato atualizado ("event":"UpdateContact")

```json
{
  "contact": {
    "id": 17256,
    "name": "Nome do Contato",
    "number": "559999099900",
    "email": "",
    "profilePicUrl": "https://pps.whatsapp.net/v/...",
    "tags": [
      "Cliente",
      "OutraTag"
    ],
    "extraInfo": [],
    "leadStatus": {
      "id": 2,
      "status": "Em atendimento",
      "color": "#0000d6",
      "active": true,
      "createdAt": "2023-03-20T17:31:12.723Z",
      "updatedAt": "2023-03-20T17:31:12.723Z",
      "userId": 1,
      "tenantId": 1
    },
    "wallets": [
      {
        "id": 1,
        "name": "Administrador",
        "ContactWallet": {
          "id": 44,
          "contactId": 17256,
          "walletId": 1,
          "tenantId": 1,
          "createdAt": "2023-06-05T12:07:48.557Z",
          "updatedAt": "2023-06-05T12:07:48.557Z"
        }
      }
    ]
  },
  "tenantId": 1,
  "event": "UpdateContact"
}

```

### Atendimento finalizado ("event":"FinishedTicket")

```json
{
  "ticket": {
    "id": 9902,
    "status": "open",
    "unreadMessages": 0,
    "lastMessage": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta",
    "channel": "whatsapp",
    "answered": true,
    "isGroup": false,
    "isActiveDemand": false,
    "isCreatedAtAPI": false,
    "lastInteractionBot": "2023-06-05T12:06:38.486Z",
    "botRetries": 0,
    "closedAt": null,
    "lastMessageAt": "1685966800307",
    "startedAttendanceAt": 1685966829586,
    "userId": 1,
    "contactId": 17256,
    "whatsappId": 1,
    "autoReplyId": null,
    "stepAutoReplyId": null,
    "chatFlowId": null,
    "stepChatFlow": null,
    "queuedId": 2,
    "closingReasonId": null,
    "tenantId": 1,
    "apiConfigId": null,
    "createdAt": "2023-06-01T13:25:05.089Z",
    "updatedAt": "2023-06-05T12:07:09.586Z",
    "contact": {
      "id": 17256,
      "name": "Nome do contato",
      "number": "559999099900",
      "email": "",
      "profilePicUrl": "https://pps.whatsapp.net/v/...",
      "pushname": "Nome do contato",
      "observations": null,
      "telegramId": null,
      "messengerId": null,
      "instagramPK": null,
      "isUser": true,
      "isWAContact": true,
      "isGroup": false,
      "leadStatusId": null,
      "tenantId": 1,
      "customFields": {
        "cpf": "12312312311"
      },
      "tags": [],
      "createdAt": "2023-05-21T21:15:15.480Z",
      "updatedAt": "2023-06-05T12:06:24.474Z",
      "extraInfo": [],
      "leadStatus": null,
      "wallets": []
    },
    "user": null
  },
  "tenantId": 1,
  "event": "FinishedTicket"
}

```

### Mensagem criada ("event":"NewMessage")

```json
{
  "message": {
    "mediaName": null,
    "mediaUrl": null,
    "msgCreatedAt": "2023-06-05T12:06:40.000Z",
    "id": "e3b501ba-91ab-4066-a8da-3b67da787f4e",
    "wabaMediaId": null,
    "isDeleted": false,
    "userId": null,
    "scheduleDate": null,
    "ticketId": 9902,
    "body": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta das 08h",
    "contactId": 17256,
    "fromMe": true,
    "read": true,
    "mediaType": "chat",
    "timestamp": "1685966800",
    "quotedMsgId": null,
    "sendType": "bot",
    "tenantId": 1,
    "note": false,
    "isTransfer": false,
    "status": "sent",
    "ack": 0,
    "messageId": "3E8073CACCBDF2B747D45E",
    "updatedAt": "2023-06-05T12:06:40.079Z",
    "createdAt": "2023-06-05T12:06:40.079Z",
    "idFront": null
  },
  "tenantId": 1,
  "event": "NewMessage"
}

```

### Atendimento atualizado ("event":"UpdateOnTicket")

```json
{
  "ticket": {
    "id": 9902,
    "status": "open",
    "unreadMessages": 0,
    "lastMessage": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta",
    "channel": "whatsapp",
    "answered": true,
    "isGroup": false,
    "isActiveDemand": false,
    "isCreatedAtAPI": false,
    "lastInteractionBot": "2023-06-05T12:06:38.486Z",
    "botRetries": 0,
    "closedAt": null,
    "lastMessageAt": "1685966800307",
    "startedAttendanceAt": 1685966829586,
    "userId": 1,
    "contactId": 17256,
    "whatsappId": 1,
    "autoReplyId": null,
    "stepAutoReplyId": null,
    "chatFlowId": null,
    "stepChatFlow": null,
    "queuedId": 2,
    "closingReasonId": null,
    "tenantId": 1,
    "apiConfigId": null,
    "createdAt": "2023-06-01T13:25:05.089Z",
    "updatedAt": "2023-06-05T12:07:09.586Z",
    "contact": {
      "id": 17256,
      "name": "Nome do contato",
      "number": "559999099900",
      "email": "",
      "profilePicUrl": "https://pps.whatsapp.net/v/...",
      "pushname": "Nome do contato",
      "observations": null,
      "telegramId": null,
      "messengerId": null,
      "instagramPK": null,
      "isUser": true,
      "isWAContact": true,
      "isGroup": false,
      "leadStatusId": null,
      "tenantId": 1,
      "customFields": {
        "cpf": "12312312311"
      },
      "tags": [],
      "createdAt": "2023-05-21T21:15:15.480Z",
      "updatedAt": "2023-06-05T12:06:24.474Z",
      "extraInfo": [],
      "leadStatus": null,
      "wallets": []
    },
    "user": null
  },
  "tenantId": 1,
  "event": "UpdateOnTicket"
}

```

### Novo atendimento ("event":"NewTicket")

```json
{
  "ticket": {
    "id": 9902,
    "status": "open",
    "unreadMessages": 0,
    "lastMessage": "Aguarde, logo você será atendido.\\nNosso atendimento atendimento é de Segunda a Sexta",
    "channel": "whatsapp",
    "answered": true,
    "isGroup": false,
    "isActiveDemand": false,
    "isCreatedAtAPI": false,
    "lastInteractionBot": "2023-06-05T12:06:38.486Z",
    "botRetries": 0,
    "closedAt": null,
    "lastMessageAt": "1685966800307",
    "startedAttendanceAt": 1685966829586,
    "userId": 1,
    "contactId": 17256,
    "whatsappId": 1,
    "autoReplyId": null,
    "stepAutoReplyId": null,
    "chatFlowId": null,
    "stepChatFlow": null,
    "queuedId": 2,
    "closingReasonId": null,
    "tenantId": 1,
    "apiConfigId": null,
    "createdAt": "2023-06-01T13:25:05.089Z",
    "updatedAt": "2023-06-05T12:07:09.586Z",
    "contact": {
      "id": 17256,
      "name": "Nome do contato",
      "number": "559999099900",
      "email": "",
      "profilePicUrl": "https://pps.whatsapp.net/v/...",
      "pushname": "Nome do contato",
      "observations": null,
      "telegramId": null,
      "messengerId": null,
      "instagramPK": null,
      "isUser": true,
      "isWAContact": true,
      "isGroup": false,
      "leadStatusId": null,
      "tenantId": 1,
      "customFields": {
        "cpf": "12312312311"
      },
      "tags": [],
      "createdAt": "2023-05-21T21:15:15.480Z",
      "updatedAt": "2023-06-05T12:06:24.474Z",
      "extraInfo": [],
      "leadStatus": null,
      "wallets": []
    },
    "user": null
  },
  "tenantId": 1,
  "event": "NewTicket"
}

```

### Status da mensagem ("event":"AckMessage")

```json
{
  "ack": 2,
  "id": "a9985ce6-671a-4de9-b7a0-ce4791fdd95fc",
  "messageId": "3EBD81AFDAE68EAFBBC2F2",
  "ticketId": 9902,
  "tenantId": 1,
  "event": "AckMessage"
}

```

Caso tenha alguma dúvida, é só chamar nosso time de suporte da Flowseller. Ou, se preferir, chame através do nosso WhatsApp. 😉

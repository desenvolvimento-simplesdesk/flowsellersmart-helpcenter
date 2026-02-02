---
description: Encontrar e disparar um template por API
icon: whatsapp
---

# Api de Templates

O jeito mais fácil de encontrar os hsmId's é indo para o **Menu suspenso -> Configurações -> Templates**

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/WhatsApp Image 2025-06-25 at 13.00.16 (1).jpeg" alt=""><figcaption><p>A última coluna é referente ao hsmId</p></figcaption></figure>

Outra forma para encontrar os hsmId (id's dos templates da API oficial do WhatsAPP via API) é por meio da url autenticada. Comece copiando ela:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FIlZO50INCol4xxc4AjzZ%252Fimage.png%3Falt%3Dmedia%26token%3Da09a0e99-a175-48bb-be34-1976d9af4b5a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=c0a1420d&#x26;sv=2" alt=""><figcaption></figcaption></figure>

E adicione a palavra template entre a palavra external e o token: **external/template/{token}**

```
https://enterprise-90api.simplesdesk.com.br/v1/api/external/template/5953c4c9-e54e-4bec-ae64-f2ee8bfaee96/?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZW5hbnRJZCI6MjUsInByb2ZpbGUiOiJhZG1pbiIsInNlc3Npb25JZCI6NjAsImNoYW5uZWxUeXBlIjoid2hhdHNhcHAiLCJpYXQiOjE3Mjc5NzQ5OTcsImV4cCI6MTc5MTA0Njk5N30.-c_D_2aQBSJjMV1ASLsXZDyg9wsT_OTkZ9n99m4M8oU
```

Agora só adicionar em um ambiente de requisição (Postman ou Insomnia), ou colar o link na barra de endereço do seu navegador e teclar enter que você terá um JSON com um array de objetos.

```
[
  {
    "id": 3352,
    "hsmId": "a46c4e95-0e50-555-be86-5a4041855dc0",
    "name": "nome_template",
    "category": "MARKETING",
    "language": "pt_BR",
    "preview": "Olá, tudo bem?\n Isso é uma mensagem teste",
    "templateType": "text",
    "templateMediaId": null,
    "status": "APPROVED",
    "whatsappId": 99999,
    "components": null,
    "tenantId": 999999,
    "deletedAt": null,
    "createdAt": "2024-09-30T12:04:36.368Z",
    "updatedAt": "2024-09-30T12:04:36.368Z"
  }
]
```

Você encontra essa informação em Configurações -> API/Webhook -> Documentação

![](https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FMWBY5En9p27PDxZz5FCe%252Fimage.png%3Falt%3Dmedia%26token%3D8031874e-b931-4691-bf91-0bb6e03e6039\&width=768\&dpr=4\&quality=100\&sign=a14574b0\&sv=2)![](https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F1sXIJzH1Jq4NCUIEvTqX%252Fimage.png%3Falt%3Dmedia%26token%3D39157400-a4ea-471d-9296-a1f0d65c91d7\&width=768\&dpr=4\&quality=100\&sign=6e8da795\&sv=2)

Na imagem acima, é só adicionar apenas o token que você também consegue ver os dados do template Id.

Você só vai conseguir visualizar os templates quando o endpoint que foi gerado tiver sido associado a um canal com a API oficial.

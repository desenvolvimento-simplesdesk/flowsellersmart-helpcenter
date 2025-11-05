---
description: >-
  Conseguimos criar contatos (POST), buscar vários contatos (GET), buscar um
  contato pelo seu id (GET) e editar um contato (PATCH).
icon: address-card
---

# API de Contatos

## Criação, busca e alteração de contato

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fep4mT3y9xZvGGzXIG87I%252Fimage.png%3Falt%3Dmedia%26token%3Ddc002f48-0117-4f56-9bcc-f1b940e65d02&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=af4505ab&#x26;sv=2" alt="" width="563"><figcaption></figcaption></figure>

Url da documentação (Solicite para a equipe de suporte o link direto do seu servidor)

`https://enterprise-90api.simplesdesk.com.br/v1/contacts/docs#`

{% hint style="info" %}
Lembrando que o **número 40** tem que ser alterado para o número do seu servidor e o **seu\_dominio** deve ser alterado pelo nome que consta na url do seu sistema. Consulte a equipe de suporte
{% endhint %}

Os endpoints serão esses:

`https://enterprise-90api.simplesdesk.com.br/v1/contacts/`

`https://enterprise-90api.simplesdesk.com.br/v1/contacts/id_contato`

{% hint style="info" %}
Caso seja necessário, temos a [variável interna](https://ajuda.simplesdesk.com.br/documentacao-api/variaveis) \{{id\}} que pega o valor do id do contato.
{% endhint %}

Esses endpoints vão precisar de um cabeçalho:

```json
{
    "Authorization": "Bearer token"
}
```

O token é gerado quando você cria seu PUSH:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FJHANLdaPG29i5VSdQhLN%252Fimage.png%3Falt%3Dmedia%26token%3D4526fdfb-2d44-4d3a-b165-e6486bdd5926&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=38083dcc&#x26;sv=2" alt=""><figcaption></figcaption></figure>

**Atualizações 15/01/2025**

Com a nova atualização, vamos conseguir **alterar, deletar ou adicionar campos customizados e/ou etiquetas**. Outro ponto é uma rota para **buscar clientes por número de WHATSAPP** (antes só era feito através do id do cliente).

Antes de explicar cada ponto, segue o payload completo do método **PATCH:**

```json
{
  "name": "string",
  "email": "string",
  "number": "string",
  "customFields": "{ 'field1': 'value1', 'field2': 'value2' }",
  "tags": [
    "string"
  ]
}
```

Ou pode ser utilizado dessa forma:

```json
{
"customFields": "{ 'field1': 'value1', 'field2': 'value2' }",
  "tags": [
    "string"
  ]
}
```

## Alterar, adicionar ou deletar campos customizados <a href="#alterar-adicionar-ou-deletar-campos-customizados" id="alterar-adicionar-ou-deletar-campos-customizados"></a>

Vamos supor que o cliente tem 3 campos customizados e apenas o **cpf\_cliente** está preenchido:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FJGBwmIRolk2YTqsmZDku%252Fimage.png%3Falt%3Dmedia%26token%3D09e690f4-b05a-4cee-a44e-853050d9711f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2daa9a65&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Se for feita uma requisição para adicionar o campo **nome\_cliente,** o campo **cpf\_cliente** vai ser apagado e vai aparecer o valor do campo **nome\_cliente.**

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F1LXgzFOlkwo4uei1cKKa%252Fimage.png%3Falt%3Dmedia%26token%3Ddbcbb19e-06ef-4c87-ad51-881d764634ab&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=89fbb6ce&#x26;sv=2" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Mas e se eu quiser adicionar ou alterar apenas um campo, como eu faço? Pois quero manter os antigos e alterar/adicionar apenas um campo.
{% endhint %}

{% stepper %}
{% step %}
### 1. Faça uma requisição anterior

Busque primeiro o contato via API, através do ID ou do número de WhatsAPP
{% endstep %}

{% step %}
#### Vefique os campos customizados atuais <a href="#vefique-os-campos-customizados-atuais" id="vefique-os-campos-customizados-atuais"></a>

Veja quais campos já existem, adicione todos na requisição **PATCH** e altere apenas o valor que você quer adicionar&#x20;
{% endstep %}
{% endstepper %}

Você pode passar apenas o item **customFields** na requisição:

```json
{
    "customFields": "{ 'field1': 'value1', 'field2': 'value2' }"
}
```

Para zerar todos os valores dos Campos Customizados é só fazer isso:

```json
"customFields": "{}"
```

## Alterar, adicionar ou deletar campos etiquetas <a href="#alterar-adicionar-ou-deletar-campos-etiquetas" id="alterar-adicionar-ou-deletar-campos-etiquetas"></a>

Diferente dos Campos Customizados, se você adiciona apenas uma etiqueta, as que já estavam vinculadas ao cliente não vão ser deletadas. Você também pode adicionar apenas o item tags no payload:

```json
{
    "tags": ["VIP", "Indicação"]
}
```

E para zerar as etiquetas é só deixar o array vazio:

```json
{
    "tags": []
}
```

## Buscar contatos por número de WhatsAPP <a href="#buscar-contatos-por-numero-de-whatsapp" id="buscar-contatos-por-numero-de-whatsapp"></a>

Forma antiga que está mantida **(BUSCA POR ID)**

```
https://enterprise-90api.simplesdesk.com.br/v1/contacts/id_contato
```

Só que quando precisamos buscar esse contato externamente, é complicado, pois é necessário buscar ele através do id do cliente no nosso sistema. Para resolver essa situação foi criado um recurso novo no endpoint para buscar clientes por número de WhatsApp.

```
https://enterprise-90api.simplesdesk.com.br/v1/contacts/number/numero_whatsapp
```

{% hint style="info" %}
O numero\_whatsapp precisa estar com o DDI e DDD, sem espaços e sem caracteres especiais. Ex.: 5573950111111
{% endhint %}

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fyg7cEqQuJvkvBJWUOwij%252Fimage.png%3Falt%3Dmedia%26token%3Dfcd0ed54-a467-462e-8123-a98f9172dac9&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=5b1f48e2&#x26;sv=2" alt=""><figcaption></figcaption></figure>

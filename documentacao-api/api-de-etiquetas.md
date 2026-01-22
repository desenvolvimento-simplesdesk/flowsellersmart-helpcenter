---
description: Criar, buscar e deletar etiquetas em configurações via API
icon: tag
---

# API de Etiquetas

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FicjawbOuFHAjcWnGJKSu%252Fimage.png%3Falt%3Dmedia%26token%3De8eb1958-85fa-4bc2-b082-0dbbe64a7c22&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2c23f071&#x26;sv=2" alt=""><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fb9T8Q4egZWboR1bCS67a%252Fimage.png%3Falt%3Dmedia%26token%3D190d9d94-870d-4231-bf02-ab0470decd34&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2d1219fd&#x26;sv=2" alt=""><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F13qZ4H5OOuMblVA7U5TN%252Fimage.png%3Falt%3Dmedia%26token%3Ddc7c8446-4dd1-457e-a65f-31ca2f54b930&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=84238080&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Agora só copiar a url e o token:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FzgJzxSniTstvKmm9wTKN%252Fimage.png%3Falt%3Dmedia%26token%3Df3bd0680-4356-4b63-9e34-03c35454f85d&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=44d08db5&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Teremos 3 métodos:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F4QDoSgsRxAo6G06945VJ%252Fimage.png%3Falt%3Dmedia%26token%3D7d8a9505-adb4-4674-8159-d1731916d3c6&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=762eea96&#x26;sv=2" alt=""><figcaption></figcaption></figure>

* **GET (buscar todas as etiquetas):** o token vai no Header da requisição. "Authorization": "Bearer seu\_token". Você também precisa adicionar **/tags** no final da url. A resposta será um array de objetos contendo todas as etiquetas, e cada item terá os seguintes parâmetros: id, tag, color, isActive, userId, tenantId, createdAt, updatedAt
* **POST (criar uma ou mais etiquetas):** o token vai no Header da requisição. "Authorization": "Bearer seu\_token". Você também precisa adicionar **/tags** no final da url. O BODY da requisição será esse:

```
[
  {
    "tag": "Tag 1",
    "color": "#FF0000",
    "userId": null
  },
  {
    "tag": "Tag 2",
    "color": "#00FF00",
    "userId": null
  },
  {
    "tag": "Tag 3",
    "color": "#0000FF",
    "userId": null
  }
]
```

Você vai precisar passar um Id de usuário, pois as etiquetas são criadas fazendo esse vínculo, se deixar o userId = null, não vai criar. Você pode criar uma ou mais de uma etiqueta.

* **DELETE (deletar etiquetas):** o token vai no Header da requisição. "Authorization": "Bearer seu\_token". Você também precisa adicionar **/tags/id\_etiqueta** no final da url.

Você também pode encontrar essas informações em Configurações -> Api/Webhook -> documentação

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

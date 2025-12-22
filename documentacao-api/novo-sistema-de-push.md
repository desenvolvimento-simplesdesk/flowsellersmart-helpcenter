---
description: >-
  Mapeando o JSON que está chegando de outra plataforma e disparando uma
  mensagem personalizada para o cliente.
icon: webhook
---

# Novo sistema de Push

## Procure por "Push" no menu suspenso à esquerda

<figure><img src="../.gitbook/assets/aqui (1).png" alt="" width="227"><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F6w0SRYt1p4UFhlzuXauD%252Fimage.png%3Falt%3Dmedia%26token%3Dd735c853-cc5e-4d21-8c28-41f1463863a0&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=807fff79&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Clicamos em **NOVO PUSH:**

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FzEDeWZabJQtiPzMX5el9%252Fimage.png%3Falt%3Dmedia%26token%3Db7ce2b71-b2bb-48b9-8bf9-d14ea2a94c15&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=cee5f5d7&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Você vai digitar o nome do PUSH, escolher a plataforma, e selecionar por qual canal você vai enviar (WhatsApp Business ou API oficial do Whatsapp).

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fkxascv9oWeElyQW4pm6Q%252Fimage.png%3Falt%3Dmedia%26token%3Da65dad69-905e-41fc-9997-0698f09098ba&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=cacf3dab&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Na imagem acima temos duas setas verdes, uma apontando para o RD Station e outra para o nome Personalizado. Você pode fazer a integração com o RD em ambos os casos. A única diferença é que no primeiro já foi hologado no sistema os eventos do RDStation.

Em alguns casos é interessante utilizar o modo **Personalizado** pois você consegue visualizar o [**JSON** ](https://ajuda.simplesdesk.com.br/documentacao-api/o-que-e-um-json)atual que está sendo enviado através do evento na plataforma externa.

### Como descobrir qual o JSON que o sistema externo envia? <a href="#como-descobrir-qual-o-json-que-o-sistema-externo-envia" id="como-descobrir-qual-o-json-que-o-sistema-externo-envia"></a>

Adicione qualquer json de teste:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FFbepwR9RMagXGo77GDWD%252Fimage.png%3Falt%3Dmedia%26token%3Dcb70e3b7-f743-4645-87d9-594ebc3f03bf&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=7e9a392e&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Adicione uma mensagem aleatória, um modelo de número qualquer e um Nome do Lead qualquer e clique em salvar.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FkP3gRvIAeii7v0vukZN7%252Fimage.png%3Falt%3Dmedia%26token%3Dc4677faf-e73e-4738-a2a4-318006ec7eda&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=342a1e9d&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Agora só copiar a url/endpoint que já vem autenticada e adicionar na parte de requisições/Webhooks do sistema externo.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fhq763o757Sv8SdMOahxP%252Fimage.png%3Falt%3Dmedia%26token%3D78563e46-dbfc-457a-8351-c773d23af2ad&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=63607e78&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Agora só ir em **HISTÓRICO DE ENVIOS** e ver o **JSON** que foi enviado:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F4kx2wJ2QNRxkHRQs3SID%252Fimage.png%3Falt%3Dmedia%26token%3De124dd4c-b5fc-4a95-9a56-f137a6fa61ce&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=3d8517ea&#x26;sv=2" alt=""><figcaption></figcaption></figure>

A mensagem de falha está correta, nesse primeiro momento estamos apenas pegando o modelo do **JSON.** Agora é só clicar em **Detalhes:**

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FPt8sWBdibaeTr2ihsRMD%252Fimage.png%3Falt%3Dmedia%26token%3D443d6431-7f85-4714-810a-abeba80a49d5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2c22aa15&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Agora só copiar o JSON:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fk8PxWck8jaqitpNYDMKL%252Fimage.png%3Falt%3Dmedia%26token%3D8e32b49b-fff5-4320-9ee1-8fd48cf64578&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=1afa1832&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Volta na página inicial do PUSH, e clique em editar:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F700q6G11BskFOg719b53%252Fimage.png%3Falt%3Dmedia%26token%3D4812e48f-8b2b-486a-b60c-42dae22a51c1&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=703dcab5&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Cole o JSON copiado no modelo de dados:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FnzhcPtOf54c8pYZCZPqZ%252Fimage.png%3Falt%3Dmedia%26token%3Da3c5d4e6-8175-4b5d-8995-5f732017af74&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=de973c8e&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Personalize a mensagem com as variáveis que foram mapeadas no JSON:

![](https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fp9ZL86ODj9z9aZlrJBOi%252Fimage.png%3Falt%3Dmedia%26token%3Dec31e0c0-f873-46f5-87cb-513ad7ee9341\&width=768\&dpr=4\&quality=100\&sign=bba082f2\&sv=2) ![](https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FA0NLieTqgepLXAQwE96p%252Fimage.png%3Falt%3Dmedia%26token%3Df10776d4-ff1b-487a-913e-df98fc54ecb9\&width=768\&dpr=4\&quality=100\&sign=a35db14f\&sv=2)

Adicione a variável do JSON referente ao número de whatsapp do cliente. Se a variável vir sem o DDI (55), adicione antes e coloque a variável depois:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FsgssxmUGI3Jap8hUlxDS%252Fimage.png%3Falt%3Dmedia%26token%3D9d64d654-d7de-4313-a6e8-8f4f3ebb956a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b4740c38&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Em **Arquivo** você vai adicionar algum link de mídia que vem no JSON. Esse link vai ser convertido em arquivo nativo e enviado junto a mensagem:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FJbHI8CkQfheufcgtneGe%252Fimage.png%3Falt%3Dmedia%26token%3D5af6b8b0-66e4-448b-b6f1-77f43145c19f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=97cf1f9b&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Quando adicionamos o Nome do lead, o valor vai ficar salvo direto no nome principal do cliente no sistema:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FsuDq3fqM9aaM2tiggYTg%252Fimage.png%3Falt%3Dmedia%26token%3Dccf0f93b-e565-4d90-8350-4d2f47100428&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=55b79425&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Depois é só clicar em Salvar que, a partir de agora, toda vez que a ação ocorrer no sistema externo irá ser disparado uma mensagem para o cliente.

## Novo Push e API Oficial do WhatsApp

A única coisa que vai mudar na API oficial é que vamos utilizar os templates, que são as mensagens aprovadas pela Meta.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FjjPqP1fFWkxzNvKzQGYD%252Fimage.png%3Falt%3Dmedia%26token%3D7f431f4b-c12f-4662-9c15-8ff01c294822&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b69db8a2&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Você também pode pegar os dados que chegam no JSON e vincular com as variáveis do seu template para personalizar a mensagem.

### Atualizações 15/01/2025 <a href="#atualizacoes-15-01-2025" id="atualizacoes-15-01-2025"></a>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F7XqNO9Z87rqaiRctM5t3%252Fimage.png%3Falt%3Dmedia%26token%3D0c66d80b-7513-43c9-a60b-9d7acbb88222&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=32560e81&#x26;sv=2" alt=""><figcaption></figcaption></figure>

1. A aba **ENVIO** não tem nenhuma funcionalidade nova, é apenas a parte onde adicionamos a mensagem, adicionamos o modelo do número, o link de arquivo e o nome do lead.
2. Na aba **CONDIÇÕES** você vai decidir se vai enviar ou não a mensagem para o cliente a depender de condições em cima dos dados que chegam no [JSON](https://ajuda.simplesdesk.com.br/documentacao-api/o-que-e-um-json). Você também vai conseguir adicionar etiquetas e status do lead.
3. Na terceira aba, você vai conseguir adicionar um **FUNIL** de mensagens naquele cliente.

#### Aba CONDIÇÕES <a href="#aba-condicoes" id="aba-condicoes"></a>

Você precisa ativar condições:

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F85RY6jVe5geUJkFPsseA%252Fimage.png%3Falt%3Dmedia%26token%3D175e4fae-e743-4d39-89e8-13d7cd0ccd5c&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=48f00bd1&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Depois você vai precisar selecionar se todas as condições precisam ser verdadeira para enviar a mensagem ou se pelo menos alguma precisa ser verdadeira para fazer os envios.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252Fw4JGenfxarmjiKKmxNkN%252Fimage.png%3Falt%3Dmedia%26token%3Dea2ebeeb-432d-461f-be10-b445b1ca0e48&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=37bed3ba&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Você pode enviar a mensagem ou não apenas com uma ou mais condições, sem escolher uma ação.

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FlnsgGu0eezEQKWayY5Ql%252Fimage.png%3Falt%3Dmedia%26token%3Dc073bfbb-255d-45c2-8239-a5f806ab636a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=dc205c57&#x26;sv=2" alt="" width="563"><figcaption><p>Duas condições sem ação</p></figcaption></figure>

Vamos ter **6 OPERADORES** para validar os dados:

* É igual
* É diferente
* Contém
* Não contém
* Inicia com
* Termina com

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FqDVmE34stcyN7RCgQ5wS%252Fimage.png%3Falt%3Dmedia%26token%3Dbf1993ea-19fc-4027-a882-09940d72f5ba&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ad346a00&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Os 5 campos das condições são:

1. A variável que você busca no modelo de dados ([JSON](https://ajuda.simplesdesk.com.br/documentacao-api/o-que-e-um-json))
2. O operador
3. O valor que você adiciona manualmente para comparar com o valor da variável do campo 1
4. Ação de adicionar etiqueta ou status do lead
5. Valor da etiqueta ou status do lead a ser adicionado

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FtHB9TIxhXnj9Tzx16KDv%252Fimage.png%3Falt%3Dmedia%26token%3Da4c41b99-8355-4357-9c6b-860918ebcd5f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=822d015d&#x26;sv=2" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Se você tiver um funil vinculado ao status do lead, não vai acionar. Para isso temos a aba FUNIL no PUSH
{% endhint %}

{% hint style="info" %}
Você só vai conseguir adicionar uma etiqueta por configuração mas, claro, podem ter várias condições com etiquetas diferentes, mas apenas uma vai ser adicionada de acordo com os dados que chegam no [JSON](https://ajuda.simplesdesk.com.br/documentacao-api/o-que-e-um-json).
{% endhint %}

## Aba FUNIL

Utilizada para vincular um funil de mensagens. É só Selecionar o funil e você ainda tem a opção de adicionar ou remover um funil de mensagens.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F4UJtHSwHCa5QjDKjHEHc%252Fimage.png%3Falt%3Dmedia%26token%3D7ae0d4cc-7662-4f66-b5b8-87b4e2cd29f5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=f05e2432&#x26;sv=2" alt=""><figcaption></figcaption></figure>

---
description: Variáveis internas do sistema
---

# 💡 Variáveis

Temos 4 tipos de variáveis em nosso sistema, as **nativas (implícitas e explícitas)**, as **customizadas e** as **temporárias (de condições e de retorno de API)**

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F5pA0bcq6z1Dktb6jzudA%252Fimage.png%3Falt%3Dmedia%26token%3D8bc535a7-810f-4640-8bf4-f6c7b53abfab&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=e5200089&#x26;sv=2" alt=""><figcaption></figcaption></figure>

No botão informado na imagem acima conseguimos ver as **variáveis nativas explicitas e as variáveis customizadas.** Já as variáveis temporárias são criadas apenas no fluxo do chatbot e ela são úteis para apresentar o seu valor de forma instantânea, já que não são salvas no banco de dados, elas nascem no bot e morrem quando o cliente sai dele.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252F5iF9BKgeD9O5LO0ZDobw%252Fimage.png%3Falt%3Dmedia%26token%3D2a13c307-3916-473f-aa52-1c20d13675d9&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=de0cd957&#x26;sv=2" alt=""><figcaption><p>Variável temporária de condição</p></figcaption></figure>

Já as **variáveis customizadas** são criadas em Configurações -> Campos Customizados. Se você quiser utilizar os Campos Customizados apenas para armazenar informação você pode adicionar caracteres especiais, mas se precisar utilizar como variável, precisa seguir um padrão: só letra minúscula e \_, sem caracteres especiais e sem espaços.

| Usar como variável e registro de dados | Apenas para Registro de dados |
| -------------------------------------- | ----------------------------- |
| cpf\_cliente                           | CPF cliente                   |
| data\_nascimento                       | Data                          |
| cep                                    | cep cliente                   |

## Como apresentar variáveis para os clientes? <a href="#como-apresentar-variaveis-para-os-clientes" id="como-apresentar-variaveis-para-os-clientes"></a>

Toda apresentação de variável vai se dar entre chaves duplas **\{{variavel\}}**

### Nativas explícitas <a href="#nativas-explicitas" id="nativas-explicitas"></a>

**\{{nome\}}** = **vai pegar o nome do cliente que está vinculado ao perfil dele**

![](https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FhN86qzts93hwyw6TzKGY%252Fimage.png%3Falt%3Dmedia%26token%3D584bcd5b-46be-4433-8dce-68862806748a\&width=768\&dpr=4\&quality=100\&sign=62c6f8a0\&sv=2)nome

**\{{saudacao\}} =** Bom dia, Boa tarde ou Boa noite. O sistema já utiliza um desses 3 valores, a depender do horário do dia.

**\{{protocolo\}} =** identificador daquele atendimento.

<figure><img src="https://docs-68.gitbook.io/documentacao/~gitbook/image?url=https%3A%2F%2F713010078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FWFwfQplhdVcaoBAx0CdD%252Fuploads%252FpMo8qmHKKb0yEAiouO3I%252Fimage.png%3Falt%3Dmedia%26token%3D2c19771f-09c0-4e72-aed8-a55ca4b7a6d1&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=c8f336cb&#x26;sv=2" alt=""><figcaption><p>Número de protocolo no atendimento</p></figcaption></figure>

**\{{dia\}} =** dia atual DD/MM/AAAA

**\{{hora\}} =** hora atual hh:mm:ss

**\{{milisegundos\}} =** total de milisegundos de 1º de janeiro de 1970 às 0h até o horário atual

### Nativas Implícitas <a href="#nativas-implicitas" id="nativas-implicitas"></a>

**\{{number\}} =** número do cliente

**\{{tags\}} =** todas as tags do cliente separadas por vírgula

**\{{leadStatus.status\}} =** status do lead do cliente

**\{{id\}} =** id do contato

**\{{user.id\}} =** id do usuário (atendente)

**\{{user.name\}} =** nome do usuário (atendente)

**\{{dia\_atual\}} =** apenas o o número do dia

**\{{mes\_atual\}} =** apenas o mês atual

**\{{ano\}} =** apenas o ano atual

**\{{queue.queue\}} =** nome do departamento do ticket

{% hint style="info" %}
Toda variável nativa tem seu valor atribuído de forma automática pelo sistema
{% endhint %}

{% hint style="danger" %}
Variáveis customizadas e temporárias (de condições e de retorno de API) precisam ter um valor atribuído
{% endhint %}

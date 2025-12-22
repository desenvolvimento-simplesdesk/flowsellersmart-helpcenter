---
description: Integrações e mapeamento de respostas via ChatBot
icon: robot
---

# Chatbot

As integrações via **ChatBot** são feitas via requisições a API's externas. Nas etapas do **chatbot, em condições -> rotear para -> API** conseguimos buscar ou enviar dados para plataformas externas.

Vou utilizar o sistema SGP como exemplo:

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

Pergunto o CPF ou CNPJ e salvo o valor que o cliente digita em uma [variável temporária](https://ajuda.simplesdesk.com.br/documentacao-api/chatbot/variaveis) (se encontra no campo "Guardar resposta na variável").-

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

Você vai escolher o método, adicionar o endpoint/url externo(a). No endpoint eu consigo adicionar variáveis caso a API exija. Ex.: https://endpointteste.com/api/\{{cpf\_cnpj\}}

Na imagem abaixo nunca utilize os campos que estão com as setas na cor verde.

Para o caso de **Parâmetros da requisição,** sempre utilize esses parâmetros direto na URL.

Adicione as autorizações, caso seja necessário, ou nos **Cabeçalhos da requisição** ou no **Body da requisição** e adicione os demais dados solicitados pela API.

O **Mapeamento da Resposta** é onde vamos pegar os dados retornados pela API externa e apresentar para o cliente na próxima etapa. O item "contratos" que está com a seta vermelha é uma variável temporária que recebe o valor de contratos (em verde), que é o retorno da API.

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

No caso acima, contratos vai ser um Array.

```json
{
  "msg": "Contrato(s) Localizado(s)",
  "contratos": [
    {
      "telefones_cargos": [
        {
          "cargo": null,
          "contato": "(55) 94643-1198",
          "nome": null
        }
      ],
      "cobPermuta": false,
      "servico_tipo_conexao": "PPPoE",
      "contratoCentralSenha": "centraldoassinante",
      "endereco_complemento": null,
      "popNome": "Renascer/RJ",
      "link_quitacao": "https://demo.sgp.net.br/api/declaracao/quitacao/FyXoZQrGyBYLEmI=/e3d86a6d9c8c6ba7b47625852f925d76/2023",
      "contratoStatus": 3,
      "servico_wifi_channel": "auto",
      "dataCadastro": "09/06/2022 16:34:10",
      "endereco_uf": "BA",
      "servico_plano": "*400MB FIBRA RURAL",
      "endereco_pontoreferencia": "ESCOLA JOÃO ELVAS",
      "servico_vlan": "None",
      "cobIsento": 0,
      "cpfCnpj": "00.111.222/0001-33",
      "servico_mac2": "",
      "endereco_logradouro": "RUA DA LADEIRA",
      "dataNascimento": "1998-07-12",
      "contratoStatusModo": 1,
      "telefones": [
        "(55) 94643-1198"
      ],
      "contratoStatusDisplay": " Cancelado",
      "contratoCentralLogin": "14998963015",
      "tags": [],
      "contratoTitulosAReceber": 2,
      "servico_wifi_ssid_5": "",
      "servico_grupo": "fibra",
      "endereco_numero": null,
      "contratoValorAberto": 0,
      "planointernet": "*400MB FIBRA RURAL",
      "clienteId": 41,
      "endereco_bairro": "LADEIRA",
      "emails": [],
      "razaoSocial": "NOVA SOLUTECH",
      "servico_mac": "",
      "servico_wifi_password_5": "",
      "popId": 116,
      "endereco_cep": "64970-000",
      "promessasPagamentoMes": 0,
      "servico_wifi_password": "",
      "endereco_cidade": "PARNAGUA",
      "servico_senha": "silva",
      "dataAlteracao": "03/11/2023 17:55:42",
      "servico_login": "henrique.silva",
      "servico_wifi_channel_5": "auto",
      "servico_wifi_ssid": "",
      "contratoId": 308,
      "endereco_ll": ""
    },
    {
      "telefones_cargos": [
        {
          "cargo": null,
          "contato": "(55) 94643-1198",
          "nome": null
        }
      ],
      "cobPermuta": false,
      "servico_tipo_conexao": "PPPoE",
      "contratoCentralSenha": "8s3hbzp9",
      "endereco_complemento": "PROXIMO A ESCOLA MILITAR",
      "popNome": "TANQUE NOVO/BA",
      "link_quitacao": "https://demo.sgp.net.br/api/declaracao/quitacao/Tn0aA4ZObAvlWno=/e7510ab6781d6afca6055048880094ad/2023",
      "contratoStatus": 3,
      "servico_wifi_channel": "auto",
      "dataCadastro": "19/05/2023 03:33:27",
      "endereco_uf": "AM",
      "servico_plano": "500MB - MOVI TELECOM",
      "endereco_pontoreferencia": "CMPMVI",
      "servico_vlan": "None",
      "cobIsento": 0,
      "cpfCnpj": "68.857.751/0001-62",
      "servico_mac2": "",
      "endereco_logradouro": "RUA RIO ARAPORIS (RES V MELHOR)",
      "dataNascimento": "1998-07-12",
      "contratoStatusModo": 1,
      "telefones": [
        "(55) 94643-1198"
      ],
      "contratoStatusDisplay": " Cancelado",
      "contratoCentralLogin": "novasolutech",
      "tags": [],
      "contratoTitulosAReceber": 8,
      "servico_wifi_ssid_5": "",
      "servico_grupo": "fibra",
      "endereco_numero": 203,
      "contratoValorAberto": 709.3,
      "planointernet": "500MB - MOVI TELECOM",
      "clienteId": 41,
      "endereco_bairro": "LAGO AZUL",
      "emails": [],
      "razaoSocial": "NOVA SOLUTECH",
      "servico_mac": "",
      "servico_wifi_password_5": "",
      "popId": 18,
      "endereco_cep": "69018-572",
      "promessasPagamentoMes": 0,
      "servico_wifi_password": "",
      "endereco_cidade": "MANAUS",
      "servico_senha": "centraldoassinate",
      "dataAlteracao": "25/10/2023 09:53:39",
      "servico_login": "novasolutech",
      "servico_wifi_channel_5": "auto",
      "servico_wifi_ssid": "",
      "contratoId": 595,
      "endereco_ll": ""
    }
  ]
}
```

Eu poderia mapear o item **"msg"**  e no mapeamento ficaria assim:

![](<../.gitbook/assets/image (75).png>)\


E na próxima etapa do chatbot imprimir essa mensagem mapeada acima assim:

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

Mas no caso do Array **"contratos",** queremos imprimir todos os **contratoId's** desse cliente.

Para imprimir dados de um Array de objetos na caixa de mensagem de integrações vamos fazer dessa forma:

```json
{{#contratos}}
{{contratoId}}
{{/contratos}}
```

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

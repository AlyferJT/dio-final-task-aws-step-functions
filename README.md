# DIO - Desafio final - Step Functions

# Assistente de Delivery com AWS Step Functions e Amazon Bedrock  

## Introdução  

Este projeto tem como objetivo desenvolver um Assistente de Delivery que utiliza AWS Step Functions e Amazon Bedrock para orquestrar e automatizar o fluxo de pedidos de delivery, desde a recepção do pedido até a entrega final. Durante este processo, diferentes serviços AWS serão integrados para garantir eficiência e proporcionar uma ótima experiência ao cliente.  

## Objetivos do Projeto  

- Criar um fluxo automatizado de gerenciamento de pedidos.  
- Integrar validação de pedidos e serviços de pagamento.  
- Atualizar o status do pedido em tempo real.  
- Utilizar Amazon Bedrock para personalização do assistente, proporcionando uma experiência otimizada ao cliente.  

## Tecnologias Utilizadas  

- **AWS Step Functions**: Para orquestrar o fluxo de trabalho entre diferentes serviços da AWS.  
- **Amazon Bedrock**: Para melhorar a personalização e eficiência do assistente.  
- **AWS Lambda**: Para implementar funções que processam eventos e interagem com outros serviços.  
- **AWS API Gateway**: Para criar APIs que permitem a comunicação entre o assistente e os usuários.  

## Estrutura do Projeto  

```plaintext  
/assistente-delivery  
|-- README.md  
|-- lambda/  
|   |-- validar_pedido.py  
|   |-- processar_pagamento.py  
|   `-- atualizar_status.py  
|-- step_functions/  
|   `-- fluxo_pedido.asl.json  
`-- docs/  
    `-- arquitetura.pdf
```

## Passos para Implementação
1. Criar as Funções Lambda:

- Implementar a função validar_pedido.py para verificar se o pedido está correto e disponível.
- Implementar processar_pagamento.py para integrar com um serviço de pagamento.
- Implementar atualizar_status.py para enviar atualizações sobre o status do pedido.

2. Configurar AWS Step Functions:
- Criar uma máquina de estados (State Machine) no formato ASL (Amazon States Language) que orquestra as funções Lambda criadas.
Exemplo de definição da máquina de estados:
```
{  
  "Comment": "Fluxo de pedidos de delivery",  
  "StartAt": "ValidarPedido",  
  "States": {  
    "ValidarPedido": {  
      "Type": "Task",  
      "Resource": "arn:aws:lambda:REGIÃO:ACCOUNT_ID:function:validar_pedido",  
      "Next": "ProcessarPagamento"  
    },  
    "ProcessarPagamento": {  
      "Type": "Task",  
      "Resource": "arn:aws:lambda:REGIÃO:ACCOUNT_ID:function:processar_pagamento",  
      "Next": "AtualizarStatus"  
    },  
    "AtualizarStatus": {  
      "Type": "Task",  
      "Resource": "arn:aws:lambda:REGIÃO:ACCOUNT_ID:function:atualizar_status",  
      "End": true  
    }  
  }  
}
```

3. Implementar o Amazon Bedrock:
- Utilizar a API do Amazon Bedrock para melhorar a experiência do assistente com recomendações personalizadas, aprendendo com as interações dos usuários.


## Aprendizados
Neste curso de introdução à engenharia de prompts, aprendi como maximizar a capacidade da IA generativa e aplicar na automação de fluxos de trabalho. Em particular, adquiri habilidades práticas nas seguintes áreas:

- Compreensão do funcionamento de serviços da AWS e sua integração.
- Como aplicar conceitos básicos de engenharia de prompts na construção de assistentes inteligentes.
- Otimização de processos utilizando IA generativa e suas capacidades.

## Conclusão

- Este projeto representa um passo importante no meu aprendizado em engenharia de prompt e na aplicação de IA generativa em cenários do mundo real. Ao construir o Assistente de Delivery, tenho certeza de que poderei aplicar essas habilidades em futuros projetos.

## Inclusive, consegui este resultado utilizando o Step Functions e o Amazon Bedrock em conjunto, agradeço a equipe da DIO pelo incrível aprendizado oferecido de forma gratuita <3

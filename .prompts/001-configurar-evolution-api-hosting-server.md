Contexto:
- API Evolution está rodando no servidor VPS Hosting.
- Acesso à dashboard: http://187.77.242.6:8081/manager/instance/c8b8ebc9-9b70-4e78-aeeb-280ece927d7f/dashboard
- Ao clicar em "GET QR CODE", aparece a mensagem de erro: "Scan the QR code with your WhatsApp Web".

Problema:
- O QR code não está sendo exibido corretamente.
- A API precisa produzir o QR code para conectar ao WhatsApp Web.

Objetivo:
- Diagnosticar e corrigir a causa do erro.
- Fazer com que a funcionalidade de geração de QR code funcione e seja exibida.

Instruções para o agente de IA:
- Seja claro e direto.
- Identifique possíveis causas no servidor, configuração do Evolution API e comunicação com o WhatsApp.
- Suspeite de conflito entre a versão da API Evolution instalada no hosting e a versão definida em `CONFIG_SESSION_PHONE_VERSION=2.2412.54` no arquivo `@file:.assets/evolution.yaml`.
- Sugira passos de verificação e correção com base em boas práticas de hosting e API.
- Se precisar de mais informações, solicite dados específicos do ambiente ou logs.
- Analise os arquivos em `@file:.assets` antes de propor qualquer solução.
- Peça confirmação antes de propor ou aplicar qualquer alteração de código ou configuração.

Resultado esperado:
- O usuário deve receber um QR code válido ao acionar a funcionalidade de geração.
- A solução deve apontar a causa e os próximos passos para correção.
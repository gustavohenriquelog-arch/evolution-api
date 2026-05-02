---
id: 001-configure-evolution-hosting
title: Configure Evolution API Hosting
description: Diagnostica e resolve problemas de QR code na Evolution API
version: 1.0.0
tags: [evolution-api, hosting, qr-code, whatsapp]
---
Instruções gerais: @file:COPILOT.md

Contexto:
- API Evolution está rodando no servidor VPS Hosting.
- Acesso à dashboard: http://187.77.242.6:8081/manager/instance/c8b8ebc9-9b70-4e78-aeeb-280ece927d7f/dashboard
- Ao clicar em "GET QR CODE", aparece a mensagem de erro: "Scan the QR code with your WhatsApp Web".

Problema:
- O QR code não está sendo exibido corretamente.
- A API precisa produzir o QR code para conectar ao WhatsApp Web.

Objetivo:
- Diagnosticar o problema e sugerir uma solução definitiva e acertiva.

Instruções para o agente de IA:
- Identifique possíveis causas no servidor, configuração do Evolution API Hostinger e comunicação com o WhatsApp.
- Suspeite de conflito entre a versão da API Evolution instalada no hosting e a versão `CONFIG_SESSION_PHONE_VERSION=2.2412.54`.

Resultado esperado:
- Gerar documento detalhado com a solução proposta para correção do problema.
- Após implementar a solução do proposta, o usuário deve ser capaz de acessar a tela de gerenciamento de instâncias da Evolution API e clicar no botão "Get QR Code" e então devereceber um QR code válido para realizar pareamento com o smartphone.
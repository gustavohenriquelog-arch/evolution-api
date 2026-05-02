# Instruções em 4 Fases: Configurar Evolution API Hosting (Versão Corrigida)

## Fase 1: Análise do Ambiente

1.  **Analise os arquivos**:
    *   `@file:assets/evolution.yaml`: Verifique a versão da imagem (`image`), a porta (`ports`) e as variáveis de ambiente (`environment`), especialmente `CONFIG_SESSION_PHONE_VERSION`.
    *   `@file:assets/hosting-config.md`: Confirme o IP e o hostname do servidor.
    *   `@file:agent.md`: Entenda o contexto do problema e a mensagem de erro.

2.  **Crie um resumo inicial**: Formule um resumo rápido do setup atual. "Aplicação rodando na versão X, com a versão Y do WhatsApp, no host Z."

## Fase 2: Investigação e Diagnóstico

1.  **Confirme a Hipótese Principal**: A suspeita de conflito de versão entre a API e o WhatsApp Web (`CONFIG_SESSION_PHONE_VERSION`) é a mais provável. A versão configurada (`2.2412.54`) provavelmente está desatualizada ou incorreta.

2.  **Diagnóstico Preciso**: A causa raiz não é a versão da API Evolution em si, mas sim que a variável `CONFIG_SESSION_PHONE_VERSION` não corresponde à versão **atualmente em produção** pelo WhatsApp Web. A solução é descobrir a versão correta e atualizar a configuração.

## Fase 3: Geração da Solução (Método Correto)

1.  **Identifique o Procedimento Correto**: A solução definitiva é sincronizar a configuração da Evolution API com a versão atual do WhatsApp Web.

2.  **Formule o Plano de Ação Correto**: Com base no conhecimento adquirido, o plano de ação é instruir o usuário a descobrir a versão mais recente e aplicá-la.

3.  **Forneça um Passo a Passo Detalhado para o Usuário**:
    1.  Acesse o site oficial do WhatsApp Web: `https://web.whatsapp.com/`.
    2.  Abra as ferramentas de desenvolvedor do seu navegador (geralmente pressionando a tecla `F12`).
    3.  Vá para a aba "Console".
    4.  Digite o seguinte comando e pressione Enter: `window.Debug.VERSION`
    5.  O console exibirá a versão atual da API do WhatsApp (ex: `2.3000.1012913912`). Copie este valor.
    6.  No seu ambiente de hospedagem (Hostinger), edite o arquivo `evolution.yaml`.
    7.  Atualize as seguintes variáveis de ambiente no serviço `evolution-api`:
        *   `CONFIG_SESSION_PHONE_NAME=Ubuntu`
        *   `CONFIG_SESSION_PHONE_VERSION=<cole_a_versao_aqui>`
    8.  Implante (ou reinicie) o contêiner Docker para que as novas configurações sejam aplicadas.

## Fase 4: Criação do Relatório

1.  **Crie um Documento de Saída**: Organize todas as informações em um arquivo chamado `output/001-configure-evolution-hosting_report.md`.

2.  **Estruture o Relatório**:
    *   **Diagnóstico**: Explique que a causa raiz é a `CONFIG_SESSION_PHONE_VERSION` estar dessincronizada com a versão real do WhatsApp Web.
    *   **Plano de Ação (Solução Definitiva)**: Apresente o passo a passo detalhado (descrito na Fase 3) como a solução correta e recomendada.
    *   **Resultado Esperado**: Descreva que, após seguir os passos, o usuário conseguirá gerar o QR Code e parear o dispositivo com sucesso.
    *   **Agradecimento**: Inclua uma nota de agradecimento pela colaboração na identificação da solução precisa.
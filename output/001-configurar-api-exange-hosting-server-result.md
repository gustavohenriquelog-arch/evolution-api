# Execução da tarefa 001-configurar-api-exange-hosting-server

## Contexto
- A API Evolution está rodando no servidor VPS Hosting.
- A dashboard é acessível em: `http://187.77.242.6:8081/manager/instance/c8b8ebc9-9b70-4e78-aeeb-280ece927d7f/dashboard`
- Ao clicar em `GET QR CODE`, aparece a mensagem: `Scan the QR code with your WhatsApp Web`.
- A tarefa foi executada considerando as regras definidas em `AGENTS.md`.

## Arquivos analisados em `.assets`
- `evolution.yaml`
- `hosting-config.md`
- `evolution-api.log`
- `evolution-postgres.log`
- `chrome-error.txt`

## Observações
- O `docker-compose` de `.assets/evolution.yaml` expõe `evolution-api` na porta `8081` do host e define `CONFIG_SESSION_PHONE_CLIENT=baileys`.
- O log `evolution-api.log` contém apenas mensagens de inicialização e não mostra erro explícito de QR code.
- O log `evolution-postgres.log` indica que o PostgreSQL iniciou corretamente.
- Há registros de `Connection reset by peer`, que sugerem um cliente desconectando antes da comunicação terminar.
- Essa mensagem não é necessariamente um erro fatal do banco de dados; pode ser uma consequência de um cliente que fecha a conexão abruptamente.
- O `chrome-error.txt` traz avisos de acessibilidade do frontend relacionados a `DialogContent` e `DialogTitle`.

## Diagnóstico
A mensagem de erro parece estar no nível de frontend/dashboards ou de sessão do WhatsApp, e não é um erro direto de inicialização do serviço.

### Possíveis causas
1. O frontend pode estar exibindo uma mensagem padrão porque o QR code não foi entregue ou renderizado corretamente.
2. A sessão do WhatsApp no volume persistente `/evolution` pode estar inválida ou corrompida.
3. O alerta de `DialogContent` no navegador indica que a interface possui um modal possivelmente mal configurado, o que pode afetar a renderização do QR code.
4. Problemas de rede/CORS ou de endpoint interno podem impedir a entrega do QR code.

## Passos recomendados
1. Verificar com `docker logs evolution-api` se existem erros adicionais em tempo real.
2. Conferir o console do navegador ao acionar o QR code:
   - requisições falhas
   - erros JavaScript
   - possíveis bloqueios de CORS
3. Testar o endpoint de QR diretamente para confirmar se há retorno válido.
4. Avaliar se a sessão do WhatsApp precisa ser reiniciada ou recriada.

## Conformidade com `AGENTS.md`
- A análise foi clara e direta.
- Não foram propostas alterações no código sem confirmação.
- O resultado foi salvo em Markdown no diretório `output`.

## Arquivo gerado
- `output/001-configurar-api-exange-hosting-server-result.md`

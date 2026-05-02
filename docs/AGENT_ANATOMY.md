# 🏗️ Anatomia de um Agente: Guia Detalhado

A estrutura interna completa de um agente bem-construído e como cada componente funciona.

---

## Estrutura Macro: Os 3 Pilares

```
┌─────────────────────────────────────────────────────┐
│  COPILOT.md (Contexto Global)                       │
│  - Persona: especialista em X                       │
│  - Boas práticas: segurança, qualidade             │
│  - Guidelines: estilo de resposta                   │
└─────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────┐
│  Agent NNN (Tarefa Específica)                      │
│  ├── agent.md: O QUÊ fazer                         │
│  ├── instructions.md: COMO fazer                   │
│  └── assets/: DADOS para fazer                     │
└─────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────┐
│  output/ (Resultado)                                │
│  - NNN-agente_report.md: saída estruturada         │
└─────────────────────────────────────────────────────┘
```

---

## Pilar 1: `agent.md` - O QUÊ Fazer

### Estrutura Completa

```markdown
---
id: 001-configure-evolution-hosting
title: Configure Evolution API Hosting
description: Diagnostica e resolve problemas de QR code na Evolution API
version: 1.2.0
author: DevOps Team
tags: [evolution-api, hosting, whatsapp, qr-code, diagnosis]
dependencies:
  - COPILOT.md (para persona)
  - assets/evolution.yaml
  - assets/hosting-config.md
output: output/001-configure-evolution-hosting_report.md
estimated_duration: 30-45 minutes
priority: high
status: active
changelog:
  1.2.0:
    date: 2024-02-15
    changes:
      - Suporte para Evolution API v2.2
      - Novo diagnóstico de QR code via WebSocket
  1.1.0:
    date: 2024-01-10
    changes:
      - Compatibilidade com Hostinger
---

# 📋 Instruções Gerais
@file:COPILOT.md

## Por que você (agente) existe
Você foi criado porque: evolução da API para produção exige diagnóstico preciso de problemas de integração.

---

# 🎯 Contexto

## Situação Atual
- **Servidor**: VPS Hostinger em São Paulo
- **API**: Evolution WhatsApp API rodando em Docker
- **Versão instalada**: Evolution API v1.6.0 (suspeita-se versão incompatível)
- **Problema principal**: QR code não é exibido ao clicar "Get QR Code"

## Sintomas Observados
- Dashboard carrega normalmente
- Botão "Get QR Code" não produz QR (apenas mensagem genérica)
- Logs mostram: "Scan the QR code with your WhatsApp Web"
- Possível conflito de versão: `CONFIG_SESSION_PHONE_VERSION=2.2412.54`

## Ambiente Afetado
- Instância: c8b8ebc9-9b70-4e78-aeeb-280ece927d7f
- URL Dashboard: http://187.77.242.6:8081/manager/instance/...

---

# 🎪 Objetivo

**Diagnosticar a causa raiz do problema de QR code** e entregar uma solução acertiva que permite:
1. Usuário clica "Get QR Code" na dashboard
2. QR code válido é exibido
3. Smartphone consegue fazer pareamento com WhatsApp Web

---

# ✅ Resultado Esperado

**Documento estruturado** (`output/001-configure-evolution-hosting_report.md`) contendo:

1. **Diagnóstico**: Causa raiz identificada (versão, config, firewall, etc)
2. **Recomendações**: 3-5 ações ordenadas por prioridade
3. **Implementação**: Passo a passo para cada ação
4. **Validação**: Como confirmar que problema foi resolvido
5. **Próximos Passos**: Monitoramento e prevenção

---

# 🤖 Instruções para o Agente de IA

## Ordem de Execução (OBRIGATÓRIA)
1. ✅ Leia @file:COPILOT.md - entenda persona e guidelines
2. ✅ Leia @file:instructions.md - fases de execução
3. ✅ Analise @file:assets/ - dados específicos da tarefa
4. 🚀 Execute conforme definido em instructions.md

## O Que Você NÃO Deve Fazer
- ❌ Fornecer soluções genéricas ("reinstale a API")
- ❌ Ignorar a versão mencionada do WhatsApp
- ❌ Propor mudanças sem validação em staging
- ❌ Expor credenciais ou tokens em relatório

## O Que Você DEVE Fazer
- ✅ Ser específico e técnico
- ✅ Referenciar versões exatas
- ✅ Incluir passo a passo executável
- ✅ Alinhar com segurança e boas práticas Vibe Code
```

### Campos Obrigatórios em `agent.md`
```
✅ YAML Frontmatter:
  - id: identificador único
  - title: nome legível
  - description: o que faz (1 linha)
  - version: x.y.z
  - tags: categorização
  - status: active|inactive|deprecated

✅ Seções Markdown:
  1. Instruções Gerais (@file:COPILOT.md)
  2. Contexto (situação atual)
  3. Objetivo (o que quer alcançar)
  4. Resultado Esperado (output específico)
  5. Instruções para Agente de IA (ordem de execução)
```

---

## Pilar 2: `instructions.md` - COMO Fazer

### Estrutura Completa

```markdown
# Instruções de Execução: Configure Evolution Hosting

**Agente**: @file:agent.md  
**Persona**: @file:COPILOT.md  
**Saída esperada**: Salvar em `output/001-configure-evolution-hosting_report.md`

---

## Fase 1: Inicialização ✅

### Etapa 1.1: Leia COPILOT.md
Absorva:
- Persona: "especialista em hosting e Evolution API"
- Boas práticas: "segurança desde a inicialização"
- Estilo: "direto, prático, alinhado com padrões modernos"

**Validação**: Você entendeu a persona? Se não, releia.

### Etapa 1.2: Analise agent.md
Extraia:
- Versão do agente: 1.2.0
- Contexto: VPS Hostinger + Evolution API + QR code
- Objetivo: Diagnosticar causa raiz
- Saída esperada: Relatório em output/

**Validação**: Consegue resumir em 2 linhas? Se sim, prossiga.

### Etapa 1.3: Revise assets/
Arquivos disponíveis:
- `assets/evolution.yaml`: Configuração atual da API
- `assets/hosting-config.md`: Setup do servidor
- `assets/dashboard-logs.txt`: Logs da dashboard
- `assets/docker-compose.yml`: Configuração Docker

**Validação**: Todos os 4 arquivos foram lidos? Se não, solicite ao usuário.

---

## Fase 2: Análise Investigativa 🔍

### Etapa 2.1: Mapeamento do Problema

**Questões a Responder**:
1. Qual versão da Evolution API está instalada?
   - Procure em: assets/evolution.yaml → image tag
   - Esperado: v1.6.0 ou v2.x
   
2. Qual é o CONFIG_SESSION_PHONE_VERSION definido?
   - Procure em: assets/evolution.yaml → environment
   - Esperado: Compatível com versão da API

3. O Docker container está rodando corretamente?
   - Procure em: assets/docker-compose.yml → health check
   - Esperado: status running

4. Há conflito de rede/firewall?
   - Procure em: assets/hosting-config.md → ports
   - Esperado: Porta 8081 aberta para localhost + acesso remoto

### Etapa 2.2: Diagnóstico Técnico

**Checklist de Investigação**:
- [ ] Versão da API vs CONFIG_SESSION_PHONE_VERSION são compatíveis?
- [ ] WhatsApp Web version 2.2412.54 é suportado?
- [ ] WebSocket está funcionando para geração de QR?
- [ ] Certificado TLS/SSL está válido?
- [ ] Rate limiting está bloqueando requisições?
- [ ] Logs mostram erros específicos?

---

## Fase 3: Geração de Solução 💡

### Etapa 3.1: Identifique a Causa Raiz

**Árvore de Decisão**:
```
QR Code não aparece
├─ Versão incompatível?
│  └─ → Recomendação: Atualizar Evolution API
├─ WhatsApp version obsoleta?
│  └─ → Recomendação: Atualizar CONFIG_SESSION_PHONE_VERSION
├─ WebSocket quebrado?
│  └─ → Recomendação: Verificar firewall/CORS
└─ Certificado inválido?
   └─ → Recomendação: Renovar TLS
```

### Etapa 3.2: Priorize Recomendações

**Ordem de Impacto**:
1. **Crítico** (bloqueia tudo): ação prioritária
2. **Alto** (resolve 80%): segunda ação
3. **Médio** (melhoria): terceira ação
4. **Baixo** (otimização): ações futuras

---

## Fase 4: Entrega 📦

### Etapa 4.1: Estruture o Relatório

Template de saída em `output/001-configure-evolution-hosting_report.md`:

```markdown
# Relatório: Configure Evolution API Hosting
**Agente**: 001 v1.2.0  
**Data**: [data atual]  
**Status**: ✅ Análise Concluída

## Resumo Executivo
[3-5 linhas conclusão]

## Análise Detalhada
### Causa Raiz
[Problema específico identificado]

### Evidência
[Referência aos assets]

## Recomendações
1. [Ação 1 - Crítico]
2. [Ação 2 - Alto]
3. [Ação 3 - Médio]

## Próximos Passos
1. [Quem / O quê / Quando]
2. ...
```

### Etapa 4.2: Validações Finais

- [ ] Relatório segue template
- [ ] Sem credenciais expostas
- [ ] Recomendações são acertivas (não genéricas)
- [ ] Passo a passo é executável
- [ ] Salvo em: `output/001-configure-evolution-hosting_report.md`

---

## Fluxo Visual

```
┌────────────────────────────────────┐
│ Inicialização (Fase 1)             │
│ - Lê COPILOT.md                    │
│ - Lé agent.md                      │
│ - Revisa assets/                   │
└─────────────┬──────────────────────┘
              ↓
┌────────────────────────────────────┐
│ Análise (Fase 2)                   │
│ - Mapeamento do problema           │
│ - Investigação técnica             │
│ - Árvore de decisão                │
└─────────────┬──────────────────────┘
              ↓
┌────────────────────────────────────┐
│ Solução (Fase 3)                   │
│ - Identifica causa raiz            │
│ - Prioriza recomendações           │
│ - Estrutura entrega                │
└─────────────┬──────────────────────┘
              ↓
┌────────────────────────────────────┐
│ Entrega (Fase 4)                   │
│ - Gera relatório                   │
│ - Valida completude                │
│ - Salva em output/                 │
└────────────────────────────────────┘
```

---

## Checklist de Qualidade

- [ ] Cada etapa tem "Validação" clara
- [ ] Questões guiam a investigação
- [ ] Causa raiz é específica (não vaga)
- [ ] Recomendações são priorizadas
- [ ] Passo a passo é executável
- [ ] Relatório segue template
- [ ] Sem exposição de dados sensíveis
```

### Campos Obrigatórios em `instructions.md`
```
✅ Cabeçalho:
  - Link para @file:agent.md
  - Link para @file:COPILOT.md
  - Caminho de saída esperado

✅ Fases (em ordem):
  1. Inicialização (leitura de contexto)
  2. Análise (investigação)
  3. Solução (diagnóstico)
  4. Entrega (geração de output)

✅ Cada fase contém:
  - Etapas numeradas
  - Questões guia ou checklist
  - Validações intermediárias
  - Links para onde procurar (em assets/)
```

---

## Pilar 3: `assets/` - OS DADOS

### Estrutura e Uso

```
assets/
├── evolution.yaml           # Config da API
├── hosting-config.md        # Setup do servidor
├── dashboard-logs.txt       # Logs do problema
├── docker-compose.yml       # Orquestração containers
└── README.md                # Índice e dicionário
```

### `assets/README.md` (Padrão Recomendado)

```markdown
# Assets: Dados de Entrada

## Descrição de Cada Arquivo

### evolution.yaml
**O que é**: Configuração operacional da Evolution API  
**Criado por**: DevOps team  
**Última atualização**: 2024-02-01  
**Campos importantes para este agente**:
- `image`: Tag de versão da imagem Docker
- `environment.CONFIG_SESSION_PHONE_VERSION`: Versão WhatsApp
- `environment.PORT`: Porta da API
- `environment.DATABASE_URL`: Conexão BD

### hosting-config.md
**O que é**: Documentação do servidor VPS Hostinger  
**Campos importantes**:
- Versão do OS
- Versão do Docker
- Firewall rules
- Certificado TLS/SSL

### dashboard-logs.txt
**O que é**: Logs da dashboard Evolution quando erro ocorre  
**Como interpretar**: [Regex patterns para erros comuns]

### docker-compose.yml
**O que é**: Orquestração dos containers  
**Campos importantes**: Health checks, volumes, networks

---

## Dicionário de Termos

- **QR Code**: Quick Response code para pareamento
- **CONFIG_SESSION_PHONE_VERSION**: Versão WhatsApp suportada
- **WebSocket**: Protocolo para comunicação real-time
- **TLS/SSL**: Protocolo de segurança HTTPS

---

## Referências

- Evolution Docs: https://evolution-api.com/docs
- WhatsApp Web Versions: https://github.com/baileys/baileys
```

### Princípios para `assets/`

```
✅ FAÇA
- Um arquivo = um conceito
- Documentação inline com comentários
- Exemplo funcional incluído
- Versionado (data última mudança)

❌ EVITE
- Misturar múltiplos conceitos em um arquivo
- Dados fictícios sem aviso
- Credenciais reais (use @env: varname)
- Arquivos muito grandes (> 10MB)
```

---

## Integração: Os 3 Pilares Juntos

### Fluxo de Execução Real

```
1. Usuário: "@agent 001-configure-evolution-hosting"

2. Sistema lê em ordem:
   ├─ COPILOT.md (persona global)
   ├─ agents/001/.../instructions.md (como fazer)
   ├─ agents/001/.../agent.md (o quê fazer)
   └─ agents/001/.../assets/ (dados)

3. Agente executa Fase 1-4 de instructions.md

4. Agente salva em:
   └─ output/001-configure-evolution-hosting_report.md

5. Usuário recebe relatório estruturado
```

---

## Exemplo Completo: Anatomia Viva

### agent.md (Resumido)
```yaml
id: 001-configure-evolution-hosting
version: 1.2.0
```

### instructions.md (Resumido)
```
Fase 2: Analise assets/evolution.yaml
- Qual versão da API?
- Qual CONFIG_SESSION_PHONE_VERSION?
```

### assets/evolution.yaml
```yaml
image: evolution-api:1.6.0  # ← Agente procura aqui
environment:
  CONFIG_SESSION_PHONE_VERSION: "2.2412.54"  # ← E aqui
```

### Resultado
Agente encontra: "API v1.6.0 + WhatsApp 2.2412.54 incompatíveis"  
Diagnóstico: "Atualizar para API v2.2+"

---

## Checklist: Anatomia Completa ✅

```markdown
# Novo Agente: ___________

## agent.md
- [ ] YAML Frontmatter com id, version, tags
- [ ] Seção Contexto (situação atual)
- [ ] Seção Objetivo (o que quer)
- [ ] Seção Resultado Esperado (output específico)
- [ ] Instruções para IA com ordem clara

## instructions.md
- [ ] Fase 1: Inicialização (leitura)
- [ ] Fase 2: Análise (investigação)
- [ ] Fase 3: Solução (diagnóstico)
- [ ] Fase 4: Entrega (output)
- [ ] Validações em cada etapa
- [ ] Referências aos assets

## assets/
- [ ] README.md com índice
- [ ] Cada arquivo documentado
- [ ] Exemplos incluídos
- [ ] Sem credenciais reais
- [ ] Versionado (data)

## Integração
- [ ] COPILOT.md referenciado
- [ ] Output path especificado
- [ ] Template de saída definido
```

---

## Referências

- [ESTRUTURA_PROPOSTA.md](../output/ESTRUTURA_PROPOSTA.md)
- [BEST_PRACTICES.md](./BEST_PRACTICES.md)
- [GETTING_STARTED.md](./GETTING_STARTED.md)


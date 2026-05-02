# Evolution API - Sistema de Agentes IA

**Data de Atualização**: 2024-02-15  
**Status**: ✅ Estrutura Nova Implementada

---

## 📋 Overview

Sistema de agentes IA especializados para configuração e manutenção da Evolution API, seguindo boas práticas Vibe Code e padrões de mercado.

---

## 🗂️ Estrutura do Projeto

```
evolution-api/
├── COPILOT.md                          # Persona global e guidelines
├── README.md                           # Este arquivo
├── .agents/                            # Catálogo e templates
│   ├── AGENTS.md                       # Registro centralizado de agentes
│   └── templates/
│       └── agent-template.md           # Template para novo agente
├── agents/                             # Agentes implementados
│   ├── 001-configure-evolution-hosting/
│   │   ├── agent.md                    # Definição do agente
│   │   ├── instructions.md             # Instruções de execução (4 fases)
│   │   └── assets/
│   │       ├── evolution.yaml
│   │       ├── hosting-config.md
│   │       └── README.md               # Documentação dos assets
│   └── 002-discover-whatsapp-version/
│       ├── agent.md
│       ├── instructions.md
│       └── assets/
├── docs/                               # Documentação central
│   ├── README.md                       # Índice de navegação
│   ├── GETTING_STARTED.md              # Tutorial: criar novo agente
│   ├── BEST_PRACTICES.md               # 10 princípios Vibe Code
│   └── AGENT_ANATOMY.md                # Estrutura técnica detalhada
├── output/                             # Saídas geradas
```

---

## 🚀 Como Usar

### Executar um Agente

```bash
# Invoke agente 001
@agent 001-configure-evolution-hosting

# Invoke agente 002
@agent 002-discover-whatsapp-version
```

O agente executará automaticamente:
1. ✅ Lê `@file:COPILOT.md` (persona)
2. ✅ Lê `@file:instructions.md` (fases)
3. ✅ Acessa `@file:assets/` (dados)
4. 🚀 Gera resultado em `output/`

### Criar Novo Agente

1. Leia: [docs/GETTING_STARTED.md](./docs/GETTING_STARTED.md)
2. Use: [.agents/templates/agent-template.md](./.agents/templates/agent-template.md)
3. Siga: [output/GUIA_IMPLEMENTACAO.md](./output/GUIA_IMPLEMENTACAO.md)

**Tempo estimado**: ~15-20 minutos

---

## 📖 Documentação

### Para Diferentes Públicos

**👨‍💻 Quer Criar Agente?**
- Siga: [docs/GETTING_STARTED.md](./docs/GETTING_STARTED.md) (15 min)
- Use: [.agents/templates/agent-template.md](./.agents/templates/agent-template.md)

**📚 Quer Entender Estrutura?**
- Leia: [docs/AGENT_ANATOMY.md](./docs/AGENT_ANATOMY.md) (40 min)

**🎓 Quer Construir com Qualidade?**
- Consulte: [docs/BEST_PRACTICES.md](./docs/BEST_PRACTICES.md) (30 min)

**🔍 Qual Agente Usar?**
- Consulte: [.agents/AGENTS.md](./.agents/AGENTS.md) (catálogo)

---

## 📋 Agentes Disponíveis

### ✅ 001 - Configure Evolution Hosting
**Status**: Ativo  
**Descrição**: Diagnostica e resolve problemas de QR code na Evolution API  
**Arquivo**: [agents/001-configure-evolution-hosting/](./agents/001-configure-evolution-hosting/)  
**Versão**: 1.0.0

**Entrada** (assets):
- `evolution.yaml` - Config da API
- `hosting-config.md` - Setup do servidor

**Saída**: `output/001-configure-evolution-hosting_report.md`

---

### 🔄 002 - Discover WhatsApp Version
**Status**: WIP (Em Desenvolvimento)  
**Descrição**: Descobre versão atual do WhatsApp API e compatibilidade  
**Arquivo**: [agents/002-discover-whatsapp-version/](./agents/002-discover-whatsapp-version/)  
**Versão**: 1.0.0

**Status**: Template criado, implementação em progresso

---

## 🎯 Boas Práticas (Vibe Code)

Todos os agentes seguem 10 princípios Vibe Code:

1. ✅ Configurações claras e repetíveis
2. ✅ Código modular e fácil de manter
3. ✅ Validação em staging antes de produção
4. ✅ Documentação de parâmetros e dependências
5. ✅ Versionamento incremental de APIs
6. ✅ Segurança desde a inicialização
7. ✅ Compatibilidade com clientes legados
8. ✅ Padrão de resposta estruturado
9. ✅ Peer review antes de deploy
10. ✅ Métricas de qualidade

Detalhes em: [docs/BEST_PRACTICES.md](./docs/BEST_PRACTICES.md)

---

## 🔗 Fluxo de Execução

```
@agent 001-configure-evolution-hosting
                ↓
┌─────────────────────────────────────┐
│ Fase 1: Inicialização              │
│ - Lê @file:COPILOT.md              │
│ - Lé @file:instructions.md         │
│ - Analisa @file:assets/            │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ Fase 2: Análise Investigativa       │
│ - Investigação técnica             │
│ - Coleta de evidências             │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ Fase 3: Geração de Solução          │
│ - Identifica causa raiz            │
│ - Gera recomendações               │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ Fase 4: Entrega                    │
│ - Gera relatório estruturado       │
│ - Salva em output/                 │
└─────────────────────────────────────┘
```

---

## 🔐 Segurança

Todos os agentes implementam:
- ✅ Sem credenciais em plain text
- ✅ Secrets via `@env:VARNAME`
- ✅ Inputs validados
- ✅ Outputs sanitizados
- ✅ Logs sem dados sensíveis

Checklist completo em: [docs/BEST_PRACTICES.md](./docs/BEST_PRACTICES.md#6-segurança-desde-a-inicialização)

---

## 📊 Status da Implementação

| Componente | Status | Data |
|-----------|--------|------|
| Estrutura Base | ✅ Completo | 2024-02-15 |
| Agente 001 | ✅ Ativo | 2024-02-15 |
| Agente 002 | 🔄 WIP | 2024-02-15 |
| Documentação | ✅ Completo | 2024-02-15 |
| Catálogo AGENTS.md | ✅ Completo | 2024-02-15 |
| Templates | ✅ Pronto | 2024-02-15 |

---

## 🆘 Precisa de Ajuda?

| Pergunta | Resposta |
|----------|----------|
| Como criar novo agente? | [docs/GETTING_STARTED.md](./docs/GETTING_STARTED.md) |
| Qual agente usar? | [.agents/AGENTS.md](./.agents/AGENTS.md) |
| Estrutura detalhada? | [docs/AGENT_ANATOMY.md](./docs/AGENT_ANATOMY.md) |
| Padrões de qualidade? | [docs/BEST_PRACTICES.md](./docs/BEST_PRACTICES.md) |
| Referência rápida? | [output/REFERENCIA_RAPIDA.md](./output/REFERENCIA_RAPIDA.md) |

---

## 📞 Contato

- **Padrão Vibe Code**: [COPILOT.md](./COPILOT.md)
- **Documentação Central**: [docs/README.md](./docs/README.md)
- **Catálogo de Agentes**: [.agents/AGENTS.md](./.agents/AGENTS.md)

---

## 📝 Histórico de Mudanças

| Versão | Data | O que mudou |
|--------|------|-----------|
| 1.0 | 2024-02-15 | ✅ Implementação completa da nova estrutura |

---

**Status**: ✅ Pronto para usar


# 🗂️ Catálogo de Agentes - Evolution API

Registro centralizado de todos os agentes disponíveis, seu status e referências.

---

## 📊 Status de Agentes

| ID | Título | Status | Versão | Owner | Última Atualização |
|----|--------|--------|--------|-------|-------------------|
| 001 | Configure Evolution Hosting | ✅ Ativo | 1.2.0 | DevOps Team | 2024-02-15 |
| 002 | Discover WhatsApp Version | 🔄 WIP | 0.1.0 | Dev Team | 2024-02-01 |

---

## 001 - Configure Evolution Hosting

**Arquivo**: [agents/001-configure-evolution-hosting/agent.md](../taks/001-configure-evolution-hosting/agent.md)

**Descrição**:  
Diagnostica e resolve problemas de QR code na Evolution API. Analisa configuração de hosting, versões de API e WhatsApp, identifica causa raiz e fornece recomendações acertivas.

**Tags**: `evolution-api`, `hosting`, `qr-code`, `whatsapp`, `diagnostics`

**Status**: ✅ Ativo  
**Versão**: 1.2.0  
**Owner**: DevOps Team  
**Criado**: 2023-12-01  
**Última Atualização**: 2024-02-15

**Função Principal**:
- Diagnostica problemas de QR code não exibindo
- Valida compatibilidade de versões (API + WhatsApp)
- Fornece solução passo a passo

**Tempo Estimado**: 30-45 minutos

**Entrada** (assets/):
- `evolution.yaml` - Config da API
- `hosting-config.md` - Setup do servidor
- `dashboard-logs.txt` - Logs do erro

**Saída**:
- `output/001-configure-evolution-hosting_report.md` - Relatório com diagnóstico e recomendações

**Padrões**: Implementa Vibe Code, segurança desde o início, documentação completa

---

## 002 - Discover WhatsApp Version

**Arquivo**: [agents/002-discover-whatsapp-version/agent.md](../taks/002-discover-whatsapp-version/agent.md)

**Descrição**:  
Descobre a versão atual do WhatsApp API e compatibilidade com Evolution API. Útil para validações pré-deploy e diagnóstico de incompatibilidades.

**Tags**: `whatsapp`, `versioning`, `compatibility`, `discovery`

**Status**: 🔄 WIP (Em Desenvolvimento)  
**Versão**: 0.1.0  
**Owner**: Dev Team  
**Criado**: 2024-02-01  
**Última Atualização**: 2024-02-01

**Função Principal**:
- Descobre versão WhatsApp Web em uso
- Valida compatibilidade com Evolution API
- Consulta matriz de compatibilidade

**Tempo Estimado**: 15-20 minutos

**Entrada** (assets/):
- [A definir]

**Saída**:
- [A definir]

**Status do Desenvolvimento**: ⚠️ Template criado, aguardando implementação

---

## 🔄 Como Adicionar um Novo Agente

### Passo 1: Clone o Template
```bash
cp -r agents/001-configure-evolution-hosting agents/NNN-seu-agente
```

### Passo 2: Customize
- Edite `agent.md` com id, title, description
- Crie `instructions.md` com fases de execução
- Adicione `assets/` conforme necessário

### Passo 3: Registre Aqui
Adicione uma nova seção neste arquivo com metadados do agente.

### Passo 4: Valide
Teste com comando: `@agent NNN-seu-agente`

---

## 📈 Métricas

### Agentes por Status
- ✅ Ativo: 1
- 🔄 WIP: 1
- ⚠️ Deprecated: 0

### Cobertura de Tópicos
- Evolution API: 2 agentes
- Hosting/DevOps: 1 agente
- Diagnostics: 1 agente

### Qualidade
- Agentes com BEST_PRACTICES aplicadas: 1/2 (50%)
- Agentes com testes: 0/2 (0%)
- Agentes documentados: 2/2 (100%)

---

## 🚀 Roadmap

### Q1 2024
- [ ] Finalizar Agente 002 (Discover WhatsApp Version)
- [ ] Criar Agente 003 (Deploy Guide)
- [ ] Implementar métricas e health checks

### Q2 2024
- [ ] Criar Agente 004 (Security Audit)
- [ ] Criar Agente 005 (Performance Optimization)
- [ ] Dashboard de status dos agentes

### Q3 2024
- [ ] Agentes para migration scenarios
- [ ] Integração com CI/CD
- [ ] Automação de deploy

---

## 📞 Contatos

| Tópico | Responsável | Email |
|--------|-------------|-------|
| Agentes 001 | DevOps Team | devops@company.com |
| Agentes 002+ | Dev Team | dev@company.com |
| Infraestrutura | Platform Team | platform@company.com |

---

## 📚 Referências Rápidas

- [ESTRUTURA_PROPOSTA.md](../output/ESTRUTURA_PROPOSTA.md) - Visão geral
- [GETTING_STARTED.md](../../docs/GETTING_STARTED.md) - Como criar novo agente
- [BEST_PRACTICES.md](../../docs/BEST_PRACTICES.md) - Padrões Vibe Code
- [AGENT_ANATOMY.md](../../docs/AGENT_ANATOMY.md) - Estrutura detalhada
- [COPILOT.md](../../COPILOT.md) - Persona e guidelines

---

## 📝 Última Atualização

**Data**: 2024-02-15  
**Atualizador**: Análise Estrutural  
**Mudanças**: Catálogo inicial criado com 2 agentes


# 🎯 Boas Práticas: Construção de Agentes de IA - Padrão Vibe Code

Aplicação dos princípios Vibe Code à construção de agentes de IA inteligentes e confiáveis.

---

## 1. Configurações Claras e Repetíveis

### ✅ Agente Bem-Estruturado

```yaml
---
id: 003-seu-agente
version: 1.0
execution_context:
  - "@file:COPILOT.md"        # Sempre primeiro
  - "@file:instructions.md"   # Específico do agente
  - "@file:assets/"           # Dados de entrada
output_path: "output/003-seu-agente_report.md"
---
```

### Por Quê?
- **Repetibilidade**: Mesma entrada → Mesmo resultado
- **Rastreabilidade**: Sabe exatamente qual versão do agente foi executada
- **Escalabilidade**: Funciona igual para 1 ou 100 agentes

### Exemplo Real
```markdown
# Agente 001 - Configuração Evolution Hosting (v1.0)

Input:
- COPILOT.md (persona)
- instructions.md (fase 1-4)
- assets/evolution.yaml (config atual)
- assets/hosting-config.md (ambiente)

Output:
- output/001-configure-evolution-hosting_report.md

Garantia: Sempre produz relatório estruturado com solução
```

---

## 2. Código Legível, Modular e Fácil de Manter

### ✅ Estrutura Modular de Agente

```
agents/001-seu-agente/
├── agent.md              # Definição (input)
├── instructions.md       # Lógica de execução (process)
├── assets/               # Dados (data)
│   ├── config.yaml
│   └── logs.txt
└── [output em output/]   # Resultado (output)
```

### ❌ Evite Monólitos
```
agents/001-agente-gigante/
├── agent.md              # Mistura tudo aqui
│   ├── instruções 1
│   ├── instruções 2
│   ├── instruções 3
│   └── dados inline (⚠️ problemático)
```

### Por Quê?
- **Reutilização**: Outro agente pode usar mesmo asset
- **Manutenção**: Mudança em config não afeta lógica
- **Teste**: Fácil validar cada componente

---

## 3. Validação em Staging Antes de Produção

### ✅ Ciclo de Desenvolvimento
```
1. Desenvolvimento Local (agent.md + instructions.md)
2. Teste com Dados Fictícios (assets/sample/)
3. Validação em Staging (ambiente de teste)
4. Aprovação (peer review de instructions.md)
5. Deploy em Produção (move para production/)
```

### ✅ Template de Validação

```markdown
## Validação Pré-Produção

- [ ] Testado com assets fictícios
- [ ] Result esperado produzido
- [ ] Sem erros em instructions.md
- [ ] @file:COPILOT.md foi lido pelo agente
- [ ] Resultado é reproduzível
- [ ] Segredos/credenciais não expostos

Aprovado por: [nome do revisor]
Data: YYYY-MM-DD
```

---

## 4. Documentação de Parâmetros e Dependências

### ✅ Sempre Documente

```markdown
# Contexto
- **Ambiente**: VPS Hostinger
- **API**: Evolution WhatsApp API v2.2
- **Dependência**: Docker deve estar rodando
- **Acesso necessário**: SSH + Dashboard admin

# Assets Necessários
- `evolution.yaml`: Config atual da API
- `hosting-config.md`: Configuração do servidor
- `logs/error.log`: Logs do problema

# Versões Testadas
- Evolution API: >= 1.6.0
- Node.js: 18.x ou 20.x
- Docker: 20.10+
```

### Por Quê?
- **Onboarding**: Novo time sabe o que precisa
- **Troubleshooting**: Quando quebra, sabe onde procurar
- **Compatibilidade**: Evita versão errada

---

## 5. Versionamento Incremental de API e Migrações

### ✅ Estrutura com Versão

```
agents/
├── 001-configure-evolution-hosting/
│   └── agent.md (v1.0 - base)
├── 001-configure-evolution-hosting_v2/
│   └── agent.md (v2.0 - Evolution API 2.x)
├── 001-configure-evolution-hosting_v3/
│   └── agent.md (v3.0 - com suporte a Hostinger)
```

### ✅ Registro de Mudanças

```markdown
---
id: 001-configure-evolution-hosting
title: Configure Evolution Hosting
version: 1.2.0
changelog:
  1.2.0:
    date: 2024-02-15
    changes:
      - Suporte para Evolution API v2.2
      - Nova validação de QR code
      - Fix: Compatibilidade com Hostinger
  1.1.0:
    date: 2024-01-10
    changes:
      - Suporte inicial para Hostinger
  1.0.0:
    date: 2023-12-01
    changes:
      - Release inicial
---
```

### Por Quê?
- **Compatibilidade**: Clientes legados rodam v1, novos rodam v2
- **Rastreabilidade**: Sabe quando mudança foi introduzida
- **Rollback**: Volta para v1 se v2 quebra

---

## 6. Segurança desde a Inicialização

### ✅ Checklist de Segurança para Agentes

```markdown
## 🔒 Segurança

- [ ] Sem credenciais em agent.md ou assets/
- [ ] Sensitive data referenciado via @env: varname
- [ ] CORS definido em hosting-config.md
- [ ] Rate limiting configurado
- [ ] TLS/HTTPS obrigatório
- [ ] Inputs validados (ex: URL, tokens)
- [ ] Outputs sanitizados (ex: sem logs com senhas)

Exemplo - SEGURO:
```
API_TOKEN: @env:EVOLUTION_API_TOKEN  # ✅ Reference
evolution.yaml contém: Bearer ${API_TOKEN}
```

Exemplo - INSEGURO:
```
API_TOKEN: sk-1234567890abcdef  # ❌ Hardcoded
```
```

### Por Quê?
- **Conformidade**: Atende OWASP, SOC2, LGPD
- **Confiança**: Clientes confiam em segurança
- **Risco**: Vazamento de credenciais = comprometimento total

---

## 7. Manutenção e Evolução Compatível com Clientes

### ✅ Evolução Sem Breaking Changes

**Cenário**: Nova versão da Evolution API

```markdown
## Estratégia: Versão Dual

### v1.x (Legado) - Manutenção Apenas
- Suporta Evolution API 1.6.x
- Status: Maintenance only
- Warnings em agent.md: "Será descontinuado em 2025-Q1"

### v2.0 (Novo) - Full Support
- Suporta Evolution API 2.x
- Teste backward compat com v1 clients
- Deprecation path claro

## Comunicação ao Cliente
```
- 📧 Aviso: Agente v1 será descontinuado
- 📋 Guia: Como migrar para v2
- 🧪 Teste: Versão trial de v2
- 📞 Suporte: Assist durante migração
```

### Por Quê?
- **Confiança**: Clientes não têm breaking changes surpresa
- **Transição suave**: Tempo para se adaptar
- **Reputação**: Considerado profissional/maduro

---

## 8. Padrão de Resposta de Agente

### ✅ Estrutura de Saída (output)

Todo agente deve gerar `output/NNN-agent_report.md` com:

```markdown
# Relatório: [Nome da Tarefa]
**Data**: 2024-02-15  
**Versão do Agente**: 001 v1.2  
**Status**: ✅ Concluído

---

## 📋 Resumo Executivo
[3-5 linhas com conclusão principal]

---

## 🔍 Análise Detalhada

### Contexto Analisado
- Config atual: [resumo]
- Problemas identificados: [lista]

### Causa Raiz
- [Diagnóstico claro]

---

## ✅ Recomendações

1. **Ação Imediata**: [O quê, Por quê]
2. **Ação Secundária**: [O quê, Por quê]
3. **Monitoramento**: [O quê, Como]

---

## 🚀 Próximos Passos

1. [Ação 1 com deadline]
2. [Ação 2 com responsável]

---

## 📎 Anexos

- Config atual: `assets/evolution.yaml`
- Logs: `assets/logs.txt`
```

### Por Quê?
- **Profissionalismo**: Cliente recebe relatório, não output cru
- **Acionabilidade**: Recomendações claras e priorizadas
- **Rastreabilidade**: Data, versão, status documentados

---

## 9. Template de Peer Review para Agentes

### ✅ Antes de Deploy

```markdown
## 🔍 Peer Review Checklist

### Instructions.md
- [ ] Fases claras (Inicialização → Análise → Solução → Entrega)
- [ ] COPILOT.md é lido primeiro
- [ ] Assets bem documentados
- [ ] Validações de erro incluídas
- [ ] Output format especificado

### Agent.md
- [ ] Contexto claro e completo
- [ ] Objetivo bem definido
- [ ] Resultado esperado específico (não vago)
- [ ] Sem credenciais hardcoded
- [ ] Versão e changelog atualizados

### Assets
- [ ] Todos os arquivos necessários presentes
- [ ] Sem dados sensíveis expostos
- [ ] Formato documentado (YAML, JSON, etc)
- [ ] Exemplos válidos incluídos

### Segurança
- [ ] Sem secrets em plain text
- [ ] Inputs validados
- [ ] Outputs sanitizados
- [ ] Acesso restrito conforme necessário

Aprovado por: [revisor]  
Data: YYYY-MM-DD
```

---

## 10. Métricas de Qualidade

### ✅ O Que Medir

```
Agente Bem-Estruturado tem:

✅ Repetibilidade: 100% (mesma entrada = mesmo resultado)
✅ Latência: < X segundos
✅ Taxa de sucesso: > 95%
✅ Documentação: > 80% de cobertura
✅ Teste de regressão: Passes em 100% dos cases
✅ Segurança: 0 secrets expostos
✅ Compatibilidade: Funciona em v1, v2, v3...
```

### Dashboard Recomendado (`.agents/METRICS.md`)
```markdown
| Agente | Status | Uptime | Taxa Sucesso | Última Execução |
|--------|--------|--------|--------------|-----------------|
| 001    | ✅ OK  | 99.9%  | 98%          | 2024-02-15 14:30 |
| 002    | ⚠️ Alerta | 95%  | 85%          | 2024-02-15 08:00 |
```

---

## 📝 Resumo: Checklist Vibe Code para Agentes

```markdown
# Novo Agente: ___________

## Estrutura
- [ ] Diretório em agents/NNN-descricao/
- [ ] agent.md com metadados YAML
- [ ] instructions.md com fases claras
- [ ] assets/ bem organizado

## Configuração
- [ ] Contexto claro e completo
- [ ] Objetivo específico e mensurável
- [ ] Resultado esperado não-ambíguo
- [ ] Dependências documentadas

## Segurança
- [ ] Sem secrets hardcoded
- [ ] Inputs validados
- [ ] Outputs sanitizados
- [ ] Acesso apropriado

## Qualidade
- [ ] Repetível 100%
- [ ] Documentado 80%+
- [ ] Testado com dados fictícios
- [ ] Peer review aprovado

## Manutenção
- [ ] Versão clara
- [ ] Changelog atualizado
- [ ] Compatibilidade backward documentada
- [ ] Deprecation path (se v2+)

## Documentação
- [ ] Registrado em `.agents/AGENTS.md`
- [ ] Template usado
- [ ] Exemplos incluídos
- [ ] Link para docs/
```

---

## 🔗 Próximas Leituras

- [ESTRUTURA_PROPOSTA.md](../output/ESTRUTURA_PROPOSTA.md)
- [GETTING_STARTED.md](./GETTING_STARTED.md)
- [AGENT_ANATOMY.md](./AGENT_ANATOMY.md)
- [COPILOT.md](../COPILOT.md) - Persona Vibe Code


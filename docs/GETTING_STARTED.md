# 🚀 Guia de Início Rápido: Criar um Novo Agente

## Pré-requisitos
- Projeto estruturado conforme `ESTRUTURA_PROPOSTA.md`
- Familiaridade com COPILOT.md (persona e guidelines)

---

## 1️⃣ Defina o Agente

Antes de criar arquivos, responda:

| Pergunta | Exemplo |
|----------|---------|
| **O que é?** | "Diagnosticar problema de QR code" |
| **Por quê?** | "Usuário não consegue parear WhatsApp" |
| **Quem vai usar?** | "Técnico de suporte" |
| **Qual é o resultado?** | "Relatório com solução" |
| **Quais dados/assets?** | "Config da API, logs de erro" |

---

## 2️⃣ Crie a Estrutura

```bash
# No diretório agents/
mkdir NNN-seu-agente-descritivo
cd NNN-seu-agente-descritivo

# Crie os arquivos
touch agent.md
touch instructions.md
mkdir assets
```

**Onde `NNN` é o próximo número sequencial** (ex: 003, 004...)

---

## 3️⃣ Preencha `agent.md`

Use o template em `.agents/templates/agent-template.md`:

```markdown
---
id: 003-seu-agente
title: Título do Seu Agente
description: Breve descrição (1 linha)
version: 1.0
tags: [tag1, tag2, tag3]
---

# Instruções gerais
@file:COPILOT.md

# Contexto
Descreva o cenário/problema do usuário aqui.

# Objetivo
Defina o objetivo do agente (o que deve fazer).

# Resultado Esperado
Descreva exatamente qual deve ser a saída (documento, análise, código, etc).

# Instruções para o Agente de IA
1. Leia @file:COPILOT.md para entender persona e guidelines
2. Analise @file:assets/ para insumos específicos
3. Siga @file:instructions.md para execução
4. Gere saída conforme seção "Resultado Esperado"
```

---

## 4️⃣ Preencha `instructions.md`

Este arquivo é **específico do agente** e força o fluxo correto:

```markdown
# Instruções para o Agente: [Seu Agente]

## Fase 1: Inicialização ✅
1. Leia @file:COPILOT.md (persona, guidelines, boas práticas Vibe Code)
2. Leia @file:agent.md (contexto, objetivo, resultado esperado)
3. Analise @file:assets/ (todos os insumos)

## Fase 2: Análise
### Etapa 1: Compreensão
- Identifique o problema principal
- Mapeie dependências
- Liste suposições

### Etapa 2: Investigação
- [Instruções específicas para seu agente]
- [O que procurar nos assets]
- [Que validações fazer]

## Fase 3: Solução
- [Como gerar a solução]
- [Formato esperado]
- [Validações finais]

## Fase 4: Entrega
- Salvar resultado em: `output/NNN-seu-agente_report.md`
- Formato: Markdown estruturado
- Incluir: Análise + Recomendações + Próximos Passos
```

---

## 5️⃣ Adicione Assets

No diretório `assets/`, adicione qualquer arquivo necessário para o agente:

```
assets/
├── config.yaml           # Configuração de referência
├── logs.txt              # Logs do problema
├── api-docs.md           # Documentação
└── current-state.json    # Estado atual do sistema
```

---

## 6️⃣ Registre em `.agents/AGENTS.md`

Adicione seu agente ao catálogo:

```markdown
## 003-seu-agente
- **Status**: ✅ Ativo
- **Owner**: [Seu nome/time]
- **Última atualização**: 2024-XX-XX
- **Descrição**: Breve descrição aqui
- **Arquivo**: @file:agents/003-seu-agente/agent.md
```

---

## 7️⃣ Execute

Invoke o agente:

```
@agent 003-seu-agente
```

O agente executará em ordem:
1. Lê COPILOT.md
2. Lê instructions.md
3. Lê agent.md
4. Processa assets/
5. Salva resultado em output/

---

## ✅ Checklist Final

- [ ] Diretório criado: `agents/NNN-seu-agente/`
- [ ] `agent.md` preenchido com metadados YAML
- [ ] `instructions.md` com fases claras
- [ ] `assets/` contém insumos necessários
- [ ] Agente registrado em `.agents/AGENTS.md`
- [ ] Testado: comando `@agent NNN-seu-agente` funciona

---

## 💡 Dicas Importantes

### ✅ Faça
- **Seja específico** em "Resultado Esperado" (não vague)
- **Liste dependências** em assets
- **Use tags** para categorizar agentes
- **Documente suposições** no contexto
- **Versionize mudanças** em agent.md

### ❌ Evite
- Deixar `instructions.md` vago
- Misturar múltiplos problemas em um agente
- Sem estrutura clara de assets
- Instruções genéricas ("faça uma análise")

---

## 📚 Referências

- [ESTRUTURA_PROPOSTA.md](../output/ESTRUTURA_PROPOSTA.md) - Visão geral
- [COPILOT.md](../COPILOT.md) - Persona e guidelines
- [BEST_PRACTICES.md](./BEST_PRACTICES.md) - Padrões Vibe Code
- [AGENT_ANATOMY.md](./AGENT_ANATOMY.md) - Estrutura detalhada


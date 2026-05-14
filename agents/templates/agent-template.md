---
id: NNN-seu-agente-descritivo
title: Título Claro do Seu Agente
description: Uma linha descrevendo o que o agente faz
version: 1.0.0
author: [Seu nome ou time]
tags: [tag1, tag2, tag3]
dependencies:
  - COPILOT.md
  - assets/
output: output/NNN-seu-agente_report.md
estimated_duration: 30 minutes
priority: high
status: active
changelog:
  1.0.0:
    date: 2024-02-XX
    changes:
      - Release inicial
---

# 📋 Instruções Gerais
@file:COPILOT.md

---

# 🎯 Contexto

## Situação Atual
Descreva o contexto e situação atual aqui. Por exemplo:
- Qual é o ambiente?
- Qual é o problema?
- Quem está afetado?
- Qual é a urgência?

## Sintomas / Observações
- [Sintoma 1]
- [Sintoma 2]
- [Sintoma 3]

## Informações Técnicas
- Versão do software/API: X.Y.Z
- Ambiente: Produção / Staging / Local
- Dependências: [lista]

---

# 🎪 Objetivo

**Em uma frase**: O que você (agente) deve alcançar?

Exemplos:
- "Diagnosticar causa raiz do problema de QR code"
- "Gerar documentação de deploy para Evolution API"
- "Analisar compatibilidade de versões"

---

# ✅ Resultado Esperado

Descreva **exatamente** qual deve ser a saída do agente. Seja específico:

**Documento**: `output/NNN-seu-agente_report.md`

**Estrutura**:
1. [Seção 1: O quê]
2. [Seção 2: Análise ou Diagnóstico]
3. [Seção 3: Recomendações]
4. [Seção 4: Próximos Passos]

**Exemplo de Saída**:
```
# Relatório: [Título]
**Status**: ✅ Concluído

## Resumo Executivo
[3-5 linhas]

## Análise
[Detalhes]

## Recomendações
1. [Ação 1 - Crítico]
2. [Ação 2 - Alto]

## Próximos Passos
1. [O quê / Quem / Quando]
```

---

# 🤖 Instruções para o Agente de IA

## Ordem de Execução (OBRIGATÓRIA)

1. ✅ **Leia @file:COPILOT.md**
   - Entenda a persona
   - Absorva as boas práticas
   - Internalize o estilo de resposta

2. ✅ **Leia @file:instructions.md**
   - Compreenda as fases de execução
   - Identifique os passos principais
   - Veja as validações esperadas

3. ✅ **Analise @file:assets/**
   - Revise todos os arquivos
   - Compreenda os dados disponíveis
   - Identifique gaps (se houver)

4. 🚀 **Execute conforme definido em instructions.md**
   - Siga fase por fase
   - Aplique validações
   - Gere saída conforme "Resultado Esperado"

## O Que Você DEVE Fazer
- ✅ Ser específico e técnico
- ✅ Referenciar versões exatas
- ✅ Incluir passo a passo executável
- ✅ Alinhar com segurança e boas práticas Vibe Code
- ✅ Salvar resultado no caminho especificado

## O Que Você NÃO Deve Fazer
- ❌ Fornecer soluções genéricas ou vagas
- ❌ Ignorar contexto específico
- ❌ Propor mudanças sem validação
- ❌ Expor credenciais ou tokens
- ❌ Pular a leitura de COPILOT.md

---

# 📚 Assets Disponíveis

Este agente usa os seguintes dados de entrada em `assets/`:

| Arquivo | Tipo | Descrição | Importante Para |
|---------|------|-----------|-----------------|
| [nome] | [tipo] | [descrição] | [usar em qual fase] |

Exemplo:
| evolution.yaml | Config | Configuração atual da API | Fase 2: Diagnóstico |
| hosting-config.md | Doc | Setup do servidor | Fase 2: Validação |
| logs.txt | Log | Erros e avisos | Fase 2: Análise |

---

# 🔗 Links de Referência

- [Documentação](../docs/)
- [COPILOT.md](../../COPILOT.md)
- [BEST_PRACTICES.md](../../docs/BEST_PRACTICES.md)
- [GETTING_STARTED.md](../../docs/GETTING_STARTED.md)


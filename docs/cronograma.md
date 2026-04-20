# 📌 Backlog (formato Trello) — Monitor de Alertas Residenciais para Deficientes Auditivos (LARAF 2026)

---

# 1º Período — Pesquisa e Prototipagem Virtual

## Épico F1 — Imersão e Pesquisa

### Card F1.1 — Escopo do MVP + Requisitos + Arquitetura macro
**Objetivo:** definir o MVP com clareza (o que entra/saí), requisitos e arquitetura geral.

**Checklist — DSP**
- [ ] Definir lista de sons-alvo do MVP (ex.: campainha/interfone/alarme)
- [ ] Definir lista de “não-alvos” (ruídos domésticos) para reduzir falso positivo
- [ ] Propor abordagem inicial de detecção (FFT/bandas/limiares/cooldown)

**Checklist — Firmware**
- [ ] Definir arquitetura FreeRTOS (tasks, filas, estados)
- [ ] Definir pinagem simulada (GPIO/I2S/LED/botões) sem conflitos
- [ ] Estruturar projeto (pastas, padrão de nomes, build)

**Checklist — Conectividade**
- [ ] Definir fluxo Wi‑Fi → Telegram (eventos, retries, timeouts)
- [ ] Definir estratégia de configuração/segredos (token/chat_id fora do código)
- [ ] Definir requisitos de confiabilidade (reconexão/backoff)

**Checklist — UX/UI**
- [ ] Definir personas e cenários (distância, ambientes, expectativas)
- [ ] Definir requisitos de acessibilidade do alerta (padrões, brilho, redundância)
- [ ] Definir fluxo do usuário (instalação → configuração → teste)

**Entregáveis**
- Documento: escopo do MVP + requisitos + decisões macro
- Mapa de arquitetura (blocos) e estados do sistema

**Aceite**
- MVP definido (eventos suportados + comportamento LED + notificação)
- Arquitetura macro aprovada por todos (responsabilidades e fluxos)

---

### Card F1.2 — Provas de conceito (PoCs) técnicas
**Objetivo:** reduzir risco técnico com PoCs simples e funcionais.

**Checklist — DSP**
- [ ] Montar script Python para espectrograma/FFT e extração de picos
- [ ] Definir janela FFT e taxa de amostragem inicial (com justificativa)
- [ ] Listar limitações esperadas (latência, resolução, ruído)

**Checklist — Firmware**
- [ ] Subir Wokwi com ESP32 + periféricos base (LED/WS2812B ou equivalente)
- [ ] PoC: controle básico de LED (on/off e padrões simples)
- [ ] PoC: FreeRTOS (2 tasks + fila simples)

**Checklist — Conectividade**
- [ ] PoC: Telegram Bot enviando mensagem simples
- [ ] Definir formato padrão de mensagem (campos mínimos)
- [ ] Registrar erros comuns e como diagnosticar

**Checklist — UX/UI**
- [ ] Benchmark de soluções similares (alerta visual/acessibilidade)
- [ ] Rascunhar padrões de alerta (ritmo/pulsos por evento)

**Entregáveis**
- PoC Telegram + PoC LED + PoC tasks FreeRTOS
- Script Python de análise + anotações

**Aceite**
- PoCs executam com roteiro reprodutível (passo a passo)

---

### Card F1.3 — Dataset de áudio (curadoria + metadata)
**Objetivo:** ter base de teste para calibrar detecção e validar falsos positivos.

**Checklist — DSP**
- [ ] Definir padrão de arquivos (formato, sample rate, normalização)
- [ ] Coletar sons-alvo em variações (distância/ambiente/volume)
- [ ] Coletar ruídos negativos (TV, conversa, panela, porta, etc.)
- [ ] Criar metadata (tipo, ambiente, distância, observações)

**Checklist — Firmware**
- [ ] Definir como simular/injetar testes (gatilhos, logs, sequências)
- [ ] Preparar logs de “decisão” (timestamp, métricas do sinal, evento)

**Checklist — Conectividade**
- [ ] Definir objeto “evento” (tipo, timestamp, confiança/nível, latência)
- [ ] Garantir mensagem do bot padronizada para avaliação

**Checklist — UX/UI**
- [ ] Definir sinalização para “modo teste” vs “evento real”
- [ ] Definir feedback de erro (sem Wi‑Fi / sem Telegram / falha detecção)

**Entregáveis**
- Dataset + metadata
- Especificação do evento

**Aceite**
- Dataset cobre cenários positivos e negativos relevantes

---

### Card F1.4 — Conceito de case + requisitos físicos/visuais
**Objetivo:** alinhar design com captação de som e visibilidade do alerta.

**Checklist — DSP**
- [ ] Requisitos acústicos (aberturas, posição do sensor, evitar abafamento)
- [ ] Observações sobre reverberação/ressonância da case

**Checklist — Firmware**
- [ ] Requisitos de botão “teste”, indicador de status, alimentação
- [ ] Requisitos de posicionamento de LEDs e acesso

**Checklist — Conectividade**
- [ ] Requisitos de indicadores visuais de estados (connecting/ready/error)
- [ ] Definir comportamento offline (alerta local continua)

**Checklist — UX/UI**
- [ ] Esboço CAD inicial (layout e dimensões aproximadas)
- [ ] Padrões de alerta acessíveis (não depender só de cor)

**Entregáveis**
- Esboço CAD + lista de requisitos físicos

**Aceite**
- Design conceitual não impede captação nem visibilidade

---

## Épico F2 — Desenvolvimento do MVP Virtual

### Card F2.1 — Detecção baseline + pipeline de decisão
**Objetivo:** primeira versão funcional da detecção e geração de eventos.

**Checklist — DSP**
- [ ] Implementar baseline (FFT/bandas/energia/picos)
- [ ] Definir parâmetros: threshold, duração mínima, cooldown
- [ ] Criar roteiro de testes usando dataset (Python)

**Checklist — Firmware**
- [ ] Task de áudio + task de decisão + fila de eventos
- [ ] Estrutura de eventos (enum/tipos) + timestamps
- [ ] Logs básicos de depuração

**Checklist — Conectividade**
- [ ] Função de envio desacoplada (fila → task rede)
- [ ] Mensagem padronizada (tipo, hora, latência, “nível/confiança” se houver)
- [ ] Tratamento básico de falhas

**Checklist — UX/UI**
- [ ] Padrões LED por tipo de evento (ritmo, intensidade, duração)
- [ ] “Modo teste” (aciona confirmação visual + Telegram)

**Entregáveis**
- Detecção baseline integrada
- Padrões LED definidos e documentados

**Aceite**
- Evento dispara LED e Telegram de forma consistente (mesmo em teste controlado)

---

### Card F2.2 — Conectividade robusta mínima + configuração
**Objetivo:** reconexão, retries e estados do sistema sem travar o processamento.

**Checklist — DSP**
- [ ] Regras para reduzir spam (cooldown e critérios mínimos)
- [ ] Ajustes rápidos anti-ruído

**Checklist — Firmware**
- [ ] Garantir que rede não bloqueie áudio (timeouts/prioridades)
- [ ] Implementar estados do sistema (BOOT/CONNECTING/READY/ERROR)
- [ ] Watchdog/logs de falha (se aplicável)

**Checklist — Conectividade**
- [ ] Reconexão Wi‑Fi (backoff, timeout)
- [ ] Retry Telegram com limites
- [ ] Config fora do código (token/chat_id)

**Checklist — UX/UI**
- [ ] Padrões de LED para estados (connecting/ready/error)
- [ ] Rascunho do guia de configuração

**Entregáveis**
- Reconexão e retries funcionando
- Estados com feedback visual

**Aceite**
- Queda de rede não trava o sistema e o estado fica claro ao usuário

---

### Card F2.3 — Integração end-to-end (DSP + Firmware + Rede + UX)
**Objetivo:** consolidar o fluxo completo e preparar validação.

**Checklist — DSP**
- [ ] Portar algoritmo do Python para C/C++ (comparar resultados básicos)
- [ ] Criar logs de features (pico/energia/banda) para calibrar

**Checklist — Firmware**
- [ ] Módulos integrados com interfaces claras
- [ ] Rate limit e anti-loop de eventos
- [ ] Inicialização/boot estáveis

**Checklist — Conectividade**
- [ ] Mensagens consistentes + mensagem “sistema pronto”
- [ ] Medição aproximada de latência (evento→envio)

**Checklist — UX/UI**
- [ ] Refinar padrões (padrões distintos e compreensíveis)
- [ ] Checklist de experiência (modo teste, erros, estados)

**Entregáveis**
- MVP integrado end-to-end + instruções de execução

**Aceite**
- Demo repetível e estável com roteiro curto

---

### Card F2.4 — Validação virtual + métricas
**Objetivo:** medir acerto/falsos positivos/latência e ajustar parâmetros.

**Checklist — DSP**
- [ ] Medir taxa de acerto vs falso positivo no dataset
- [ ] Ajustar thresholds e regras
- [ ] Registrar resultados (tabela/relatório)

**Checklist — Firmware**
- [ ] Instrumentar timestamps (pipeline) para medir latência
- [ ] Criar cenários de estresse (sequência de eventos)

**Checklist — Conectividade**
- [ ] Testar quedas de rede/atrasos/fila cheia
- [ ] Confirmar recuperação automática e logs

**Checklist — UX/UI**
- [ ] Validar legibilidade dos padrões
- [ ] Ajustar feedback de erro e modo teste

**Entregáveis**
- Relatório de validação + lista de problemas priorizada

**Aceite**
- Métricas mínimas coletadas e ajustes aplicados

---

## Épico F3 — Refinamento e Design

### Card F3.1 — Otimização (CPU/memória/latência) + estabilidade
**Checklist — DSP**
- [ ] Otimizar FFT/janelas/extração
- [ ] Ajustar regras para reduzir falsos positivos

**Checklist — Firmware**
- [ ] Reduzir alocações e padronizar buffers
- [ ] Revisar prioridades FreeRTOS e evitar travamentos
- [ ] Modo debug vs modo demo (logs)

**Checklist — Conectividade**
- [ ] Boas práticas de segurança e validações
- [ ] Melhorar tratamento de erros/reconexão

**Checklist — UX/UI**
- [ ] Ajustar brilho/conforto visual
- [ ] Padronizar mensagens e estados

**Entregáveis**
- Versão otimizada do MVP

**Aceite**
- Melhora mensurável (ou observável) vs baseline (latência/estabilidade/FP)

---

### Card F3.2 — CAD final + especificação de montagem
**Checklist — DSP**
- [ ] Revisar requisitos acústicos no CAD final

**Checklist — Firmware**
- [ ] Definir pontos de fixação e acesso a interfaces

**Checklist — Conectividade**
- [ ] Requisitos de indicação de estado e identificação do setup

**Checklist — UX/UI**
- [ ] Finalizar CAD (furações som, difusor de luz, botão, energia)
- [ ] Render/vistas para apresentação

**Entregáveis**
- CAD final + renders + mini-guia de montagem

**Aceite**
- Design pronto para apresentação e coerente com requisitos

---

### Card F3.3 — Calibração anti-falso-positivo (parâmetros finais)
**Checklist — DSP**
- [ ] Ajustar thresholds/cooldown/duração mínima
- [ ] Criar “presets” se necessário (ambiente silencioso/barulhento)
- [ ] Registrar antes/depois

**Checklist — Firmware**
- [ ] Centralizar parâmetros (config)
- [ ] Garantir que calibragem não degrade estabilidade

**Checklist — Conectividade**
- [ ] Anti-spam (rate limit/agrupamento)
- [ ] Mensagens de resumo (se ocorrerem muitos eventos)

**Checklist — UX/UI**
- [ ] Ajustar padrão para não ser agressivo em falsos alarmes
- [ ] Feedback claro se houver “detecção incerta” (se adotarem)

**Entregáveis**
- Tabela de parâmetros finais + justificativas

**Aceite**
- Redução clara de falsos positivos nos testes definidos

---

### Card F3.4 — Robustez de falhas (rede/fluxo/filas) + degradação
**Checklist — DSP**
- [ ] Definir comportamento quando rede falha (detecção local continua)

**Checklist — Firmware**
- [ ] Simular falhas (Wi‑Fi off, Telegram off, fila cheia)
- [ ] Garantir alerta visual mesmo offline
- [ ] Reconexão automática + estados

**Checklist — Conectividade**
- [ ] Backoff consistente + limites + logs
- [ ] Garantir que falhas não travem o sistema

**Checklist — UX/UI**
- [ ] Padrões claros: sem rede ≠ sem detecção
- [ ] Troubleshooting básico

**Entregáveis**
- Plano de falhas + evidências de testes

**Aceite**
- Função principal (alerta visual) permanece confiável mesmo com rede instável

---

# 2º Período — Finalização e Entrega

## Épico F4 — Consolidação e Entrega do MVP

### Card F4.1 — Consolidar logs, evidências e métricas finais
**Checklist — DSP**
- [ ] Consolidar métricas (acerto/FP/latência)
- [ ] Preparar gráficos/tabelas para o relatório

**Checklist — Firmware**
- [ ] Consolidar logs e resultados de estabilidade
- [ ] Revisar organização do repositório

**Checklist — Conectividade**
- [ ] Consolidar métricas de envio (sucesso/falha/retry)
- [ ] Padronizar exemplos de mensagens

**Checklist — UX/UI**
- [ ] Consolidar imagens do CAD e padrões
- [ ] Checklist final de experiência

**Entregáveis**
- Pacote de evidências (tabelas, logs, prints)

**Aceite**
- Dados suficientes para sustentar conclusões e apresentação

---

### Card F4.2 — Relatório técnico (final) + arquitetura
**Checklist (divisão por seção)**
- [ ] DSP: metodologia + dataset + resultados + limitações
- [ ] Firmware: arquitetura + simulação + desempenho + estados
- [ ] Conectividade: fluxo + resiliência + segurança
- [ ] UX/UI: fluxo do usuário + acessibilidade + CAD + padrões

**Entregáveis**
- Relatório final completo

**Aceite**
- Documento reproduzível (alguém consegue rodar e entender o MVP)

---

### Card F4.3 — Mídia + Pitch (slides e demo)
**Checklist — DSP**
- [ ] Narrativa problema→solução→métricas

**Checklist — Firmware**
- [ ] Roteiro de demo e estabilidade da apresentação

**Checklist — Conectividade**
- [ ] Demonstração de notificação e estados de rede

**Checklist — UX/UI**
- [ ] Vídeo demo + imagens CAD + slides com foco em acessibilidade

**Entregáveis**
- Slides + vídeo + roteiro de demo

**Aceite**
- Apresentação executa sem improviso técnico

---

### Card F4.4 — Manual do usuário + FAQ + Troubleshooting
**Checklist — DSP**
- [ ] Orientações simples sobre fatores que impactam detecção

**Checklist — Firmware**
- [ ] Como usar modo teste + interpretar LEDs

**Checklist — Conectividade**
- [ ] Configurar Wi‑Fi/Telegram + problemas comuns

**Checklist — UX/UI**
- [ ] Manual com prints + linguagem acessível + FAQ

**Entregáveis**
- Manual + FAQ

**Aceite**
- Usuário leigo consegue configurar e testar seguindo o manual

---

### Card F4.5 — Preparação final do repositório + ensaio geral
**Checklist — DSP**
- [ ] Revisar parâmetros finais e documentar

**Checklist — Firmware**
- [ ] README final (como rodar/testar) + limpeza do repositório

**Checklist — Conectividade**
- [ ] Remover segredos do repo + instruções seguras

**Checklist — UX/UI**
- [ ] Revisar consistência visual e documentação

**Entregáveis**
- Repo “pronto para entrega” + checklist de ensaio concluído

**Aceite**
- Tudo funciona a partir do repositório com instruções claras

---

### Card F4.6 — Entrega do MVP
**Checklist — Todos**
- [ ] Apresentação final LARAF
- [ ] Entregar relatório + manual + protótipo simulado + mídia

**Entregáveis**
- Pacote final completo

**Aceite**
- Entrega realizada e demonstrada com sucesso

---

## ✅ Definição de Pronto (DoD) — para qualquer Card
- [ ] Código/artefatos relacionados executam/compilam no ambiente definido
- [ ] Evidência de teste anexada (log/print/vídeo/checklist)
- [ ] Documentação atualizada (docs/README/relatório)
- [ ] Validação registrada em reunião (OK)

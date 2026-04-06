# 📅 Cronograma Detalhado: Monitor de Alertas Residenciais para Deficientes Auditivos (LARAF 2026)

Este cronograma detalha as 18 semanas de desenvolvimento do "Tradutor Sensorial". Devido à ausência temporária de hardware, o foco está na **validação lógica e simulação virtual**. O plano está dividido em dois períodos para respeitar o recesso escolar.

## 👥 Estrutura da Equipe e Responsabilidades

* **Especialista em DSP (Processamento de Sinais):** Responsável por algoritmos de áudio, FFT, filtragem e análise de frequências.
* **Arquiteto de Firmware:** Responsável pela lógica do ESP32, uso do FreeRTOS e simulação de componentes no Wokwi.
* **Engenheiro de Conectividade:** Responsável pela integração com Telegram Bot API, protocolos de rede (Wi-Fi/HTTP) e segurança.
* **Designer de Produto (UX/UI):** Responsável pelo design da case (CAD), fluxos de experiência do usuário e acessibilidade.

---

## 1º Período: Pesquisa e Prototipagem Virtual (Abril - Junho)

### Fase 1: Imersão e Pesquisa
**Foco:** Fundamentação teórica e setup de simuladores.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **01** | 08/04 - 14/04 | Setup e Requisitos | **Todos:** Mapeamento de requisitos de acessibilidade; Definição da pinagem (GPIO) simulada no ESP32 para evitar conflitos. |
| **02** | 15/04 - 21/04 | Estudos Técnicos | **DSP:** Estudo da biblioteca `driver/i2s.h` e FFT. **Firmware:** Configuração do simulador Wokwi. **Conexão:** Estudo da API de Bots do Telegram. **UX:** Pesquisa de padrões visuais de alerta. |
| **03** | 22/04 - 28/04 | Validação Digital | **DSP:** Coleta de áudios de campainhas para análise. **Firmware:** Hello World de LED no simulador. **Conexão:** Teste de envio de mensagens simples via Bot. **UX:** Desenho do fluxo de interação usuário-dispositivo. |
| **04** | 29/04 - 05/05 | Modelagem Inicial | **DSP:** Análise espectral dos áudios no Python. **Firmware:** Teste de concorrência Wi-Fi no simulador. **UX:** Esboços iniciais da case considerando acústica para o microfone INMP441. |

### Fase 2: Desenvolvimento do MVP Virtual
**Foco:** Implementação da lógica central e integração em software.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **05** | 06/05 - 12/05 | Sprint de Lógica | **DSP:** Script em Python para detecção de frequências específicas. **Firmware:** Lógica de controle de animações da Fita LED (WS2812B). |
| **06** | 13/05 - 19/05 | Sprint Conectividade | **Conexão:** Implementação da API do Telegram e lógica de notificações em tempo real. **UX:** Modelagem 3D básica da case para fabricação. |
| **07** | 20/05 - 26/05 | Integração de Software | **Firmware/DSP:** Tradução do algoritmo Python para C++. Uso de FreeRTOS Tasks no ESP32 para processar áudio e rede. |
| **08** | 27/05 - 02/06 | Validação Virtual | **Todos:** Testes de latência no Wokwi entre o gatilho sonoro simulado e o alerta visual/digital. |

### Fase 3: Refinamento e Design (Início)
**Foco:** Otimização do código e design para fabricação.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **09** | 03/06 - 09/06 | Otimização | **DSP/Firmware:** Otimização de memória e processamento FFT. **Conexão:** Implementação de segurança SSL/TLS nas requisições. |
| **10** | 10/06 - 16/06 | Design Industrial | **UX:** Finalização do CAD 3D com furações para entrada de som e saída de luz. |
| **11** | 17/06 - 23/06 | Calibração Lógica | **DSP:** Ajuste de sensibilidade teórica para ignorar barulhos domésticos e focar no interfone. |
| **12** | 24/06 - 30/06 | Robustez Virtual | **Firmware:** Simulação de quedas de conexão e teste de reconexão automática após falha de rede. |

---

## RECESSO / FÉRIAS (Julho)

---

## 2º Período: Finalização e Entrega (Agosto - Setembro)

### Fase 4: Consolidação de Dados e Entrega do MVP
**Foco:** Métricas, manuais e apresentação dos resultados.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **13** | 03/08 - 09/08 | Retomada e Logs | **DSP:** Coleta de logs de acerto teórico na detecção. **Conexão:** Testes de estresse de rede em ambiente simulado. |
| **14** | 10/08 - 16/08 | Relatório Técnico | **Todos:** Escrita do documento detalhando a arquitetura de software e os desafios de simulação superados. |
| **15** | 17/08 - 23/08 | Mídia e Pitch | **UX:** Produção de vídeo demonstrativo da simulação e fotografia profissional do modelo 3D. |
| **16** | 24/08 - 30/08 | Manual do Usuário | **UX/Conexão:** Criação de guia passo-a-passo para instalação e configuração do Wi-Fi/Telegram pelo usuário. |
| **17** | 31/08 - 06/09 | Preparação Final | **Firmware:** Revisão final do código no GitHub e ensaio da apresentação final. |
| **18** | 07/09 - 13/09 | Entrega do MVP | **Todos:** Apresentação para o LARAF e entrega do relatório final e protótipo funcional simulado. |

---

## Definição de Pronto (DoD)
Para cada semana ser considerada concluída:
* O código gerado deve compilar sem erros no simulador ou IDE.
* A documentação de pesquisa ou simulação da semana deve estar atualizada no log do projeto.
* As tarefas individuais devem ser validadas em reunião de sincronização da equipe.

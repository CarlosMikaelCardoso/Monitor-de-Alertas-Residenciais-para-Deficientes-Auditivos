# 📅 Cronograma Detalhado: Projeto Alerta Interfone (LARAF 2026)

Este cronograma detalha as 18 semanas de desenvolvimento do "Tradutor Sensorial". Devido à ausência temporária de hardware, as atividades foram redirecionadas para a criação de um **Gêmeo Digital**, garantindo a validação lógica e matemática do sistema antes da montagem física.

## 👥 Estrutura da Equipe e Responsabilidades

* **Especialista em DSP (Processamento de Sinais):** Foco em algoritmos de áudio, FFT, filtragem e análise de frequências.
* **Arquiteto de Firmware:** Responsável pela lógica do ESP32, uso do FreeRTOS e simulação de componentes no Wokwi.
* **Engenheiro de Conectividade:** Foco na integração com Telegram Bot API, protocolos de rede (Wi-Fi/HTTP) e segurança.
* **Designer de Produto (UX/UI):** Responsável pelo design da case (CAD), fluxos de experiência do usuário e acessibilidade.

---

## 🗓️ Fase 1: Imersão e Pesquisa (Semanas 1-4)
**Objetivo:** Configuração de ambientes virtuais e fundamentação teórica.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **01** | 23/02 - 01/03 | Setup e Requisitos | **Todos:** Mapeamento de requisitos de acessibilidade; Definição da pinagem (GPIO) simulada no ESP32 para evitar conflitos. |
| **02** | 02/03 - 08/03 | Estudos Técnicos | **DSP:** Estudo da biblioteca `driver/i2s.h` e FFT. <br> **Firmware:** Configuração do simulador Wokwi. <br> **Conectividade:** Estudo da API de Bots do Telegram. <br> **UX:** Pesquisa de padrões visuais de alerta. |
| **03** | 09/03 - 15/03 | Validação de Ferramentas | **DSP:** Coleta de áudios de campainhas para análise. <br> **Firmware:** Hello World de LED no simulador. <br> **Conectividade:** Criação do Bot e teste de mensagens via cURL/Postman. <br> **UX:** Desenho do fluxo de interação usuário-dispositivo. |
| **04** | 16/03 - 22/03 | Modelagem Inicial | **DSP:** Análise espectral dos áudios no Audacity/Python. <br> **Firmware:** Teste de concorrência Wi-Fi no simulador. <br> **UX:** Esboços iniciais da case considerando acústica. |

---

## 🚀 Fase 2: Desenvolvimento do MVP Virtual (Semanas 5-8)
**Objetivo:** Implementação da lógica central e integração de sistemas em software.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **05** | 23/03 - 29/03 | Sprint de Lógica Base | **DSP:** Script em Python para detectar frequências específicas. <br> **Firmware:** Lógica de controle de animações da Fita LED (WS2812B). <br> **Conectividade:** Implementação da lógica de envio de alertas em C++. |
| **06** | 30/03 - 05/04 | Sprint Conectividade | **Conectividade:** Gestão de notificações em tempo real e reconexão automática. <br> **UX:** Modelagem 3D básica da case para impressão. |
| **07** | 06/04 - 12/04 | Integração de Software | **Firmware/DSP:** Tradução do algoritmo Python para C++. <br> **Todos:** Junção dos módulos usando FreeRTOS Tasks no ESP32 para processar "áudio" simulado e rede simultaneamente. |
| **08** | 13/04 - 19/04 | Validação em Simulador | **Todos:** Testes de latência no Wokwi entre o gatilho sonoro (simulado) e o alerta visual/digital. |

---

## 🛠️ Fase 3: Refinamento e Modelagem Mecânica (Semanas 9-12)
**Objetivo:** Otimização do código e design final para fabricação.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **09** | 20/04 - 26/04 | Otimização de Código | **DSP/Firmware:** Otimização de memória e processamento FFT. <br> **Conectividade:** Implementação de segurança SSL/TLS nas requisições. |
| **10** | 27/04 - 03/05 | Design Industrial | **UX:** Finalização do CAD 3D com furações para microfone INMP441 e difusão de LEDs. |
| **11** | 04/05 - 10/05 | Calibração Lógica | **DSP:** Ajuste de sensibilidade teórica para ignorar ruídos (palmas, portas) baseando-se nos dados da Fase 1. |
| **12** | 11/05 - 17/05 | Teste de Robustez | **Firmware:** Simulação de quedas de energia e Wi-Fi no código para validar a resiliência do sistema. |

---

## 📊 Fase 4: Documentação e Entrega do MVP (Semanas 13-18)
**Objetivo:** Consolidação de dados e preparação para o hardware.

| Semana | Datas | Atividade | Detalhamento por Membro |
| :--- | :--- | :--- | :--- |
| **13** | 18/05 - 24/05 | Geração de Métricas | **DSP:** Relatório de taxa de acerto teórica vs falsos positivos. <br> **Conectividade:** Log de sucesso de entrega de notificações. |
| **14** | 25/05 - 31/05 | Relatório Técnico | **Todos:** Escrita detalhada da arquitetura de software e decisões de design. |
| **15** | 01/06 - 07/06 | Mídia e Pitch | **UX:** Produção de vídeo demonstrativo usando a simulação e o modelo 3D. |
| **16** | 08/06 - 14/06 | Manual do Usuário | **UX/Conectividade:** Guia de configuração do Bot e guia de instalação física. |
| **17** | 15/06 - 21/06 | Preparação Final | **Firmware:** Revisão final do código no GitHub e organização de pastas. |
| **18** | 22/06 - 30/06 | Entrega do MVP Virtual | Apresentação para o LARAF e entrega do protótipo funcional simulado. |

---

## ✅ Definição de Pronto (DoD)
Para cada semana ser considerada concluída:
1.  O código gerado deve estar compilando (no simulador ou IDE).
2.  A documentação de pesquisa/simulação da semana deve estar no repositório.
3.  As tarefas individuais devem ser validadas em reunião de sincronização.

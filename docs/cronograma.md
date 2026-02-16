# 📅 Cronograma Detalhado: Projeto Alerta Interfone (LARAF 2026)

Este cronograma detalha as 18 semanas de desenvolvimento do "Tradutor Sensorial", separando as responsabilidades técnicas entre os Squads **P2 (Processamento de Som)** e **P4 (Conectividade e UX)**.

### 🏗️ Estrutura de Squads

* **Squad P2 (Sensor de Som):** Responsável pelo Microfone INMP441, protocolo I2S, algoritmos de filtragem de ruído e calibração de frequência.
* **Squad P4 (Conexão e Alerta):** Responsável pelo ESP32, conexão Wi-Fi, integração com Telegram Bot e controle da Fita LED.

---

## 🗓️ Fase 1: Imersão Técnica
**Foco:** Configuração de ambiente e validação individual de componentes.

| Semana | Datas | Atividade | Detalhamento das Tarefas (P2 e P4) |
| :--- | :--- | :--- | :--- |
| **01** | 23/02 - 01/03 | Kickoff e Foco | Definição de requisitos do MVP; Mapeamento de pinagem (GPIO) para evitar conflitos no ESP32; Setup do repositório Git. |
| **02** | 02/03 - 08/03 | Estudos: IoT e ESP32 | **P2:** Estudo da biblioteca driver/i2s.h. <br> **P4:** Configuração de conexão Wi-Fi estável e bibliotecas HTTP/Telegram. |
| **03** | 09/03 - 15/03 | Deep Dive: Componentes | **P2:** Testes de leitura do INMP441 (Serial Plotter). <br> **P4:** Criação do Bot no Telegram e teste de envio de mensagens simples. |
| **04** | 16/03 - 22/03 | Unboxing e Bancada | Chegada dos materiais; Testes unitários de hardware; Verificação de interferência do Wi-Fi na captura de áudio. |

---

## 🚀 Fase 2: Desenvolvimento MVP
**Foco:** Lógica de processamento e integração de sistemas de software.

| Semana | Datas | Atividade | Detalhamento das Tarefas (P2 e P4) |
| :--- | :--- | :--- | :--- |
| **05** | 23/03 - 29/03 | Sprint de Lógica Base | **P2:** Algoritmo de diferenciação de som (Filtro de média ou FFT). <br> **P4:** Lógica de controle de cores da Fita LED via código. |
| **06** | 30/03 - 05/04 | Sprint Conectividade | **P4:** Implementação da API do Telegram; Lógica de notificações em tempo real. <br> **P2:** Ajuste de ganho do microfone via software. |
| **07** | 06/04 - 12/04 | Integração de Hardware | Junção dos códigos (P2 + P4); Uso de *FreeRTOS Tasks* no ESP32 para processar áudio e rede em paralelo. |
| **08** | 13/04 - 19/04 | Validação de Bancada | Testes de integração na protoboard; Correção de bugs de latência entre o som e o alerta visual/digital. |

---

## 🛠️ Fase 3: Refinamento e Case
**Foco:** Construção física do dispositivo e calibração para o mundo real.

| Semana | Datas | Atividade | Detalhamento das Tarefas (P2 e P4) |
| :--- | :--- | :--- | :--- |
| **09** | 20/04 - 26/04 | Soldagem Definitiva | Transferência do circuito para placa perfurada; Soldagem de conectores; Adição de capacitores para filtro de energia. |
| **10** | 27/04 - 03/05 | Construção das Cases | Montagem mecânica; Furação para saída de luz dos LEDs e entrada de som para o microfone. |
| **11** | 04/05 - 10/05 | Calibração Fina | Ajuste de sensibilidade para ignorar barulhos domésticos (palmas, portas) e focar apenas no interfone. |
| **12** | 11/05 - 17/05 | Teste de Robustez | Simulação de uso contínuo; Teste de reconexão automática após queda de energia ou Wi-Fi. |

---

## 📊 Fase 4: Coleta de Dados e Entrega
**Foco:** Documentação, manuais e apresentação dos resultados.

| Semana | Datas | Atividade | Detalhamento das Tarefas (P2 e P4) |
| :--- | :--- | :--- | :--- |
| **13** | 18/05 - 24/05 | Geração de Métricas | Coleta de logs: Taxa de acerto na detecção vs. Falsos positivos em ambiente real. |
| **14** | 25/05 - 31/05 | Relatório Técnico | Escrita do documento detalhando a arquitetura de software e os desafios de hardware superados. |
| **15** | 01/06 - 07/06 | Mídia e Portfólio | Gravação de vídeo demonstrativo (Pitch); Fotografia profissional do protótipo finalizado. |
| **16** | 08/06 - 14/06 | Manual do Usuário | Criação de guia passo-a-passo para instalação e configuração do Wi-Fi/Telegram pelo usuário. |
| **17** | 15/06 - 21/06 | Preparação Final | Revisão do código no GitHub; Organização de pastas; Ensaio da apresentação final. |
| **18** | 22/06 - 30/06 | Entrega do MVP | Apresentação para o LARAF e entrega do relatório final e protótipo funcional. |

---

## ✅ Definição de Pronto (DoD)
Para cada semana ser considerada concluída:
* O código deve estar no repositório.
* A funcionalidade deve ser validada fisicamente (LED ou Serial).
* A documentação da semana deve estar atualizada no log do projeto.

> Gerado para o Projeto Monitor de Alertas Residenciais - LARAF 2026

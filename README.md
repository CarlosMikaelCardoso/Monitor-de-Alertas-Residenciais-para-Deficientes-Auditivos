# 🔊 Monitor de Alertas Residenciais para Deficientes Auditivos (LARAF 2026)

> **Status do Projeto:** 💻 Fase de Simulação e Validação Lógica (Aguardando Chegada de Hardware)

## 📝 Visão Geral
Este projeto atua como um **"tradutor sensorial"** inteligente para promover a autonomia de pessoas com deficiência auditiva, monitorando o ambiente para identificar padrões sonoros (interfones, campainhas) e convertendo-os em alertas visuais e notificações. 

Devido à indisponibilidade momentânea dos componentes físicos, o plano de desenvolvimento foi refatorado para focar em **modelagem matemática, simulação virtual e arquitetura de software**, garantindo que a lógica esteja pronta para o *deploy* assim que o hardware chegar.

---

## 👥 Estrutura da Equipe (4 Membros)

Para otimizar o desenvolvimento teórico e a simulação, a equipe foi dividida nas seguintes especialidades:

1.  **Especialista em Processamento Digital de Sinais (DSP):**
    * **Foco:** Modelagem matemática e algoritmos de detecção sonora.
    * **Responsabilidades:** Simulação de FFT (Fast Fourier Transform) e filtros de áudio em Python/C++.
2.  **Arquiteto de Firmware e Simulação:**
    * **Foco:** Lógica do ESP32 e ambientes virtuais (Wokwi).
    * **Responsabilidades:** Desenvolvimento da lógica de estados e multitarefa (FreeRTOS) para gerenciar sensores e atuadores.
3.  **Engenheiro de Conectividade e Integração:**
    * **Foco:** Protocolos de rede e API do Telegram.
    * **Responsabilidades:** Configuração do bot de notificações, segurança da conexão e simulação de tráfego de dados.
4.  **Designer de Produto e UX/UI:**
    * **Foco:** Design industrial, documentação e experiência do usuário.
    * **Responsabilidades:** Modelagem 3D da case (CAD), fluxogramas de interação e manuais técnicos.

---

## 🗓️ Cronograma de Desenvolvimento (Foco em Simulação)

Este cronograma de 18 semanas prioriza a criação de um "Gêmeo Digital" do projeto.

### Fase 1: Imersão e Setup Virtual (Semanas 1-4)
| Semana | Atividade | Foco das Tarefas |
| :--- | :--- | :--- |
| **01-02** | Configuração de Ambiente | Setup do Wokwi (simulador ESP32) e bibliotecas de processamento de áudio. |
| **03-04** | Estudos de Protocolo | Validação teórica do protocolo I2S e arquitetura Webhook para o Telegram. |

### Fase 2: Desenvolvimento de Lógica e MVP Simulado (Semanas 5-8)
| Semana | Atividade | Foco das Tarefas |
| :--- | :--- | :--- |
| **05-06** | Sprint de DSP | Testes de algoritmos de diferenciação de som usando arquivos de áudio pré-gravados (.wav). |
| **07-08** | Integração Virtual | Unificação do código de processamento com a lógica de Wi-Fi em ambiente simulado. |

### Fase 3: Arquitetura de Software e Design Mecânico (Semanas 9-12)
| Semana | Atividade | Foco das Tarefas |
| :--- | :--- | :--- |
| **09-10** | Refinamento de Código | Otimização do uso de memória do ESP32 e implementação de segurança SSL/TLS. |
| **11-12** | Modelagem 3D | Design da estrutura física (case) considerando furos para captação de som e difusão de luz LED. |

### Fase 4: Coleta de Dados e Prontidão de Hardware (Semanas 13-18)
| Semana | Atividade | Foco das Tarefas |
| :--- | :--- | :--- |
| **13-14** | Testes de Estresse | Simulação de funcionamento contínuo e tratamento de erros de conexão. |
| **15-16** | Documentação Final | Criação de manuais de usuário e relatórios técnicos de performance teórica. |
| **17-18** | Entrega do MVP Virtual | Apresentação do protótipo simulado e preparação para montagem física. |

---

## 🛠️ Tecnologias e Ferramentas de Apoio
* **Simulação de Hardware:** [Wokwi](https://wokwi.com/) (ESP32 / WS2812B).
* **Análise de Áudio:** Python (Librosa/NumPy) para prototipagem de FFT.
* **Modelagem 3D:** Tinkercad ou Fusion 360 para o design da case.
* **Firmware:** VS Code + PlatformIO / Arduino IDE.

---
*Projeto desenvolvido para o Laboratório de Automação e Robótica Aplicada e Fabricação (LARAF).*

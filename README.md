# 🔊 Monitor de Alertas Residenciais para Deficientes Auditivos (LARAF 2026)

> **Status do Projeto:** 🛠️ Em Desenvolvimento (Fase de Imersão Técnica)

## 📝 Sobre o Projeto
Este projeto atua como um **"tradutor sensorial"** inteligente. Desenvolvido para promover a autonomia de pessoas com deficiência auditiva, o dispositivo monitora o ambiente 24 horas por dia, identificando padrões sonoros específicos (interfones, campainhas ou alarmes) e convertendo-os em alertas visuais (LEDs RGB) e notificações digitais via Wi-Fi.

### 🌟 Valor Agregado
* **Autonomia:** Independência para receber encomendas e visitas.
* **Integração IoT:** Moderniza campainhas analógicas sem necessidade de reformas.
* **Versatilidade:** Calibração ajustável para diferentes frequências sonoras.

---

## 🚀 Tecnologias Utilizadas

### Hardware
* **Microcontrolador:** ESP32 NodeMCU (30/38 pinos).
* **Sensor de Áudio:** Microfone I2S INMP441 (Alta precisão).
* **Atuador Visual:** Fita LED RGB 5V (WS2812B endereçável).
* **Interface:** Protocolo I2S para áudio e Wi-Fi para conectividade.

### Software & Protocolos
* **Linguagem:** C++ (Arduino IDE / PlatformIO).
* **Notificações:** Telegram Bot API.
* **Processamento:** Algoritmos de filtragem de som (FFT - Fast Fourier Transform).

---

## 📅 Cronograma de Desenvolvimento (Sprint 2026)

O projeto está dividido em 4 fases principais baseadas na metodologia Ágil:

1.  **Fase 1: Imersão Técnica (Semanas 1-4):** Estudos de IoT, configuração de ambiente e unboxing de componentes.
2.  **Fase 2: Desenvolvimento MVP (Semanas 5-8):** Lógica de diferenciação de som e integração com Telegram.
3.  **Fase 3: Refinamento e Case (Semanas 9-12):** Soldagem definitiva, ajuste de sensibilidade e montagem da estrutura física.
4.  **Fase 4: Coleta de Dados e Entrega (Semanas 13-18):** Testes de campo, documentação final e entrega do MVP.

---

## 🔧 Configuração e Instalação (Em breve)
*Instruções sobre como clonar o repositório, configurar as bibliotecas do ESP32 e realizar a primeira queima do código.*

---

## 👥 Equipe (Squads)
* **Squad P2 (Processamento de Som):** Foco em algoritmos de áudio e sensor INMP441.
* **Squad P4 (Conectividade):** Foco em integração Wi-Fi e notificações mobile.

---

## 📄 Licença
Este projeto está sob a licença [MIT](LICENSE).

---
*Projeto desenvolvido para o Laboratório de Automação e Robótica Aplicada e Fabricação (LARAF).*

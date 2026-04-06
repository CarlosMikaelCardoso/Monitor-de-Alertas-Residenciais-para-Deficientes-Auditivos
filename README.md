# 🔊 Monitor de Alertas Residenciais para Deficientes Auditivos (LARAF 2026)

> **Status do Projeto:** 🔍 Fase de Pesquisa e Simulação (Aguardando Hardware)

Este projeto atua como um **"tradutor sensorial"** inteligente, desenvolvido para promover a autonomia de pessoas com deficiência auditiva. O dispositivo monitora o ambiente para identificar padrões sonoros específicos (interfones, campainhas ou alarmes) e converte-os em alertas visuais (LEDs RGB) e notificações digitais via Wi-Fi.

---

## 🎯 Estratégia de Contingência: Gêmeo Digital
Devido à indisponibilidade momentânea dos componentes físicos, o foco do desenvolvimento foi redirecionado para a **validação científica** e **prototipagem virtual**. Esta abordagem garante que a inteligência do sistema (algoritmos de DSP e lógica de rede) esteja pronta para o *deploy* imediato assim que o hardware chegar.

---

## 👥 Estrutura da Equipe (4 Especialistas)

A equipe foi reorganizada para cobrir todas as frentes de pesquisa e simulação:

1.  **Especialista em Processamento Digital de Sinais (DSP):** Modelagem matemática, análise de frequências e simulação de filtros FFT em Python.
2.  **Arquiteto de Firmware e Simulação:** Desenvolvimento da lógica multitarefa (FreeRTOS) e prototipagem no simulador Wokwi.
3.  **Engenheiro de Conectividade e Integração:** Configuração da API do Telegram Bot, segurança da informação e fluxos de rede.
4.  **Designer de Produto e UX/UI:** Modelagem 3D da case, estudo de ergonomia visual e documentação técnica de acessibilidade.

---

## 🗓️ Cronograma de 18 Semanas (Refatorado)

O cronograma original foi adaptado para marcos de validação teórica:

* **Fase 1: Imersão e Pesquisa (Sem. 1-4):** Levantamento de assinaturas sonoras e estudo de protocolos de áudio I2S.
* **Fase 2: Desenvolvimento Virtual (Sem. 5-8):** Criação de algoritmos de detecção em Python e simulação de notificações via Telegram.
* **Fase 3: Arquitetura e Design (Sem. 9-12):** Otimização do código C++ e modelagem CAD 3D para a estrutura física do dispositivo.
* **Fase 4: Coleta de Dados e Entrega (Sem. 13-18):** Testes de estresse em ambiente simulado e finalização da documentação técnica para o LARAF.

---

## 🧪 Frentes de Pesquisa Atuais

### 1. Pesquisa de Assinaturas Sonoras
* Análise espectral de diferentes tipos de campainhas e interfones para identificar frequências dominantes (Hz).
* Estudo de janelas de amostragem (FFT) para minimizar falsos positivos causados por ruídos domésticos.

### 2. Simulação Computacional
* **Wokwi:** Validação da lógica do ESP32, controle da fita LED WS2812B e integração Wi-Fi.
* **Python (Librosa/NumPy):** Prototipagem de filtros digitais e validação matemática da detecção sonora.
* **CAD (Fusion 360/Tinkercad):** Design da case considerando a acústica necessária para o microfone INMP441.

---

## 🚀 Tecnologias e Referências
* **Microcontrolador:** ESP32 NodeMCU (30/38 pinos).
* **Sensor de Áudio:** Microfone I2S INMP441.
* **Atuadores:** Fita LED RGB 5V (WS2812B).
* **Notificações:** Telegram Bot API e Protocolo HTTP/HTTPS.

---
*Projeto desenvolvido para o Laboratório de Automação e Robótica Aplicada e Fabricação (LARAF).*

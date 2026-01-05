# dw-iot-gateway <!-- omit from toc -->

![Static Badge](https://img.shields.io/badge/Hardware-ESP32--C6-black) ![Static Badge](https://img.shields.io/badge/Platform-ESP--IDF-red) ![GitHub top language](https://img.shields.io/github/languages/top/Murilotrevisan/dw-iot-gateway)


> Projeto de Hobby de Automação IoT profissional de uma lava-louças eletromecânica (Praxis LLP04) focada em segurança e arquitetura limpa de software.

## Índice <!-- omit from toc -->

- [Visão Geral](#visão-geral)
  - [Motivação](#motivação)
- [Arquitetura de Segurança](#arquitetura-de-segurança)
- [Hardware](#hardware)
- [Software](#software)
  - [Tecnologias](#tecnologias)
- [Diagramas](#diagramas)
- [Configuração e Build](#configuração-e-build)
- [Legal e Aviso de Segurança](#legal-e-aviso-de-segurança)
  - [DISCLAIMER](#disclaimer)
- [Autor](#autor)


## Visão Geral

O projeto dw-iot-gateway é um "Sidecar" (caixa externa) que moderniza uma máquina de lavar louças semi-automática (A cobaia foi a máquina de lavar louças Praxis LLP04 127V) sem alterar sua estrutura interna de segurança. O objetivo é substituir os controles manuais (Timer e Seletor de Temperatura) e as entradas e saídas de água manuais por uma unidade de controle baseada em ESP32-C6, permitindo automação via rede e monitoramento de estados.

### Motivação

Atuando como líder de software embarcado e tendo maior experiência no desenvolvimento de STM32 em sistemas crítico; Este projeto foi desenvolvido como um laboratório de engenharia para "desenferrujar" habilidades de software embarcado em baixo nível e aprender habilidades de softwares embarcado focados em conectividade e domótica, que são áreas pessoais de interesse, focando em:

- Clean Architecture e camadas de abstração (HAL).
- ESP-IDF Framework.
- Comunicação IOT de dispositivos inteligentes.

Além disso, esse projeto resolve uma dificuldade que é operar a máquina de lavar louças manual, automatizando alguns processos mais simples que exigem menor intervenção no sistema, e simplificando a vida do operador.

## Arquitetura de Segurança

Para garantir segurança operacional (evitar incêndios ou danos), o projeto adota uma abordagem de Intertravamento Híbrido. O firmware apenas "permite" o fluxo de energia; a segurança é garantida pela cadeia física original da máquina.

As adaptações realizadas na máquina devem substituir somente os botões manuais que são selecionados, sem substituir as lógicas internas ou componentes internos, isso reduz a complexidade e criticidade do projeto, expondo uma eventual falha de software a um risco reduzido.

## Hardware

- **MCU:** ESP32-C6 (MuseLab Nano - Dual USB).
- **Interface de potência:** Módulo de 4 Relés (10A) com isolamento óptico.
- **Atuadores:** 
  - Válvula Solenoide de Entrada (Água Limpa).
  - Válvula Solenoide de Saída (Drenagem por gravidade).
  - Motores e aquecedores já são internos da máquina e não foram alterados
- **Energia:** Em avaliação

OBS: Essa lista está em desenvolvimento, por este motivo são usados dev kits e não possui ainda todos os itens necessários.


## Software

O projeto é desenvolvido em C++ utilizando o framework ESP-IDF v5.x.

### Tecnologias

- **SO:** FreeRTOS;
- **Comunicação:** Wi-Fi;
- **Interface de controle externa:** TBD (comandos HTTP, Bot Telegram, MQTT, outros...);

## Diagramas

O projeto é documentado visualmente via Draw.io para garantir a coerência entre fiação e software.

![Water Circuit](https://github.com/Murilotrevisan/dw-iot-gateway/blob/main/docs/diagrams/water-circuit.png)

![Command Circuit](https://github.com/Murilotrevisan/dw-iot-gateway/blob/main/docs/diagrams/command-circuit.png)

## Configuração e Build

Under development

## Legal e Aviso de Segurança
**ALTA TENSÃO (127V/220V)**
Este projeto envolve manipulação de corrente elétrica em alta tensão e água.

- **NÃO** conecte a máquina à rede elétrica com a caixa aberta ou componentes expostos;
- Utilize isolamento apropriado em todas as emendas;
- Respeite sempre a polaridade Fase/Neutro;
- **NÃO** faça alterações elétricas se não tiver conhecimento do que está sendo feito, ou assuma o risco de danos ao equipamento, esse projeto não é um guia completo sem chance de falhas de como aplicar uma modificação em seu equipamento.
- **Esse projeto não tem a intenção de ser uma alteração oficial ou segura/certificada, faça as alterações por sua conta e risco, assumindo a responsabilidade própria pelos danos causados ao equipamento ou o seu entorno.**

### DISCLAIMER
Este projeto é um protótipo de hobby e fins educacionais. O autor não se responsabiliza por danos à propriedade, incêndios, choques elétricos ou quaisquer outros danos resultantes do uso ou montagem deste projeto. Use por sua conta e risco.

## Autor
Murilo Trevisan 
[GitHub](https://github.com/Murilotrevisan)
[Linkedin](https://www.linkedin.com/in/murilo-trevisan/)
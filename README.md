# PROJETO IOT - MONITORAMENTO INTELIGENTE DE MOTOS (MOTTU)

## CONTEXTO
A Mottu é uma das maiores empresas de aluguel de motos do Brasil, com presença também no México.  
Um dos principais desafios operacionais é o gerenciamento das motos dentro dos pátios das filiais, garantindo organização, segurança e disponibilidade da frota.

---

## OBJETIVO
O protótipo demonstra como sensores e atuadores podem ser integrados para:

- Monitorar o status de motos no pátio.
- Alertar sobre mudanças de estado (moto em uso, moto parada, moto em posição incorreta).
- Registrar informações de forma persistente (EEPROM).
- Exibir dados em tempo real em um display LCD.
- Enviar dados para a nuvem via Thinger.io e permitir monitoramento remoto.

---

## COMPONENTES UTILIZADOS
- ESP32 DevKit V4 (microcontrolador principal com Wi-Fi integrado)
- DHT22 (sensor de temperatura e umidade – simulação de telemetria ambiental no pátio)
- Botão (Pushbutton) → usado para alternar o estado do sistema (ON/OFF)
- LED → indica visualmente se o sistema está ativo ou não
- Buzzer → emite alerta sonoro quando o sistema está ativo
- LCD I2C 16x2 → exibe status do sistema e leituras de sensores
- EEPROM interna do ESP32 → garante persistência do estado (mantém o último valor salvo)
- Thinger.io → plataforma IoT utilizada para conectar o dispositivo e criar o dashboard web

---

## FUNCIONALIDADES

### 1. CONTROLE ON/OFF DO SISTEMA
- Ao pressionar o botão físico, o sistema alterna entre ligado e desligado.
- O estado é salvo na EEPROM e restaurado automaticamente ao reiniciar o ESP32.
- LED e buzzer seguem o estado do sistema.

### 2. INDICAÇÃO VISUAL E SONORA
- LED acende e buzzer soa quando o sistema está ON.
- Ambos desligam quando o sistema está OFF.

### 3. TELEMETRIA AMBIENTAL
- A cada 10 segundos, o sistema lê os valores de temperatura e umidade do sensor DHT22.
- As leituras são exibidas no LCD e enviadas para o Thinger.io.
- Caso o sensor falhe, o LCD exibe “Read fail!” e o erro é registrado no Serial Monitor.

### 4. INTEGRAÇÃO COM A NUVEM (THINGER.IO)
- O ESP32 conecta-se via Wi-Fi ao Thinger.io e envia as leituras para a nuvem.
- É possível visualizar e controlar o sistema remotamente através de um dashboard web.

Recursos principais configurados:
- dht/temp → valores de temperatura
- dht/hum → valores de umidade
- state → status ON/OFF do sistema

### 5. PERSISTÊNCIA DE ESTADO
- Mesmo após desligar ou reiniciar, o sistema mantém o último estado (ON/OFF) salvo na EEPROM.

---

## DASHBOARD NO THINGER.IO

O painel web foi desenvolvido com os seguintes widgets:

| Widget | Recurso | Função |
|--------|----------|--------|
| Gauge | dht/temp | Exibe a temperatura ambiente (°C) |
| Gauge | dht/hum | Exibe a umidade relativa do ar (%) |
| True/False State | state | Exobe se a moto está em uso ou não |

O dashboard fornece uma visualização em tempo real do ambiente e do status da moto simulada.

---

## CASOS DE USO DEMONSTRADOS
- Moto retirada do pátio → botão pressionado ou switch ativado → LED e buzzer ligados → sistema ON.
- Moto devolvida → botão pressionado novamente → LED e buzzer desligados → sistema OFF.
- Falha de sensor → LCD exibe “Read fail!”.
- Queda de energia → ao religar, o ESP32 lê a EEPROM e restaura o último estado.
- Monitoramento remoto → Thinger.io exibe temperatura, umidade e status do sistema em tempo real.

---

## COMO O PROTÓTIPO APOIA A MOTTU
Este protótipo é uma prova de conceito (PoC) que demonstra o potencial da IoT no gerenciamento de frotas:

- Botão, LED e Buzzer: simulam o controle físico de uma moto sendo retirada ou devolvida ao pátio.
- LCD: funciona como painel local, exibindo dados do ambiente e do sistema.
- DHT22: representa sensores ambientais que podem ser aplicados em pátios reais.
- Thinger.io: mostra o conceito de centralização e controle remoto via nuvem.

---

## PRÓXIMOS PASSOS
- Integração com dashboards avançados (Node-RED, Power BI ou Web App)
- Expansão do projeto para múltiplas motos e sensores
- Envio dos dados via MQTT/HTTP para um servidor central
- Integração com visão computacional para leitura automática de placas
- Comunicação direta com o backend da Mottu

---

## INSTRUÇÕES DE USO

### SIMULAÇÃO
- O projeto pode ser executado no Wokwi (https://wokwi.com/) utilizando o arquivo diagram.json e o código disponível no repositório.
- Configure os pinos conforme especificado no código.
- Execute a simulação e observe o comportamento no Serial Monitor e no LCD.

### INTEGRAÇÃO COM THINGER.IO
1. Crie uma conta gratuita em https://thinger.io.
2. Cadastre um novo dispositivo com:
   - Device ID: esp32_dht22
   - Device Credential: conforme definido no código.
3. Crie um dashboard e adicione os widgets descritos acima.
4. Execute o projeto no Wokwi e aguarde a conexão Wi-Fi para visualizar os dados em tempo real.

---

## EQUIPE DE DESENVOLVIMENTO

| Nome | RM | Turma |
|------|----|--------|
| Eduarda Tiemi | 554756 | 2TDSPH |
| Felipe Pizzinato | 555141 | 2TDSPW |
| Gustavo Sandrini | 557505 | 2TDSPW |

---

## RECURSOS
- Vídeo de Apresentação: [https://youtu.be/-1XiyG2rE-o]

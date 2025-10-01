# 🚀 Projeto IoT - Gerenciamento de Motos no Pátio (Mottu)

## 📌 Contexto
A **Mottu** é uma das maiores empresas de aluguel de motos do Brasil, com operações também no México.  
Um dos desafios enfrentados é o **gerenciamento das motos dentro dos pátios** das filiais, garantindo organização, controle e prevenção de falhas no posicionamento e disponibilidade da frota.

Este projeto é parte da disciplina de **Disruptive Architectures: IoT, IoB & Generative IA** e tem como objetivo criar um **protótipo funcional em IoT** que simula esse gerenciamento.

---

## 🎯 Objetivo
O protótipo demonstra como sensores e atuadores podem ser integrados para:
- Monitorar o status de motos no pátio.  
- Alertar sobre mudanças de estado (moto em uso, moto parada, moto em posição incorreta).  
- Registrar informações de forma persistente (EEPROM).  
- Exibir dados em tempo real em um display LCD.  

---

## 🛠️ Componentes Utilizados
- **Arduino UNO** (microcontrolador principal)  
- **DHT22** (sensor de temperatura e umidade → simulação de telemetria ambiental no pátio)  
- **Botão (Pushbutton)** → usado para alternar o estado do sistema (ON/OFF).  
- **LED** → indica visualmente se o sistema está ativo ou não.  
- **Buzzer** → emite alerta sonoro quando o sistema está ativo.  
- **LCD I2C 16x2** → exibe status do sistema e leituras de sensores.  
- **EEPROM** (memória interna do Arduino) → garante persistência do estado (se estava ON ou OFF antes de desligar, ao ligar novamente mantém o mesmo estado).  

---

## ⚙️ Funcionalidades
1. **Controle ON/OFF do sistema**  
   - Ao pressionar o botão, alterna entre ligado e desligado.  
   - O estado é salvo na EEPROM e restaurado ao reiniciar o sistema.  

2. **Indicação visual e sonora**  
   - LED acende e buzzer soa quando o sistema está **ON**.  
   - Ambos desligam quando o sistema está **OFF**.  

3. **Telemetria simulada**  
   - A cada 10 segundos, o sistema lê os valores do DHT22 (temperatura e umidade).  
   - Exibe os valores no LCD e também envia via Serial Monitor.  

4. **Registro de falhas**  
   - Caso o sensor não responda, uma mensagem de erro aparece no LCD e no Serial Monitor.  

---

## 📚 Como esse protótipo ajuda no sistema da Mottu
Este protótipo não é o sistema final, mas **uma prova de conceito** que mostra como a IoT pode apoiar o gerenciamento de motos no pátio da Mottu:

- **Botão + LED + Buzzer**  
  Simulam o controle de uma moto sendo retirada ou devolvida ao pátio.  
  → ON: moto em uso / registrada.  
  → OFF: moto parada no pátio.  

- **EEPROM**  
  Garante que, mesmo se houver queda de energia, o status da moto permanece registrado.  

- **LCD**  
  Funciona como um painel local de telemetria, mostrando informações simples de status e condições ambientais.  

- **DHT22**  
  Simula coleta de dados do ambiente (exemplo: temperatura do pátio).  
  No futuro, pode ser expandido para monitorar condições que afetam a frota, como calor excessivo ou umidade.  

---

## 🚦 Casos de Uso Demonstrados
- **Moto retirada do pátio** → Botão pressionado → sistema marca como ON → LED + buzzer ativados.  
- **Moto devolvida** → Botão pressionado → sistema marca como OFF → LED + buzzer desligados.  
- **Falha de sensor** → LCD exibe `Read fail!`.  
- **Queda de energia** → Ao religar, o Arduino lê a EEPROM e restaura o estado da última moto registrada.  

---

## 📈 Próximos Passos
- Integração com dashboards externos (Node-RED, Power BI ou Web App).  
- Expansão para múltiplos sensores (simulando várias motos no pátio).  
- Uso de comunicação em rede (MQTT/HTTP) para enviar dados para um servidor central.  
- Integração com visão computacional (ex.: leitura de placas para automatizar entrada/saída).  

---

## 👨‍💻 Autores
| Nome Completo	    | RM    | Turma  |
|-------------------|-------|--------|
| Eduarda Tiemi	    |554756 | 2TDSPH |
| Felipe Pizzinato	|555141 | 2TDSPW |
| Gustavo Sandrini	|557505 | 2TDSPW |

---

## LNK VÍDEO

[https://youtu.be/-1XiyG2rE-o]

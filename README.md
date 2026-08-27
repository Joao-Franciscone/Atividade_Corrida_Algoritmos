# 🚕 Simulação de Corridas de Táxi

## 📖 Sobre o Projeto
Este projeto é uma aplicação web desenvolvida para simular e acompanhar o consumo de combustível diário do taxista Agostinho. A simulação permite calcular o tempo de viagem, o gasto de combustível de cada corrida e emitir alertas automáticos sobre a necessidade de reabastecimento.

## ⚙️ Funcionalidades e Requisitos
O programa possui dois campos de entrada para o usuário:
* **Distância da corrida:** em quilômetros (km).
* **Velocidade média:** em quilômetros por hora (km/h).

Ao clicar no botão **"Simular"**, o sistema realiza as seguintes ações:
1. **Calcula o tempo médio** da corrida relacionando a distância e a velocidade.
2. **Calcula o combustível gasto** (em litros e sua respectiva porcentagem em relação ao tanque inicial).
3. **Calcula o combustível restante** (em litros e porcentagem).
4. **Exibe o resumo da viagem** no seguinte formato:
   > "Ao percorrer AA km, em velocidade média de BB km/h, a viagem durou CC horas. Ao todo, foram gastos DD litros de combustível (EE%). Restam FF litros de combustível (GG%)."
5. **Emite um alerta de segurança** baseado na reserva de 30%:
   * Se o combustível restante for **≥ 30%** do inicial: exibe `"Continue a rodar!"`
   * Se o combustível restante for **< 30%** do inicial: exibe `"É melhor parar para reabastecer!"`

## 🧠 Regras de Negócio e Lógica
* **Combustível Inicial:** O dia de trabalho sempre começa com **25 litros** (equivalente a 100% da capacidade do dia).
* **Consumo do Veículo:** O carro percorre, em média, **10 km com 1 litro**.
* **Controle Global:** O combustível gasto em uma corrida é descontado do total, garantindo que a próxima simulação use o valor atualizado (usando uma variável global `let`).
* **Cálculo de Porcentagem:** Utiliza-se Regra de 3 (Ex: 25L = 100%, X Litros = Y%).
* **Validação dos 30%:** A verificação de reabastecimento considera sempre 30% do combustível inicial (ou seja, 7.5 litros).
* **Estrutura Técnica:** Uso de variáveis locais para o escopo das corridas, operadores matemáticos (`+`, `-`, `/`, `*`) e estrutura de decisão (`if/else`).

## 🖥️ Exemplo de Funcionamento

**Simulação 1:**
* Distância: `100 km` | Velocidade: `50 km/h`
* **Saídas:**
  > Ao percorrer 100 km, em velocidade média de 50 km/h, a viagem durou 2 horas. Ao todo, foram gastos 10 litro(s) de combustível (40%). Restam 15 litro(s) de combustível (60%).
  
  > Continue a rodar! *(Ainda resta 60% do combustível inicial)*

**Simulação 2 (Inserindo os mesmos valores logo em seguida):**
* Distância: `100 km` | Velocidade: `50 km/h`
* **Saídas:**
  > Ao percorrer 100 km, em velocidade média de 50 km/h, a viagem durou 2 horas. Ao todo, foram gastos 10 litro(s) de combustível (40%). Restam 5 litro(s) de combustível (20%).
  
  > É melhor parar para reabastecer! *(Caiu para 20%, abaixo da margem de 30%)*

## 🛠️ Tecnologias Utilizadas
* HTML5
* JavaScript 
* CSS
# Instalação do Arduino IDE e seleção de placa

Os passos abaixo foram conferidos no Arduino IDE 2.3.10 com o pacote `esp32` 3.3.12.

## 1. Instale o Arduino IDE 2

Baixe em <https://www.arduino.cc/en/software> e instale normalmente.

## 2. Adicione o endereço de placas da Espressif

1. Abra **Arquivo → Preferências**.
2. Em **URLs do Gerenciador de Placas Adicionais**, cole:

```text
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

3. Clique em **OK**.

## 3. Instale o pacote esp32

1. Abra o **Gerenciador de Placas**, no ícone de placa da barra lateral.
2. Procure por `esp32`.
3. Instale **esp32 por Espressif Systems**. Não confunda com "Arduino ESP32 Boards", que é outro pacote.

O download é grande: nesta produção, o pacote ocupou cerca de 8,5 GB em disco.

## 4. Selecione a placa

1. Clique em **Selecionar Placa → Selecionar outra placa e porta**.
2. Procure por `ESP32 Dev Module` e selecione.
3. Se a placa física estiver conectada, selecione também a porta dela.

Sem porta, você ainda consegue compilar, mas não consegue enviar o programa.

## 5. Crie o sketch

1. Abra **Arquivo → Novo Esboço**.
2. Cole o código de `firmware/blink/blink.ino`.
3. Salve com o nome `blink`.

## 6. Compile

Clique em **Verificar**, o botão com o sinal de confirmação. Compilar transforma o texto em firmware. A placa não precisa estar conectada.

## 7. Envie para a placa física

Clique em **Enviar**, o botão com a seta. Na DevKitC V4, o envio costuma ser automático.

Se aparecer erro de conexão, segure o botão **BOOT** enquanto o envio tenta conectar.

Em nosso laboratório, a aula foi executada apenas em simulador. O envio para uma placa física não foi testado nesta produção.

## Compilar, gravar e simular

| Etapa | O que acontece | Precisa de placa? |
|---|---|---|
| Compilar | O texto vira firmware | Não |
| Gravar | O firmware vai pelo USB para a memória da placa | Sim |
| Simular | O firmware roda em um programa que imita o ESP32 | Não |

## Pela linha de comando

```bash
arduino-cli config add board_manager.additional_urls https://espressif.github.io/arduino-esp32/package_esp32_index.json
arduino-cli core update-index
arduino-cli core install esp32:esp32@3.3.12
arduino-cli compile --fqbn esp32:esp32:esp32 firmware/blink
```

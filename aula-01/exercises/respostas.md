# Respostas comentadas: Aula 01

## Compreensão

**1.** O chip ESP32 é o microcontrolador. O módulo WROOM-32E reúne o chip, a memória flash e a antena dentro da parte metálica e da sua pequena placa. A DevKitC V4 é a placa de desenvolvimento: leva os sinais até pinos e adiciona USB, regulador e botões.

**2.** HIGH significa que o programa colocou o pino perto de 3,3 V em relação ao GND. É uma tensão mantida, não um envio de corrente.

**3.** Sem o GND, o caminho fica aberto. Existe tensão no pino, mas não há caminho completo, então não surge corrente.

**4.** O ânodo, a perna longa. A corrente entra pelo ânodo e sai pelo cátodo.

**5.** Compilar transforma texto em firmware. Gravar envia o firmware para a placa física pelo USB. Simular executa o firmware em um programa que imita o ESP32.

## Prática no código

**6.** O período original é de 2000 ms. Quatro vezes mais rápido é 500 ms, ou seja, `delay(250)` nas duas pausas.

```cpp
void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(250);

  digitalWrite(LED_PIN, LOW);
  delay(250);
}
```

**7.** O primeiro `delay` controla o tempo aceso, e o segundo, o tempo apagado.

```cpp
void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(100);

  digitalWrite(LED_PIN, LOW);
  delay(900);
}
```

**8.** Basta mudar a primeira linha, e esse é o motivo de usarmos um nome: `const int LED_PIN = 22;`. No circuito, o fio passa para a coluna do pino 22, a coluna 20 neste layout.

## Raciocínio

**9.** A corrente diminui, porque a resistência aumentou. Com cerca de 1,3 V no resistor, ela cai para perto de 1,3 mA, e o LED fica mais fraco.

**10.** A configuração só precisa acontecer uma vez. Repetir em `loop` não ajuda e deixa o programa mais confuso.

## Desafio

**11.** Uma solução possível:

```cpp
const int LED_PIN = 23;

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(150);
  digitalWrite(LED_PIN, LOW);
  delay(150);

  digitalWrite(LED_PIN, HIGH);
  delay(150);
  digitalWrite(LED_PIN, LOW);
  delay(1000);
}
```

As três pausas curtas criam as piscadas. A pausa maior, no final, cria o intervalo antes de repetir.

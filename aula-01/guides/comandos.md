# Explicação de cada comando

## O programa inteiro

```cpp
const int LED_PIN = 23;

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(1000);

  digitalWrite(LED_PIN, LOW);
  delay(1000);
}
```

## Linha a linha

| Trecho | O que significa |
|---|---|
| `int` | Número inteiro |
| `LED_PIN` | Nome que escolhemos |
| `23` | Valor: o número do GPIO |
| `const` | O valor não muda durante o programa |
| `;` | Encerra a instrução |
| `void` | A função não devolve valor |
| `setup()` | Roda uma vez, quando a placa inicia |
| `loop()` | Repete enquanto a placa estiver ligada |
| `{ }` | Marcam o início e o fim de um bloco |
| `pinMode(pino, modo)` | Define como o pino vai funcionar |
| `OUTPUT` | Modo de saída: o programa define o nível |
| `digitalWrite(pino, nível)` | Escreve um nível no pino |
| `HIGH` | Nível alto: perto de 3,3 V no ESP32 |
| `LOW` | Nível baixo: perto de 0 V |
| `delay(ms)` | Pausa o programa pelo tempo indicado |
| `1000` | Mil milissegundos, ou um segundo |

## O que acontece no circuito

**Com `HIGH`**, o GPIO23 fica perto de 3,3 V em relação ao GND. Como existe um caminho fechado, surge corrente pelo resistor e pelo LED, e o LED acende.

**Com `LOW`**, o GPIO23 fica perto de 0 V. A tensão no circuito não basta para o LED conduzir, a corrente para e o LED apaga.

HIGH não significa enviar corrente. O pino mantém uma tensão, e a corrente depende do circuito ligado a ele.

## Por que o resistor é necessário

Um LED vermelho típico fica com cerca de 2 V entre as pernas enquanto acende. Esse valor varia de LED para LED.

```text
Tensão no resistor: 3,3 V − 2 V = 1,3 V
Corrente: 1,3 V ÷ 330 Ω ≈ 4 mA
```

Para tensões de LED entre 1,8 V e 2,2 V, a corrente fica entre cerca de 3,3 mA e 4,5 mA.

## O que `delay()` faz no ESP32

Durante o `delay`, o nosso programa fica parado esperando, mas o ESP32 não fica gastando processamento nesse laço: o FreeRTOS coloca a tarefa para aguardar. Outras tarefas do sistema continuam funcionando. FreeRTOS é o pequeno sistema que organiza essas tarefas dentro do ESP32.

## Por que usamos o GPIO23

- Ele fica ao lado de um pino GND, o que deixa a montagem curta.
- Ele não é um pino de configuração de boot do ESP32.
- Ele aceita a função de saída.

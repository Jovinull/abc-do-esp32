# Principais erros e soluções

## O LED não acende

| Causa provável | O que fazer |
|---|---|
| LED invertido | Coloque a perna longa no lado do resistor |
| Fio na coluna errada | Confira as colunas 21, 27, 33 e 34, sempre na metade de baixo, fileiras f a j |
| GND não ligado | Confira os dois fios até a trilha azul |
| Pino errado | Confirme que o fio sai do GPIO23, ao lado do GND |
| Protoboard com trilha dividida | Em alguns modelos, a trilha é interrompida no meio. Ligue os dois fios no mesmo trecho |
| Resistor de valor muito alto | Confira as faixas: laranja, laranja, marrom |

## O código não compila

| Mensagem ou sintoma | O que fazer |
|---|---|
| `expected ';' before ...` | Falta um ponto e vírgula na linha anterior |
| `'LED_PIN' was not declared in this scope` | Confira a escrita. O C++ diferencia maiúsculas e minúsculas |
| `expected '}' at end of input` | Falta fechar uma chave |
| Placa não selecionada | Selecione **ESP32 Dev Module** |

## O envio para a placa falha

| Sintoma | O que fazer |
|---|---|
| Nenhuma porta aparece | Troque o cabo: muitos cabos USB só carregam |
| Nenhuma porta aparece, com outro cabo | Instale o driver do conversor USB da sua placa |
| `Failed to connect to ESP32: Timed out waiting for packet header` | Segure **BOOT** enquanto o envio tenta conectar |
| O erro continua | Teste outra porta USB e evite hubs |

## O LED fica sempre aceso ou sempre apagado

| Causa provável | O que fazer |
|---|---|
| Valores de `delay` muito pequenos | Com intervalos muito curtos, o olho não percebe a piscada |
| Falta o segundo `delay` | Sem ele, o LED fica apagado por um instante curto demais para ver |
| `pinMode` ausente | Sem `OUTPUT`, o pino não funciona como saída |

## Tempos medidos na simulação

Registro das escritas no GPIO23, no QEMU:

| Programa | Aceso | Apagado |
|---|---|---|
| 1000/1000 ms | 1000,4 ms | 1001,5 ms |
| 200/200 ms | 200,9 ms | 200,9 ms |
| 2000/500 ms | 2002,3 ms | 503,6 ms |

## Cuidados com a placa

- Nunca ligue 5 V diretamente em um GPIO.
- Use apenas uma forma de alimentação por vez: USB, pino 5V ou pino 3V3.
- Evite os pinos D0, D1, D2, D3, CMD e CLK. Eles são usados internamente pela memória flash.

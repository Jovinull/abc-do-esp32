# Exercícios — Aula 01

Tente resolver antes de abrir as [respostas comentadas](respostas.md).

## Compreensão

1. Qual é a diferença entre o chip ESP32, o módulo WROOM-32E e a placa DevKitC V4?
2. Com suas palavras, o que significa HIGH em um GPIO do ESP32?
3. Por que o LED não acende se o fio do GND for retirado, mesmo com o pino em HIGH?
4. Qual perna do LED deve ficar do lado do resistor neste circuito?
5. Qual é a diferença entre compilar, gravar e simular?

## Prática no código

6. Faça o LED piscar quatro vezes mais rápido que o programa original.
7. Faça o LED ficar aceso por 100 ms e apagado por 900 ms.
8. Mude o circuito e o código para usar o GPIO22. Quais linhas do programa precisam mudar?

## Raciocínio

9. Se você trocar o resistor de 330 Ω por um de 1 kΩ, o que acontece com a corrente e com o brilho?
10. Por que colocar `pinMode` dentro de `setup` e não dentro de `loop`?

## Desafio

11. Faça o LED piscar duas vezes rápido, ficar apagado por um segundo e repetir esse padrão.

# Segundo teste 15/10/2026
Houve sim outros testes, mas basicamente foi com o mesmo código envolvendo testar componentes coisa que já fizemos antes e descrevemos estávamos passando bastante dificuldade com a parte de hardware, pois vários componentes davam problemas, e também acontecia erros nossos. mas, conseguimos superar e fizemos o código pro carrinho funcionar em bluetooth:

## Codigo
```cpp
#include "BluetoothSerial.h"
BluetoothSerial SerialBT;

// Ponte H (ENA = motor esquerdo, ENB = motor direito)
const int IN1 = 26;
const int IN2 = 25;
const int IN3 = 33;
const int IN4 = 32;
//const int ENA = 25;
//const int ENB = 33;

void setup() {
  Serial.begin(115200);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  
  // Começa parado
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
  //analogWrite(ENA, 0);
  //analogWrite(ENB, 0);
  
  SerialBT.begin("CARRINHO");   // liga o Bluetooth
  Serial.println("Pronto. Pareie com CARRINHO.");
  
}

void loop() {
  if (SerialBT.available()) {
    char c = SerialBT.read();
    Serial.println(c);

    switch (c) {
      case 'F':   // Frente
        digitalWrite(IN1, HIGH);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, HIGH);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 255);
        //analogWrite(ENB, 255);
        break;

      case 'B':   // Trás
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, HIGH);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, HIGH);
        //analogWrite(ENA, 255);
        //analogWrite(ENB, 255);
        break;

      case 'L':   // Esquerda
        digitalWrite(IN1, HIGH);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 255);
        //analogWrite(ENB, 0);
        break;

      case 'R':   // Direita
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, HIGH);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 0);
        //analogWrite(ENB, 255);
        break;

      case 'G':   // Frente e esquerda
        digitalWrite(IN1, HIGH);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 255/2);
        //analogWrite(ENB, 0);
        break;

      case 'I':   // Frente e direita
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, HIGH);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 0);
        //analogWrite(ENB, 255/2);
        break;

      case 'H':   // Trás e esquerda
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, HIGH);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 255/2);
        //analogWrite(ENB, 0);
        break;

      case 'J':   // Trás e direita
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, HIGH);
        //analogWrite(ENA, 0);
        //analogWrite(ENB, 255/2);
        break;

      case 'S':   // Parar
        digitalWrite(IN1, LOW);
        digitalWrite(IN2, LOW);
        digitalWrite(IN3, LOW);
        digitalWrite(IN4, LOW);
        //analogWrite(ENA, 0);
        //analogWrite(ENB, 0);
        break;
    }
  }
```

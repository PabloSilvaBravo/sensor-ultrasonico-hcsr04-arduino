# Medir distancia con Arduino y el sensor ultrasónico HC-SR04

Este ejemplo muestra cómo utilizar el sensor ultrasónico **HC-SR04** con una placa **Arduino UNO** para medir distancias. Ideal para proyectos educativos o makers que estén comenzando.

> 🔗 Puedes conseguir el sensor directamente en [MechatronicStore.cl](https://www.mechatronicstore.cl/sensor-ultrasonico-hc-sr04/)

---

## 🧰 Materiales

- 1x Arduino UNO
- 1x Sensor ultrasónico HC-SR04
- Cables dupont
- Protoboard (opcional)

---

## 🔌 Esquema de conexión

| Pin HC-SR04 | Pin Arduino |
|-------------|-------------|
| VCC         | 5V          |
| GND         | GND         |
| TRIG        | 9           |
| ECHO        | 10          |

---

## 📜 Código de ejemplo

```cpp
#define trigPin 9
#define echoPin 10

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  float distance = duration * 0.034 / 2;

  Serial.print("Distancia: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500);
}

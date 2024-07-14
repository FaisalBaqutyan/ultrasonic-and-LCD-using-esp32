# ultrasonic-and-LCD-using-esp32

i desgined a circuit diagram that uses the ultrasonc sensor to calculate the distance the disply it in the LCD using esp32 and here is the circuit diagram 


![Screenshot 2024-07-14 102648](https://github.com/user-attachments/assets/54897fbc-ce35-4c89-b102-3193be4cd8a2)


and the arduino code 

```
#include <LiquidCrystal_I2C.h>
#include <Wire.h>
#define echoPin 18
#define trigPin 19
long duration, distance;
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  
 lcd.init();
 lcd.backlight();

 pinMode(trigPin, OUTPUT);
 pinMode(echoPin, INPUT);

 lcd.setCursor(0, 0);
 lcd.print("Distance");
}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin,  HIGH);
  distance = duration / 58.2;

  lcd.setCursor(0, 1);
  lcd.print("                ");
  lcd.setCursor(0, 1);
  lcd.print(distance);
  lcd.print(" cm");
  delay(500); // this speeds up the simulation
}
```

and it works perfectly 


![Screenshot 2024-07-14 103044](https://github.com/user-attachments/assets/1f0d2f0e-b913-4dae-a1ea-20a4bb5709f4)

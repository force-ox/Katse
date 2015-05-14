#include <LiquidCrystal.h>

// vormindab numbritega liideste viigud
LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

// muutuja sisendid juhivad valgusdioode
  int analogInput = 1;
  float vout = 0.0;
  float vin = 0.0;
  float R1 = 50000.0;    // R1 takistus
  float R2 = 4400.0;     // R2 takistus

// muutuja salvestab väärtuse
  int value = 0;

void setup(){
  // võtab omaks viigu režiimid
  pinMode(analogInput, INPUT);

  // sätib paika ekraani ridade ja veergude numbrid
  lcd.begin(16, 2);
  lcd.print("Vin=");
}

void loop(){
  //loeb vääruse analoogsisendilt
  value = analogRead(analogInput);

  vout = (value * 5.0) / 1024.0;
  vin = vout / (R2/(R1+R2));  

  // kuvab näidu ekraanile
  lcd.setCursor(4, 0);
  lcd.print(vin);
  lcd.print("V");

//jõudeolek
  delay(500);
}

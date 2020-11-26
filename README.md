# Codigo_slider
void pantalla_uno() {
  readgrados = analogRead(A0);
  gradostilt = map(readgrados, 0, 1023, 0, 120);

  readtiempo = analogRead(A1);
  tiempotilt = map(readtiempo, 0, 1023, 0, 60);

  pasos_tilt_set = cantidad_pasos_tilt(gradostilt);
  retardo_tilt_set = tiempotilt;

  lcd.setCursor(6, 0);
  lcd.print("TILT");
  lcd.setCursor(0, 1);
  lcd.print("ANGL:");
  lcd.setCursor(5, 1);
  lcd.print(gradostilt);
  lcd.setCursor(9, 1);
  lcd.print("TIME:");
  lcd.setCursor(14, 1);
  lcd.print(tiempotilt);
}

void pantalla_dos() {

  readgrados = analogRead(A0);
  gradospan = map(readgrados, 0, 1023, 0, 180);

  readtiempo = analogRead(A1);
  tiempopan = map(readtiempo, 0, 1023, 0, 60);
  
  pasos_pan_set = cantidad_pasos_pan(gradospan);
  retardo_pan_set = tiempopan;

  lcd.setCursor(6, 0);
  lcd.print("PAN");
  lcd.setCursor(0, 1);
  lcd.print("ANGL:");
  lcd.setCursor(5, 1);
  lcd.print(gradospan);
  lcd.setCursor(9, 1);
  lcd.print("TIME:");
  lcd.setCursor(14, 1);
  lcd.print(tiempopan);
}

void pantalla_tres() {
  readgrados = analogRead(A0);
  distlong = map(readgrados, 0, 1023, 0, 50);

  readtiempo = analogRead(A1);
  tiempolong = map(readtiempo, 0, 1023, 0, 60);

  pasos_long_set = cantidad_pasos_long(distlong);
  retardo_long_set = tiempolong;

  lcd.setCursor(6, 0);
  lcd.print("Long");
  lcd.setCursor(0, 1);
  lcd.print("DIST:");
  lcd.setCursor(5, 1);
  lcd.print(distlong);
  lcd.setCursor(9, 1);
  lcd.print("TIME:");
  lcd.setCursor(14, 1);
  lcd.print(tiempolong);

}














int long_move(int retardo_long, int pasos_long, bool direct_long) {
  //libreria a4988
}

int pan_move(int retardo_pan, int pasos_pan, bool direct_pan) {
  //libreria a4988
}



int tilt_move(int retardo_tilt, int pasos_tilt, bool direct_tilt) {
  //libreria a4988
}




void homeaxis_func() {
      while (digitalRead(32) == 0) {
        long_move(5,1,true);
      }
      while (digitalRead(33) == 0) {
        pan_move(5,1,true);
      }
      while (digitalRead(34) == 0) {
        tilt_move(5,1,true);
      }

    
  }














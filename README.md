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
  
  
  
  #include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int pantalla = 1;
int modo_configuracion = 1;

//Variables de lectura de los perifericos de entrada
int readgrados;
int readtiempo;
int gradostilt;
int tiempotilt;
int gradospan;
int tiempopan;
int distlong;
int tiempolong;

//Variables de target de los pasos
int pasos_tilt_set;
int pasos_long_set;
int pasos_pan_set;

//Variables que condicionan la velocidad del motor
int retardo_long_set;
int retardo_pan_set;
int retardo_tilt_set;
//funciones para calcular los pasos
int cantidad_pasos_tilt(int  grados_tilt);
int cantidad_pasos_pan(int grados_pan);
int cantidad_pasos_long(int dist_long);


void setup() {
  // put your setup code here, to run once:

  pinMode(6, INPUT);
  pinMode(7, INPUT);
  pinMode(32, INPUT); //Switch final de carrera long
  pinMode(33, INPUT); //Switch final de carrera pan
  pinMode(34, INPUT); //Switch final de carrera tilt


  lcd.begin(16, 2);
  lcd.setCursor(3, 0);
  lcd.print("Bienvenidos");
  delay(1000);
  lcd.clear();
  pantalla = 1;


}

void loop() {


  //boton avance
  if (digitalRead(7) == 1) {
    pantalla++;
  }
  //boton retroceso
  if (digitalRead(6) == 1) {
    if (pantalla > 1) {
      pantalla--;
    }

  }

  if (pantalla == 1) {
    void pantalla_uno();
  }
  if (pantalla == 2) {
    void pantalla_dos();
  }
  if (pantalla == 3) {
    void pantalla_tres();
  }

  if (pantalla == 4) {
    void pantalla_cuatro();

  }
  if (pantalla == 5) {
    void homeaxis_func();
    long_move(retardo_long_set, pasos_long_set, false);
    pan_move(retardo_pan_set, pasos_pan_set, false);
    tilt_move(retardo_tilt_set, pasos_tilt_set, false);
    pantalla=1;
  }
}
















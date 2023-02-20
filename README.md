int trig=2;
int echo=3;

void setup()
 {
   serial.begin(9600);
   pinMode(trig,OUTPUT);
   pinMOde(echo,INPUT);
 }
void loop()
 {
  digitalWrite(trig,HIGH);
  delayMicroseconds(10);
  digitalWrite(trig,LOW);
  int distance=pulseln(echo,HIGH)
  Serial.print(disance);
  Serial.println("CM")
  delay(100);
  }

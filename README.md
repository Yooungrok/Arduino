#include<SoftwareSerial.h>
int A_1A=6,A_1B=11,B_1A=3,B_1B=5;
int btRxpin=12,btTxpin=13;
int speed=255;
SoftwareSerial bluetoothSerial(btRxpin,btTxpin);
int line=7,rline=8;

void setup()
{
  bluetoothSerial.begin(9600);

  pinMode(A_1A,OUTPUT);
  pinMode(A_1B,OUTPUT);
  pinMode(B_1A,OUTPUT);
  pinMode(B_1B,OUTPUT);

  pinMode(line,INPUT);
  pinMode(rline,INPUT);
}

void loop()
{
  char cmd=bluetoothSerial.read();

  switch(cmd)
  {
    case'f':
    analogWrite(A_1A,0);
    analogWrite(A_1B,speed);
    analogWrite(B_1A,0);
    analogWrite(B_1B,speed);
    break;

    case'b':
    analogWrite(A_1A,speed);
    analogWrite(A_1B,0);
    analogWrite(B_1A,speed);
    analogWrite(B_1B,0);
    break;

    case'r':
    analogWrite(A_1A,0);
    analogWrite(A_1B,0);
    analogWrite(B_1A,speed);
    analogWrite(B_1B,0);
    break;

    case'l':
    analogWrite(A_1A,speed);
    analogWrite(A_1B,0);
    analogWrite(B_1A,0);
    analogWrite(B_1B,0);
    break;

    case's':
    analogWrite(A_1A,0);
    analogWrite(A_1B,0);
    analogWrite(B_1A,0);
    analogWrite(B_1B,0);
    break;
  }
  //line_trace()
}
void line_trace()
{
  if(!digitalRead(line)&&!digitalRead(rline))
  {
    analogWrite(A_1A,speed);
    analogWrite(A_1B,0);
    analogWrite(B_1A,speed);
    analogWrite(B_1B,0);
  }
  else if(!digitalRead(line)&&!digitalRead(rline))
  {
    analogWrite(A_1A,speed);
    analogWrite(A_1B,255);
    analogWrite(B_1A,speed);
    analogWrite(B_1B,0);
    delay(100);
  }
  else if(!digitalRead(line)&&!digitalRead(rline))
  {
    analogWrite(A_1A,speed);
    analogWrite(A_1B,0);
    analogWrite(B_1A,0);
    analogWrite(B_1B,255);
    delay(100);

  }
  else if(!digitalRead(line)&&!digitalRead(rline))
  {
    analogWrite(A_1A,0);
    analogWrite(A_1B,0);
    analogWrite(B_1A,0);
    analogWrite(B_1B,0);
    delay(100);
   }
}


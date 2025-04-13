# Codigo
Tarea Arquitectura
int A = 0; 
int B = 0; 
char  data[26];
int   number_of_bytes_received;

void setup() {

  pinMode(2, INPUT);   
  pinMode(3, INPUT);    
  pinMode(12, OUTPUT);  
  pinMode(13, OUTPUT); 

  Serial.begin(9600);
  Serial.println("Esperando instrucciones...");

}
void loop() {

  A = digitalRead(2);
  B = digitalRead(3);
 
  while(Serial.available())
  {
    number_of_bytes_received = Serial.readBytesUntil(13, data, 25); 
    data[number_of_bytes_received] = 0;
     bool result0 = strcmp(data, "AND");
    if (!result0) {Serial.println("Operación AND"); if (A && B) { digitalWrite(12, HIGH); }
    }
    bool result1 = strcmp(data, "OR"); 
    if (!result1) {Serial.println("Operación OR"); if (A || B) { digitalWrite(12, HIGH); }
    }
    bool result2 =strcmp(data, "XOR");    
    if (!result2) {Serial.println("Operación XOR"); if (A ^ B) { digitalWrite(12, HIGH); }
    }
    bool result3 = strcmp(data, "NAND");   
    if (!result3) {Serial.println("Operación NAND"); if (!(A && B)) { digitalWrite(12, HIGH); }
    }
    bool result4 = strcmp(data, "NOR");    
    if (!result4) {Serial.println("Operación NOR"); if (!(A || B)) { digitalWrite(12, HIGH); }
    }
    bool result5 = strcmp(data, "XNOR");   
    if (!result5) {Serial.println("Operación XNOR"); if (!(A ^ B)) { digitalWrite(12, HIGH); }
    }
    bool result6 = strcmp(data, "NOTA");   
    if (!result6) {Serial.println("Operación NOT A"); if (!A) { digitalWrite(12, HIGH); }
    }
   delay(1000);
    digitalWrite(12, LOW);
    digitalWrite(13, LOW);
  }

}

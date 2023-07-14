### 📄Documentación del recuperatorio del primer parcial para la materia Sistemas de procesamiento de datos - UTN Tecnicatura Superior en Programación.

### Nombre: Torres Matías Daniel

### **Sistema de Procesamiento de Datos (SPD)**

![Arduino](https://github.com/matiasdtorres/RECU-2-SPD/blob/fadcf87b728d5b2968905f6cd988bb7e0d3b8ed4/ArduinoTinkercad.jpg)

### Setteo de temperaturas funcional

![Setteo de temperaturas](https://github.com/matiasdtorres/RECU-1-SPD/blob/15aa85c6d0809d7b3a47be942728f049123f23d9/DIV%20K-1.png)
### 🦴Modelo esquematico del Display de temperaturas

![Setteo de temperaturas](https://github.com/matiasdtorres/RECU-1-SPD/blob/15aa85c6d0809d7b3a47be942728f049123f23d9/RPP%20DIV%20K-1.png)

## 📄Consigna Setteo de temperaturas:
Se quiere manejar el señalar el nivel de temperatura con 
el encendido y apagado de los leds.
Cuando la temperatura este entre -40 y 0 se encendera
el led blanco y en el display se mostrara el nivel 1,
cuando la temperatura este entre 1 y 42 se encendera solo el led azul
y se mostrara en el display el nivel 2,
cuando la temperatura este entre 43 y 84 se encendera solo el led amarillo
y se mostrara en el display el nivel 3,
cuando la temperatura este entre 85 y 124 se encendera solo el led naranaja
y se mostrara en el display el nivel 4 y
cuando la temperatura sea 125 se encendera solo el led rojo
y se mostrara en el display el nivel 5.
Nota: se valorara el uso de funciones propias.

### 🚀Codigo del proyecto
``` C++
#define LED1 13
#define LED2 12
#define LED3 11
#define LED4 10
#define LED5 9

#define A 8
#define B 7
#define C 6
#define D 5
#define E 4
#define F 3
#define G 2

#define sensor A0

void setup()
{
  for(int i = 2;i < 14;i++)
    {
      pinMode(i, OUTPUT);
    }
    pinMode(sensor, INPUT);
  Serial.begin(9600);
  
}

int num = 0;

void loop()
{
  int lecturaSensor = analogRead(sensor);
  int rangoSensor = map(lecturaSensor,20, 358, -40, 125);
  
  if (rangoSensor >= -40 && rangoSensor <= 0)
  {
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,LOW);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,LOW);
    Serial.println(rangoSensor);
    num = 1;
  }
  else if (rangoSensor >= 1 && rangoSensor <= 42)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,HIGH);
    digitalWrite(LED3,LOW);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,LOW);
    Serial.println(rangoSensor);
    num = 2;
  }
  else if (rangoSensor >= 43 && rangoSensor <= 84)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,LOW);
    Serial.println(rangoSensor);
    num = 3;
  }
  else if (rangoSensor >= 85 && rangoSensor <= 124)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,LOW);
    digitalWrite(LED4,HIGH);
    digitalWrite(LED5,LOW);
    Serial.println(rangoSensor);
    num = 4;
  }
  else if (rangoSensor <= 125)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,LOW);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,HIGH);
    Serial.println(rangoSensor);
    num = 5;
  }
  
  mostrarNumero(num);
  
  delay(25);
  
}

void mostrarNumero (int num)
{
  switch(num)
  {
    case 1:
    digitalWrite(A,LOW);
    digitalWrite(B,HIGH);
    digitalWrite(C,HIGH);
    digitalWrite(D,LOW);
    digitalWrite(E,LOW);
    digitalWrite(F,LOW);
    digitalWrite(G,LOW);
    break;
    case 2:
    digitalWrite(A,HIGH);
    digitalWrite(B,HIGH);
    digitalWrite(C,LOW);
    digitalWrite(D,HIGH);
    digitalWrite(E,HIGH);
    digitalWrite(F,LOW);
    digitalWrite(G,HIGH);
    break;
    case 3:
    digitalWrite(A,HIGH);
    digitalWrite(B,HIGH);
    digitalWrite(C,HIGH);
    digitalWrite(D,HIGH);
    digitalWrite(E,LOW);
    digitalWrite(F,LOW);
    digitalWrite(G,HIGH);
    break;
    case 4:
    digitalWrite(A,LOW);
    digitalWrite(B,HIGH);
    digitalWrite(C,HIGH);
    digitalWrite(D,LOW);
    digitalWrite(E,LOW);
    digitalWrite(F,HIGH);
    digitalWrite(G,HIGH);
    break;
    case 5:
    digitalWrite(A,HIGH);
    digitalWrite(B,LOW);
    digitalWrite(C,HIGH);
    digitalWrite(D,HIGH);
    digitalWrite(E,LOW);
    digitalWrite(F,HIGH);
    digitalWrite(G,HIGH);
    break;
  }
}
```
### 🤖Funcionando
![Setteo de temperaturas](https://github.com/matiasdtorres/RECU-2-SPD/blob/fadcf87b728d5b2968905f6cd988bb7e0d3b8ed4/2023-07-11-20-32-46.gif)

### 🧠Explicacion

``` C++
#define LED1 13
#define LED2 12
#define LED3 11
#define LED4 10
#define LED5 9

#define A 8
#define B 7
#define C 6
#define D 5
#define E 4
#define F 3
#define G 2

#define sensor A0

void setup()
{
  // Establecer los pines como salidas
  for (int i = 2; i < 14; i++)
  {
    pinMode(i, OUTPUT);
  }
  pinMode(sensor, INPUT); // Establecer el pin del sensor como entrada
  Serial.begin(9600); // Iniciar la comunicación serial a 9600 baudios
}

int num = 0;

void loop()
{
  int lecturaSensor = analogRead(sensor); // Leer el valor del sensor analógico
  int rangoSensor = map(lecturaSensor, 20, 358, -40, 125); // Mapear el valor del sensor a un rango específico

  // Determinar en qué rango se encuentra el valor mapeado del sensor y encender el LED correspondiente
  if (rangoSensor >= -40 && rangoSensor <= 0)
  {
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, LOW);
    Serial.println(rangoSensor);
    num = 1;
  }
  else if (rangoSensor >= 1 && rangoSensor <= 42)
  {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, HIGH);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, LOW);
    Serial.println(rangoSensor);
    num = 2;
  }
  else if (rangoSensor >= 43 && rangoSensor <= 84)
  {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, HIGH);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, LOW);
    Serial.println(rangoSensor);
    num = 3;
  }
  else if (rangoSensor >= 85 && rangoSensor <= 124)
  {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, HIGH);
    digitalWrite(LED5, LOW);
    Serial.println(rangoSensor);
    num = 4;
  }
  else if (rangoSensor <= 125)
  {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, HIGH);
    Serial.println(rangoSensor);
    num = 5;
  }

  mostrarNumero(num); // Llamar a la función para mostrar el número en el display de 7 segmentos

  delay(25); // Esperar 25 milisegundos antes de repetir el ciclo
}

void mostrarNumero(int num)
{
  switch (num)
  {
  case 1:
    digitalWrite(A, LOW);
    digitalWrite(B, HIGH);
    digitalWrite(C, HIGH);
    digitalWrite(D, LOW);
    digitalWrite(E, LOW);
    digitalWrite(F, LOW);
    digitalWrite(G, LOW);
    break;
  case 2:
    digitalWrite(A, HIGH);
    digitalWrite(B, HIGH);
    digitalWrite(C, LOW);
    digitalWrite(D, HIGH);
    digitalWrite(E, HIGH);
    digitalWrite(F, LOW);
    digitalWrite(G, HIGH);
    break;
  case 3:
    digitalWrite(A, HIGH);
    digitalWrite(B, HIGH);
    digitalWrite(C, HIGH);
    digitalWrite(D, HIGH);
    digitalWrite(E, LOW);
    digitalWrite(F, LOW);
    digitalWrite(G, HIGH);
    break;
  case 4:
    digitalWrite(A, LOW);
    digitalWrite(B, HIGH);
    digitalWrite(C, HIGH);
    digitalWrite(D, LOW);
    digitalWrite(E, LOW);
    digitalWrite(F, HIGH);
    digitalWrite(G, HIGH);
    break;
  case 5:
    digitalWrite(A, HIGH);
    digitalWrite(B, LOW);
    digitalWrite(C, HIGH);
    digitalWrite(D, HIGH);
    digitalWrite(E, LOW);
    digitalWrite(F, HIGH);
    digitalWrite(G, HIGH);
    break;
  }
}

```

``` C++
// FUNCIONES
void mostrarNumero(int num)
{
  switch (num)
  {
    case 1:
      // Encender los segmentos necesarios para mostrar el número 1
      digitalWrite(A, LOW);
      digitalWrite(B, HIGH);
      digitalWrite(C, HIGH);
      digitalWrite(D, LOW);
      digitalWrite(E, LOW);
      digitalWrite(F, LOW);
      digitalWrite(G, LOW);
      break;
    case 2:
      // Encender los segmentos necesarios para mostrar el número 2
      digitalWrite(A, HIGH);
      digitalWrite(B, HIGH);
      digitalWrite(C, LOW);
      digitalWrite(D, HIGH);
      digitalWrite(E, HIGH);
      digitalWrite(F, LOW);
      digitalWrite(G, HIGH);
      break;
    case 3:
      // Encender los segmentos necesarios para mostrar el número 3
      digitalWrite(A, HIGH);
      digitalWrite(B, HIGH);
      digitalWrite(C, HIGH);
      digitalWrite(D, HIGH);
      digitalWrite(E, LOW);
      digitalWrite(F, LOW);
      digitalWrite(G, HIGH);
      break;
    case 4:
      // Encender los segmentos necesarios para mostrar el número 4
      digitalWrite(A, LOW);
      digitalWrite(B, HIGH);
      digitalWrite(C, HIGH);
      digitalWrite(D, LOW);
      digitalWrite(E, LOW);
      digitalWrite(F, HIGH);
      digitalWrite(G, HIGH);
      break;
    case 5:
      // Encender los segmentos necesarios para mostrar el número 5
      digitalWrite(A, HIGH);
      digitalWrite(B, LOW);
      digitalWrite(C, HIGH);
      digitalWrite(D, HIGH);
      digitalWrite(E, LOW);
      digitalWrite(F, HIGH);
      digitalWrite(G, HIGH);
      break;
  }
}

// FIN FUNCIONES
```
La función **mostrarNumero()** se utiliza para aada caso dentro del switch corresponde a un número del 1 al 5. 
Los pines A, B, C, D, E, F y G representan los segmentos del display de 7 segmentos.


## <img src="tinkercad.png" alt="Tinkercad" height="32px"> Link al proyecto

- [Proyecto](https://www.tinkercad.com/things/3AvzWLukKph)

### 📄Parcial:

- [Enunciado](https://github.com/matiasdtorres/RECU-1-SPD/blob/768982a5105fca9087b38c70a7236362882e162d/Enunciado.pdf)

### 📄Fuentes

- [Youtube](https://www.youtube.com)
- [arduino](https://www.arduino.cc/)
- [Utn](http://www.sistemas-utnfra.com.ar/#/home)

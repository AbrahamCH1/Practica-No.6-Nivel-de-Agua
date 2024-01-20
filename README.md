# Practica-No.6-Nivel-de-Agua
Dentro de este repositorio se muestra la manera de programar una ESP32 con el sensor **ULTRASÓNICO** y diodos emisores de luz (LED) para representar el nivel de agua de un recipiente.
## Introducción
### Descripción
La **ESP32** se utiliza en un entorno de adquisición de datos, por lo cual en esta práctica utilizaremos un sensor **ULTRASÓNICO** para obtener el registro de distancia de un nivel de agua. Los LED nos brindaran apoyo visual para conocer si el recipiente se enceuntra lleno o vacío. Para esta practica se hace uso de un simulador llamado [WOKWI](https://wokwi.com/projects/new/esp32).
## Material necesario
Para realizar esta práctica necesitas lo siguiente

- [WOKWI](https://wokwi.com/projects/new/esp32)
- Tarjeta ESP32
- Sensor ULTRASONICO
- 4 LED´s
## Instrucciones
### Requisitos previos
Para poder hacer uso de este repositorio se requiere entrar a la plataforma de [WOKWI](https://wokwi.com/projects/new/esp32).
### Instrucciones de preparación del entorno
1. Abrir la terminal de programación y colocar el siguiente código:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=10 && safetyDistance<=100)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=100 && safetyDistance<=200) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=200 && safetyDistance<=300) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=300 && safetyDistance<=400) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}

```
2. Hacer la conexion del sensor **ULTRASONICO** y los **LED´S** con la **ESP32** como se muestra en la siguente imagen.
![](https://github.com/AbrahamCH1/Practica-No.6-Nivel-de-Agua/blob/main/Captura%20de%20pantalla%20(310).png?raw=true)

### Instrucciones de operación
1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia dando *doble click* al sensor **ULTRASONICO**.
5. Observar el comportamiento de los Led´s con respecto a las diferentes distancias. 
## Resultados
Cuando haya funcionado, se podrán observar los valores dentro de la pantalla LCD.
![](https://github.com/AbrahamCH1/Practica-No.6-Nivel-de-Agua/blob/main/Captura%20de%20pantalla%20(311).png?raw=true)
![](https://github.com/AbrahamCH1/Practica-No.6-Nivel-de-Agua/blob/main/Captura%20de%20pantalla%20(312).png?raw=true)
![](https://github.com/AbrahamCH1/Practica-No.6-Nivel-de-Agua/blob/main/Captura%20de%20pantalla%20(313).png?raw=true)
![](https://github.com/AbrahamCH1/Practica-No.6-Nivel-de-Agua/blob/main/Captura%20de%20pantalla%20(314).png?raw=true)

# Créditos
Desarrollado por Ing. Abraham Contreras Herrera
[GITHUB](https://github.com/AbrahamCH1)

# arduino

- Arduino UNO ATMEL MEGA328P
- LED MAX7219EWG
- WIFI ESP8266EX

## instalacion en arch linux

```
sudo pacman -S arduino
```


Si recibimos el mensaje `permission denied` cuando subimos el programita blink:

```cpp
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```

Tenemos que cambiar los permisos para acceder al puerto serial USB:

```bash
sudo chmod a+rw /dev/ttyUSB0
```
The "a" signifies that we're in a-mode, which modifies all users, and the "+rw" means we "+" (add) "rw" (read and write permissions).

## LED MAX7219EWG

Codigo minimo, usando las librerias `md_parola` y `md_max72xx`:

```cpp
#include <MD_Parola.h>
#include <MD_MAX72xx.h>
#include <SPI.h>

// Define the number of devices we have in the chain and the hardware interface
// NOTE: These pin numbers will probably not work with your hardware and may
// need to be adapted
#define HARDWARE_TYPE MD_MAX72XX::FC16_HW
#define MAX_DEVICES 4

#define CLK_PIN   13
#define DATA_PIN  11
#define CS_PIN    10

// Hardware SPI connection
MD_Parola P = MD_Parola(HARDWARE_TYPE, CS_PIN, MAX_DEVICES);
// Arbitrary output pins
// MD_Parola P = MD_Parola(HARDWARE_TYPE, DATA_PIN, CLK_PIN, CS_PIN, MAX_DEVICES);

void setup(void)
{
  P.begin();
  P.print("Hola mundo!");
}

void loop(void)
{
```

Ademas de conectar los pines clk, din, cs necesitamos conectar 5v y GND.




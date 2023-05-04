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




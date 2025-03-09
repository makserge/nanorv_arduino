# LicheeRV nano Arduino Howto

Used Mllk-V Arduino howto as reference (https://milkv.io/docs/duo/getting-started/arduino)

1. Install arduino-milkv-duo256m-sd-v1.1.4 using [BalenaEtcher](https://etcher.balena.io/)

https://github.com/milkv-duo/duo-buildroot-sdk/releases/download/v1.1.4/arduino-milkv-duo256m-sd-v1.1.4.img.zip

2. Boot image and disable blink.sh and reboot

   mv /mnt/system/blink.sh /mnt/system/blink.sh_backup && sync
   reboot

3. Check if additional serial port exists (/dev/cu.usbmodemXXXX on Mac)
4. Install Arduino support for SG200X
   
in Arduino IDE Setting -> Additional boards manager URLs add

https://github.com/kubuds/sophgo-arduino/releases/download/v0.2.6/package_sg200x_index.json

After configuring, select Board in the Tools menu, open the Boards Manager, search for SG200X, and click Install.

5. Flash blink script
   Put code to Arduino IDE

void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(19, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(19, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(19, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}

Burn it to board using port /dev/cu.usbmodemXXXX

Make sure to pyserial module for Python was installed 

pip install pyserial

If pip not work, add aliases for Python and pip first to ~/.bash_profile

alias python=/usr/local/bin/python3
alias pip=/usr/local/bin/pip3

then apply changes

source ~/.bash_profile

6. Check if blue LED start blinking

# ha-alarm-clock v2
A fully functional alarm clock for home assistant version 2.
Yes, the enclosure is ugly, but it's still work in progress)
Credit where credit's due: This was possible due to the immense help of BC547, if you know him ;)

This is the PCB of an alarm clock I designed because there is nothing like it on the entire net. At least not as far as I know/found.

The inspiration is a cheap alarm clock that I soldered myself, from Aliexpress that had some nice features... but lacks others. So here is a list of what the goal is:
![picture of the clock](https://github.com/harrydg1/ha-alarm-clock/blob/main/Pictures/signal-2025-02-15-10-02-27-468.jpg)
- an alarm clock that you never have to set the time (like daylight saving time, ...), based on the ESP32-S3 chip
- simple good old fashioned red (or any other color you might like) 7 segment display
  - 1 larger one for the time: https://nl.aliexpress.com/item/1005002059351703.html
  - 1 smaller one for the temperature: https://nl.aliexpress.com/item/1005006099563523.html
    for some strange reason the power and gnd on these modules are different on both, so also in my schematic this is the case, it's NOT an error
- with the LDR, this display can be dimmed to not blind you at night, but readable during the day
- 3 buttons, currently in the code: 1 for the LED light, 1 for muting/unmuting the DAC (puts it in very low power mode) and 1 freely configurable in home assistant. Probably I will use it for my curtains.
- a buzzer because it reminds me of the good old nokia phones and you can play the Super Mario Bros tune (if needed you can add a resistor/diode on R7, probably not needed)
- USB-C connector for plenty of power, including ESD protection, impedance maching and all else
- a powerful and high quality voltage regulator (1.2A!)


From bottom, left to right on the PCB
![PCB design](https://github.com/harrydg1/ha-alarm-clock/blob/version-2/Pictures/pcb%20design.png)
- a built-in high power LED "night light" that is dimmable, with room for a big (2-3W) resistor to limit current if needed: [https://nl.aliexpress.com/item/1005006401939984.html](https://nl.aliexpress.com/item/1005006334229998.html)
- a 5V connector to connect a 5V wireless charging pad: https://nl.aliexpress.com/item/1005005716095383.html
- an extra connector, if you have any ideas what is missing, so it's up to you if you want to add something. PIR maybe? There is room (R9) for a 4.7k pull-up resistor
- a DAC + amplifier to play music: https://nl.aliexpress.com/item/1005006711010527.html
  and a speaker to go with the amp, but they are too weak/bad quality: https://nl.aliexpress.com/item/1005007390381560.html
- a connector for I2C where I connected my Bosch BME680, there is also room for a pullup resistor (R13-R14): https://nl.aliexpress.com/item/1005004803087064.html
- (top right): a UART connector, not needed as you can upload via the USB-C connector

The files:
- fusion 360 design file (still needs a lot of improvement, i know!)
- the EasyEDA design files, pictures of the schema and so on are also there
- the yaml code for esphome

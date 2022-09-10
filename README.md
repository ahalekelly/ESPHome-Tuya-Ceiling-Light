# ESPHome Tuya Ceiling Light
I bought a [Tuya 60W Ceiling Light](https://www.amazon.com/gp/product/B09HZG1Q9Y) because it was cheap and I ignored the reviews where many people had it failed on them. Sure enough, after a few months the after a few months the light would no longer connect to WiFi and was constantly flashing off and on. But we can fix this with open source software!

The brains of this light are a proprietary CB3S Tuya WiFi module, but it's pin compatible with the ESP-12 ESP8266 modules, so let's take control of our electronics.

## Soldering
Use a hot air rework station to desolder the Tuya module, there's no center under the module so you can solder the new ESP-12S module in with a soldering iron.

Solder jumper wires to the ESP pads and connect it to a USB to Serial adapter like a CH340 or FTDI. You need to connect the 3.3V, ground, GPIO0 to ground, RX to TX, and TX to RX. Alternatively, you could use an ESP-12 programming jig like [this](https://www.amazon.com/Adapter-Support-ESP8266-Compatible-Development/dp/B08GBFV35G) to flash the module before soldering it.

## Flashing

Enter your WiFi details in `secrets.yaml` then follow the [ESPHome instructions](https://esphome.io/guides/getting_started_hassio.html). Here's [another tutorial](https://www.pieterbrinkman.com/2020/12/14/flash-esp-chip-with-esphome-node-firmware/), or if you're running Home Assistant in a docker container like I am, you can install the ESPHome [command line](https://esphome.io/guides/installing_esphome.html) and then run `esphome run ESPHome-Tuya-Ceiling-Light.yaml`

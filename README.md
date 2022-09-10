# ESPHome Tuya Ceiling Light
I bought a [Tuya Ceiling Light](https://www.amazon.com/gp/product/B09HZG1Q9Y) because it was cheap and ignored the reviews where many people were having problems. Sure enough, after a few months the after a few months the light started frequently disconnecting from WiFi and flashing off and on. But we can fix this using open source software!

The brains of this light are a proprietary CB3S Tuya WiFi module, but it's pin compatible with the ESP-12 ESP8266 modules, so let's take control of our electronics.

## Soldering
Use a hot air rework station to desolder the Tuya module, there's no center under the module so you can solder the new ESP-12S module in with a soldering iron.

Solder jumper wires to the ESP pads and connect it to a USB to Serial adapter like a CH340 or FTDI. You need to connect the 3.3V, ground, GPIO0 to ground, RX to TX, and TX to RX. Alternatively, you could use an ESP-12 programming jig like [this](https://www.amazon.com/Adapter-Support-ESP8266-Compatible-Development/dp/B08GBFV35G) to flash the module before soldering it.

## Flashing

Plug it in to your computer, make sure your USB to serial adapter drivers are installed, and install esphome

Enter your WiFi details in `secrets.yaml`

In your terminal, navigate to to this directory and run `esphome run esphome-tuya-ceiling-light.yaml` to compile the firmware and upload to the ESP

Connect your light back to mains power, open Home Assistant and you should see a notification asking you if you want to add your new ceiling light!

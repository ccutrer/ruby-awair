# Awair Gem

This is a simple gem to pull data from a local Awair Element device, and push it to MQTT.

## Usage

An MQTT bridge is provided to allow easy integration into other systems. You
will need a separate MQTT server running ([Mosquitto](https://mosquitto.org) is
a relatively easy and robust one). The MQTT topics follow the [Homie
convention](https://homieiot.github.io), making them self-describing. If you're
using a systemd Linux distribution, an example unit file is provided in
`contrib/awair_mqtt_bridge.service`. So a full example would be (once you have
Ruby installed):

```sh
sudo gem install awair
sudo curl https://github.com/ccutrer/ruby-awair/raw/main/contrib/awair_mqtt_bridge.service -L -o /etc/systemd/system/awair_mqtt_bridge.service
<modify the file to pass the correct IP to your sensor, and URI to your MQTT server>
<If you use MQTT authentication you can use the following format to provide login information mqtt://username:password@mqtt.domain.tld >
<Make sure to change the "User" parameters to fit your environnement>
sudo systemctl enable awair_mqtt_bridge
sudo systemctl start awair_mqtt_bridge
```

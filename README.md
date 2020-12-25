![Docker compose file with the resulting (short-term) dashboard next to it](https://media.discordapp.net/attachments/754952031164432405/755446728588787762/2020-09-15_17-12-07.png)
![Long-term energy consumption dashboard](https://media.discordapp.net/attachments/754952031164432405/755446732690686193/chrome_2020-09-15_17-14-02.png)

Metergrafiekjes docker-compose
==============================
The goal of this docker-compose is to deliver a configuration  to view data coming from the [Metertrekker firmware](https://github.com/Pwutseltronics/Metertrekker2MQTT).

## Installation
1. Download this repository (or `git clone git@github.com:Pwutseltronics/Metergrafiekjes-docker-compose.git`)
2. Make sure you have `docker-compose` available
3. Open the (extracted) folder of the repository
4. Optional: edit `docker-compose.yml` to suit your own preferences
5. `docker-compose up -d`

This will work on a Raspberry Pi and most other Linux computers.
If you want to run this on a different environment (like a NAS or Docker Desktop), refer to guides for the respective host software.
It should work fine, but the way of setting it up will be different.

### But I already have an MQTT broker!
To use your own MQTT broker instead of the `eclipse-mosquitto` container:
1. In `docker-compose.yml`, comment or delete the entire `mosquitto` section
2. In `telegraf.conf`, change `tcp://mosquitto:1883` to the address of your MQTT broker.
To access a service on the host device, the IP address should be `172.17.0.1`. More info [here](https://stackoverflow.com/questions/31324981/how-to-access-host-port-from-docker-container).

## Usage
If you have correctly executed the steps under *Installation*, you can now access Grafana at port `3000` of the device you have installed it on, e.g. `http://[IP address]:3000`.
Log in with the default username and password (both `admin`).
You will be asked to enter a new password; this is not required but strongly recommended if you want to make the dashboard reachable externally (e.g. via port-forwarding on your router).

Once you have logged in, you will see the Grafana home page.
Click **Home** in the top of the screen and select **Energie** or **Energie lange-termijn**.
Voilà, you now have fancy energy consumption graphs!

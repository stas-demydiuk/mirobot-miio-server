# mirobot-miio-server

Docker container with server for [domoticz-mirobot-plugin](https://github.com/mrin/domoticz-mirobot-plugin)

## How to use
**Pull image**

```
docker pull demydiuk/mirobot-miio-server
```
**Run container**
```
docker run -d -p 22222:22222 -e "ROBOT_IP=<your robot ip>" -e "ROBOT_TOKEN=<your robot token>" --name=<container name> demydiuk/mirobot-miio-server
```

22222 can be another port (you change `-p 22222:22222` to `-p 3000:22222` to have 3000 out of the container for example).

### Docker compose file example

```
version: '2'
services:
  mirobot-miio-server:
    image: demydiuk/mirobot-miio-server
    container_name: mirobot-miio-server
    environment:
      - ROBOT_IP=<your robot ip>
      - ROBOT_TOKEN=<your robot token>
    ports:
      - "22222:22222"
    restart: always
```

## Setup original domoticz-mirobot-plugin

Just follow the original [installation guide](https://github.com/mrin/domoticz-mirobot-plugin) and skip all MIIO Server related steps.
Which basically just require:
```
cd domoticz/plugins
git clone https://github.com/mrin/domoticz-mirobot-plugin.git xiaomi-mirobot
cd xiaomi-mirobot
pip3 install msgpack-python
```
and proceed with Domoticz Hardware setup

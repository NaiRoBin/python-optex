# python-egardia
Python library to interface with Egardia / Woonveilig alarm. Tested with **WV-1716**, **GATE-01**, **GATE-02** and **GATE-03** version of Egardia / Woonveilig. Other versions might work, but unsure. Originally written for integration with [Home Assistant](home-assistant.io) it can also by used to integrate with these alarms in other solutions.

Egardiadevice is the representation of the alarm control panel and the Egardiaserver can be used to handle alarm status changes including triggering. Test files are included for both device and server. 

## EgardiaDevice ##
This script talks to the Egardia alarm control panel and can read and set it's status. Note that if the alarm is triggered the state is not published through the interface available to this script. To be able to respond to alarm triggers, set up the Egardia Server (see below). For testing purposes have a look at the `test_egardiadevice.py` script. It's usage:
`test_egardiadevice.py [-h] host port username password version`, so for example:
`python test_egardiadevice.py 192.168.1.X 80 user pass GATE-02`.

## EgardiaServer ##
This script captures codes generated by the Egardia alarm control panel after it was set up to forward the codes to the machine running the script ([see the Home Assistant docs](https://home-assistant.io/components/egardia#advanced-configuration)).

```bash
usage: egardiaserver.py [-h] [-P PORT]

Run the EgardiaServer

optional arguments:
  -h, --help            show this help message and exit
  -P PORT, --port PORT  the port number to run the server on (defaults to 52010)
```

The test script for the EgardiaServer is `test_egardiaserver.py` which tests if the `egardiaserver` you are running is accessible.
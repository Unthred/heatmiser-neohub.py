# Heatmiser NeoHub, NeoStat, NeoPlug Library

This library controls the wireless mesh NeoStat thermostats, via the NeoHub.

It talks the JSON-over-TCP protocol, on the LAN, to the Neo Hub - so no internet
access is required.

I do not have any wifi neostats, just the "mesh networked" (aka zigbee) ones.

This library uses `asyncio`, and strives to be a well-behaved async 
home-assistant component.

## Python 3.5 required!

Although as of Nov 2017, home-assistant only requires python 3.4 or newer,
this component needs python 3.5+ (async/await).

Home-assistant is planning to require python 3.5 sometime early 2018 anyway,
and many distributions are already using it anyway.


### Example CLI Usage

    $ ./neocli.py list

    <NeoStat id=1  temp=20.8 name='Bedroom'>
    <NeoStat id=2 temp=21.7 name='Office'>
    <NeoStat id=3  temp=23.4 name='Kitchen'>

    <NeoPlug id=4  status=OFF name='Desktop fan plug'>


    $ ./neocli.py rename_zone "Bedroom" "Master Bedroom"
    $ ./neocli.py frost_on "Master Bedroom"
    $ ./neocli.py switch_on "Desktop fan plug"

Bit of a half-assed CLI, because I mainly built this libary for the...

## Home Assistant Integration

Although functional, this is not production ready. For now, installation via
custom\_components dir in your `~/.homeassistant` config dir:

    custom_components/
      climate/
        neohub --> link to this repo neohub dir
        heatmiser_neohub.py --> link to this repo heatmiser_neohub.py

and in `configuration.yaml`:

    climate:
      platform: heatmiser_neohub
      host: 10.0.0.197
      port: 4242
      debug: True


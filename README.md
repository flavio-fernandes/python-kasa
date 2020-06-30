# python-kasa

[![PyPI version](https://badge.fury.io/py/python-kasa.svg)](https://badge.fury.io/py/python-kasa)
[![Build Status](https://dev.azure.com/python-kasa/python-kasa/_apis/build/status/python-kasa.python-kasa?branchName=master)](https://dev.azure.com/python-kasa/python-kasa/_build/latest?definitionId=2&branchName=master)
[![Coverage Status](https://coveralls.io/repos/github/python-kasa/python-kasa/badge.svg?branch=master)](https://coveralls.io/github/python-kasa/python-kasa?branch=master)

python-kasa is a Python library to control TPLink smart home devices (plugs, wall switches, power strips, and bulbs) using asyncio.
This project is a maintainer-made fork of [pyHS100](https://github.com/GadgetReactor/pyHS100) project.


**Supported devices**

* Plugs
  * HS100
  * HS103
  * HS105
  * HS107
  * HS110
* Power Strips
  * HS300
  * KP303
* Wall switches
  * HS200
  * HS210
  * HS220
* Bulbs
  * LB100
  * LB110
  * LB120
  * LB130
  * LB230
  * KL60
  * KL110
  * KL120
  * KL130

**Contributions (be it adding missing features, fixing bugs or improving documentation) are more than welcome, feel free to submit pull requests! See below for instructions for setting up a development environment.**



## Discovering devices

The devices can be discovered either by using `kasa discover` or by calling `kasa` without any parameters.

```
$ kasa
No --bulb nor --plug given, discovering..
Discovering devices for 3 seconds
== My Smart Plug - HS110(EU) ==
Device state: ON
IP address: 192.168.x.x
LED state: False
On since: 2017-03-26 18:29:17.242219
== Generic information ==
Time:         1970-06-22 02:39:41
Hardware:     1.0
Software:     1.0.8 Build 151101 Rel.24452
MAC (rssi):   50:C7:BF:XX:XX:XX (-77)
Location:     {'latitude': XXXX, 'longitude': XXXX}
== Emeter ==
Current state: {'total': 133.082, 'power': 100.418681, 'current': 0.510967, 'voltage': 225.600477}
```

## Basic controls

All devices support a variety of common commands, including:
 * `state` which returns state information
 * `on` and `off` for turning the device on or off
 * `emeter` (where applicable) to return energy consumption information
 * `sysinfo` to return raw system information

## Energy meter

Passing no options to `emeter` command will return the current consumption.
Possible options include `--year` and `--month` for retrieving historical state,
and reseting the counters is done with `--erase`.

```
$ kasa emeter
== Emeter ==
Current state: {'total': 133.105, 'power': 108.223577, 'current': 0.54463, 'voltage': 225.296283}
```

## Bulb-specific commands

At the moment setting brightness, color temperature and color (in HSV) are supported depending on the device.
The commands are straightforward, so feel free to check `--help` for instructions how to use them.

# Library usage

You can find several code examples in [the API documentation](broken link).

## Contributing

Contributions are very welcome! To simplify the process, we are leveraging automated checks and tests for contributions.

### Resources

* [softScheck's github contains lot of information and wireshark dissector](https://github.com/softScheck/tplink-smartplug#wireshark-dissector)
* [https://github.com/plasticrake/tplink-smarthome-simulator](tplink-smarthome-simulator)

### Setting up development environment

```bash
poetry install
pre-commit install
```

### Code-style checks

We use several tools to automatically check all contributions, which are run automatically when you commit your code.

If you want to manually execute the checks, you can run `tox -e lint` to do the linting checks or `tox` to also execute the tests.

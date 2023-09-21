# Robot driver

![The main image](./documentation/images/general.PNG)

*Documentation for version: Mk3.0.0*  
*Schmatic version: Mk3.0.0*  
*Last updated: 21/09/2023*

## Overview

- [Summary](#summary)
- [Power supply](#power-supply-j1-plug)
- [Controller unit](#controller-unit)
- [Devices section](#devices-section)
- [Tool supply unit](#tool-supply-unit)
- [KiCad use](#kicad-use)

## Summary

A basic robot driver for controlling up to four stepper motors, a large number of devices like endstop switches or servo motors.

NOTE: This diagram does not include voltage/current limits, as they depend on which components are actually being used.

The GPIO pin requirements have been designed to fit a raspberry pi, so it is recommended to use a raspberry pi 3 or newer for this driver.

## Power supply (J1 plug)

![Power supply](./documentation/images/power_supply.PNG)

The driver needs two different supply sources: A control voltage with about 5V and a power voltage, usually between 12-48V. Both grounds are unified to a single one and the microcontroller, that sends the logical signals for the drivers, has to be connected to the ground and control voltage.

## Controller unit

![Control unit](./documentation/images/controller_unit.PNG)

When it comes to precise movements, the controller unit is the main part in play. Each motor is connected with a plug (**J3 - J10**), so it can be easily changed or replaced.

Logic control happens over the [J2 plug](#j2-plug).

### J2 plug

The [J2 plug](#j2-plug) consists of 10 pins, where 9 of them are GPIO ones (one GND). All motors can be disabled using the enable pin, as they have been unified to a single one.

The remaining eight pins are four PWM-pins (often referenced as "step"-pins too) and four DIR-pins, both for each controller. The maximum frequency of the PWM-signal depends on the controllers used.

## Devices section

![Devices section](./documentation/images/devices_section.PNG)

The devices section is equipped with a lot of 3pin connectors which can be used to power servo motors or measurement units.

## Tool supply unit

![Tool supply](./documentation/images/tool_supply.PNG)

When it comes to completing more complex tasks, then advanced tools are required, which can take a lot of resources to maintain. Therefore, the tool supply has to be as flexible as possible to cover most of the different applications.

The tool supply has one input plug (**J12**) and three output plugs, two of them being servo output plugs (**J14**, **J15**) and one general purpose one (**J16**).

Using the PWM pins on the input plug (1 and 2 on **J12**), up to two servos can be controlled, as it is often required. Furthermore, the general purpose plug is equipped with both control and power voltage and, as it is required, a GND.

## KiCad use

![KiCad Symbol](./documentation/images/symbol.PNG)

To include the driver into a KiCad circuit diagram, simply import the symbol found in the "export" folder. Once imported, it can be found in the "Driver_Motor" library under the name "SYRD_MK3".

# BoxTurtle V1.0
BoxTurtle Automated Filament Changer (requires AFC-Klipper-Add-On (Beta))

![BT_Render](https://github.com/user-attachments/assets/c06e961f-8d1d-41ae-9c80-036669ba2657)
[![Join me on Discord](https://discord.com/api/guilds/1229586267671629945/widget.png?style=banner2)](https://discord.gg/eT8zc3bvPR)

BoxTurtle is exactly what it appears to be — an open source AMS style filament changer for [Klipper](https://klipper3d.org) machines. 
BoxTurtle requires the AFC-Klipper Add-On (found [here](https://github.com/ArmoredTurtle/AFC-Klipper-Add-On)).
The goal of BoxTurtle is to deliver a user experience as close to an AMS as possible in vanilla Klipper. i.e. an "AMS" for any klipperized printer regardless of form factor but [VORON Design](https://vorondesign.com) printers in particular.

If you appreciate the work we are doing, you can support us [here](https://www.armoredturtle.com/pages/donate).

# How it works

BoxTurtle is an automated, lane-based filament changing system, also known by some as a "Type B MMU." Each lane is equipped with its own dedicated motor that moves filament to and from the tool head independently, eliminating the need for a selector cart or servos. Synchronization between the lane motor and the tool head occurs when the filament triggers a sensor (such as [FilaTector](https://github.com/ArmoredTurtle/Filatector)) that is located in or near the tool head.

To accommodate any differences in rotation distance between the extruder in the tool head and the lane motors, BoxTurtle uses a toolhead buffer, such as the [Belay by Annex Engineering](https://github.com/Annex-Engineering/Belay) or the [TurtleNeck](https://github.com/ArmoredTurtle/TurtleNeck) by ArmoredTurtle. This system is "bufferless," meaning no filament boxes (no spaghetti boxes) are required, similar to the AMS. Each lane features an independent respooler equipped with a brushed motor, which helps rewind the spool and assists the lane motor in feeding the filament smoothly. This prevents issues like spool tangling or "bucking."

For precise PWM control of the brushed motors, BoxTurtle relies on a custom MCU, AFC-lite, developed by [Isik's Tech @xbst](https://github.com/xbst/AFC-Lite/)  While the system currently supports BTT MMB CAN, this is a temporary solution to facilitate broader testing and will not be a permanent feature.

# Manual (WIP)

[Will update this as progress is made](https://armoredturtle.xyz)

# Wiring

![BoxTurtle_AFC-Lite_Pinout](https://github.com/user-attachments/assets/134796f6-8458-4a61-9967-1292963d7b4b)

# Slicer configuration

[Orca Slicer](https://github.com/SoftFever/OrcaSlicer) is the preferred slicer for BoxTurtle use.
## Printer Settings
![Orca_Pinter_Settings](https://github.com/user-attachments/assets/1aa56051-dbbf-49a4-b818-368e00406b17)
## Material Settings
![Orca_Material_Settings](https://github.com/user-attachments/assets/a1569e5a-24c5-48f9-98fb-26465bf7c75c)
## Ramming Settings
![Orca_Matterial_Settings](https://github.com/user-attachments/assets/2744fb86-afae-4645-9215-3f8507558509)

## Printer Machine G-Code
```
M104 S0 ; Stops OS from sending temp waits separately
M140 S0
PRINT_START EXTRUDER=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer_single] Chamber=[chamber_temperature] PRINT_MIN={first_layer_print_min[0]},{first_layer_print_min[1]} PRINT_MAX={first_layer_print_max[0]},{first_layer_print_max[1]} TOOL={initial_tool}
```
## Change Filament G-Code
```
T[next_extruder]
```

## BoxTurtle sourcing/vendors
While BoxTurtle can be mostly self-sourced, some vendors offer partial or full BoxTurtle kits. These vendors also have dedicated channels on the Armored Turtle Discord.

US:
- [DLLPDF](https://dllpdf.com) sells a [BoxTurtle frame kit](http://dllpdf.com/box-turtle-frame)
- [Isik's Tech](https://store.isiks.tech/) has BOM parts, including full kits [here](https://store.isiks.tech/collections/box-turtle-parts). Isik's Tech also ships internationally.
- [Fabreeko](https://www.fabreeko.com/products/box-turtle?_pos=4&_psq=box&_ss=e&_v=1.0)
- [KB3D](https://kb-3d.com/store/boxturtle/2132-pre-order-ldo-box-turtle-automated-filament-changer-kit-v10.html)
- [West3D](https://west3d.com/products/box-turtle-automated-filament-changer-multi-material-unit-by-armored-turtle)
  
EU:
- [Alchemy3D.de](https://alchemy3d.de) has a [BOM in a box kit](https://alchemy3d.de/products/boxturtle)
- [Lab4450.com](https://lab4450.com) resells the [AFC-Lite MCU](https://lab4450.com/product/afc-lite-board/)
- [3DO](https://3do.dk/3d-printer/2942-ldo-boxturtle-afc-kit-til-klipper-printere-forudbestilling.html)

UK:
- [OneTwo3D.co.uk](https://www.onetwo3d.co.uk)
- [Desktop Machine Shop](https://www.desktopmachineshop.com/shop/ldo-boxturtle-afc-kit-v1-0-163?category=4#attribute_values=)
  
AU:
- [DREMC](https://store.dremc.com.au/products/ldo-box-turtle-hardware-kit)
  
## Merch
- BoxTurtle T-Shirt ($3 from each sale goes to support ArmoredTurtle) via [Cotton Bureau](https://cottonbureau.com/p/QKF5XC/shirt/colored-box-turtle#/26921844/tee-men-premium-lightweight-vintage-black-tri-blend-s)- also has sweatshirt/hoodie variants
- BoxTurtle Sticker via [Dr. Mursey](https://drmursey.myshopify.com/products/box-turtle)

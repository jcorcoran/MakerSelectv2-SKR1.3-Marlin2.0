# MakerSelectv2-SKR1.3-Marlin2.0

## Hardware configuration
This project is the Marlin firmware configuration for a Monoprice Maker Select v2.1 (https://www.monoprice.com/product?p_id=13860)
3D printer with after market customizations.

The stock configuration of this printer had voltage on male header pins for the extruder fan. While performing maintenance,
with the fan unplugged, 12VDC  from the fan header pins contacted the chassis (grounded). This in turn blew out stepper
drivers on the Melzi board. The stepper drivers are soldered directly to the main PCB, so instead of replacing the whole PCB
($$$) or getting the hot air rework station warmed up, I decided to do a complete conversion of the control electronics to a
RAMPS 1.4 board. Subsequently this was swapped for an SKR 1.3 to get into 32bit Marlin 2.0 land, and make use of TMC quieter
stepper drivers.

### Stepper Motors (Stock)
* X,Y,E - C17HD6039-06N  - 1.2A Rating
* Z     - C17HD40102-01N - 1.3A Rating

### Control / Electronics
   * [BTT SKR 1.3](https://github.com/bigtreetech/BIGTREETECH-SKR-V1.3/tree/master/BTT%20SKR%20V1.3) motherboard 
   * ymp200n080 MOSFET board driving the heated bed
   * [TMC2130](https://www.trinamic.com/products/integrated-circuits/details/tmc2130/) on X, Y (1/256 microsteps)
   * [DRV8825](https://www.pololu.com/product/2133) on E & Z (1/32 steps)
     There are two Z steppers. They are each wired to their own stepper driver channel (Z and E1 respectively). This allows for
     their current load to be spread across two drivers, and makes it less likely for an individual motor to skip a step and have
     the two get out of sync (they aren't mechanically coupled)  
   * Stock LCD

### Extruder
   * Micro Swiss all metal hotend for Wanhao i3
   * [40T Extruder drive feeder gear](https://www.amazon.com/gp/product/B00ZZRI0DC)

## Marlin 3D Printer Firmware
https://github.com/MarlinFirmware/Marlin

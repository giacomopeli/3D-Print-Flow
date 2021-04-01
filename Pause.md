# Simple Pause Guide

## M0 and M1 - Simple Pause
M0 and M1 do the same type of pause. During the print, when the machine arrives to read the M0 or M1 line of the gcode simply stop the extruder block at the last position.
That's bad because in most cases you're having the hot nozzle stopped on the prints, this cause blobs or bad artifacts on the print. To avoid this you needs to move the extruder block off the printed parts.
The printer wait for a simple click input.

## M600 - Change Filament Pause
M600 does a simple change filament: raise the extruder block, unload filament, wait for filament loaded, extruder does a purge and then it restarts the print process.
This will be useful if you need to see how a print came out with different filament.
You need to set it before in your Marlin firmware, then compile it. In most case, if you don't set it properly after some seconds it starts the cooling process wasting time to heat up.

## M25 - Pause SD Print
M25 does a pause as you would do it during the print process. Using M25, unlike M0, M1 and M600, allows you to access the whole menu of the printing process, even the "Change filament" (M600 command) too.
M25 could be the best option if you want to try different parameters as temperature, fan speed, printing speed, accelertion and so on.
In Marlin firmware you can set PARK_HEAD_ON_PAUSE which move the extruder block in the set position before pausing the print. This avoid the blob or artifacts.
That's the preferred option as it is the most versitile option (as it give you access on what the M0, M1, M600 commands do).

## Some useful example
> M0
> M1
> 


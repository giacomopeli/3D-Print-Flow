# Simple Pause Guide

## M0 and M1 - Simple Pause
M0 and M1 do the same type of pause. During the print, when the machine arrives to read the M0 or M1 line of the gcode simply stop the extruder block at the last position.
That's bad because in most cases you're having the hot nozzle stopped on the prints, this cause blobs or bad artifacts on the print. To avoid this you needs to move the extruder block off the printed parts.
The printer wait for a simple click input.

## M600 - Change Filament Pause
M600 does a simple change filament: raise the extruder block, unload filament, wait for filament loaded, extruder does a purge and then it restarts the print process.
This will be useful if you need to see how a print came out with different filament.
You need to set it before in your Marlin firmware, then compile it. In most case, if you don't set it properly after some seconds it starts the cooling process wasting time to heat up. You need to enable it in firmware defining and setting NOZZLE_PARK_FEATURE and ADVANCED_PAUSE_FEATURE.

## M25 - Pause SD Print
M25 does a pause as you would do it during the print process. Using M25, unlike M0, M1 and M600, allows you to access the whole menu of the printing process, even the "Change filament" (M600 command) too.
M25 could be the best option if you want to try different parameters as temperature, fan speed, printing speed, accelertion and so on.
In Marlin firmware you can set PARK_HEAD_ON_PAUSE which move the extruder block in the set position before pausing the print. This avoid the blob or artifacts.
That's the preferred option as it is the most versitile option (as it give you access on what the M0, M1, M600 commands do).

## M125 - Park Head 
M125 is pretty same the M25 command. You can use it before M600 if you have PARK_HEAD_ON_PAUSE enabled and well set. Try it if you have problem with M25. Probably if you print from USB device or USB port M125 is more convenient.

## Some useful example
You can copy and paste in Batch Printing, but better if you look on what you're doing.

### M0 and M1 usage
```
G91                  ; relative coordinates 
G1 Z20               ; move nozzle up 20 mm
G90                  ; absolute coordinates 
G1 X0 Y180 F1000     ; move nozzle to these coordinates 
M400                 ; wait movement finishes 
M300 S300 P1000      ; acoustic signal, it play a simple beep
M0                   ; pause 
G91                  ; relative coordinates 
G1 Z-20              ; move nozzle down 20 mm 
G90                  ; absolute coordinates 
```

### M25 and M125 usage
Before, for a smart use, define on your firmware PARK_HEAD_ON_PAUSE and NOZZLE_PARK_FEATURE.
Then you can use these commands in Batch Printing.
```
M25                   ; pause
```
Very simple.

If you don't want touch your firmware you can use temporarely these commands.
```
G91                  ; relative coordinates
G1 Z20               ; move nozzle up 20 mm 
G90                  ; absolute coordinates 
G1 X0 Y180 F1000     ; move nozzle to these coordinates 
M400                 ; wait movement finishes 
M300 S300 P1000      ; acoustic signal, it play a simple beep 
M25                   ; pause 
G91                  ; relative coordinates 
G1 Z-20              ; move nozzle down 20 mm 
G90                  ; absolute coordinates 
```

### M600 usage
Before, for a smart use, define and set on your firmware NOZZLE_PARK_FEATURE and ADVANCED_PAUSE_FEATURE. If you don't enable these features it would not work.
```
M600                 ; change filament
```


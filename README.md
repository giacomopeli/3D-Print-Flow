# Batch Printing

## Summary
The purpose of this software is to give a simple and efficient way of batch printing solutions. 

There are a few ways to batch print, but this software will take you to the best way of doing it.

Normally when comes the need of producing the same part many times you cover your bed's surface until it results full. But what you will do if a part detached from the bed? Yes, you will throw away your batch. Same thing if the electric currents goes off. Resume print and you will see a defective layer on all the parts, not the best. But why continue doing this? There's no reason.

You can print the same part once a time and if you're having a mess you would not waste filament and time. It's logic. But what about time? Pretty the same as it is determined by the volume of your parts and not by how you print them. The only waste of time in this case is removing the print, re-heat up your bed and your nozzle, restart the print.

With the first way your risk of wasting material and time are bigger than the second way, but with the second way you have to be near the printer and take care of the process.

This software automates the second way giving you also the benefits of the first way. 

## How does it function?
Basically you prepare file .gcode of what you want to print and you will do it with your preferred slicer. Batch Printing recognises what part of the .gcode has to batch printed and cooks a .gcode multiplying your parts. Between the parts there's the option to execute custom commands, the print can be paused or the extruder block can be moved in order to hit the printed parts and free the bed. This is up to you, but you can see some example in Pause.md.

## What you need to do
In your slicer you need to modify your start gcode and your end gcode in your slicer settings in this way.

### Start gcode
```
;start_startgcode

[here goes your entire actual start gcode]

;end_startgcode
;start_bodygcode
```
### End gcode
```
;end_bodygcode
;start_endgcode

[here goes your entire actual end gcode]

;end_endgcode
```

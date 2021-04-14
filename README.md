# Batch Printing

## Summary
The purpose of this software is to give a simple and efficient way of batch printing solutions. 

There are a few ways to batch print, but this software will take you to the best way of doing it.

Normally, when comes the need of producing the same part for many times you cover your bed's surface until it results full. But what will you do if a part detaches from the bed? Yes, you will throw your batch away. Same thing if the electric currents goes off. Resume the print and you will see a defective layer on all the parts, not the best. But why continue doing this? There's no reason.

You can print the same part once at a time and if you're having a mess you won't waste filament and time. It's logical. But what about time? Pretty the same as it is determined by the volume of your parts and not by how you print them. In this case, the only waste of time is removing the print, re-heating up your bed and your nozzle, restarting the print.

With the first way the risk of wasting material and time are bigger than the second way, but with the second way you have to be near the printer and take care of the process.

This software automates the second way giving you also the benefits of the first way. 

## How does it work?
Basically, you prepare the file .gcode of what you want to print and you will do it with your preferred slicing software. Batch Printing recognises what part of the .gcode has to batch printed and cooks a .gcode multiplying your parts. Between the parts there's the option to execute custom commands, the print can be paused or the extruder block can be moved in order to hit the printed parts and free the bed. This is up to you, but you can see some examples in Pause.md.

## Installation
In your preferred slicer you need to modify your Start gcode and your End gcode in your slicer's settings in this way:

### Start gcode
```
;start_startgcode

[here goes your entire actual start gcode]

;end_startgcode
;start_bodygcode
```
As the example
![startgcode](https://user-images.githubusercontent.com/71249563/114771901-6cf62980-9d6d-11eb-82e3-f33286d8e929.PNG)

### End gcode
```
;end_bodygcode
;start_endgcode

[here goes your entire actual end gcode]

;end_endgcode
```
As the example


### Pause gcode
Please, look at Pause.md for further information.

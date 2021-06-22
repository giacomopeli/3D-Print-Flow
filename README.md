# Batch Printing

## Summary
The purpose of this software is to give a simple and efficient way of batch printing solutions with FDM 3d printers. 

There are a few ways to batch print, but this software will take you to the best way of doing it.

Normally, when comes the need of producing the same part for many times you cover your bed's surface until it results full. But what will you do if a part detaches from the bed? Yes, you will throw your batch away. Same thing if the electric currents goes off. Resume the print and you will see a defective layer on all the parts, not the best. But why continue doing this? There's no reason.

You can print the same part once at a time and if you're having a mess you won't waste filament and time. It's logical. But what about time? Pretty the same as it is determined by the volume of your parts and not by how you print them. In this case, the only waste of time is removing the print, re-heating up your bed and your nozzle, restarting the print.

With the first way the risk of wasting material and time are bigger than the second way, but with the second way you have to be near the printer and take care of the process.

This software automates the second way giving you also the benefits of the first way. 

## How does it work?
Basically, you prepare the file .gcode of what you want to print and you will do it with your preferred slicing software. Batch Printing recognises what part of the .gcode has to batch printed and cooks a .gcode multiplying your parts. Between the parts there's the option to execute custom commands, the print can be paused or the extruder block can be moved in order to hit the printed parts and free the bed. This is up to you, but you can see some examples in Pause.md.

## Installation and Configuration
You can download the software [here](https://github.com/giacomopeli/batchprinting/releases)  
After you've downloaded the file you need to control that the file spool.ico is in the same folder of batchprinting.exe.

Then you need to configure come things.
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
![endgcode](https://user-images.githubusercontent.com/71249563/114771897-6cf62980-9d6d-11eb-9d77-568a82c8157c.PNG)



### Pause or extruder movements gcode
When you open the software you need to set what your printer need to do after has printed a part and before it starts printing the next.
You can modify this in this text box. You can set a simple pause as descripted below, but you can move the extruder block (or the x-axes) in order to detach your parts from the bed or even re-level the bed using G29 command. By default you'll find the M25 command.

![pause](https://user-images.githubusercontent.com/71249563/114772937-b4c98080-9d6e-11eb-9dc6-c5e0423930b7.PNG)


#### M0 and M1 - Simple Pause
M0 and M1 do the same type of pause. During the print, when the machine arrives to read the M0 or M1 line of the gcode simply stop the extruder block at the last position.
That's bad because in most cases you're having the hot nozzle stopped on the prints, this causes blobs or bad artifacts on the print. To avoid this you need to move the extruder block off the printed parts.
The printer waits for a simple click input. 

#### M600 - Change Filament Pause
M600 does a simple change filament: raises the extruder block, unloads filament, waits for filament loaded, extruder does a purge and then it restarts the print process.
This will be useful if you need to see how a print comes out with different filament.
You need to set it before in your Marlin firmware, then compile it. In most cases, if you don't set it properly after some seconds it starts the cooling process wasting time to heat up. You need to enable it in firmware defining and setting NOZZLE_PARK_FEATURE and ADVANCED_PAUSE_FEATURE.

#### M25 - Pause SD Print
M25 does a pause as you would do it during the print process. Using M25, unlike M0, M1 and M600, allows you to access the whole menu of the printing process, even the "Change filament" (M600 command).
M25 could be the best option if you want to try different parameters as temperature, fan speed, printing speed, accelertion and so on.
In Marlin firmware you can set PARK_HEAD_ON_PAUSE which moves the extruder block in the set position before pausing the print. This avoids the blob or artifacts.
That's the preferred option as it is the most versitile option (as it gives you access on what the M0, M1, M600 commands do).

#### M125 - Park Head 
M125 is pretty the same as the M25 command. You can use it before M600 if you have PARK_HEAD_ON_PAUSE enabled and well set. Try it if you have some problems with M25. Probably if you print from USB device or USB port M125 is more suitable.

#### G29 - Bed levelling
After a part is printed and the machine is waiting to printing a new one, if you have detached your bed or moved it in anyway, and you have a set in your firmware a bed levelling procedure you can do it adding G29 command. Pay attention to insert it after the pause command (you don't want to re-level the bed with a part on your bed).

#### Some useful examples
You can copy and paste in Batch Printing, but it is better to look on what you're doing.

##### M0 and M1 usage
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

##### M25 and M125 usage
For a smart use, you must define on your firmware PARK_HEAD_ON_PAUSE and NOZZLE_PARK_FEATURE before.
Then you can use these commands in Batch Printing.
```
M25                   ; pause
```
Very simple.

If you don't want to touch your firmware, you can use these commands temporarely.
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

##### M600 usage
For a smart use, you must define and set on your firmware NOZZLE_PARK_FEATURE and ADVANCED_PAUSE_FEATURE before. If you don't enable these features it won't work.
```
M600                 ; change filament
```
## Usage
### Selecting the file
By clicking on "Select file .gcode" it opens a window where you can choose the file you have saved from your slicer and the path of your file appears on the left of the button.

### Printing time
If the slicer you use set print progress using M73 command and R parameter the software will show you how much time it takes to print all the parts. PrusaSlicer does it well.

### Generating the batch file
After you have defined how many copies you want you have only to generate the file. After this you can find the file in the same folder of the executable file batchprinting.exe.


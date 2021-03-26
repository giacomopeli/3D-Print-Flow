# Batch Printing

The purpose of this software is to give a simple and efficient way of batch printing solutions. 

As I 3D print almost every day, sometimes I need to create the same part more times. Today slicers give two solutions. The first, which is more obvious, consist of copying and placing the same part up to the bed results covered. In this case the printer prints the same layer for all the parts, goes high, prints the next layer and so on. The second way consist of printing the parts once at time. This way has the disadvantage of to be unable to place many parts because the extruder block volume doesn't have to touch the parts already printed. Really, this isn't a disadvantage because the print time is more or less the same and also takes less movements of the extruder, reducing stringing with viscous material as the PETG. Also, if first method is chosen, might be that a part detaches from the bed constraining the operator to stop the printer losing material already extruded and time. 

So, printing one part at time is more reliable, but the print needs to be started many times, the printer needs to be powered up many times and all that is to made by you. Suppose to print a 50x50x50 mm part, 20 times, once a time, that your machine needs up to 3 minute to be hot and ready, and when a print finish the printer starts the cooldown (I suppose, as I'm cosindering a normal situation, that you want your machine cooldowns). Doing some maths, results that in this way, in the better case, 20x3 minutes are lost. 

Disclaimer: that's what I need and I'm not a programmer. I choose to code it in Python as I know its fundamental, but probably there is a better language. Because Python reliability and simplicity this source can be implemented almost everywhere.

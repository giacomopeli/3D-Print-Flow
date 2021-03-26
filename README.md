# Batch Printing

The purpose of this software is to give a simple and efficient way of batch printing solutions. 

As I 3D print almost every day, sometimes I need to create the same part more times. Today slicers give two solutions. The first, which is more obvious, consist of copying and placing the same part up to the bed results covered. In this case the printer prints the same layer for all the parts, goes high, prints the next layer and so on. The second way consist of printing the parts once at time. This way has the disadvantage of to be unable to place many parts because the extruder block volume doesn't have to touch the parts already printed. Really, this isn't a disadvantage because the print time is more or less the same and also takes less movements of the extruder, reducing stringing with viscous material as the PETG. Also, if first method is chosen, might be that a part detaches from the bed constraining the operator top stop the printer losing material already printed and time. 

Disclaimer: that's what I need and I'm not a programmer. I choose to code it in Python as I know its fundamental, but probably there is a better language. Because Python reliability and simplicity this source can be implemented almost everywhere.

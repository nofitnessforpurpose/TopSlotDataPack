# Top Slot Data Pack  

PSION Organiser II - Top Slot Data Pack Adapter

This repository holds files needed to create a Top Slot Data Pack Adapter for the Psion Organiser 2  
 (Data Pack Not Included ;-) )
<div align="center">
  <div style="display: flex; align-items: flex-start;">
    
  <img src="https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/images/TSDP-01.png?raw=true" width="400px" alt="PSION Organiser II Top Slot Case. Image copyright (c) 10 August 2024 nofitnessforpurpose All Rights Reserved">
  </div>
</div>
<BR>

[![Organiser](https://img.shields.io/badge/gadget-Organiser_II-blueviolet.svg?%3D&style=flat-square)]([https://en.wikipedia.org/wiki/Psion_Organiser])
[![GitHub License](https://img.shields.io/github/license/nofitnessforpurpose/TopSlotDataPack?style=flat-square)](https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/LICENSE) 
[![Maintenance](https://img.shields.io/badge/maintained%3F-yes-green.svg?style=flat-square)](https://github.com/nofitnessforpurpose/TopSlotDataPack/graphs/commit-activity)
![GitHub repo size](https://img.shields.io/github/repo-size/nofitnessforpurpose/TopSlotDataPack?style=flat-square)
[![Static Badge](https://img.shields.io/badge/format-STEP%20Solid%20Model-blue?style=flat-square)](https://en.wikipedia.org/wiki/ISO_10303)
[![Static Badge](https://img.shields.io/badge/format-GERBER%20PCB-blue?style=flat-square)](https://en.wikipedia.org/wiki/Gerber_format)
<br>  
  All the files are required.  <br>
  The default repository format for 3D files is STEP (<a target="_blank" rel="noopener noreferrer" href="https://en.wikipedia.org/wiki/ISO_10303"> ISO 10303</a> ) due to its high fidelity.  { STL files are surface geometry as opposed to solid model representations, often containing export processing artifacts }. 
<br>  
  The default repository format for PCB files is <a targer="_blank" rel="noopener noreferrer" href="https://en.wikipedia.org/wiki/Gerber_format">GERBER</a> .
<br>

<br>  
<a target="_blank" rel="noopener noreferrer" href="https://www.freecad.org/" > FreeCAD </a> may prove suitable for viewing, handling and, if desired modifying STEP files.
<br>
<a target="_blank" rel="noopener noreferrer" href="https://www.kicad.org/" >KiCad </a> may prove suitable for viewing GERBER files.
<br>

## Use Case
There are two scenarios envisaged for this design
- Read only EEPROM Data Pack
- Top Slot Hardware testing in conjunction with <a target="_blank" rel="noopener noreferrer" href="https://github.com/nofitnessforpurpose/TopSlotSpy" >Top Slot Spy</a>

There are a number of types of Data Pack, the first iteration is intended to support Linear addressed packs:  
Data Pack Type Summary  
| Size |	Linear | Paged | Segmented |
| ---- | ------ | ----- | --------- |
|   8K |	   X   |       |           |
|  16K	|    X   |       |           | 
|  32K | 	  X   |   X   |           |
|  64K	|    X   |   X   |           | 
| 128K	|        |   X   |     X     |
  
RAM Packs Type Summary  
| Size |	Linear | Paged | Segmented |
| ---- | ------ | ----- | --------- |
|  32K	|        |   X   |           |
|  64K	|        |   X   |           |
| 128K	|        |   X   |     X     |
  
In summary supported are 8 to 64 K Linear Data Packs, or devices emulating these pack addressing schemes. There is no inherent limit to the size which is only problematic for random access use. 

<BR>

## Limitations
The Operating system on the test CM and LZ variants did not index through drive D: e.g. FIND, SAVE etc. However, COPY D: To A: (or other location does function.  

Running programs diretly on the top slot is readily achieved as described below:
Create a stub program on A:, B: or C:  
In the example case with the Info and Y2K fix pack, the stub program INF: on A: would be:  

```
INF:
REM Stub code to run program on pack D:
INFO:
```
Notice the location is not specified. However, the system will locate the code on drive D: and run it from that location.

<BR>

## Considerations
The 3D model makes no accomodation for manufacturing tolerances, process or material - see Notes below.  

The PCB has been tested in CM and LZ machines, it remains your responsiblity to asses suitability!  
The assembly of PCB and case has been tested.  
Many pieces of software, including the authors ;-) may accidently, never have considerd allowing selection of Pack D: in menus.  

The original male 8 way 2 row top slot header style connector (marked <a target="_blank" rel="noopener noreferrer" href="https://github.com/nofitnessforpurpose/TopSlotCase/blob/main/images/MXS-70224-02%20(2).jpg">MXS 70224</a>) may have included a custom pin support moulding. Data from a parts list kindly indicated in this <a href="https://www.organiser2.com"> hardware forum</a> seemed to confirm this theory. Readily available 8 way 2 row header connectors tend to have smaller pin support mouldings. The effect of using pin headers with smaller moulding is to permit the PCB to displace vertically in the slot guide channel, resulting in poor alignment with the mating female connector and potential insertion difficulty. There are a number of mitigations, such as changing the height of the male header connector in the PCB and adding material to support the top of a smaller male header pin support moulding. The precise accommodation will depend on your selected pin header moulding, though this case is inteded to reduce issues. 

## Questions / Discussion
See <a target="_blank" rel="noopener noreferrer" href="https://www.organiser2.com/"> Organiser 2 Hardware </a> forum, though see note below first.


## Please note:  
All information is For Indication Only.
No association, affiliation, recommendation, suitability, fitness for purpose should be assumed or is implied.
Registered trademarks are owned by their respective registrants.

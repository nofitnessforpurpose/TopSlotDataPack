# Top Slot Data Pack  

Organiser II - Top Slot Data Pack Adapter

This repository holds files needed to create a Top Slot Data Pack Adapter for the Organiser II family of devices.  
 (Data Pack Not Included ;-) )
<div align="center">
  <div style="display: flex; align-items: flex-start;">
    
  <img src="https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/images/TSDP04.jpg?raw=true" width="400px" alt="PSION Organiser II Top Slot Case. Image copyright (c) 10 August 2024 nofitnessforpurpose All Rights Reserved">
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
<a target="_blank" rel="noopener noreferrer" href="https://www.freecad.org/">FreeCAD</a> may prove suitable for viewing, handling and, if desired modifying STEP files.
<br>
<a target="_blank" rel="noopener noreferrer" href="https://www.kicad.org/">KiCad</a> may prove suitable for viewing GERBER files.
<br>

### On-Line Preview   
Models might be viewed on line using the following links. Noting display of any mesh lines is a feature of the renderer and are not contained in the source STEP model. It is strongly recommended to use the source STEP file where ever possible, as any export process will introduce artifacts.  
 - Top - <a target="_blank" href="https://3dviewer.net/#model=https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/CAD/Top%2009-DP02.stp">here</a>  
 - Bottom - <a target="_blank" href="https://3dviewer.net/#model=https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/CAD/Bottom%20TSS%2003.stp">here</a>  
 - Assembly - <a target="_blank" href="https://3dviewer.net/#model=https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/CAD/AssTSDP02.stp">here</a>  
<BR>
<BR>

## Use Case
There are two principle scenarios envisaged for this design:
- Read only EEPROM Data Pack
- Hardware testing in conjunction with [Top Slot Spy](https://github.com/nofitnessforpurpose/TopSlotSpy) or [Side Slot Spy](https://github.com/nofitnessforpurpose/SideSlotSpy)

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
  
The system supports 8K to 64K Linear Data Packs, and data pack devices that emulate these addressing schemes. While there is no inherent limit to the data pack size other than imposed by the operating system. Paged packs are generally more suitable for random access scenarios and are not supported at this time.

### 32K Linear & Paged Data Packs
Example 32K Data Pack Configuration is shown in the image below.

<div align="center">
  <div style="display: flex; align-items: flex-start;">
  <img src="https://github.com/nofitnessforpurpose/TopSlotDataPack/blob/main/images/32K-Pack-Mod.jpg?raw=true" width="400px" alt="PSION Organiser 32 K Byte Data Pack configuration comparison between Linear and Paged modes. Image copyright (c) 08 February 2025 nofitnessforpurpose All Rights Reserved">
  </div>
</div>
<BR>
Configuration link located on the right side of the board top left of the HEF4024BT counter I.C.  <BR>
Top Pack - Modified - Linear - See Blue 0 Ohm Link  <BR>
Bottom Pack - Original - Paged - See Green 0 Ohm Link  <BR>

Note: Both pack types operate normally in the Side Slots.<BR>
<BR>

## Construction  
Construction requires a minimum of:  
- 2 layer PCB  
- 2 off, 2 x 8 way Right angle header (~8 mm engagement length, gold plated)  
<BR>
Carefully verify connector heights where using typical header connectors not having 'classic' Organiser connector full body mouldings. See <a href="https://github.com/nofitnessforpurpose/TopSlotCase-2/?tab=readme-ov-file#connector-alignment">here</a> for construction techniques.  

<BR>
<BR>

## Limitations  
The Operating System menu features of the test CM and LZ variants did not index through drive D: e.g. FIND, SAVE etc. However, COPY D: To A: (or other location) does function.  

Running programs directly on the top slot is readily achieved as described below:  
Create a stub program on A:, B: or C:  
In the example case with the Info and Y2K fix pack, the stub program INF: on A: would be:  

```
INF:
REM Stub code to run program on pack D:
INFO:
```
Notice the location of INFO: is not specified. However, the operating system will locate the procedure code on drive D: and run it from that location.  

This behaviour is detailed in the Technical Reference manual in section <a target="_blank" rel="noopener noreferrer" href="https://www.jaapsch.net/psion/tech17.htm">17.7.20  QCO_PROC</a>  
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

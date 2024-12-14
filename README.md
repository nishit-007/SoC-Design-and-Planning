
# Digital VLSI SoC Design And Planning

This repository is about the 14 day workshop conducted by VSD-IAT on Physical Design using the open source EDA Tool OpenLANE and open source pdk skywater 130nm.
## Day 1 : Inception of open source EDA , OpenLANE and sky130pdk
**OpenLANE ASIC Design Flow** 

The three components of an ASIC are RTL IPs , EDA Tools and PDK Data.

The Process Design Kit (pdk) acts as an interface between the fab and the designers. We used the skywater 130nm pdk. OpenLANE is built around the skywater and is capable of perfoming the RTL2GDS Flow.
<img width="865" alt="Screenshot 2024-12-12 132333" src="https://github.com/user-attachments/assets/6dec1a52-c946-409f-b3d5-32f0b6a2e621" />

<details>
<summary>Day 1  Lab</summary>
 
Directory structure : Desktop/work/tools/openlane_working_dir/openlane

The docker contains all the pre installed tools


<img width="319" alt="image" src="https://github.com/user-attachments/assets/aaefc55f-a2b8-41cc-9835-2afe04df3f43" />

Successfully synthesized.

<img width="405" alt="image" src="https://github.com/user-attachments/assets/66fec57e-aa8a-4948-a424-0adc05e3dc99" />



designs/picorv32a/runs/results



<img width="599" alt="image" src="https://github.com/user-attachments/assets/9dddeaf2-f724-4873-94db-484a6b3c112b" />

Here , the Number of Cells = 14876

Number of Flip Flops = 1613

 Flop Ratio = Number of Flip Flops / Number of Cells
  
Therefore , Flop ratio = 0.1084 or 10.84 %

Files created on Dec 12 19:29

<img width="686" alt="image" src="https://github.com/user-attachments/assets/3f271b79-a615-47a2-a5fc-e68e4920fc87" />

Verified it with stats report


<img width="595" alt="image" src="https://github.com/user-attachments/assets/a4308e3a-3f5b-49f6-9f45-3fd89b2c7ff8" />
</details>



****
## Day 2 : Floorplanning , Placement and Library cells

**Floorplanning**


During floor planning a number of parameters are to be set. A well defined floor plan leads to an ASIC design with high performance and optimum area. 

**Concept of Pre Placed cell :**

Pre placed cells allows the granulizing of a larger design for usage whenever required in the design. Pre placed cells or Macros and IP's have user defined loactions and hence are placed on the chip before automated placement and routing. The pre placed are implemented once and can be used mulitiple times in the netlist.

**Decoupled Capacitors :**


Decoupling capacitors are placed locally around the pre-placed cells. The decoupling capacitor is a large capacitor completely full of charge whose voltage is equivalent to the power supply. During switching activity the decoupling capacitor decouples the circuit from the main supply and provides the necessary voltage required by the pre placed cells.

**Power Planning :**

During this stage mulltiple power supplies are placed in the chip for proper functioning.All the coupling capacitors present in the circuit demand the power supply simultaneously  which results in noise in the circuit due to voltage droop or ground bounce.


**Pin Placement :**

Optimal pin placement for less power consumption.







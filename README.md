
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

****
**Cell Design Flow And Characterisation**
****
Standard cell library contains cells with different threshold voltages and different sizes.They are characterised using the software GUNA.

The characterisation flow is :

1 . Read the model file
2 . Read the extracted spice netlist
3 . Recognize the behavior of the buffer
4 . Read the sub circuit of buffer
5 . Read in the necessary power supply
6 . Apply the stimulus
7 . Provide the necessary output capacitances
8 . Provide the necessary simulation command
9 . Feed in the characterisation file containing steps 1-8 into the GUNA software whose output is .lib file containing the timing, noise and power characterization
<details>
<summary>Day 2 Lab</summary>
 Run the floor plan command :
 
 ```
   run_floorplan
 ```

<img width="852" alt="image" src="https://github.com/user-attachments/assets/1c396a24-3f3a-4258-a0da-b25d0f14f680" />


<img width="847" alt="image" src="https://github.com/user-attachments/assets/84d68b47-7215-4708-8aa8-7d94335ecd41" />


<img width="935" alt="image" src="https://github.com/user-attachments/assets/6f162ff2-9fff-458d-8261-59d2b474824f" />


**Port Layers in MAGIC for visualization**

<img width="944" alt="image" src="https://github.com/user-attachments/assets/af908103-c2ee-4a26-96e0-b3f1244983ae" />

**Decap and Tap Cells**

<img width="947" alt="image" src="https://github.com/user-attachments/assets/f79cc5d7-c19a-4fdf-b2fa-afe0450ce6e6" />

**Unplaced Standard Cells**

<img width="947" alt="image" src="https://github.com/user-attachments/assets/4f6b42f1-a21b-4d58-87e8-84bb152e11a4" />

**Placement**

```
 run_placement
```

**Command for Magic for visualization**

<img width="948" alt="image" src="https://github.com/user-attachments/assets/fe5b44db-c08d-43ed-99d3-d9231d9861c6" />

**Placement Layout**
 
<img width="944" alt="image" src="https://github.com/user-attachments/assets/4daa465b-b817-4511-8b3e-768c1bec00d8" />

<img width="946" alt="image" src="https://github.com/user-attachments/assets/2bad9872-8dba-405f-85d9-3c5439d6e0f6" />

</details>

****
## Day 3 : Design Library Cells and ngspice Characterisation

**16 Mask CMOS Process**

1. Selecting a substrate.
2 . Creating active regions for transistors.
3 . Formation of N-well and P-well.
4 . Formation of the gate.
5 . Formation of lightly doped drain (LDD).
6 . Source and drain formation.
7 . Formation of contacts and local interconnects.
8 . Higher-level metal formation.

<img width="550" alt="image" src="https://github.com/user-attachments/assets/47caa765-23c2-4d55-b9e5-6d484c306b39" />

****
<details>
<summary>Day 3 Lab</summary>

 Configure the vsdstdcelldesign directory
 ![day 3(2)](https://github.com/user-attachments/assets/c74b212f-1764-44b9-afec-5b875de4c486)

View the inverter design in MAGIC
 ![magic vsdstdcell](https://github.com/user-attachments/assets/b81e92f0-50dd-412c-b7f4-048059962c46)

Extract the inverter to spice
![extract ngspice(1)](https://github.com/user-attachments/assets/85856e91-c01b-433d-991c-ada55df7c4ec)

![extract ngspice](https://github.com/user-attachments/assets/41b7707f-081b-4fee-9773-c03c8a2e6fe9)

spice3file created
![ngspice(3)](https://github.com/user-attachments/assets/fa061123-a3f8-4a30-826e-46b20346edd0)

Run NGSpice simulation and plot y vs time a
![rise transition](https://github.com/user-attachments/assets/9ceeebce-00b7-46cc-b12e-6eb387b30559)

Transient Response
![trans(2)](https://github.com/user-attachments/assets/2420b69a-4f61-4fcd-88cf-81506ecb5251)

Now we Calculate the following parameters
**Rise Transition Time:**

The time taken for the output waveform to transition from 20% to 80% of its maximum value.
```
 Using data points:
 x0 = 2.18543e-09, y0 = 0.660022
 x1 = 2.2575e-09, y1 = 2.63969
 Rise time = x1 - x0 = 0.07207 ns
```
**Fall Transition Time:**

The time taken for the output waveform to transition from 80% to 20% of its maximum value.
``` 
 Using data points:
 x0 = 4.05579e-09, y0 = 2.64003
 x1 = 4.09788e-09, y1 = 0.659969
 Fall time = x1 - x0 = 0.04209 ns
```
**Rise Cell Delay:**

The time taken for a 50% transition at the output corresponding to a 50% fall at the input.
```
 Using data points:
 x0 = 2.15e-09, y0 = 1.65
 x1 = 2.21647e-09, y1 = 1.65
 Rise Cell Delay = x1 - x0 = 0.06647ns
```
**Fall Cell Delay:**

The time taken for a 50% fall at the output corresponding to a 50% rise at the input.
```
 Using data points:
 x0 = 4.05e-09, y0 = 1.64994
 x1 = 4.08055e-09, y1 = 1.64994
 Fall Cell delay = x1 - x0 = 0.03055 ns
```
Open the lab files
![drc](https://github.com/user-attachments/assets/cffce6ac-61ad-4fc4-8460-cae7fe2aec4d)

Open the magic.crc file in VIM Editor
![2](https://github.com/user-attachments/assets/4224a6c1-10c6-4db5-84e4-f150a1c938e7)

Open empty magic layout
![empty magic](https://github.com/user-attachments/assets/a7426cd6-08b6-4679-9ecc-157da4c3d03f)


</details>









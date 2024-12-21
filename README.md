
# Digital VLSI SoC Design And Planning

This repository is about the 14 day workshop conducted by VSD-IAT on Physical Design using the open source EDA Tool OpenLANE and open source pdk skywater 130nm.
## Day 1 : Inception of open source EDA , OpenLANE and sky130pdk

<details>
<summary>Day 1  Theory</summary>
 
**OpenLANE ASIC Design Flow** 

The three components of an ASIC are RTL IPs , EDA Tools and PDK Data.

The Process Design Kit (pdk) acts as an interface between the fab and the designers. We used the skywater 130nm pdk. OpenLANE is built around the skywater and is capable of perfoming the RTL2GDS Flow.
<img width="865" alt="Screenshot 2024-12-12 132333" src="https://github.com/user-attachments/assets/6dec1a52-c946-409f-b3d5-32f0b6a2e621" />

</details>


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

<details>
<summary>Day 2 Theory</summary>
 
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
</details>


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

****
<details>
<summary>Day 3  Theory</summary>
 
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
</details>

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

Magic layout after adding a new rule for poly.9 in the sky130A.tech file and performing DRC check

![VirtualBox_VSDWorkshop_17_12_2024_21_38_36](https://github.com/user-attachments/assets/e8bccbac-9067-41f7-82e4-2fc984a5cded)

Now adding a new rule for  ```        
                             nwell.4
                             ```
                             in the ```
                                      sky130A.tech 
                                    ```  file.
 ![VirtualBox_VSDWorkshop_17_12_2024_22_25_10](https://github.com/user-attachments/assets/8dd93111-56d2-4d2b-8424-170219b55788)

![VirtualBox_VSDWorkshop_17_12_2024_22_26_51](https://github.com/user-attachments/assets/73278029-9580-4e20-a1f3-47d353d180e5)

Reloading and performing DRC check
![VirtualBox_VSDWorkshop_17_12_2024_22_00_50](https://github.com/user-attachments/assets/73d02ddd-0607-4459-8da4-ee843d7330fc)
![VirtualBox_VSDWorkshop_17_12_2024_22_23_11](https://github.com/user-attachments/assets/4ffba5fc-4fe7-46a3-9ac0-01900c53b93e)

                          



</details>

****

**Day 4 : Pre - Layout Timing Analysis and Importance of good Clock Tree**

<details>
<summary>Day 4 Theory</summary>

**Delay Tables in Power-Aware Clock Tree Synthesis**

It shows the relation between the output load and input slew for each buffer.

They are used to model the behaviour of standard cells , macros and other components.

**Setup Timing Analysis (Real Clock)**

The setup condition is (Δ1 + Θ < T + Δ2 - S -S.U )

( Δ1 ): Launch flop delay.

( Δ2 ): Capture flop delay.

( |Δ1 - Δ2| ): Clock slew.

(Θ) : Combinational Delay between launch and capture flip flops.

(T) : Clock Time.

(S) : Setup Time.

(SU) : Setup Uncertainty

**Hold Timing Conditions**

With real clocks, the condition becomes: [ Θ + Δ1 > H + Δ2 + HU ]

Slack : Data Arrival Time - Data Required Time

</details>

<details>
<summary>Day 4 Lab</summary>

 The following command is fed in the Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign directory
```
   magic -T sky130A.tech sky130_inv.mag &
```
![mag file](https://github.com/user-attachments/assets/97448b21-6b0b-4ea7-8341-c898a05175af)


In the Tkcon window : 

```
   help grid
```

```
   grid 0.46um 0.34um 0.23um 0.17um
```
![VirtualBox_VSDWorkshop_19_12_2024_12_03_27](https://github.com/user-attachments/assets/26d45fc9-2af4-47a5-bd5d-f6b87209a2e2)

![VirtualBox_VSDWorkshop_19_12_2024_12_04_27](https://github.com/user-attachments/assets/75ff36c0-7819-4634-9d6d-b2e9c7b01716)

Save the layout with a custom name
![VirtualBox_VSDWorkshop_19_12_2024_12_26_52](https://github.com/user-attachments/assets/ba11dd8a-8600-40bc-9069-ec03784e3129)

Generate the LEF file
![VirtualBox_VSDWorkshop_19_12_2024_12_29_43](https://github.com/user-attachments/assets/60893658-6643-4f8d-b9f3-a3388530cf3f)

Verifying the LEF file
![VirtualBox_VSDWorkshop_19_12_2024_12_32_34](https://github.com/user-attachments/assets/234acb49-369a-46c3-9375-13c873138404)

Copying the new LEF files along with the libraries to the following directory
![VirtualBox_VSDWorkshop_19_12_2024_12_46_49](https://github.com/user-attachments/assets/cd3b14f2-df8b-439c-981a-d30112ff0fb6)

Edit the  ``` config.tcl ``` file
![VirtualBox_VSDWorkshop_19_12_2024_12_58_26](https://github.com/user-attachments/assets/ff5f945c-4f67-43b0-a45c-82a68f044116)

RUN The Synthesis followed by 2 new commands
```
   set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
   add_lefs -src $lefs
```
![VirtualBox_VSDWorkshop_19_12_2024_13_10_43](https://github.com/user-attachments/assets/5596d28b-9f4d-442f-8b52-f0abc5713cca)
![VirtualBox_VSDWorkshop_19_12_2024_13_12_29](https://github.com/user-attachments/assets/57e9e665-0c89-40a5-addf-0e2e78f6f47a)

Changing the values of some variables : 
```
    set ::env(SYNTH_STRATEGY) "DELAY 3"
    set ::env(SYNTH_SIZING) 1
 ```
``` run_synthesis ```
![VirtualBox_VSDWorkshop_19_12_2024_13_42_27](https://github.com/user-attachments/assets/e8d8c34c-2b23-4f62-a3dd-c494655c190e)

```
    init_floorplan 
    place_io
    tap_decap_or
```
![VirtualBox_VSDWorkshop_19_12_2024_15_01_35](https://github.com/user-attachments/assets/3d7ac2e7-2f45-45ce-bd9c-5bfc7efdf62d)

![VirtualBox_VSDWorkshop_19_12_2024_15_03_49](https://github.com/user-attachments/assets/246d8626-232b-47f6-a294-bcf7886a2af6)

``` run_placement ```

![VirtualBox_VSDWorkshop_19_12_2024_15_05_19](https://github.com/user-attachments/assets/8eed86f9-a22c-470f-9023-de3d004d5cf8)

View the placement.def file in MAGIC
![VirtualBox_VSDWorkshop_19_12_2024_15_09_37](https://github.com/user-attachments/assets/c90cedab-84bd-4b8d-9cc6-eaf6f8859e16)
![VirtualBox_VSDWorkshop_19_12_2024_15_12_05](https://github.com/user-attachments/assets/f384ed33-74a8-494f-979b-21e570efd41d)
![VirtualBox_VSDWorkshop_19_12_2024_15_14_09 - Copy](https://github.com/user-attachments/assets/52f048dd-68bb-4068-9ed9-1bcc21e97177)

``` sta pre_sta.conf ```

Post - STA Analysis
![VirtualBox_VSDWorkshop_19_12_2024_17_27_51](https://github.com/user-attachments/assets/039219cd-a9fa-4b0f-aad5-7d96a642eb3c)

``` run_cts ```
![run cts](https://github.com/user-attachments/assets/ca5721b5-013e-4d40-a39a-abcb56be3c12)

![VirtualBox_VSDWorkshop_19_12_2024_19_40_28](https://github.com/user-attachments/assets/f576210c-7a3f-40f4-91f8-8b4707858ed8)

</details>

****

**Day 5 : Final Steps for RTL 2 GDS**

<details>
<summary>Day 5 Theory</summary>

 **Global and Detailed Routing using TritonRoute**

 ![image](https://github.com/user-attachments/assets/4a990392-bdbb-49a5-bbb8-2a52e72c715d)

 ![image](https://github.com/user-attachments/assets/117c8870-9c9b-4f2b-85cb-f7fadb756fd5)

 ![image](https://github.com/user-attachments/assets/4bd0b245-dbc3-4a69-baf3-6898a9733b28)

 ![image](https://github.com/user-attachments/assets/8fa489d3-0269-407a-8c64-4e8d5eca13a5)

 ![image](https://github.com/user-attachments/assets/e24f990c-ff62-4c90-9ac2-7db0c0f42f2a)


 
</details>

<details>
<summary>Day 5 Lab</summary>
**PDN (Power Distribution Network)**
 ``` gen_pdn ```
 
 ![VirtualBox_VSDWorkshop_21_12_2024_09_14_07](https://github.com/user-attachments/assets/69099568-9121-4216-b800-6382ea73e874)

 Loading THE PDN in MAGIC
 ![VirtualBox_VSDWorkshop_21_12_2024_09_19_24](https://github.com/user-attachments/assets/de921877-11e2-4a6e-99a4-f7a6f28fdd90)
 ![VirtualBox_VSDWorkshop_21_12_2024_09_19_58](https://github.com/user-attachments/assets/f5234c03-a920-4aeb-bdb8-a20e9a0d2634)
 ![after gen-pdn](https://github.com/user-attachments/assets/8a86a8f0-74ae-4a0a-b781-88317f858baa)

 
``` run_routing ```
![VirtualBox_VSDWorkshop_21_12_2024_09_21_40](https://github.com/user-attachments/assets/b192f83b-8d25-4acb-8f7c-eb7a351f9694)
![VirtualBox_VSDWorkshop_21_12_2024_09_42_31](https://github.com/user-attachments/assets/588445a0-4e5d-4926-a74e-22dd258a46b7)
![VirtualBox_VSDWorkshop_21_12_2024_10_01_16](https://github.com/user-attachments/assets/aa7fddfe-5a5c-4a83-bec1-02986104b3ad)

Routed def FILE IN MAGIC
![VirtualBox_VSDWorkshop_21_12_2024_09_45_46](https://github.com/user-attachments/assets/3222471f-82d7-4788-b539-921c1e55e3fc)
![VirtualBox_VSDWorkshop_21_12_2024_09_48_48](https://github.com/user-attachments/assets/007371cd-5d97-45a2-8de9-2110925639a0)
![VirtualBox_VSDWorkshop_21_12_2024_09_49_34](https://github.com/user-attachments/assets/fc6732f2-c0b5-4934-af64-50ce4c918b23)

**Timing Analysis**

Using Open STA 
![VirtualBox_VSDWorkshop_21_12_2024_10_28_48](https://github.com/user-attachments/assets/0b0c471e-2adc-4035-b7ff-bdd9862cb719)
![VirtualBox_VSDWorkshop_21_12_2024_10_29_35](https://github.com/user-attachments/assets/4a2ee0a3-f96f-4c45-b6db-feb2ab312e24)

</details>

****

**Acknowledgements**

1. [Kunal Ghosh](https://github.com/kunalg123)

2. [Nickson Jose](https://github.com/nickson-jose)

3. [Timothy Edwards](https://github.com/RTimothyEdwards)













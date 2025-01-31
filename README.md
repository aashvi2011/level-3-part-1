# level-3
# part 1
Theory:

Pads – any signal that must travel outside the chip or inside the chip goes through the pads 

Core- it holds all the gates. 

Foundry – a factory where the chips get manufactured 

Foundry ips- they are the blocks of intelligence 

Blocks placed are- macros

# LABS:
Tasks:
1. to run openLane on Linux terminal
2. To run synthesis of design file of picorv32a
3. to calculate flop ratio of design file

# Labs

Code used(with screenshots)
1.
```vsdsquadron@vsduser:~ cd Desktop/work/tools/openlane_working_dir/openlane
vsdsquadron@vsduser:Desktop/work/tools/openlane_working_dir/openlane/$ docker
bash 4.2$ pwd
bash 4.2$ ./flow.tcl -interactive
% package require openlane 0.9
% prep -design picorv32a

2.
vsdsquadron@vsduser:~ cd Desktop/work/tools/openlane_working_dir/openlane
vsdsquadron@vsduser:Desktop/work/tools/openlane_working_dir/openlane/$ docker
bash 4.2$ pwd
bash 4.2$ ./flow.tcl -interactive
% package require openlane 0.9
% prep -design picorv32a
% run_synthesis
```
![image](https://github.com/user-attachments/assets/7a7a699c-2a8a-4d5e-a8e3-0f54f0a54511)
![image](https://github.com/user-attachments/assets/7b44c0ea-7ccf-4347-9c2e-e98a81c66242)
![image](https://github.com/user-attachments/assets/8fb64689-d320-4c04-bd23-c248c22c7e46)
![image](https://github.com/user-attachments/assets/80b8738b-3206-4a26-9867-996c15e6dec6)

$$
Flop  ratio = number  of  flops / number  of  cells
$$

$$
1631/14876
$$

$$
0.108 = flop ratio
$$

$$
flop percent = 10.8 percent
$$

# part 2
# Theory:
Core is where the logic is placed 

Die encapsulates the core 

Utilization factor = area occupied by netlist/total area of core 

Aspect ratio = height / width  

Ex: If height of core is 2 unit and width is 4 unit and if area occupied by netlist is 4 unit^2, utilization factor is 0.5 and aspect ratio is also 0.5 

Ex: If height of core is 4 unit and width is 4 unit and if area occupied by netlist is 4 unit^2, utilization factor is 0.25 and aspect ratio is 1. 

This is how you produce width of core and die 

**Preplaced cells** 

Arrangement of IP’s in a chip is called floorplanning 

Preplaced cells-   The IP’s have user-defined locations, and are placed before automated placement-and-routing and are called as pre-placed cells. 

Automated placement-and-routing tools place remaining logical cells in the design onto chip 

**Decoupling capacitators**

Anything which has physical dimensions has some resistance 

It is a huge capacitor full of charge 

Replenishes charge frommain power supply 

Decouples circuit from main power supply

# Labs
Task:
1. To run the floorplan of the design file of picorv32a
2. To calculate the area of the die in microns
3. To see the layout of the floorplan in magic tool
4. To run placement in openlane
5. To show placement in magic tool

Code used(with screenshots)
```
1.
vsdsquadron@vsduser:~ cd Desktop/work/tools/openlane_working_dir/openlane
vsdsquadron@vsduser:Desktop/work/tools/openlane_working_dir/openlane/$ docker
bash 4.2$ pwd
bash 4.2$ ./flow.tcl -interactive
% package require openlane 0.9
% prep -design picorv32a
% run_synthesis
% run_floorplan

3.
vsdsquadron@vsduser:~Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-01_/results/floorplan$ magic -T/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```
![image](https://github.com/user-attachments/assets/d2ae14b8-2b29-4533-b842-84da27fea7f0)
<img width="880" alt="image" src="https://github.com/user-attachments/assets/f221c12c-70a3-40ff-b789-fa808be3d09e" />


$$
Formula for area of die in microns = die height * die width / 1000
$$
$$
660685*671405/1000

```
4.
% run_placement
5.
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/30-01_12-38/results/placement/

$$

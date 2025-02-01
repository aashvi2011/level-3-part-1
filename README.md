# level-3
# part 1
Theory:

Pads: These are the interface points through which signals enter or exit the chip, either traveling externally or within the chip itself.

Core: The central region of the chip that contains all the logic gates and functional units essential for the chip's operation.

Foundry: A manufacturing facility where semiconductor chips are produced through various fabrication processes.

Foundry IPs (Intellectual Properties): Pre-designed, reusable blocks or components of a chip that provide specific functions and are sourced from the foundry or third parties.

Macros: Larger, predefined functional blocks or modules placed within the chip design, typically containing complex logic or IP that can be reused across different designs.

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
# Core and Die in Chip Design
Core: The region where the logic (circuitry) is placed.
Die: Encapsulates the core and includes additional regions such as IOs and power delivery.

 # Key Metrics in Chip Floorplanning
 
**Utilization Factor:**
Utilization Factor= Total area of core / Area occupied by netlist
​
-> Represents how efficiently the core area is used.

**Aspect Ratio**
Aspect Ratio= Height of core / Width of core

-> Determines the shape of the core.

**Examples**

**Example 1**

Core dimensions: Height = 2 units, Width = 4 units

Netlist area: 4 unit²

Utilization Factor: 4 / 2×4 = 0.5

Aspect Ratio: 2 / 4 = 0.5

Example 2

Core dimensions: Height = 4 units, Width = 4 units

Netlist area: 4 unit²

Utilization Factor: 4 / 4 × 4 = 0.25

Aspect Ratio: 4 / 4 = 1

**Preplaced Cells and Floorplanning**
**Floorplanning:* 
The process of arranging IP blocks in a chip.

**Preplaced Cells:*
-> Certain IP blocks have user-defined locations.
-> Placed before automated placement and routing (P&R).

*Automated Placement & Routing (P&R):*
-> Remaining logical cells are placed and interconnected by P&R tools.

**Decoupling Capacitors (Decaps)**
Purpose: Helps stabilize power delivery by mitigating voltage fluctuations.

**Why Needed?**
-> Any physical structure has inherent resistance.
-> Decaps act as large charge reservoirs to provide stable power to logic components.Core is where the logic is placed 



# Part - 3
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
![Capture4](https://github.com/user-attachments/assets/bd65b134-3791-40d2-ad17-f4f1b9d9531a)




$$
Formula for area of die in microns = die height * die width / 1000
$$

$$
660685*671405/1000
$$

```
4.
% run_placement
5.
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/30-01_12-38/results/placement/

6.
magic -T /Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
Showing placement in magic tool

![Capture6](https://github.com/user-attachments/assets/519f413b-4958-4cb7-984c-7a3113d8e2b8)
![Capture5](https://github.com/user-attachments/assets/689c8cdd-7f5c-4a4e-8561-18f49210307f)


# Part-3

# Labs
Tasks:
1. Reset variable value and run floorplan and show in magic tool
2. Clone github file and add to openlane directory
3. Copy .tech file to new gitfub file
4. Opening .mag and .tech file in magic tool to show inverter and check connections
5. Extract spice file
6. Modify spice file





Code used:
``` 
2. git clone https://github.com/nickson-jose/vsdstdcelldesign.git
3. cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/
4. 
# moving to vsdstdcelldesign directory
magic -T sky130A.mag sky130A.tech &
5.
#in vsdstdcelldesign directory in tkcon window
extract all
ext2spice cthresh 0 rthresh 0
ext2spice

```
1. ![Capture8 (1)](https://github.com/user-attachments/assets/a448ad3d-4086-4e5f-8e8f-4bda42233595)
2.![Capture9 (1)](https://github.com/user-attachments/assets/f02a5538-96cf-46eb-8b76-c532cbd2f7d2)
4. ![Capture8](https://github.com/user-attachments/assets/150c8cdc-a9e3-45b0-a716-f3716748d660)
Verifying conditions:
![Capture12](https://github.com/user-attachments/assets/97dab573-f80e-401c-8546-31e43ce8b654)
![Capture13](https://github.com/user-attachments/assets/b4aaa5f0-5671-4050-849e-966ca1d8e677)
![Capture14](https://github.com/user-attachments/assets/09de7444-2d30-44f0-a812-7fa07c3cf061)

5.![Capture15 (1)](https://github.com/user-attachments/assets/99730969-600e-4db7-aa42-dfa1ff004e85)
6.![Capture19 (1)](https://github.com/user-attachments/assets/c95b1ca1-79d2-4b36-87f2-5aa2a1552a95)


# Part-4

# Labs
Tasks:
1. Set grid definitions to track definitions
2. extract lef file
3. copy lef file to src irectory
4. To modify config.tcl to add library and lef files
5. run synthesis with new lef
6. run floorplan
7. run placement
8. Post-synthesis in OpenSTA
9. Optimizing synthesis


Screenshots:
![Capture20](https://github.com/user-attachments/assets/872b39fa-1451-44e8-b273-1a5dc7a0f4ef)

![Capture21](https://github.com/user-attachments/assets/b556f606-f726-420b-b406-9848d3b852eb)

![Capture22](https://github.com/user-attachments/assets/c1c9b0cd-e365-42b1-b0a2-64960503e078)

![Capture23](https://github.com/user-attachments/assets/c0e9ed9b-8541-4d2d-9e54-0245d4b44913)

![Capture24](https://github.com/user-attachments/assets/d79cc25e-fa61-4395-976e-1928bbc19187)

![Capture25](https://github.com/user-attachments/assets/17b8b484-2d32-45b2-a34c-8455d2d6fee2)

![Capture26](https://github.com/user-attachments/assets/15d0ace0-d806-40c1-b03f-19607cd9c6aa)

![Capture27](https://github.com/user-attachments/assets/33db695a-55b9-46d7-88fa-1feabbff55dd)

![Capture28](https://github.com/user-attachments/assets/5085ac84-fe80-4304-bcbe-1ebbadce4534)

![Capture29 (1)](https://github.com/user-attachments/assets/03876995-e968-4d86-a22f-48de0a8f553e)

![Capture30](https://github.com/user-attachments/assets/e1dea824-f522-4d8c-828e-f40bf87340a9)

![Capture31](https://github.com/user-attachments/assets/69b68b8c-02d0-459e-ad21-0709ffc6e457)

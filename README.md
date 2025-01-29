# level-3
# part 1
Theory:
# LABS:
Tasks:
1. to run openLane on Linux terminal
2. To run synthesis of design file of picorv32a
3. to calculate flop ratio of design file

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
$$
Flop  ratio = number  of  flops / number  of  cells
$$

#

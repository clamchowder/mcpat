# Running Power Sims

The power simulator we are using is McPAT (2015 version). It is located at:
`HotGauge/McPAT`


Everything you need to run the power simulation portion of the toolchain has been integrated, so you shouldn’t need to make any changes to McPAT. 

The relevant scripts are located in: 
`HotGauge/tools/`


The scripts that will be used are: 
`HotGauge/tools/change_tech_node_14_to_*.py`
`HotGauge/tools/process_mcpat.sh`
`HotGauge/tools/run_mcpat.py`
`HotGauge/tools/mcpat_txt_to_json.py`
`HotGauge/tools/mcpat_to_blk_lvl_power_dict.py`


Let’s walk through each of these:

## Pre-processing and Run scripts

`change_tech_node_14_to_*.py`
This script copies raw 14nm performance data and configures it for 10nm and 7nm power simulations. 

`run_mcpat.py`
This script builds a file with the necessary McPAT run commands 

`process_mcpat.sh`
This script contains the necessary pre-processing for running McPAT on each output file from the performance simulator. This is the “top-level” script that you will run. It will take care of calling the other scripts (pre-processing, run, and post-processing (below)). 

## Post-processing scripts

`mcpat_txt_to_json.py`
This script converts a McPAT output file from a human readable text format to a JSON format to allow for easier parsing by the thermal simulator (3D-ICE)

`mcpat_to_blk_lvl_power_dict.py`
This script parses the McPAT output file and calculates hierarchical power values which are not explicitly reported but are needed by the thermal simulator. 


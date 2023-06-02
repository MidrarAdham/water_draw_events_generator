sequenceDiagram
    %% EDMCore-->EDMCore:connect_to_gridappsd
    %% EDMCore-->EDMCore:load_config_from_file
    %% EDMCore-->EDMCore:establish_line_mrid
    %% EDMCore-->EDMCore:establish_mrid_name_lookup_table
    %% EDMCore-->EDMCore:connect_to_simulation
    %% EDMCore-->EDMCore:initialize_sim_start_time
    %% EDMCore-->EDMCore:initialize_sim_mrid
    %% EDMCore-->EDMCore:create_objects
    %% EDMCore-->EDMCore: initialize_all_der_s
    EDMCore->>+DERSHistoricalDataInput: initialize_der_s
    DERSHistoricalDataInput-->DERSHistoricalDataInput:open_input_file
    DERSHistoricalDataInput-->DERSHistoricalDataInput:read_input_file
    EDMCore->>+DERAssignmentHandler:create_assignment_lookup_table
    EDMCore->>+DERAssignmentHandler:assign_all_ders
    DERAssignmentHandler->>+DERSHistoricalDataInput:assign_der_s_to_der_em
    DERSHistoricalDataInput-->DERSHistoricalDataInput:get_mrid_for_der_on_bus
    DERSHistoricalDataInput-->DERSHistoricalDataInput:append_new_values_to_association_table
    EDMCore->>+DERIdentificationManager:initialize_association_lookup_table
    DERIdentificationManager->>+DERAssignmentHandler:get association_table

# water_draw_events_generator

Based on the standard DHW sheets.

[**SOURCE**](https://www.energy.gov/eere/buildings/building-america-analysis-spreadsheets)

## Requirements:

- Python3 
- GridLAB-D (mandatory for testing)
  - GridLAB-D can be easily installed from [**here.**](https://github.com/gridlab-d/gridlab-d/releases)

## usage:
- Clone this repository to your local machine
----
- Go to the scripts folder:
    ```
    cd scripts/
    ```
----
- Run the unique.py script:
    
    ```python3 dhw_daily.py```

  - The above command will export several stacked water draw profiles.
---
- Run the resample_wd_profiles script:
    
    ```python3 resample_wd_profiles.py```

  - The above command will export full-day water draw profiles with a one-minute time resolution.
  - The time resolution can be adjusted from the script, as well as the starting time and ending time.
  - Instructions are available in the 'resample_wd_profiles' script.
---
- To test the exported water draw profiles on water heater objects using GridLAB-D:
  
  - Change the directory to the glm file:
    - ```cd populated_13_node_feeder_whs/glm/```
  - Run the GridLAB-D file using the following command in your terminal:
    - ```gridlabd 13_node_feder_whs.glm```
  - The simulation may take some time, depending on your OS. Once the simulation is done, the output files can be found in the following directory:
    - ```cd glm_output/```
  - Within the above directory, you'll find 39 files. Each file contains data for 25 water heaters in one-minute resolution.

# water_draw_events_generator

Based on the standard DHW sheets.

[**SOURCE**](https://www.energy.gov/eere/buildings/building-america-analysis-spreadsheets)

## Requirements:

- Python3 

## usage:
- Clone this repository to your local machine
----
- Go to the scripts folder:
    ```
    cd scripts/
    ```
----
- Run the unique.py script:
    
    ```python3 unique.py```

  - The above command will export many, stacked water draw profiles.
---
- Run the resample_wd_profiles script:
    
    ```python3 resample_wd_profiles.py```

  - The above command will export full-day water draw profiles with a one-minute time resolution.
  - The time resolution can be adjusted from the script, as well as the starting time and ending time.
  - Instructions are available in the 'resample_wd_profiles' script.

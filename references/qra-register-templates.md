# QRA Register Templates

## Assumption Register

| assumption_id | topic | assumption | basis | status | owner | review_action |
|---|---|---|---|---|---|---|

## Scenario Register

| scenario_id | source_unit | source_coordinates | material | phase | temperature | pressure | hole_size | release_rate | duration | release_mass | consequence_models | data_status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|

## Release Frequency Register

| scenario_id | leak_unit | hole_class | base_frequency_per_year | component_count_basis | operation_factor | corrected_frequency_per_year | data_source | assumption_id |
|---|---|---|---|---|---|---|---|---|

## Event Tree Register

| scenario_id | branch_id | branch_name | release_frequency | weather_weight | barrier_probability | ignition_probability | consequence_probability | branch_frequency_per_year | consequence_result_source |
|---|---|---|---|---|---|---|---|---|---|

## Weather Register

| weather_id | day_night | wind_speed | stability | wind_direction | frequency | source | status |
|---|---|---|---|---|---|---|---|

## Population And Vulnerability Register

| receptor_id | receptor_name | coordinates | occupancy_mode | annual_person_hours | equivalent_population | concurrent_population | indoor_fraction | building_type | vulnerability_id | notes |
|---|---|---|---|---|---|---|---|---|---|---|

## Risk Result Register

| receptor_id | LSIR_per_year | IRPA_per_year | PLL_contribution_per_year | dominant_scenario | dominant_branch | judgment |
|---|---|---|---|---|---|---|

## F-N Register

| n_fatalities | F_N_ge_n_per_year | dominant_event | notes |
|---|---|---|---|

## Pending Information Register

| item_id | missing_information | why_it_matters | current_treatment | required_source | priority |
|---|---|---|---|---|---|

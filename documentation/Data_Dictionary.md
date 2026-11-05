# Final data dictionary
    
    `Column_Profiles.csv` and the Phase 0 dictionary snapshot cover every supplied field. `Cleaned_Column_Profiles.csv` adds full-file post-rule profiles, skewness, excess kurtosis and unique counts. `all_parameter_completeness.csv` summarizes all original pollutant fields; `primary_hourly_descriptive_statistics.csv` describes primary-period analysis variables.
    
    | Analysis name | Original meaning | Unit / qualification |
    | --- | --- | --- |
    | pm25, pm10 | PM2.5, PM10 | µg/m³ |
    | no, no2, nh3, so2, o3 | NO, NO2, NH3, SO2, ozone | µg/m³ |
    | nox | NOx | ppb; not directly additive with mass units |
    | co | Carbon monoxide | mg/m³ |
    | benzene, toluene, xylene, o_xylene, eth_benzene, mp_xylene | Aromatic pollutants | µg/m³; full profiles retained |
    | temp, rh | Co-reported temperature / relative humidity | °C / % |
    | ws, wd, vws | Horizontal wind speed / direction / signed vertical wind | m/s / degrees / m/s; negative VWS retained |
    | rain | Co-reported RF | mm per hour; summed daily only with ≥18 valid hours |
    | total_rain_counter | TOT-RF | Header mm; cumulative/reset behavior unresolved; not hourly rain |
    | pressure_header_mmhg | BP source field | Header mmHg inconsistent with many values; excluded from explanatory models |
    | solar | Co-reported radiation | W/m² |
    | site_id | Filename source identifier | Separate source IDs retained across apparent replacements |
    | timestamp | Parsed source timestamp | Naive recorded clock; timezone unverified for pollutant/weather exports |
    | source_folder/source_file/source_label | Provenance | Preserved labels; alias corrections have an explicit crosswalk |
    | analysis_eligible/exclusion_reason | Inclusion policy | Copies retained in cleaned layer but excluded from independent-site analysis |
    | original_missing_mask/invalid_value_mask | Cell lineage | uint32 bit k corresponds to the ordered numeric fields below |
    | pm_order_review / pm_ceiling_review | Particle consistency / 1000 ceiling flag | Review, not deletion |
    | pressure_unit_review / temperature_review | BP >850 under mmHg header / T >55°C | Review, not correction |
    | pm25_spike_review / pm10_spike_review | Centred rolling median/MAD anomaly flag | Retrospective review only, no deletion |
    | *_lag1h | Prior-hour concentration | Correct timestamp alignment; no look-ahead |
    | *_rolling24h | Trailing 24-hour mean | ≥18 valid hours, includes current hour |
    | *_hours | Valid hourly count within day | Used for daily sufficiency |
    | *_max | Observed daily maximum | Not imputed; coverage varies |
    | year/month/hour/weekday/weekend/season | Time features | Source clock; weekday 0=Monday |
    | season_year | Winter-year convention | December belongs to the following DJF winter |
    | wd_resultant | Circular wind concentration | 0–1; small values imply variable daily direction |
    | *_observed / *_originally_missing / *_imputed | PM sensitivity lineage | Original values and exact imputation flags retained |
    | model_*_signature | Identical-series fingerprints | Not independently verified physical grid IDs |
    | wind_ms / rain_mm | Converted supplementary model weather | km/h ÷3.6; rain_cm ×10, as source headers specify |
    | clock_scenario | Provisional daily integration assumption | Same recorded date vs weather labels interpreted UTC |
    | aqi / smog_pm25 / fog_level / smoke_level | Supplied supplementary fields | AQI scheme, smog units and score algorithms unverified |
    | aqi5_lower_bound/category | Five-pollutant research index/category | Not official overall AQI; no CO/O3/Pb; severe represented as ≥401 |
    | research_episode | Network episode indicator | PM2.5 >150 for ≥3 consecutive calendar days; ≥5 sites/day |
    | timestamp_utc/timestamp_ist/local_date | FIRMS times | Documented UTC acquisition clock converted to IST |
    | fire_count/frp_mw | Detected pixels / summed fire radiative power | Not unique fires, burned area or total emissions |
    | recorded_context_both_UTC_dates | Conservative fire-date availability | Both contributing UTC dates appear; still no proof of acquisition completeness |
    | Population / epoch | Supplied grid values and snapshot year | People/cell conditional on unverified GHSL provenance; 2025/2030 projections if R2023A |
    | emission_value_source_units | Reshaped urban-centre inventory value | Absolute units and release unverified; comparisons use within-substance ratios |
    
    Missing/invalid bit order (zero-based):
    
0=pm25, 1=pm10, 2=no, 3=no2, 4=nox, 5=nh3, 6=so2, 7=co, 8=o3, 9=benzene, 10=toluene, 11=xylene, 12=o_xylene, 13=eth_benzene, 14=mp_xylene, 15=temp, 16=rh, 17=ws, 18=wd, 19=rain, 20=total_rain_counter, 21=solar, 22=pressure_header_mmhg, 23=vws

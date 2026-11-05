# Final timeline coverage
    
    Do not confuse timestamp grids with parameter availability. The discovery file/column/monthly matrices remain available from Phase 0. The final run additionally exports `Executed_File_Inventory.csv`, `weather_parameter_timeline.csv`, `station_monthly_full_history.parquet`, and per-site hourly outputs. `integration_overlap_counts.csv` documents the actual paired period for every model comparison and clock scenario.
    
    | Source | Own actual coverage | Analysis treatment |
    | --- | --- | --- |
    | Pollutant source grids | 2009–31 Oct 2026; site/parameter-specific first values | Preserve all history; main 2017–Oct 2026; older data separate; no pre-coverage filling |
    | Basic model weather | 1 Jan 2017–31 Oct 2026, hourly | Full independent EDA |
    | Model composition / supplied AQI | 4 Aug 2022 05:00–31 Oct 2026 23:00 | Actual shorter EDA; daily paired comparisons only on simultaneous valid overlap |
    | FIRMS | Oct–Nov 2024 and Oct–Nov 2025 | Two discontinuous windows; missing dates never zero-filled |
    | Population | 2010, 2015, 2020, 2025, 2030 | Independent snapshots; projected 2025/2030 conditional on GHS-POP R2023A provenance |
    | Sector inventory | 1975/1980/1985/1990/1995/2000/2005/2010/2015/2020/2024 | Sparse actual epochs; no fabricated annual records |
    | Roads, boundaries, coordinates | Static snapshots; OSM cache timestamp 2 Nov 2026 | Spatial context, no historical road trends |
    
    Different dataset start years reflect genuine supplied availability. A file named 2017–2026 may contain several variables whose first valid value is in 2022. Every direct comparison requires valid time overlap plus compatible station identity, units, resolution and clock assumptions.
    
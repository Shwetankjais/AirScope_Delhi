# Final data-quality report
    
    All originals remain unchanged. See the execution manifest, cleaned column profiles, source-level cleaning actions, primary quality review counts, outlier review counts, model-signature table and imputation validation/sensitivity tables. F01 and F02 visualize availability and imputation; F04 shows particulate consistency.
    
    Confirmed file-copy conflicts are excluded only from the analytical layer. Header-only or all-missing pollution grids do not imply zero concentrations. Review flags preserve extreme pollution. Pressure/TOT-RF ambiguities prevent unjustified unit correction. Constant fog/mist flags and unidentified AQI/score definitions limit their scientific use. One coordinate is outside the supplied boundary, and none has an authenticated monitor-registry match. All 500,055 road geometries were valid; identical reverse major-road geometries were removed only for recomputed proximity context.
    
    Final row/hash checks, bounded-gap interpolation and valid-overlap joins are recorded in Final_Validation.json. No unresolved limitation is hidden as a zero, an imputed historical observation or a causal conclusion.
    
# Reading the analysis
    
    Start with the PDF, then open Key_Findings.csv and follow the named figure/table. The notebook explains each major stage before its modular functions. Full-detail tables and source files are retained so every result can be checked.
    
    - A timestamp grid can be complete even when every pollutant value is missing. Availability percentages always state their denominator.
    - A station-day is one station on one day. Thousands of station-days do not behave like thousands of independent experiments because nearby sites share weather and adjacent days are correlated.
    - Station fixed effects account for persistently higher/lower levels at different source sites. Calendar-month effects account for a recurring seasonal cycle. They do not prove a causal explanation or repair a misidentified monitor.
    - Block uncertainty resamples/groups neighbouring days or months together. This avoids pretending each hourly row supplies wholly new independent information. Changing block length is a useful sensitivity check.
    - A 95% confidence interval describes uncertainty under a model. An interval crossing zero makes the direction of that model's association less conclusive; a narrow interval does not remove source-provenance or causal limitations.
    - A p-value is not an effect size. A small p-value does not mean a large environmental change. Compare estimated annual trends with the much larger winter–monsoon concentration difference.
    - BH adjustment addresses a declared family of multiple exploratory tests. A result may look convincing in one basic model and weaken when controls or the test family change; the fire analysis illustrates this.
    - Pearson measures linear co-variation; Spearman measures monotonic rank co-variation. Neither identifies a cause. Temperature and humidity comparisons are especially sensitive to season and conditioning variables.
    - A model estimate, an ambient monitor concentration, an emissions inventory value, a satellite fire detection and a population snapshot describe different things. Shared units or dates alone do not make them interchangeable.
    - The five-pollutant research AQI is a lower bound from a restricted subset, not official overall AQI. The separate supplied model AQI has an unknown scheme.
    - Raw files are in data/original. Cleaned Parquet files retain provenance and flags. Processed files add coverage-aware summaries/features. Imputed PM files are an optional sensitivity product and never supply the main findings.
    - Read Parquet with pandas.read_parquet. Read CSV summary tables in a spreadsheet or pandas. PNGs are convenient for slides; SVGs retain sharp text/lines when enlarged. The interactive timelines allow zooming.
    
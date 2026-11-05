# AirScope India
    
    NIErmaya – DAV-26-080 | Delhi, India | SDG 13 | Primary period January 2017–October 2026
    
    ## Open first
    
    - `reports/EDA_Report.pdf`: academic report with evidence, methods, figures and limitations.
    - `reports/EDA_Report.html` / `.md`: matching editable/readable versions.
    - `reports/Key_Findings.csv` / `.json`: 15 findings with question, evidence, timeline, figure and limitation.
    - `notebooks/Complete_EDA.ipynb`: executed, self-contained Colab-compatible workflow.
    - `documentation/Final_Validation.json`: actual scientific checks and run status.
    
    ## Dataset upload in Colab
    
    Provide these four folders, preserving their nested structure, and the workbook:
    
    1. Weather 2017-2026/
    2. Pollutants 2017-2026/ (all station subfolders)
    3. Population (5 Years)/
    4. delhi_air_project/ (data/raw, data/processed, stations and supporting metadata)
    5. All from 1985 - 2024.xlsx
    
    For small test corpora use the notebook's `files.upload()` ZIP workflow. For this large corpus use optional Google Drive mounting and set the folder containing these five inputs. One combined ZIP or separate folder ZIPs plus the workbook are supported. Nested ZIPs are inspected and safely extracted. The notebook does not assume any files already exist in Colab and contains no Desktop path dependency. Keep `.venv`, `.env`, `.DS_Store` and previously generated AirScope_India output folders out of uploads. None is needed for analysis.
    
    Run cells sequentially. The notebook installs missing analysis/report dependencies, recursively discovers sources, copies originals, cleans and audits, analyzes/plots, writes reports and offers compact/full ZIP export. Input and output roots must be separate. Re-running overwrites generated outputs but never changes inputs. Source-copy decisions are explicit and remain valid only for this provided corpus; review them when adding new sources.
    
    ## Data layers
    
    - `data/original`: byte-preserved non-secret source corpus; software/secret/generated folders excluded, with reasons in the manifest.
    - `data/cleaned/pollutants`: one full hourly Parquet per original station-labelled folder, including quarantined copies and cell lineage masks.
    - `data/cleaned/weather`: hourly model/weather fields with original shorter air-composition coverage; basic weather unit conversions are additional columns.
    - `data/imputed`: optional two-hour-gap PM sensitivity datasets with original values and exact flags; never used as the main evidence layer.
    - `data/processed/hourly`: one observed-only, feature-enriched file per retained filename site ID, with its full available history.
    - `data/processed/primary_hourly_observed.parquet`: primary study hours, preserving missingness and source-site identity.
    - Other processed Parquets/CSVs: daily/monthly/full-history summaries, overlap scenarios, episodes, limited research AQI, population context, emissions and fire data.
    - `data/processed/tables`: figure/statistical source tables, coverage/uncertainty and sensitivity results.
    
    Read Parquet with `pd.read_parquet(path)`; use the notebook or a Parquet-capable tool. This preserves datetimes/types and avoids many gigabytes of CSV expansion. Small summary tables are CSV. Plotly timelines embed JavaScript for offline use; the Folium map needs CDN assets, and a static map is supplied. No monitoring registry or model request metadata is fabricated.
    
    ## Interpretation
    
    Two copied folder series are quarantined, while multiple site IDs remain separate. Source clocks and approximate coordinates are unverified. Pressure and cumulative rainfall do not enter the main explanatory model. Model AQI is not relabelled as Indian AQI; the separately derived five-pollutant research index is a lower bound, not official overall AQI. Population projections, unknown inventory units and regional fire detections retain their explicit limits. Statistical associations are not causal explanations.
    
    ## Reproduce locally
    
    Install `requirements.txt` in an isolated Python environment. Run the notebook with `AIRSCOPE_DATA_ROOT` set to the directory containing the five inputs and `AIRSCOPE_OUTPUT_ROOT` set to the desired output directory. The companion `src/airscope_pipeline.py` provides the same code and a command-line `--data-root` / `--output-root` workflow. The executed library versions are recorded separately; Colab dependency installation uses compatible lower bounds and records the actual versions of each rerun.
    
    The Phase 0 discovery report and snapshot tables are retained for provenance. `Execution_Source_Manifest.csv` is the final-run census; counts can differ from Phase 0 because generated prior results are now present and explicitly excluded.
    
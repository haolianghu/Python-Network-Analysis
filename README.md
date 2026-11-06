# Network traffic investigation

`Visualizations.ipynb` explores flow, host-monitoring, and intrusion-prevention
logs from the VAST Challenge 2013 Big Marketing scenario. Its conclusions
describe patterns in synthetic challenge data; they are not validated
attribution of real attacks. Network data files are not included in this
repository, and there is no Excel source.

## Data and setup

1. Obtain the challenge dataset from the VAST Challenge 2013 MC3 source linked
   in the original project and review its terms before use.
2. Extract the CSV files next to the notebook. The notebook expects
   `week1_nf_chunk1.csv`, `week1_nf_chunk2.csv`, `week1_nf_chunk3.csv`,
   `week1_bb.csv`, `week2_nf.csv`, `week2_bb.csv`, and `week2_ips.csv`.
3. Install dependencies and launch Jupyter:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook
```

The optional geographic-enrichment cells additionally require a separately
obtained GeoLite2 Country `.mmdb` database named `GeoLite2-Country.mmdb` in the
notebook directory. GeoLite data has separate terms and licensing requirements;
the database is deliberately not redistributed here. The notebook contains
inline package-install commands for `geoip2` and `pycountry`; install from the
requirements file beforehand instead.

## Interpretation and safe handling

Hourly top-N counts are exploratory signals, not proof of DDoS, scanning,
exfiltration, or botnet activity. Corroborate them against independent
telemetry and documented network context before drawing conclusions. The
challenge dataset is historical; the address ranges and narratives are
scenario-specific. Treat IP addresses and logs as potentially sensitive,
minimize retention, and avoid publishing real network telemetry.

Notebook execution has not been validated because the source CSVs and GeoLite2
database are not included. It can require substantial memory when loading and
concatenating flow records.

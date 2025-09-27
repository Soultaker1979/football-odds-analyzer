# Release Checklist – Football Odds Analyzer

## Packaging a New Release

1. **Prepare Files**
   - `stageXX_dashboard.py` (latest dashboard logic)
   - `run_dashboard.bat`
   - `setup.bat`
   - `requirements.txt`
   - `updater.py`
   - `.streamlit/config.toml`
   - `cache/` (with `hist_all.parquet` and `CACHE_VERSION.txt`)
   - `exports/` (empty or with example Excel outputs)
   - `README.md`
   - `VERSION` file with release number

2. **Create ZIP**
   - Name format: `NL_Analyzer_<version>_full.zip`
   - Ensure folder structure:
     ```
     NL_Analyzer_<version>_full/
       ├─ stageXX_dashboard.py
       ├─ run_dashboard.bat
       ├─ setup.bat
       ├─ requirements.txt
       ├─ updater.py
       ├─ .streamlit/config.toml
       ├─ cache/
       │   ├─ hist_all.parquet
       │   └─ CACHE_VERSION.txt
       └─ exports/
     ```

3. **Publish on GitHub**
   - Go to **Releases → Draft new release**.
   - Tag: `v<version>` (e.g. `v4.4.8`).
   - Title: `Stage <version> – NL_Analyzer`.
   - Add description with changes.
   - Attach the ZIP under **Assets**.
   - Publish.

4. **(Optional) Integrity Check**
   - Run on Windows PowerShell:
     ```powershell
     Get-FileHash .\NL_Analyzer_<version>_full.zip -Algorithm SHA256
     ```
   - Copy the hash into the release description.

## After Release
- Users download the ZIP from GitHub Releases.
- Extract to `C:\` (or workspace).
- Run `setup.bat` (once).
- Run `run_dashboard.bat`.

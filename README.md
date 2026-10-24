# P05 decision verification

Reproducibility materials for **Decision risk in vehicle-control simulation: Reference-dependent interface selection, regret and command-replay diagnosis**.

This repository provides executable score-level checks of the reported HMMWV rankings and replay, Bullet reference paths, and the separate measured-response application. It does not replace the native simulator, calibrated physical validation, or a continuous-time truth guarantee.

## Contents

`P05-reproducibility-v24.zip` contains the code, frozen plans, retained scores and manifests. Extract it into an empty directory. Python 3.10 or later is sufficient for the first two checks:

```bash
python audit_claims24.py
python check_native_receipts17.py
python verify_manifest24.py
```

The first reconstructs the three ranking cohorts, Table 9 terrain comparison, all Bullet numerical-step paths and application choice paths. The second checks 8,976 native-repeat receipts and reconstructs the first ranking cohort and HMMWV four-corner replay. It verifies recorded arithmetic and hashes; it does not reread the original native arrays or rerun Chrono. Repeated native episodes add no independent draws.

## Measured-response application

The application fits a continuous-time yaw-response surrogate on two records and checks four withheld manoeuvre records. The 12 segment/gain conditions are dependent within those four records from one vehicle campaign. The subsequent feedback-interface simulations are an application-tier illustration, **not a validation of the HMMWV-SCM parameters or real-vehicle interfaces**. Euler has seven endpoint reversals and three returning paths; RK4 preserves all exact-model choices. The largest numerical path regret is 0.0006596653 on this application's dimensionless loss scale.

The six third-party MAT files and derived measured-trace NPZ files are excluded. The source is the LMSD Concept Car dataset, version 1.0, DOI [10.48804/PHMF9D](https://doi.org/10.48804/PHMF9D). Data, figures and text carry CC BY-NC 4.0; upstream code carries MIT. Obtain and use the data under those original terms. All source file IDs, roles and checksums appear in `LMSD-SOURCES22.json`; the full original terms are in `THIRD-PARTY-LMSD-LICENSE.md`.

```bash
python fetch_lmsd22.py --verify-dir /directory/containing/the/six/MAT/files
python fetch_lmsd22.py --download-to experiment21
python reproduce_application21.py --out /new/empty/application-reproduction
```

The downloader requires explicit invocation and refuses existing targets. The scientific reproducer requires NumPy, SciPy and the recorded runtime in `runtime22.json`; it refits and runs two complete matrices plus independent scalar consumers. Exact trajectory hashes were checked on the recorded runtime, not guaranteed across platforms. This release does not claim that these computations were rerun during submission packaging.

## Scope and exclusions

`figure-data/` contains the reported native score exports. `compact-verification/` contains all original native-repeat scalar receipts and their hashes. Separate simulator executables, vehicle assets, large native raw arrays and AV-21 raw measurements are not redistributed. Native re-execution therefore requires the externally supplied runtime and assets; the public package supports the stated score and receipt reconstruction tier.

Appendix T remains supplementary. Its AV-21 analysis concerns conditional response prediction and calibration horizon, not interface validation; its uncertain dataset-specific redistribution rights are not bypassed by this release.

The finest native step is a declared finite comparator. Zero comparator regret is not physical truth, and counts of conditions are not independent sample sizes. Study44's original frozen confirmation remains inconclusive in the retained research history; this release makes no refinement-superiority claim.

## License and citation

The P05 authors authorize MIT licensing of their own code. `LICENSE` applies to first-party code only. Third-party terms remain separate and are not relicensed. No measured source data or upstream plotting script is included. Numeric results are provided with source provenance.

Use `CITATION.cff`, identify version `v24`, and record the Git commit or the SHA256 of the ZIP used. This GitHub repository has no claimed archive DOI. Contact: Jianxun Cui, cuijianxun@hit.edu.cn.

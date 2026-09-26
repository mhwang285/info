# Run 3 data record

Information on the Run 3 data and MC stored on Perlmutter and Hiccup.

## Table of contents

- [Run 3 data record](#run-3-data-record)
  - [Table of contents](#table-of-contents)
  - [Data](#data)
    - [For analysis](#for-analysis)
    - [For embedding or trigger efficency studies](#for-embedding-or-trigger-efficency-studies)
    - [Deprecated data](#deprecated-data)
  - [MC (central)](#mc-central)
    - [Standard BerkeleyTree format](#standard-berkeleytree-format)
    - [Alternative formats](#alternative-formats)
  - [MC (fast simulation)](#mc-fast-simulation)

## Data

Raw data converted to BerkeleyTree format.

1. To find the path on Perlmutter, prepend the path found in the Path column with: `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/data`. On Hiccup, prepend the path with: `/rstorage/alice/run3/data`. A file list of the BerkeleyTrees for each dataset can be found in `tree_list.txt` in the corresponding directory.
2. All datasets that have an entry in the Path column are available on NERSC. Only datasets that are checked in the Hiccup column have been transferred there. Datasets with no Path entry have not been converted. Contact Tucker if you need a dataset converted, and/or if you need a dataset copied to Hiccup.
   - In principle, any JE derived dataset that has been produced can be converted. A full list of JE derived data can be found on [this spreadsheet](https://docs.google.com/spreadsheets/d/1zsD_StvPqN2-7dOlfN9W03TB4Opj9EwdrBQHOQi3ViU/edit?usp=sharing) (first sheet).
3. You will need your Grid certificate installed in your browser to access the Hyperloop links. Check this [O2Physics documentation page](https://aliceo2group.github.io/analysis-framework/docs/gettingstarted/certificate.html) for more information.
4. All pp datasets are at 13.6 TeV, with the exception of the 2024 pp reference, which is at 5.36 TeV. All Pb-Pb and OO data is at 5.36 TeV.
5. All datasets contain event and track information. Those that also have cluster information are marked in the Cluster column.

> [!CAUTION]
> The JE derived data format is still in flux, so the selection and trigger bits for tracks and events that you see in O2Physics **may not match the data you have.** Go to the dataset's train page on Hyperloop, find the Package tag, and look at the corresponding tag on the [O2Physics GitHub repository](https://github.com/AliceO2Group/O2Physics) to find exactly which bits mapped to which selection during the derived data production.

### For analysis

These datasets are ready for analysis.

1. In creating JE derived datasets, some selections are performed to reduce the size.
   - For skimmed datasets, only events that fired JE software triggers are saved.
   - All other datasets have some selections on clusters, charged jets, full jets, and trigger tracks; check the description of the linked JE derived dataset for more details and make sure it is suitable for your analysis.
2. Filelists can be found in the directory specified in the Path column, in a file named `tree_list.txt`.

| ALICE dataset                                                                                                 | System | JE dataset                                                                                                   | Train                                                                   | Clusters | Path                                  | Hiccup? | Notes              | Int. lumi. |
|---------------------------------------------------------------------------------------------------------------|--------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|----------|---------------------------------------|---------|--------------------|------------|
| [LHC24_ppref_pass1](https://alimonitor.cern.ch/hyperloop/view-dataset/1728?timestamp=1772541683834)           | pp     | [JE_LHC24_ppref_pass1_CJ8_FJ8_CL5_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3011)    | [626869](https://alimonitor.cern.ch/hyperloop/train-run/626869/general) |          | `LHC24_ppref/BerkeleyTrees`           | &check; |                    | 5/pb       |
| [LHC22o_pass7_minBias](https://alimonitor.cern.ch/hyperloop/view-dataset/1071?timestamp=1772544939563)        | pp     | [JE_LHC22o_pass7_minBias_CJ8_FJ8_CL5_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3012) | [626927](https://alimonitor.cern.ch/hyperloop/train-run/626927/general) |          | `LHC22o/BerkeleyTrees`                |         |                    | 1/pb       |
| [LHC24_pass1_skimmed](https://alimonitor.cern.ch/hyperloop/view-dataset/1661?timestamp=1772618397685)         | pp     | [JE_LHC24_pass1_skimmed](https://alimonitor.cern.ch/hyperloop/view-dataset/3010)                             | [627650](https://alimonitor.cern.ch/hyperloop/train-run/627650/general) | &check;  | `LHC24_skimmed/BerkeleyTrees`         | &check; | V1 clusters only   | 53/pb      |
| [LHC24_pass1_skimmed](https://alimonitor.cern.ch/hyperloop/view-dataset/1661?timestamp=1772618397685)         | pp     | [JE_LHC24_pass1_skimmed](https://alimonitor.cern.ch/hyperloop/view-dataset/3010)                             | [627650](https://alimonitor.cern.ch/hyperloop/train-run/627650/general) | &check;  | `LHC24_skimmed_v3/BerkeleyTrees`      |         | V3 clusters only   | 53/pb      |
| [LHC26_pass1_MinBias](https://alimonitor.cern.ch/hyperloop/view-dataset/3437?timestamp=1787238077362)         | pp     |                                                                                                              | [743024](https://alimonitor.cern.ch/hyperloop/train-run/743024/general) |          | `LHC26_sampled/BerkeleyTrees`         |         |                    |            |
| [LHC26ac_pass1_Thin_medium](https://alimonitor.cern.ch/hyperloop/view-dataset/3195?timestamp=1787634073730)   | pp     |                                                                                                              | [745393](https://alimonitor.cern.ch/hyperloop/train-run/745393/general) |          | `LHC26_thin_medium/BerkeleyTrees`     |         |                    |            |
| [LHC25ae_pass2](https://alimonitor.cern.ch/hyperloop/view-dataset/2319?timestamp=1773072135385)               | OO     |                                                                                                              | [747875](https://alimonitor.cern.ch/hyperloop/train-run/747875/general) |          | `LHC25ae_fix/BerkeleyTrees`           | &check; |                    |            |
| [LHC24ar_pass3_small](https://alimonitor.cern.ch/hyperloop/view-dataset/2584?timestamp=1787677272184)         | PbPb   | [JE_LHC24ar_pass1_small_CJEWS19_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3551)      | [746255](https://alimonitor.cern.ch/hyperloop/train-run/746255/general) |          | `LHC24ar_fix_small/BerkeleyTrees`     | &check; |                    |            |
| [LHC25an_pass1_small](https://alimonitor.cern.ch/hyperloop/view-dataset/2763?timestamp=1787648479322)         | PbPb   | [JE_LHC25an_pass1_small_CJEWS19_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3191)      | [745909](https://alimonitor.cern.ch/hyperloop/train-run/745909/general) |          | `LHC25an_fix_small/BerkeleyTrees`     | &check; |                    |            |

### For embedding or trigger efficency studies

These datasets are true minimum-bias datasets.

1. This is done by requesting a JE derived dataset to the conveners but with the derived data selections removed; i.e. they are truly minimum-bias but with some downscaling; the factor is noted in the Downscale column.
2. There are two recommended uses:
   - Embedding: embedding MC events into these events. Eventually these datasets will be superseded by specific embedding datasets created centrally for PWG-JE.
   - Trigger efficiency: calculating trigger efficiencies for analysis triggers different to those used in the JE derived data selection.
3. Because these are not official JE derived datasets, but were done on special request to the conveners, they do not have a corresponding named JE derived dataset.

| ALICE dataset                                                                                         | System | Train                                                                   | Path                             | Hiccup? | Downscaling |
|-------------------------------------------------------------------------------------------------------|--------|-------------------------------------------------------------------------|----------------------------------|---------|-------------|
| [LHC25ae_pass2](https://alimonitor.cern.ch/hyperloop/view-dataset/2319?timestamp=1781190115262)       | OO     | [698814](https://alimonitor.cern.ch/hyperloop/train-run/698814/general) | `LHC25ae_mb/BerkeleyTrees`       | &check; | 1000        |
| [LHC25ae_pass2](https://alimonitor.cern.ch/hyperloop/view-dataset/2319?timestamp=1788793316614)       | OO     | [755324](https://alimonitor.cern.ch/hyperloop/train-run/755324/general) | `LHC25ae_mb_100/BerkeleyTrees`   | &check; | 100         |
| [LHC24ar_pass3_small](https://alimonitor.cern.ch/hyperloop/view-dataset/2584?timestamp=1787677278211) | PbPb   | [746256](https://alimonitor.cern.ch/hyperloop/train-run/746256/general) | `LHC24ar_mb_small/BerkeleyTrees` | &check; | 1000        |

### Deprecated data

These datasets have been deprecated due to bugs, more recent JE derived datasets, or updates to the BerkeleyTree format. They should only be used for specific cross-checks, and **should not be used for analysis or embedding**. They will eventually be deleted.

| ALICE dataset                                                                                            | System | JE dataset                                                                                                 | Train                                                                   | Path                     | Hiccup?                       | Reason                  |
|----------------------------------------------------------------------------------------------------------|--------|------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|--------------------------|-------------------------------|-------------------------|
| [LHC22o_pass7_minBias](https://alimonitor.cern.ch/hyperloop/view-dataset/1071?timestamp=1739209991732)   | pp     | [JE_LHC22o_pass7_CJ_R6_5_FJ_R6_5_CL_5_TT_5](https://alimonitor.cern.ch/hyperloop/view-dataset/1745)        | [346364](https://alimonitor.cern.ch/hyperloop/train-run/346364/general) |                          | `/rstorage/alice/data/LHC22o` | Old BerkeleyTree format |
| [LHC25ae_pass2](https://alimonitor.cern.ch/hyperloop/view-dataset/2319?timestamp=1773072135385)          | OO     | [JE_LHC25ae_pass2_CEWSJ10_FJ12_CL8_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3009) | [631181](https://alimonitor.cern.ch/hyperloop/train-run/631181/general) | `LHC25ae/BerkeleyTrees`  | &check;                       | Bugged pTsub selection  |
| [LHC23zzm_pass4_EMCgood](https://alimonitor.cern.ch/hyperloop/view-dataset/1286?timestamp=1733308129865) | PbPb   | [JE_LHC23zzm_pass4_Cl_8](https://alimonitor.cern.ch/hyperloop/view-dataset/1301)                           | [304817](https://alimonitor.cern.ch/hyperloop/train-run/304817/general) | `LHC23zzm/BerkeleyTrees` |                               | Old BerkeleyTree format |
| [LHC24ar_pass3](https://alimonitor.cern.ch/hyperloop/view-dataset/2471?timestamp=1772541722890)          | PbPb   | [JE_LHC24ar_pass3_CJEWS19_TTSig15_TTRef5](https://alimonitor.cern.ch/hyperloop/view-dataset/3014)          | [626871](https://alimonitor.cern.ch/hyperloop/train-run/626871/general) | `LHC24ar/BerkeleyTrees`  | &check;                       | Bugged pTsub selection  |

## MC (central)

A list of central MC productions from ALICE that are available on Perlmutter and Hiccup.

1. All simulations use Pythia 8 pp. For Pb-Pb and OO, this pp MC should be embedded in minimum-bias data (see the section on [embedding](#for-embedding-or-trigger-efficency-studies)). All simulations have continuous weighting with oversampling power 4 and reference 10 GeV.
2. A full list of PWG-JE productions can be found on [this spreadsheet](https://docs.google.com/spreadsheets/d/1zsD_StvPqN2-7dOlfN9W03TB4Opj9EwdrBQHOQi3ViU/edit?gid=1990835816#gid=1990835816).
3. All paths in the Path column should be prepended by `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/mc_central` for Perlmutter, and `/rstorage/alice/run3/mc_central` for Hiccup.

### Standard BerkeleyTree format

These datasets were converted via the [berkeleyTreeProducer.cxx](https://github.com/AliceO2Group/O2Physics/blob/master/PWGJE/TableProducer/berkeleyTreeProducer.cxx) analysis task in O2Physics and run on Hyperloop.

1. We have a centralized [Hyperloop analysis ticket](https://alimonitor.cern.ch/hyperloop/view-analysis/51612) for our conversions. Contact Tucker if you would like to be added as an analyzer to run trains.
2. Check the linked train to see the settings used for the conversion (e.g. event and track selections).
   - Generally, the event selection is set to the minimal `selMC` so additional selections should be placed on analysis level as appropriate.
   - The default track selection is global tracks.

| Dataset                                                                                    | Anchor              | Pass | System | Type | JIRA                                               | Train                                                                   | Path                             | Hiccup? | Notes                                                        |
|--------------------------------------------------------------------------------------------|---------------------|------|--------|------|----------------------------------------------------|-------------------------------------------------------------------------|----------------------------------|---------|--------------------------------------------------------------|
| [LHC26c5](https://alimonitor.cern.ch/hyperloop/view-dataset/3020?timestamp=1788418920264)  | 2024 pp ref (ap+aq) | 1    | pp     | JJ   | [O2-6744](https://its.cern.ch/jira/browse/O2-6744) | [752323](https://alimonitor.cern.ch/hyperloop/train-run/752323/general) | `LHC26c5_HLtest1/BerkeleyTrees`  |         |                                                              |
| [LHC25a2b](https://alimonitor.cern.ch/hyperloop/view-dataset/1998?timestamp=1788868861955) | LHC22o              | 7    | pp     | JJ   | [O2-5654](https://its.cern.ch/jira/browse/O2-5654) | [755946](https://alimonitor.cern.ch/hyperloop/train-run/755946/general) | `LHC25a2b_HYL/BerkeleyTrees`     |         |                                                              |
| [LHC25a2b](https://alimonitor.cern.ch/hyperloop/view-dataset/1998?timestamp=1789473662506) | LHC22o              | 7    | pp     | JJ   | [O2-5654](https://its.cern.ch/jira/browse/O2-5654) | [760547](https://alimonitor.cern.ch/hyperloop/train-run/760547/general) | `LHC25a2b_wtuner/BerkeleyTrees`  |         | With track tuner                                             |
| LHC26b6                                                                                    | LHC25ae             | 1    | OO     | JJ   | [O2-6660](https://its.cern.ch/jira/browse/O2-6660) |                                                                         |                                  | &check; | OK to use with pass2 data (diff w.r.t pass1 is only ZDC/TOF) |
| [LHC26a7](https://alimonitor.cern.ch/hyperloop/view-dataset/2878?timestamp=1788415309278)  | 2024 Pb-Pb (ar+as)  | 3    | PbPb   | JJ   | [O2-6633](https://its.cern.ch/jira/browse/O2-6633) | [752293](https://alimonitor.cern.ch/hyperloop/train-run/752293/general) | `LHC26a7_10pc_HYL/BerkeleyTrees` |         | 10% QA sample                                                |

### Alternative formats

Below are some other conversions, usually done locally. These conversions do not necessarily have a standardized TTree format, directory structure, or event/track selections, so using them may require changes to analysis code. Some will eventually be deleted.

| Dataset  | Anchor              | Pass | System | Type | JIRA                                               | Path                                                                                  | Notes                                          |
|----------|---------------------|------|--------|------|----------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------------------------|
| LHC26c5  | 2024 pp ref (ap+aq) | 1    | pp     | JJ   | [O2-6744](https://its.cern.ch/jira/browse/O2-6744) | `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/mc_central/LHC26c5`      |                                                |
| LHC25a2b | LHC22o              | 7    | pp     | JJ   | [O2-5654](https://its.cern.ch/jira/browse/O2-5654) | `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/mc_central/LHC25a2b`     | Old format                                     |
| LHC25a2b | LHC22o              | 7    | pp     | JJ   | [O2-5654](https://its.cern.ch/jira/browse/O2-5654) | `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/mc_central/LHC25a2b_new` | Old format                                     |
| LHC26b6  | LHC25ae             | 1    | OO     | JJ   | [O2-6660](https://its.cern.ch/jira/browse/O2-6660) | `/rstorage/alice/run3/mc_central/LHC26b6`                                             | On Hiccup                                      |
| LHC26a7  | 2024 Pb-Pb (ar+as)  | 3    | PbPb   | JJ   | [O2-6633](https://its.cern.ch/jira/browse/O2-6633) | `/global/cfs/cdirs/alice/alicepro/hiccup/rstorage/alice/run3/mc_central/LHC26a7_10pc` | Also on Hiccup (remove up to `hiccup` in path) |

## MC (fast simulation)

Fast simulation events saved to disk. These events contain generated events and a parametrized version of the Run 3 detector response to approximate a corresponding reconstructed event.

There are currently no Run 3-based fast simulations available.

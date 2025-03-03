Preliminary code and results related to mapping regulatory elements; currently not aimed at any use beyond the lab.

Work-in-progress documentation:
- [Description of the software environment (INSTALL.md)](INSTALL.md)
- [Running the processing pipeline (batch/README.md)](batch/README.md)
- [Step-by-step description of the standard processing (processed_tracks/README.md)](processed_tracks/README.md)
- [Notes on how the internal processing is organised](workflows/README.md)

## Notes
- Genomic coordinates are in [`WBcel215/ce10`](http://hgdownload.soe.ucsc.edu/goldenPath/ce10/bigZips/) ([`WS220`](https://github.com/WormBase/website/issues/2003)), except where explicitly stated otherwise
- Gene annotations are a subset of WS260 with coordinates backlifted to `WBcel215/ce10` ([`WS260_ce10`](/WS260_ce10))
- Abbreviations used when describing column names:
    - `%stage` quantities defined for multiple stages(/strains):
        - development: `wt_emb`, `wt_l1`, `wt_l2`, `wt_l3`, `wt_l4`, `wt_ya`
        - aging: `glp1_d1`, `glp1_d2`, `glp1_d6`, `glp1_d9`, `glp1_d13`, ...
    - `%rep` quantities defined separately in two biological replicates: `rep1`, `rep2`
    - `%strand` strand-specific quantity represented by two columns with `%strand` either set to `fwd` or `rev`
- .bed-files are formatted as [BED9](https://genome.ucsc.edu/FAQ/FAQformat.html#format1); 4th column (name field) is often used to store/visualise additional quantities (e.g. stage-specific annotations) using the [IGV gffTags option](https://software.broadinstitute.org/software/igv/TrackLine)

# Batch processing
Primary processing -- alignment, coverage tracks, peak calling, etc -- is done in `snakemake`.

1. [Download](https://www.continuum.io) and install anaconda or miniconda, python 3.x (=not 2.x)

2. Create a separate environment called `relmapping` with the necessary packages:
  ```bash
  conda create --name relmapping -c bioconda -c conda-forge \
      'python > 3' 'bwa < 0.7' \
      samtools fastx_toolkit trim-galore seqtk idr ucsc-bedgraphtobigwig \
      ucsc-bigwigtobedgraph ucsc-bigwiginfo git git-lfs htseq pyBigWig weblogo \
      twobitreader matplotlib-venn wiggletools snakemake pybedtools scikit-learn ipython
  ```

3. Clone the pipeline repository into `~/relmapping`:
  ```bash
  git clone https://github.com/jurgjn/relmapping.git
  ```

4. Activate the environment:
  ```bash
  source activate relmapping
  ```

5. One can then submit batch jobs using `snakemake` by, at minimum, specifying `--cluster sbatch` and the number of jobs (test by adding `--dry-run`), e.g.:
  ```bash
  snakemake --cluster sbatch --jobs NCORES batch --use-conda -n
  ```

6. These two aliases (for `~/.bash_aliases`) add a few things, such as logging in sensible places :
  ```bash
  alias smj="snakemake --cluster 'sbatch -o $HOME/relmapping/logs/slurm_%j_%N.out.txt -e $HOME/relmapping/logs/slurm_%j_%N.err.txt' --use-conda --jobs "   
  alias smc="snakemake --use-conda --cores "
  ```
`smc` runs `RULE` on the head node:
  ```bash
  smc NCORES RULE
  ```
and `smj` runs `RULE` in batch mode:
  ```bash
  smj NCORES RULE
  ```
(also, add `-n` or `--dry-run` for testing a command)...

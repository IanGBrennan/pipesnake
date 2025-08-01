---
title: Tutorial I
weight: 1
---


## Running Test Data

You can simultaneously download the pipeline and run a test example with a single command. 

<details>
<summary>Using Docker</summary>
   
```
nextflow run ausarg/pipesnake -profile test,docker --outdir <OUTDIR>
```

</details>

<details>
<summary>Using Singularity</summary>

If you are using `singularity`, first use [`nf-core download`](https://nf-co.re/tools/#downloading-pipelines-for-offline-use) to download the singularity images for the necessary software before running the pipeline. If you don't already have `nf-core` ([`nf-core/tools`](https://nf-co.re/tools)) installed, you can do that easily in a variety of ways (e.g. conda, pip, etc), [see here](https://nf-co.re/tools#installation). 

   ```
   nf-core download ausarg/pipesnake
   ```
Once you have installed `pipesnake` with `nf-core` you can run the test. 
   ```
   nextflow run ausarg/pipesnake -profile test,singularity --outdir <OUTDIR>
   ```
</details>

### Results

The test data should complete in just a few minutes.  
`-profile test` limits usage to 2 CPU and 8 Gb of memory (you can change this in the `conf/test.config` file). 

Great. Once it has completed, we can check out all the outputs. There should be 13 directories in your specified output directory. Importantly, your species tree will be in `aster`, your trimmed alignments in `clipkit`, and sample-specific fasta files of assembled targets are in `make`.  

<details>
<summary>Results Directories</summary>

|  directory   |  outputs   |
|  ----------|------------   |
|  **assembly**/  | `.fasta` files for each of the four samples containing *all* assembled contigs
|  **aster**/  | the output species tree as estimated from hybrid weighted ASTRAL
|  **clipkit**/  | trimmed multiple sequence alignments
|  **combine**/  | a `.csv` file of the pre- and post-trimming alignment statistics
|  **mafft**/  | basic multiple sequence alignments resulting from `mafft`
|  **make**/  | pseudo-reference genome (PRG) `.fasta` files for each sample containing only the best matched contig for each target
|  **merge**/  | all locus trees concatenated into a single file
|  **pipeline_info**/  | `.yml` file of all software used with versions specified
|  **raxml**/  | output files of RAxML phylogenetic estimation for each locus
|  **read**/  | read depth statistics for each sample and locus for the best matched contig
|  **segul**/  | pre-trimmed alignment and taxon summaries from `SEGUL`
|  **segul2**/  | post-trimmed alignment and taxon summaries from `SEGUL`
|  **spades**/  | `SPAdes` output

</details>

\***Note**: the names of some directories will change if you specify different software. E.g. if you choose to estimate locus trees with `IQTREE` by flagging `--tree_method iqtree`, then your trees will be in a directory called `iqtree` instead of `raxml`. 

### Monitoring Usage
We can find more information on our run in the `tracing/pipeline_info` directory, which should be in the same place as your specified output. For each ***pipesnake*** run, there should be four outputs.

<details>
<summary>Run Statistics</summary>

|  file   |  content   |
|  ----------|------------   |
| **execution_trace**_\<...>.txt | tab-delimited text file of all run stats|
| **execution_report**_\<...>.html | nextflow graphical workflow report |
| **execution_timeline**_\<...>.html | process-specific timeline |
| **pipeline_dag**_<...>.html | directed acyclic graph of all workflow processes|

</summary>
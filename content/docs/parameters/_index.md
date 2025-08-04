---
title: Parameters
weight: 3
sidebar:
  open: false
---

A typical `pipesnake` command might rely on the predetermined parameters in the `conf/base.config` file, but there are *many* parameters we can change to fit the workflow to our needs. We outline all available parameters in the [parameters-usage](https://github.com/AusARG/pipesnake/blob/main/docs/usage.md) file, but below we highlight a limited number that are most likely to be of broad interest. 

---

<details>
<summary>Required pipesnake Parameters</summary>

## Required pipesnake Parameters

| Required Parameter       | Type |  Description  |
|---------------|:---------------:|---------------------|
| \--input   | string |   Path to comma-separated file containing information about the samples in the experiment.
| \--outdir  | string |   The output directory where the results will be saved. <br/> You <u>must</u> use absolute paths to store on Cloud infrastructure. |
| \--blat_db   | string | Path to a FASTA file of the target loci sequences.|

</details>

---

<details>
<summary>Optional pipesnake Parameters</summary>

## Optional pipesnake Parameters

| Optional Parameter       | Type |  Description  |
|---------------|:---------------:|---------------------|
| \--filter | string | Path to the filter sequences FASTA file. <br/> Only if `--disable_filter false`.|
| \--tree_method  | string | Default is `raxml`.<br /> The supported options are: `iqtree` or `raxml`. <br/> Both methods should offer qualitatively identical results. | 
| \--assembly | string | Default is `SPAdes`.<br /> Supported software options for contig assembly are: `trinity` or `SPAdes`.<br /> SPAdes is generally <u>considerably</u> faster, but results should be comparable. Trinity is retained for consistency with existing phylogenomic projects. |
| \--trim_method  | string | Default is `clipkit`.<br /> Trims initial MAFFT alignments. The supported options are `clipkit`, `trimal`, `gblocks`, or `none`. <br/> For methods other than `none`, there are are a number of additional tuneable parameters (e.g. see [Usage](https://github.com/AusARG/pipesnake/blob/main/docs/usage.md) for more details). |
| \--batching_size  | integer |  Default is `250`.<br /> Number of files to be processed sequentially in batches <br/> to avoid submitting a large number of jobs when using HPCs. | 
| \--trinity_scratch_tmp  | boolean |  Default is `true`.<br /> Trinity generates large number of intermediate files. <br/>This can be an issue for some HPCs that limits the file number for each user.<br/> This option will make trinity writes to the `/tmp` directory on the compute node <br/> then copy the compressed output directory (not the fasta) to the working directory to avoid this issue. |  
|\--phylogeny_make_alignments_minsamp|`integer`|Default is `4` <br/>Minimum number of samples to constitute an alignment <br/> Some phylogeny building methods rely on a minimum number of samples in an alignment. <br/> E.g. to estimate bootstraps for a genetree (IQTREE/RAxML) or include a genetree in an ASTRAL analysis, the minimum number of samples is 4.
|\--make_rgb_kept_tags|`string`|Default is `easy_recip_match,complicated_recip_match` <br/> ***easy_recip_match***: 1-to-1 unique match between contig and targeted locus <br/> ***complicated_recip_match***: 1-to-1 non-unique match, in which one targeted locus matches to multiple contigs <br/> if you'd like a stricter search (fewer, more-reliable matches) use `--make_rgb_kept_tags easy_recip_match` only.|
|\--stage|`string`|Default is `from-start` <br/> ***from-start***: runs pipeline from raw data (fastq.gz) through to end <br/> ***from-prg***: runs pipeline from PRGs through to end <br/> ***end-prg***: ends a run after generating sample specific PRG files <br/> ***end-alignment***: ends a run after generating locus alignment files <br/> ***start-alignment***: runs pipeline from user specified alignment files through to end <br/> For more info about running the pipeline from the start or the middle see [Tutorials I-IV](https://iangbrennan.github.io/pipesnake2/docs/tutorials/)|

<!-- --disable_filter  | boolean | Default is `true`.<br />Disable bbmap filtration process. <br/> When enabled (`--disable_filter false`), the `--filter` parameter is required. <br/> Consider the tradeoff between filtering reads (`--disable_filter false`; slow mapping of reads to reference sequences, faster contig assembly) versus not filtering reads (`--disable_filter true`; no read mapping, slower contig assembly). -->

</details>

---

<details>
<summary>Optional Nextflow Parameters</summary>

## Optional Nextflow Parameters

| Optional Parameter       | Type |  Description  |
|---------------|:---------------:|---------------------|
|-resume|`string`|Will resume an interrupted run by using cached results in the working directory.|
|-c|`string`|Specifies a configuration file for preferred system specifications.|
|-work-dir|`string`|Default is the current directory. <br/> Specifying an alternate working directory can be useful on HPC systems to avoid storage limits on shared drives.|

</details>
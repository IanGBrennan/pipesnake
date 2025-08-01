---
title: Tutorial III
weight: 3
---


## Start/Stop at PRG

One benefit to using ***pipesnake*** is its flexibility. In this tutorial we'll practice running the pipeline to stop when we have completed making pseudo-reference genomes (PRG) for each sample, and also picking up from a set of PRG files. 

<details>
<summary>--stage end-prg</summary>

## --stage end-prg

Imagine we're collecting data for a project, but we don't yet have data for all the samples we hope to sequence. We can run ***pipesnake*** to generate fasta files of assembled data per sample, but stop short of the labor intensive steps of alignment and gene tree estimation. 

We can tell ***pipesnake*** to stop once we have generated the PRG files for each sample using the `--stage` flag and specifying `--stage end-prg`.

```
run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo.csv --blat_db data/ToyData_SqCL_25Targets.fasta --stage end-prg --outdir ToyData_end-prg
```

Importantly your PRG files will be in the `make/` directory!

</details>

<details>
<summary>--stage from-prg</summary>

## --stage from-prg

Now imagine we've collected all our data, and want to include some from a previous project. We can run ***pipesnake*** on already assembled molecular data in the form of PRG files. This skips the slow steps of reassembling our data, but will carry us through alignment, gene tree estimation, and provide us a species tree. 

One important thing here is that our `--input` sample sheet is no longer valid. We need to create one that tells us the paths to the assembled fasta files. It needs to look like this:

| sample_id  | prg_file  |
| ---------  | -----  | 
| Sample1 | <PATH>/Sample1.fasta |
| Sample2 | <PATH>/Sample2.fasta |
| Sample3 | <PATH>/Sample3.fasta |
| Sample4 | <PATH>/Sample4.fasta | 

Luckily we have a premade version of this in `data/ToyData_SampleInfo_PRG.csv`. So let's just run the whole thing.

```
nextflow run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo_PRG.csv --blat_db data/ToyData_SqCL_25Targets.fasta --stage from-prg --outdir ToyData_from-pr
```

However, if you need to generate one of these for a lot of files, there's a script available in `bin/generate_sample_info.py`. Note, to run properly your samples will need to have `PRG_` prefixed to their file names (e.g. PRG_Delma.fasta). 

```
./bin/generate_sample_info.py PRG_SampleInfo.csv from-prg --prg_dir <path_to_prgs>
```

As in other instances, this will output alignments (`mafft/`), gene trees (`raxml/`), and the species tree (`aster/`)

</details>

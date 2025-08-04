---
title: Tutorial IV
weight: 4
---


## Start/Stop at Alignments

In addition to starting/stopping at the assembled PRG stage, users may also be interested in stopping after alignments are made (but before estimating locus trees), or providing alignments as a starting point. In this tutorial we'll practice running the pipeline to stop when we have completed making alignments for each locus, and also picking up from a set of multiple sequence alignment files. 

___

<details>
<summary>--stage end-alignment</summary>

## --stage end-alignment

Maybe we want to assemble our data and generate alignments but aren't ready to take the plunge and estimate locus trees. This might be because we have a specific alignment protocol or method that we want to implement. To do that, we can run ***pipesnake*** to generate multiple sequence alignment files. 

We can tell ***pipesnake*** to stop once we have generated the alignments for each locus using the `--stage` flag and specifying `--stage end-alignment`.

```
run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo.csv --blat_db data/ToyData_SqCL_25Targets.fasta --stage end-alignment --outdir ToyData_end-aln
```

The basic alignment files will be in the `mafft/` directory. If you would like to trim the alignments before exiting the pipeline, use `--trim_method`, e.g. `--trim_method clipkit`. 

```
run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo.csv --blat_db data/ToyData_SqCL_25Targets.fasta --stage end-alignment --outdir ToyData_end-aln-clip --trim_method clipkit
```

</details>

___

<details>
<summary>--stage from-alignment</summary>

## --stage from-alignment

Now imagine we've inspected and processed our alignments outside of the pipeline, but want to finish off the analyses and estimate locus trees. We can run ***pipesnake*** on already aligned sequence data by providing alignment files. This skips the slow steps of reassembling our data and aligning them, but will carry us through gene tree estimation and provide us a species tree. 

One important thing here is that our `--input` sample sheet is no longer valid. We need to create one that tells us the paths to the aligned fasta files. It needs to look like this:

| alignment_file  | 
| ---------  | 
| example/data/ToyData_Alignments/uce-4443.fasta.aln | 
| example/data/ToyData_Alignments/AHE-L208.fasta.aln | 
| example/data/ToyData_Alignments/gene-GALR1.fasta.aln | 
| example/data/ToyData_Alignments/uce-5673.fasta.aln | 

Luckily we have a premade version of this in `example/data/ToyData_SampleInfo_Aln.csv`. So let's just run the whole thing.

```
nextflow run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo_Aln.csv --blat_db data/ToyData_SqCL_25Targets.fasta --stage from-alignment --outdir ToyData_from-aln
```

As in other instances, this will output gene trees (`raxml/`) and the species tree (`aster/`).

<details>
<summary>need to generate an --input?</summary>

If you need to generate an input .csv for a lot of files, there's a script available in `bin/generate_sample_info.py`. 

```
python ./bin/generate_sample_info.py Aln_SampleInfo.csv from-alignment --alignment_dir <path_to_alignments>

```
</details>


</details>
